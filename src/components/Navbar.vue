<template>
    <nav>
        <v-app-bar color="blue" dark app>
            <v-app-bar-nav-icon @click.stop="drawer = !drawer">

            </v-app-bar-nav-icon>
            <v-toobal-title class="text-uppercase">
                <span class="font-weight-light">DASH</span>
                <span>Dashboard</span>
            </v-toobal-title>
            <v-spacer></v-spacer>
            <div class="text-center">
                <v-menu offset-y>
                    <template v-slot:activator="{ on }">
                        <v-btn text v-on="on"><i class="fab fa-user"></i>Menu</v-btn>
                    </template>  
                    <v-list flat>
                        <v-list-item v-for="link in links" :key="link.text" router :to="link.route" active-class="border">
                            <v-list-item-title> {{ link.text }} </v-list-item-title>
                        </v-list-item>
                    </v-list>      
                </v-menu>
            </div>
            
            <v-btn text>
                <span>Exit</span>
                <v-icon right></v-icon>
            </v-btn>
        </v-app-bar>
        <v-navigation-drawer v-model="drawer" dark app class="blue darken-4">
            <v-layout column align-center>
                <v-flex class="mt-5">
                    <v-avatar size="100">
                        <v-img src="/img1.png"></v-img>
                    </v-avatar>
                    <p class="white--text subheading mt-1 text-center">Username</p>
                </v-flex>
                <v-flex class="mt-4 mb-4">
                    <Popup />
                </v-flex>
            </v-layout>
            <v-list flat>
                <v-list-item v-for="link in links" :key="link.text" router :to="link.route" active-class="border">
                    <v-list-item-content>
                        <v-list-item-title>{{ link.text }}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>

<script>

import Popup from'./Popup'
export default {
    data: () => ({
        drawer: true,
        links: [
            {icon: 'dashboard', text: 'Dashboard', route:'/'},
            {icon: 'folder', text: 'My Project', route: '/projects'},
            {icon: 'person', text: 'Team', route: '/team'},

        ]
    }),
    components: {
        Popup
    }
}
</script>

<style scoped>
    .border {
        border-left: 4px solid #fff;
    }
</style>