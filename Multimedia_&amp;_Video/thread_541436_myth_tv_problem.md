---
title: "myth tv problem"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by blue4paper on 2007-09-02
Yes, when i click watch tv on myth tv it says "cannot connect to backend - check your ip" ( it isn't word for word but similar). I'm guessing this is because i dont have a tv tuner card? but i do have "ultratv" which is what i use for my windows (i'm on a dual boot) is there anyway to connect ultratv usb with mythtv? i tried  wine for ultratv but when i clicked on the exe nothing happens and wine is pretty buggy.

---

### Post by blue4paper on 2007-09-02
Alright word for word what it says when i try to watch or click on server statu. "Could not connect to the master backend server -- is it rrunning? is the ip address set for it in the setup program correct?"

Anyone know how to set the ip adress up? or connect to master backend server. The ip im' using is 127.0.0.1

---

### Post by PilotJLR on 2007-09-02
MythTV is a great app, but it can be a challening install for people new to Linux... you'll need to do some reading to get up to speed on it.
Start here for a nice install guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Basically, first run "mythtv-setup", and then "sudo /etc/init.d/mythtv-backend start" to start the backend server referenced in your error message.

---

### Post by bowmanr@mailcity.com on 2007-09-03
Following on from PilotJLR, you /may/ need to check the contents of :

'/var/logs/mythtv/mythbackend.log'

You'll potentially need to review this log file AFTER the 'mythtv-setup' and 'sudo /etc/init.d/mythtv-backend start' commands.

---

### Post by blue4paper on 2007-09-03
Alright when i ran the command "sudo /etc/init.d/mythtv-backend start" it said backend was already running. When i tried clicking "watch tv" it still said "Could not connect to the master backend server -- is it rrunning? is the ip address set for it in the setup program correct?"

Here is the log for "/var/logs/mythtv/mythbackend.log"

2007-09-01 12:38:19.682 Using runtime prefix = /usr
2007-09-01 12:38:19.761 New DB connection, total: 1
2007-09-01 12:38:19.774 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:38:19.779 Current Schema Version: 
2007-09-01 12:38:19.878 Newest Schema Version : 1160
2007-09-01 12:38:19.882 New DB connection, total: 2
2007-09-01 12:38:19.883 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:38:19.886 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-09-01 12:38:19.888 New DB connection, total: 3
2007-09-01 12:38:19.889 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:38:19.891 Inserting MythTV initial database information.
2007-09-01 12:38:19.894 New DB connection, total: 4
2007-09-01 12:38:19.895 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:38:19.896 Upgrading to schema version 1112
2007-09-01 12:38:20.127 New DB connection, total: 5
2007-09-01 12:38:20.128 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:38:20.130 Upgrading to schema version 1113
2007-09-01 12:38:20.131 Upgrading to schema version 1114
2007-09-01 12:38:20.132 Upgrading to schema version 1115
2007-09-01 12:38:20.135 Upgrading to schema version 1116
2007-09-01 12:38:20.137 Upgrading to schema version 1117
2007-09-01 12:38:20.140 Upgrading to schema version 1118
2007-09-01 12:38:20.145 Upgrading to schema version 1119
2007-09-01 12:38:20.146 Upgrading to schema version 1120
2007-09-01 12:38:20.149 Upgrading to schema version 1121
2007-09-01 12:38:20.150 Upgrading to schema version 1122
2007-09-01 12:38:20.153 Upgrading to schema version 1123
2007-09-01 12:38:20.156 Upgrading to schema version 1124
2007-09-01 12:38:20.159 Upgrading to schema version 1125
2007-09-01 12:38:20.164 Upgrading to schema version 1126
2007-09-01 12:38:20.167 Upgrading to schema version 1127
2007-09-01 12:38:20.171 Upgrading to schema version 1128
2007-09-01 12:38:20.174 Upgrading to schema version 1129
2007-09-01 12:38:20.180 Upgrading to schema version 1130
2007-09-01 12:38:20.182 Upgrading to schema version 1131
2007-09-01 12:38:20.185 Upgrading to schema version 1132
2007-09-01 12:38:20.188 Upgrading to schema version 1133
2007-09-01 12:38:20.190 Upgrading to schema version 1134
2007-09-01 12:38:20.192 Upgrading to schema version 1135
2007-09-01 12:38:20.196 Upgrading to schema version 1136
2007-09-01 12:38:20.200 Upgrading to schema version 1137
2007-09-01 12:38:20.202 Upgrading to schema version 1138
2007-09-01 12:38:20.204 Upgrading to schema version 1139
2007-09-01 12:38:20.212 Upgrading to schema version 1140
2007-09-01 12:38:20.213 Upgrading to schema version 1141
2007-09-01 12:38:20.218 Upgrading to schema version 1142
2007-09-01 12:38:20.220 Upgrading to schema version 1143
2007-09-01 12:38:20.223 Upgrading to schema version 1144
2007-09-01 12:38:20.225 Upgrading to schema version 1145
2007-09-01 12:38:20.227 Upgrading to schema version 1146
2007-09-01 12:38:20.228 Upgrading to schema version 1147
2007-09-01 12:38:20.233 Upgrading to schema version 1148
2007-09-01 12:38:20.238 Upgrading to schema version 1149
2007-09-01 12:38:20.241 Upgrading to schema version 1150
2007-09-01 12:38:20.242 Upgrading to schema version 1151
2007-09-01 12:38:20.247 Upgrading to schema version 1152
2007-09-01 12:38:20.250 Upgrading to schema version 1153
2007-09-01 12:38:20.254 Upgrading to schema version 1154
2007-09-01 12:38:20.260 Upgrading to schema version 1155
2007-09-01 12:38:20.295 Upgrading to schema version 1156
2007-09-01 12:38:20.298 Upgrading to schema version 1157
2007-09-01 12:38:20.300 Upgrading to schema version 1158
2007-09-01 12:38:20.307 Upgrading to schema version 1159
2007-09-01 12:38:20.310 Upgrading to schema version 1160
2007-09-01 12:38:20.311 Database Schema upgrade complete, unlocking.
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 12:40:18.014 Using runtime prefix = /usr
2007-09-01 12:40:18.465 New DB connection, total: 1
2007-09-01 12:40:18.579 Connected to database 'mythconverg' at host: localhost
2007-09-01 12:40:18.824 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 16:29:13.714 Using runtime prefix = /usr
2007-09-01 16:29:14.306 New DB connection, total: 1
2007-09-01 16:29:14.380 Connected to database 'mythconverg' at host: localhost
2007-09-01 16:29:14.574 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 16:32:34.085 Using runtime prefix = /usr
2007-09-01 16:32:34.107 New DB connection, total: 1
2007-09-01 16:32:34.115 Connected to database 'mythconverg' at host: localhost
2007-09-01 16:32:34.119 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 17:23:13.800 Using runtime prefix = /usr
2007-09-01 17:23:14.118 New DB connection, total: 1
2007-09-01 17:23:14.127 Connected to database 'mythconverg' at host: localhost
2007-09-01 17:23:14.177 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 19:47:44.594 Using runtime prefix = /usr
2007-09-01 19:47:44.771 New DB connection, total: 1
2007-09-01 19:47:44.804 Connected to database 'mythconverg' at host: localhost
2007-09-01 19:47:44.871 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-01 21:22:51.185 Using runtime prefix = /usr
2007-09-01 21:22:51.376 New DB connection, total: 1
2007-09-01 21:22:51.404 Connected to database 'mythconverg' at host: localhost
2007-09-01 21:22:51.420 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-02 12:30:26.385 Using runtime prefix = /usr
2007-09-02 12:30:26.568 New DB connection, total: 1
2007-09-02 12:30:26.596 Connected to database 'mythconverg' at host: localhost
2007-09-02 12:30:26.614 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-02 13:44:39.842 Using runtime prefix = /usr
2007-09-02 13:44:40.089 New DB connection, total: 1
2007-09-02 13:44:40.109 Connected to database 'mythconverg' at host: localhost
2007-09-02 13:44:40.127 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-02 17:24:57.355 Using runtime prefix = /usr
2007-09-02 17:24:57.588 New DB connection, total: 1
2007-09-02 17:24:57.624 Connected to database 'mythconverg' at host: localhost
2007-09-02 17:24:57.640 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-03 10:43:27.312 Using runtime prefix = /usr
2007-09-03 10:43:27.570 New DB connection, total: 1
2007-09-03 10:43:27.594 Connected to database 'mythconverg' at host: localhost
2007-09-03 10:43:27.605 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-03 10:47:54.285 Using runtime prefix = /usr
2007-09-03 10:47:54.312 New DB connection, total: 1
2007-09-03 10:47:54.320 Connected to database 'mythconverg' at host: localhost
2007-09-03 10:47:54.326 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-09-03 10:48:31.174 Using runtime prefix = /usr
2007-09-03 10:48:31.190 New DB connection, total: 1
2007-09-03 10:48:31.197 Connected to database 'mythconverg' at host: localhost
2007-09-03 10:48:31.201 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

---

### Post by blue4paper on 2007-09-03
Actually, i sorta got it to work. I changed the ip's. Now it says "mythtv is already using all available inputs for the channel you selected. If you want to watch an in-progress recording, select one from the playback menu. If you want to watch live TV, cancel one of the in-progress recordings from the delete menu." I want to watch live tv

---

### Post by Chaos5lw on 2007-09-03
Are you running "mythbackend"? Open a terminal and type "mythbackend" followed by enter and then try opening the frontend again.

---

### Post by bowmanr@mailcity.com on 2007-09-04
Just to check :

* Did enable your capture card(s)? 
* Have you configured your inputs on your capture card(s)?
* Did you configure channels in mythtv-setup? 
* Have you sorted your listings grabber? 
* Have you attached your listings to the appropriate capture card input? 

( All done in 'mythtv-setup' )

All this needs to be done before even trying mythfrontend. MythTV is great, but a little complex to configure. Not for casual use!!

Please send your mythbackend.log now that you can get the frontend to log in. Make sure this is sent ONCE you've attempted to watch LiveTV.

Thanks

---

### Post by blue4paper on 2007-09-04
just a quick question, do i need any hardware? or can mythtv really work with everything you already have?

---

### Post by blue4paper on 2007-09-04
actually is it possible to  use my ultratv USB 300 on ubuntu?

---

### Post by bowmanr@mailcity.com on 2007-09-06
try searching for 'ultratv USB 300 linux driver'. if there's a driver, there's a chance it'll work with mythtv.

have to say, i could not find any evidence of a linux driver witha  cursory glance ... but i don't know the product range. is it using another brand chipset? if so, you may find the chipset itself is supported as packaged in that another brand.

---

