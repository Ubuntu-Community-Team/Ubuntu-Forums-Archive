---
title: "Does anyone else find Mythtv to be impossible to get going?"
date: 2008-10-20
forum: Multimedia Software
---

### Post by sofasurfer on 2008-10-20
I have read all the how-tos and manuals and I am not able to get Mythtv to do anything for me? It seems that everything I read is written with the assumption that a new user already has some built-in understanding of the terminology and processes involved.

I did finally manage to get it to when I click on "watch tv" I got a screen that said that the backend needed to be started. But I have no idea how I got that far and I can't get it to do that again.

Are there any tutorials geared toward someone who just fell off the turnip truck? Or a secret tip that makes everything fall into place?

Help in Michigan. Thanks?

---

### Post by Afkpuz on 2008-10-20
I can help.  I'll start from the top and explain terms.

Mythtv needs both a backend and a frontend to do anything.  
**Backend**-software that actually records the TV, talks to your tuner card, schedules recordings, and sends a signal to frontends on your network.
**Frontend**-Receives signal from backend and actually plays the media.  The frontend is a glorified media player.

Both backend and frontend can run on same computer.  So first, make sure you have the backend installed.  Goto System>Administration and see if there is an entry called "mythtv backend".  If not, follow these steps to install it.


Goto System>Administration>Synaptic Package Manager
Search for "myth"

look for the package "mythtv-backend" in the that list.  There also other helpful plugins that you can install to make the frontend even beefier, like themes and music plugins.  


That's where you set up your tv tuner card.  


If you did have the backend all along, then I wasted your time and all you need to do is start the backend.  Use this command


```
sudo killall mythbackend
```
then press alt+f2 and run
```
mythbackend
```

Try that.  Hope it helps

---

### Post by sofasurfer on 2008-10-20
AFKPUZ.
Thanks for your reply.
Before I get started I am going to clean up my system.
In the meantime let me ask, are you saying that you want me to only install the backend? Or will that automatically install everything else as dependancies?

I have tinkered with mythubuntu, mythtv, mythbuntu-desktop. So I request that you be specific about what you want me to install.

I just got home from work. I should have this thing ready to get working on it by the time I go to bed. Hope to hear from you tomorrow.

Thanks, Daryl

---

### Post by Afkpuz on 2008-10-20
To watch tv using mythtv, you must have both installed, so yes, install the backend.  That must be running in order to watch tv.

If you use synaptic and install "mythtv", it will install everything you need.  Then you've got to set up the backend, which I can also help you with if you so need.

---

### Post by jrogers99 on 2008-10-21
Hi,

I know what you are going through. It took me almost 6 weeks of on and off again work to get mythtv working with my setup. I even tried 3 different linux distros.

The best one I found was mythtv with ubuntu. The guide I used which has great steps for getting it going is located here: [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

This will guide you through setting up a backend and frontend on a server that is NOT dedicated (meaning you can use it for other things as well).

The main issue I had that took all the time was the setup of the drivers for the card. I have a Hauppauge WinTV-HVR-1600. If this is your card, I can walk you through getting linux to see it.

Hope this helps, and it takes you less time to get running then it took me. BTW, it was worth it.

PS - I know the guide says 7.10, but it worked perfectly for me on 8.04!

---

### Post by sofasurfer on 2008-10-22
Ok. I am going to try using the site that jrogers99 sent. I am trying his recommendation first because he has the same card that I am using... Hauppauge 1600. And this is a set of instructions that I have not tried yet. So after I go through this website I will post my results.

---

### Post by sofasurfer on 2008-10-22
I tried the link in post #5. I got an error for unable to load some package. So I went to synaptic and removed all myth packages.

Now I installed 'mythtv' with synaptic. Now when I click on system>administration>mythtv backend setup I get a message "backend must be closed before continueing. Is it ok to close backend processes". I chose 'ok'.
A ternimal window then opened for a couple seconds and the I am asked to chose a preferred language. I chose english. The next message is 'NO UPnP BACKENDS FOUND'. I click on 'ok' and 'database configuration 1/2' comes up.

What does the UPnP Backends message mean? I do have a backend in the system menu.

Before I go any further, am I doing the right stuff so far?

---

### Post by sofasurfer on 2008-10-23
Bump

---

### Post by eternalnewbee on 2008-10-23
I do. My system goes into slowmotion..

---

### Post by Dynamo_Joe on 2008-10-23
Hi sofasurfer, 

Long time no see and hope that you are keeping well! 

I've also just started my MythTV project ... just the media playback bit first as I have yet to find a comptible digital TV card for my part of the world. 

Try Parker's web site: 

[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

This is a good starter and then their is the MythTV forum here. 

Anyway, good luck and see you soon!

---

### Post by sofasurfer on 2008-10-23
Hi D_Joe. I don't recognize you. Have we spoken before? Nice to meet you anyway.

The site you recommend looks interesting I will take a better look at it tomorrow.

I can't ssem to get anything to do anything no matter what I do. But if we keep at this thread and the gurus see that many people just don't get it, I bet we'll get some help.

---

### Post by sofasurfer on 2008-10-23
I guess the 'NO UPnP BACKENDS FOUND' was simply verifying that the backend was shut down.

My localhost name is 'localhost'.There is no port setting.Database name is 'mythconverg'. Username was 'mythtv' but I changed it to 'daryl' since I am in the mythtv group. It then lists password which was also 'mythtv'. 

I think I should change it but I don't know if it wants my account password or my mysql password which I found in the 'mysql.txt' file. What should I do?

---

### Post by cariboo on 2008-10-23
When dealing with mysql always use the user name and password you setup when you installed mysql.

I have one suggestion, before you go to all the trouble of setting up MythTV, make sure your TV tuner card works first. MythTV depends on a working Tv tuner card, it will not miraculously set it up for you.

Jim

---

### Post by sofasurfer on 2008-10-23
TV Tuner card Hauppauge PXR 1600 is recognized according to dmesg cx18. Am currently using Mplayer and VLC.
Thank you for your input.

---

### Post by sofasurfer on 2008-10-23
Next to where is says "ping test server" there is a space labeled "port". Should there be anything in it?

Page 2 has these options. "Use custom identifier for frontend preferences" and "Enable database server wakeup". I think these can be left alone for now. Correct?

Now when I click the "finish" button I get this message "Cannot find (ping) database host on network. Clicking on "ok" takes my back to the first configuration page.

I can not do anything but go in circles that lead nowhere.

---

### Post by sofasurfer on 2008-10-24
Bump

---

### Post by Afkpuz on 2008-10-25
You shouldn't really need to change anything in there other than adding a TV and scanning for channels.

Although, you should check in General on the 2nd page I think.  The part about table frequency.  Mythtv defaults to us-bcast, which is the free stuff.  If you have real cable, switch that to us-cable (assuming you're in the US).  Just check the settings on that page, set up tuner/channel and you should be good.  Don't change any of the network settings unless you specifically need to.

---

### Post by bawilson2 on 2008-10-30
I've seen the errors you're getting and it is because the frontend can't connect to the backend.  There are a number of things that could be the issue.  

Are you running the frontend and the backend on the same machine? 

If you're still working on it you could try posting your /var/log/mythtv/mythbackend.log and your /var/log/mythtv/mythfrontend.log then we could check out how the backend is setup and what the frontend is trying to contact.

---

### Post by sofasurfer on 2008-11-08
bawilson2...
Thanks for your advice. Sorry I took a week to reply to you. 

Frontend and backend are on the same machine
Here is my frontend.log (followed by the backend.log)...

```

Starting mythfrontend.real..
2008-11-02 17:39:39.474 New DB connection, total: 2
2008-11-02 17:39:39.475 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:39.476 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 17:39:39.477 Enabled verbose msgs:  important general
2008-11-02 17:39:41.487 Writing settings file /home/test/.mythtv/mysql.txt
2008-11-02 17:39:41.487 Closing DB connection named 'DBManager1'
2008-11-02 17:39:41.487 Closing DB connection named 'DBManager0'
2008-11-02 17:39:41.488 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:41.497 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:39:41.498 Primary screen 0.
2008-11-02 17:39:41.499 Using screen 0, 1680x1050 at 0,0
2008-11-02 17:39:41.500 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:39:41.500 Switching to square mode (Mythbuntu-8.04)
2008-11-02 17:39:41.833 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-02 17:39:41.834 lirc_init failed for mythtv, see preceding messages
2008-11-02 17:39:41.834 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
2008-11-02 17:40:43.018 Specified base font 'medium' does not exist for font clock
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font small
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font medium
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font large
2008-11-02 17:40:43.020 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-02 17:40:43.154 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-02 17:40:43.201 Registering Internal as a media playback plugin.
2008-11-02 17:40:43.260 Upgrading to MythArchive schema version 1001
2008-11-02 17:40:43.286 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:40:43.325 Inserting MythFlix initial database information.
2008-11-02 17:40:43.325 Upgrading to MythFlix schema version 1000
2008-11-02 17:40:43.352 Upgrading to MythFlix schema version 1001
2008-11-02 17:40:43.530 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-02 17:40:43.571 Setting Up MythMovies Database Tables
2008-11-02 17:40:43.670 MythMovies Database Setup Complete
2008-11-02 17:40:43.977 Upgrading to MythMusic schema version 1007
2008-11-02 17:40:44.020 Upgrading to MythMusic schema version 1008
2008-11-02 17:40:44.156 Upgrading to MythMusic schema version 1009
2008-11-02 17:40:44.196 Upgrading to MythMusic schema version 1010
2008-11-02 17:40:44.230 Updating music_albumart image types
2008-11-02 17:40:44.232 Upgrading to MythMusic schema version 1011
2008-11-02 17:40:44.233 Upgrading to MythMusic schema version 1012
2008-11-02 17:40:44.339 Upgrading to MythMusic schema version 1013
2008-11-02 17:40:44.501 Failed to run 'cdrecord --scanbus'
2008-11-02 17:40:44.504 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-02 17:40:44.507 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-02 17:40:44.537 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-02 17:40:44.837 Inserting MythWeather initial database information.
2008-11-02 17:40:44.837 Upgrading to MythWeather schema version 1000
2008-11-02 17:40:45.054 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:40:49.354 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 17:40:49.367 Using protocol version 40
2008-11-02 17:40:58.805 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:15.125 New DB connection, total: 3
2008-11-02 17:41:15.126 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:41:15.136 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2008-11-02 17:41:22.742 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:22.742 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2008-11-02 17:41:22.742 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2008-11-02 17:41:22.748 Failed to parse a container. Ignoring.
2008-11-02 17:41:23.098 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:23.099 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:30.385 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:30.386 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2008-11-02 17:41:30.386 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2008-11-02 17:41:30.387 Failed to parse a container. Ignoring.
2008-11-02 17:41:30.729 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:30.729 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:36.640 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:50.720 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:41:58.571 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:01.589 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:05.091 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:08.986 Deleting UPnP client...
2008-11-02 17:42:08.991 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-11-02 19:07:12.448 New DB connection, total: 2
2008-11-02 19:07:12.449 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:07:12.450 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 19:07:12.450 Enabled verbose msgs:  important general
2008-11-02 19:07:14.581 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:14.582 Primary screen 0.
2008-11-02 19:07:14.582 Using screen 0, 1680x1050 at 0,0
2008-11-02 19:07:14.582 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:14.583 Switching to square mode (Mythbuntu-8.04)
2008-11-02 19:07:14.848 Using the Qt painter
2008-11-02 19:07:14.848 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-02 19:07:14.849 lirc_init failed for mythtv, see preceding messages
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font clock
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font small
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font medium
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font large
2008-11-02 19:07:16.535 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-02 19:07:16.675 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-02 19:07:16.736 Registering Internal as a media playback plugin.
2008-11-02 19:07:16.895 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-02 19:07:17.228 Failed to run 'cdrecord --scanbus'
2008-11-02 19:07:17.231 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-02 19:07:17.232 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-02 19:07:17.250 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-02 19:07:17.500 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:23.234 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 19:07:23.256 Using protocol version 40
2008-11-02 19:07:29.388 Deleting UPnP client...
2008-11-02 19:07:29.388 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-11-03 10:10:55.888 New DB connection, total: 2
2008-11-03 10:10:55.889 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:55.890 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-03 10:10:55.890 Enabled verbose msgs:  important general
2008-11-03 10:10:57.700 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-03 10:10:57.701 Primary screen 0.
2008-11-03 10:10:57.701 Using screen 0, 1680x1050 at 0,0
2008-11-03 10:10:57.702 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-03 10:10:57.702 Switching to square mode (Mythbuntu-8.04)
2008-11-03 10:10:57.990 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-03 10:10:57.990 lirc_init failed for mythtv, see preceding messages
2008-11-03 10:10:57.991 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font clock
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font small
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font medium
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font large
2008-11-03 10:11:00.247 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-03 10:11:00.393 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-03 10:11:00.450 Registering Internal as a media playback plugin.
2008-11-03 10:11:00.611 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-03 10:11:00.944 Failed to run 'cdrecord --scanbus'
2008-11-03 10:11:00.947 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-03 10:11:00.949 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-03 10:11:00.972 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-03 10:11:01.231 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
Starting mythfrontend.real..
2008-11-04 14:39:30.234 New DB connection, total: 2
2008-11-04 14:39:30.234 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:30.235 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-04 14:39:30.236 Enabled verbose msgs:  important general
2008-11-04 14:39:32.324 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-04 14:39:32.325 Primary screen 0.
2008-11-04 14:39:32.326 Using screen 0, 1680x1050 at 0,0
2008-11-04 14:39:32.326 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-04 14:39:32.326 Switching to square mode (Mythbuntu-8.04)
2008-11-04 14:39:32.544 Using the Qt painter
2008-11-04 14:39:32.544 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-04 14:39:32.544 lirc_init failed for mythtv, see preceding messages
2008-11-04 14:39:34.163 Specified base font 'medium' does not exist for font clock
2008-11-04 14:39:34.163 Specified base font 'medium' does not exist for font small
2008-11-04 14:39:34.165 Specified base font 'medium' does not exist for font medium
2008-11-04 14:39:34.165 Specified base font 'medium' does not exist for font large
2008-11-04 14:39:34.166 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-04 14:39:34.378 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-04 14:39:34.440 Registering Internal as a media playback plugin.
2008-11-04 14:39:34.601 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-04 14:39:34.932 Failed to run 'cdrecord --scanbus'
2008-11-04 14:39:34.936 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-04 14:39:34.938 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-04 14:39:34.955 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-04 14:39:35.246 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
Starting mythfrontend.real..
2008-11-08 01:20:00.732 New DB connection, total: 2
2008-11-08 01:20:00.732 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:20:00.734 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-08 01:20:00.734 Enabled verbose msgs:  important general
2008-11-08 01:20:02.682 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:02.683 Primary screen 0.
2008-11-08 01:20:02.683 Using screen 0, 1680x1050 at 0,0
2008-11-08 01:20:02.684 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:02.684 Switching to square mode (Mythbuntu-8.04)
2008-11-08 01:20:02.851 Using the Qt painter
2008-11-08 01:20:02.851 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-08 01:20:02.851 lirc_init failed for mythtv, see preceding messages
2008-11-08 01:20:04.454 Specified base font 'medium' does not exist for font clock
2008-11-08 01:20:04.454 Specified base font 'medium' does not exist for font small
2008-11-08 01:20:04.455 Specified base font 'medium' does not exist for font medium
2008-11-08 01:20:04.455 Specified base font 'medium' does not exist for font large
2008-11-08 01:20:04.456 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-08 01:20:04.607 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-08 01:20:04.662 Registering Internal as a media playback plugin.
2008-11-08 01:20:04.815 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-08 01:20:05.149 Failed to run 'cdrecord --scanbus'
2008-11-08 01:20:05.152 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-08 01:20:05.210 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-08 01:20:05.227 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-08 01:20:05.485 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:13.222 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-08 01:20:13.234 Using protocol version 40
2008-11-08 01:20:19.094 Deleting UPnP client...
2008-11-08 01:20:19.095 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

```


Here is the backend.log...

```

2008-11-02 17:39:24.578 Using runtime prefix = /usr
2008-11-02 17:39:24.683 Empty LocalHostName.
2008-11-02 17:39:24.689 Using localhost value of test-desktop
2008-11-02 17:39:24.726 New DB connection, total: 1
2008-11-02 17:39:24.839 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:24.881 Closing DB connection named 'DBManager0'
2008-11-02 17:39:24.892 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:24.895 New DB connection, total: 2
2008-11-02 17:39:25.008 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:25.177 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-02 17:39:25.568 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-02 17:39:25.810 Main::Registering HttpStatus Extension
2008-11-02 17:39:26.038 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 17:39:26.045 Enabled verbose msgs:  important general
2008-11-02 17:39:26.372 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 17:40:45.507 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 17:40:49.367 MainServer::HandleAnnounce Monitor
2008-11-02 17:40:49.423 adding: test-desktop as a client (events: 0)
2008-11-02 17:40:49.425 MainServer::HandleAnnounce Monitor
2008-11-02 17:40:49.426 adding: test-desktop as a client (events: 1)
2008-11-02 19:06:57.917 Using runtime prefix = /usr
2008-11-02 19:06:57.959 Empty LocalHostName.
2008-11-02 19:06:58.010 Using localhost value of test-desktop
2008-11-02 19:06:58.048 New DB connection, total: 1
2008-11-02 19:06:58.169 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.245 Closing DB connection named 'DBManager0'
2008-11-02 19:06:58.258 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.372 New DB connection, total: 2
2008-11-02 19:06:58.475 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.562 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-02 19:06:58.823 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-02 19:06:58.938 Main::Registering HttpStatus Extension
2008-11-02 19:06:59.028 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 19:06:59.048 Enabled verbose msgs:  important general
2008-11-02 19:06:59.196 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 19:07:23.256 MainServer::HandleAnnounce Monitor
2008-11-02 19:07:23.264 adding: test-desktop as a client (events: 0)
2008-11-02 19:07:23.265 MainServer::HandleAnnounce Monitor
2008-11-02 19:07:23.267 adding: test-desktop as a client (events: 1)
2008-11-02 19:08:18.771 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-03 10:10:41.821 Using runtime prefix = /usr
2008-11-03 10:10:41.880 Empty LocalHostName.
2008-11-03 10:10:41.915 Using localhost value of test-desktop
2008-11-03 10:10:41.952 New DB connection, total: 1
2008-11-03 10:10:42.073 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.107 Closing DB connection named 'DBManager0'
2008-11-03 10:10:42.121 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.235 New DB connection, total: 2
2008-11-03 10:10:42.337 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.632 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-03 10:10:43.333 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-03 10:10:43.350 Main::Registering HttpStatus Extension
2008-11-03 10:10:43.351 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-03 10:10:43.352 Enabled verbose msgs:  important general
2008-11-03 10:10:43.449 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-04 14:39:15.818 Using runtime prefix = /usr
2008-11-04 14:39:15.877 Empty LocalHostName.
2008-11-04 14:39:15.929 Using localhost value of test-desktop
2008-11-04 14:39:15.966 New DB connection, total: 1
2008-11-04 14:39:16.087 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.146 Closing DB connection named 'DBManager0'
2008-11-04 14:39:16.158 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.299 New DB connection, total: 2
2008-11-04 14:39:16.476 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.623 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-04 14:39:17.192 New DB connection, total: 3
2008-11-04 14:39:17.377 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:17.413 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-04 14:39:17.415 Main::Registering HttpStatus Extension
2008-11-04 14:39:17.487 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-04 14:39:17.489 Enabled verbose msgs:  important general
2008-11-04 14:39:17.521 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-04 14:40:37.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-08 01:19:47.447 Using runtime prefix = /usr
2008-11-08 01:19:47.506 Empty LocalHostName.
2008-11-08 01:19:47.513 Using localhost value of test-desktop
2008-11-08 01:19:47.545 New DB connection, total: 1
2008-11-08 01:19:47.666 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:47.701 Closing DB connection named 'DBManager0'
2008-11-08 01:19:47.714 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:47.897 New DB connection, total: 2
2008-11-08 01:19:47.925 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:48.041 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-08 01:19:48.428 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-08 01:19:48.576 Main::Registering HttpStatus Extension
2008-11-08 01:19:48.734 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-08 01:19:48.827 Enabled verbose msgs:  important general
2008-11-08 01:19:48.859 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-08 01:20:13.235 MainServer::HandleAnnounce Monitor
2008-11-08 01:20:13.243 adding: test-desktop as a client (events: 0)
2008-11-08 01:20:13.244 MainServer::HandleAnnounce Monitor
2008-11-08 01:20:13.246 adding: test-desktop as a client (events: 1)
2008-11-08 01:21:07.818 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

---

### Post by bawilson2 on 2008-11-08
> **sofasurfer said:**
> bawilson2...
Thanks for your advice. Sorry I took a week to reply to you. 

Frontend and backend are on the same machine
Here is my frontend.log (followed by the backend.log)...

```

Starting mythfrontend.real..
2008-11-02 17:39:39.474 New DB connection, total: 2
2008-11-02 17:39:39.475 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:39.476 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 17:39:39.477 Enabled verbose msgs:  important general
2008-11-02 17:39:41.487 Writing settings file /home/test/.mythtv/mysql.txt
2008-11-02 17:39:41.487 Closing DB connection named 'DBManager1'
2008-11-02 17:39:41.487 Closing DB connection named 'DBManager0'
2008-11-02 17:39:41.488 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:41.497 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:39:41.498 Primary screen 0.
2008-11-02 17:39:41.499 Using screen 0, 1680x1050 at 0,0
2008-11-02 17:39:41.500 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:39:41.500 Switching to square mode (Mythbuntu-8.04)
2008-11-02 17:39:41.833 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-02 17:39:41.834 lirc_init failed for mythtv, see preceding messages
2008-11-02 17:39:41.834 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
2008-11-02 17:40:43.018 Specified base font 'medium' does not exist for font clock
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font small
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font medium
2008-11-02 17:40:43.019 Specified base font 'medium' does not exist for font large
2008-11-02 17:40:43.020 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-02 17:40:43.154 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-02 17:40:43.201 Registering Internal as a media playback plugin.
2008-11-02 17:40:43.260 Upgrading to MythArchive schema version 1001
2008-11-02 17:40:43.286 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:40:43.325 Inserting MythFlix initial database information.
2008-11-02 17:40:43.325 Upgrading to MythFlix schema version 1000
2008-11-02 17:40:43.352 Upgrading to MythFlix schema version 1001
2008-11-02 17:40:43.530 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-02 17:40:43.571 Setting Up MythMovies Database Tables
2008-11-02 17:40:43.670 MythMovies Database Setup Complete
2008-11-02 17:40:43.977 Upgrading to MythMusic schema version 1007
2008-11-02 17:40:44.020 Upgrading to MythMusic schema version 1008
2008-11-02 17:40:44.156 Upgrading to MythMusic schema version 1009
2008-11-02 17:40:44.196 Upgrading to MythMusic schema version 1010
2008-11-02 17:40:44.230 Updating music_albumart image types
2008-11-02 17:40:44.232 Upgrading to MythMusic schema version 1011
2008-11-02 17:40:44.233 Upgrading to MythMusic schema version 1012
2008-11-02 17:40:44.339 Upgrading to MythMusic schema version 1013
2008-11-02 17:40:44.501 Failed to run 'cdrecord --scanbus'
2008-11-02 17:40:44.504 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-02 17:40:44.507 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-02 17:40:44.537 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-02 17:40:44.837 Inserting MythWeather initial database information.
2008-11-02 17:40:44.837 Upgrading to MythWeather schema version 1000
2008-11-02 17:40:45.054 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:40:49.354 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 17:40:49.367 Using protocol version 40
2008-11-02 17:40:58.805 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:15.125 New DB connection, total: 3
2008-11-02 17:41:15.126 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:41:15.136 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2008-11-02 17:41:22.742 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:22.742 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2008-11-02 17:41:22.742 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2008-11-02 17:41:22.748 Failed to parse a container. Ignoring.
2008-11-02 17:41:23.098 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:23.099 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:30.385 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-11-02 17:41:30.386 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2008-11-02 17:41:30.386 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2008-11-02 17:41:30.387 Failed to parse a container. Ignoring.
2008-11-02 17:41:30.729 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:30.729 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:36.640 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-11-02 17:41:50.720 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:41:58.571 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:01.589 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:05.091 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 17:42:08.986 Deleting UPnP client...
2008-11-02 17:42:08.991 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-11-02 19:07:12.448 New DB connection, total: 2
2008-11-02 19:07:12.449 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:07:12.450 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 19:07:12.450 Enabled verbose msgs:  important general
2008-11-02 19:07:14.581 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:14.582 Primary screen 0.
2008-11-02 19:07:14.582 Using screen 0, 1680x1050 at 0,0
2008-11-02 19:07:14.582 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:14.583 Switching to square mode (Mythbuntu-8.04)
2008-11-02 19:07:14.848 Using the Qt painter
2008-11-02 19:07:14.848 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-02 19:07:14.849 lirc_init failed for mythtv, see preceding messages
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font clock
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font small
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font medium
2008-11-02 19:07:16.534 Specified base font 'medium' does not exist for font large
2008-11-02 19:07:16.535 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-02 19:07:16.675 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-02 19:07:16.736 Registering Internal as a media playback plugin.
2008-11-02 19:07:16.895 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-02 19:07:17.228 Failed to run 'cdrecord --scanbus'
2008-11-02 19:07:17.231 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-02 19:07:17.232 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-02 19:07:17.250 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-02 19:07:17.500 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-02 19:07:23.234 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 19:07:23.256 Using protocol version 40
2008-11-02 19:07:29.388 Deleting UPnP client...
2008-11-02 19:07:29.388 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-11-03 10:10:55.888 New DB connection, total: 2
2008-11-03 10:10:55.889 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:55.890 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-03 10:10:55.890 Enabled verbose msgs:  important general
2008-11-03 10:10:57.700 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-03 10:10:57.701 Primary screen 0.
2008-11-03 10:10:57.701 Using screen 0, 1680x1050 at 0,0
2008-11-03 10:10:57.702 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-03 10:10:57.702 Switching to square mode (Mythbuntu-8.04)
2008-11-03 10:10:57.990 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-03 10:10:57.990 lirc_init failed for mythtv, see preceding messages
2008-11-03 10:10:57.991 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font clock
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font small
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font medium
2008-11-03 10:11:00.246 Specified base font 'medium' does not exist for font large
2008-11-03 10:11:00.247 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-03 10:11:00.393 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-03 10:11:00.450 Registering Internal as a media playback plugin.
2008-11-03 10:11:00.611 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-03 10:11:00.944 Failed to run 'cdrecord --scanbus'
2008-11-03 10:11:00.947 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-03 10:11:00.949 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-03 10:11:00.972 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-03 10:11:01.231 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
Starting mythfrontend.real..
2008-11-04 14:39:30.234 New DB connection, total: 2
2008-11-04 14:39:30.234 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:30.235 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-04 14:39:30.236 Enabled verbose msgs:  important general
2008-11-04 14:39:32.324 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-04 14:39:32.325 Primary screen 0.
2008-11-04 14:39:32.326 Using screen 0, 1680x1050 at 0,0
2008-11-04 14:39:32.326 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-04 14:39:32.326 Switching to square mode (Mythbuntu-8.04)
2008-11-04 14:39:32.544 Using the Qt painter
2008-11-04 14:39:32.544 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-04 14:39:32.544 lirc_init failed for mythtv, see preceding messages
2008-11-04 14:39:34.163 Specified base font 'medium' does not exist for font clock
2008-11-04 14:39:34.163 Specified base font 'medium' does not exist for font small
2008-11-04 14:39:34.165 Specified base font 'medium' does not exist for font medium
2008-11-04 14:39:34.165 Specified base font 'medium' does not exist for font large
2008-11-04 14:39:34.166 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-04 14:39:34.378 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-04 14:39:34.440 Registering Internal as a media playback plugin.
2008-11-04 14:39:34.601 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-04 14:39:34.932 Failed to run 'cdrecord --scanbus'
2008-11-04 14:39:34.936 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-04 14:39:34.938 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-04 14:39:34.955 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-04 14:39:35.246 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
Starting mythfrontend.real..
2008-11-08 01:20:00.732 New DB connection, total: 2
2008-11-08 01:20:00.732 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:20:00.734 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-08 01:20:00.734 Enabled verbose msgs:  important general
2008-11-08 01:20:02.682 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:02.683 Primary screen 0.
2008-11-08 01:20:02.683 Using screen 0, 1680x1050 at 0,0
2008-11-08 01:20:02.684 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:02.684 Switching to square mode (Mythbuntu-8.04)
2008-11-08 01:20:02.851 Using the Qt painter
2008-11-08 01:20:02.851 JoystickMenuClient Error: Joystick disabled - Failed to read /home/test/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-08 01:20:02.851 lirc_init failed for mythtv, see preceding messages
2008-11-08 01:20:04.454 Specified base font 'medium' does not exist for font clock
2008-11-08 01:20:04.454 Specified base font 'medium' does not exist for font small
2008-11-08 01:20:04.455 Specified base font 'medium' does not exist for font medium
2008-11-08 01:20:04.455 Specified base font 'medium' does not exist for font large
2008-11-08 01:20:04.456 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-08 01:20:04.607 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-08 01:20:04.662 Registering Internal as a media playback plugin.
2008-11-08 01:20:04.815 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-08 01:20:05.149 Failed to run 'cdrecord --scanbus'
2008-11-08 01:20:05.152 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-08 01:20:05.210 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-08 01:20:05.227 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-08 01:20:05.485 No theme dir: /home/test/.mythtv/themes/Mythbuntu-8.04
2008-11-08 01:20:13.222 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-08 01:20:13.234 Using protocol version 40
2008-11-08 01:20:19.094 Deleting UPnP client...
2008-11-08 01:20:19.095 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

```


Here is the backend.log...

```

2008-11-02 17:39:24.578 Using runtime prefix = /usr
2008-11-02 17:39:24.683 Empty LocalHostName.
2008-11-02 17:39:24.689 Using localhost value of test-desktop
2008-11-02 17:39:24.726 New DB connection, total: 1
2008-11-02 17:39:24.839 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:24.881 Closing DB connection named 'DBManager0'
2008-11-02 17:39:24.892 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:24.895 New DB connection, total: 2
2008-11-02 17:39:25.008 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 17:39:25.177 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-02 17:39:25.568 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-02 17:39:25.810 Main::Registering HttpStatus Extension
2008-11-02 17:39:26.038 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 17:39:26.045 Enabled verbose msgs:  important general
2008-11-02 17:39:26.372 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 17:40:45.507 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 17:40:49.367 MainServer::HandleAnnounce Monitor
2008-11-02 17:40:49.423 adding: test-desktop as a client (events: 0)
2008-11-02 17:40:49.425 MainServer::HandleAnnounce Monitor
2008-11-02 17:40:49.426 adding: test-desktop as a client (events: 1)
2008-11-02 19:06:57.917 Using runtime prefix = /usr
2008-11-02 19:06:57.959 Empty LocalHostName.
2008-11-02 19:06:58.010 Using localhost value of test-desktop
2008-11-02 19:06:58.048 New DB connection, total: 1
2008-11-02 19:06:58.169 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.245 Closing DB connection named 'DBManager0'
2008-11-02 19:06:58.258 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.372 New DB connection, total: 2
2008-11-02 19:06:58.475 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-02 19:06:58.562 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-02 19:06:58.823 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-02 19:06:58.938 Main::Registering HttpStatus Extension
2008-11-02 19:06:59.028 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-02 19:06:59.048 Enabled verbose msgs:  important general
2008-11-02 19:06:59.196 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-02 19:07:23.256 MainServer::HandleAnnounce Monitor
2008-11-02 19:07:23.264 adding: test-desktop as a client (events: 0)
2008-11-02 19:07:23.265 MainServer::HandleAnnounce Monitor
2008-11-02 19:07:23.267 adding: test-desktop as a client (events: 1)
2008-11-02 19:08:18.771 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-03 10:10:41.821 Using runtime prefix = /usr
2008-11-03 10:10:41.880 Empty LocalHostName.
2008-11-03 10:10:41.915 Using localhost value of test-desktop
2008-11-03 10:10:41.952 New DB connection, total: 1
2008-11-03 10:10:42.073 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.107 Closing DB connection named 'DBManager0'
2008-11-03 10:10:42.121 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.235 New DB connection, total: 2
2008-11-03 10:10:42.337 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-03 10:10:42.632 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-03 10:10:43.333 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-03 10:10:43.350 Main::Registering HttpStatus Extension
2008-11-03 10:10:43.351 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-03 10:10:43.352 Enabled verbose msgs:  important general
2008-11-03 10:10:43.449 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-04 14:39:15.818 Using runtime prefix = /usr
2008-11-04 14:39:15.877 Empty LocalHostName.
2008-11-04 14:39:15.929 Using localhost value of test-desktop
2008-11-04 14:39:15.966 New DB connection, total: 1
2008-11-04 14:39:16.087 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.146 Closing DB connection named 'DBManager0'
2008-11-04 14:39:16.158 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.299 New DB connection, total: 2
2008-11-04 14:39:16.476 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:16.623 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-04 14:39:17.192 New DB connection, total: 3
2008-11-04 14:39:17.377 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 14:39:17.413 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-04 14:39:17.415 Main::Registering HttpStatus Extension
2008-11-04 14:39:17.487 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-04 14:39:17.489 Enabled verbose msgs:  important general
2008-11-04 14:39:17.521 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-04 14:40:37.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-08 01:19:47.447 Using runtime prefix = /usr
2008-11-08 01:19:47.506 Empty LocalHostName.
2008-11-08 01:19:47.513 Using localhost value of test-desktop
2008-11-08 01:19:47.545 New DB connection, total: 1
2008-11-08 01:19:47.666 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:47.701 Closing DB connection named 'DBManager0'
2008-11-08 01:19:47.714 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:47.897 New DB connection, total: 2
2008-11-08 01:19:47.925 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-08 01:19:48.041 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-08 01:19:48.428 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-08 01:19:48.576 Main::Registering HttpStatus Extension
2008-11-08 01:19:48.734 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-08 01:19:48.827 Enabled verbose msgs:  important general
2008-11-08 01:19:48.859 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-08 01:20:13.235 MainServer::HandleAnnounce Monitor
2008-11-08 01:20:13.243 adding: test-desktop as a client (events: 0)
2008-11-08 01:20:13.244 MainServer::HandleAnnounce Monitor
2008-11-08 01:20:13.246 adding: test-desktop as a client (events: 1)
2008-11-08 01:21:07.818 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

So I haven't tried this so I don't know if it is really a problem but in your backend log it says:

```

Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

```

I'm not sure if that would keep the backend from starting up but it is something that should probably be fixed.  Try going into the backend setup and register your capture card.  Not sure if that will change anything but just trying to throw out suggestions.

---

### Post by sofasurfer on 2008-11-08
I went to 'backend setup' and under 'capture card setup' it shows...
card type = 'analog v4l'
video device = '/dev/video0'
probed info = 'hauppauge hvr-1600'
vbi device = blank
default input = 'tuner 1'

So it appears that it is configured for my card. What do you think?

---

### Post by bawilson2 on 2008-11-08
> **sofasurfer said:**
> I went to 'backend setup' and under 'capture card setup' it shows...
card type = 'analog v4l'
video device = '/dev/video0'
probed info = 'hauppauge hvr-1600'
vbi device = blank
default input = 'tuner 1'

So it appears that it is configured for my card. What do you think?

I don't think it is setup right.  I have the same card and I followed this guide for setting up the card in mythtv:

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

You need to have the analog tuner set as the 'MPEG-2 encoder card (PVR-x50, PVR-500)' and the digital tuner set as 'DVB DTV capture card (v3.x)'

Like I said I don't know if this will solve the problem you're seeing but it isn't setup correctly.  Also make sure you have the firmware as it lists in the guide.

---

### Post by sofasurfer on 2008-11-08
I went to the link you provided and I performed the settings that you suggested. But the "scan for channels" button is not activated. So I must stil be mssing something.

You may not think that your help is nessessarily that good but you are giving me information that no one else has. So if I can get more information out of you I will be happy to continue to follow it.

EDIT::

Hold it. Don't answer yet. I am making progress. I will write again in a few minutes.

---

### Post by sofasurfer on 2008-11-08
I got the channel scanner to work. It picked up a few channels. I then started the frontend and the video screen came up but all I was able to see was static. So, we're getting very close.

I know I have signals coming into the house because I can view tv using mplayer and vlc.

If I am understanding, I beleive that I think that I should be able to choose either atsc (digital) or ntsc (analog) signals from somewhere in Mythtv. I suspect that if I choose the one other than what I have viewed so far I may have better luck.

---

### Post by bawilson2 on 2008-11-08
Are you able to pickup both analog and digital channels where you're at?  I've found that the digital tuner part of the tuner works much better.  When you're in the mythtv frontend you can press "m" to enter the menu.  That should allow you to switch your tuner.  Also are you using schedule direct?  For the listing information?

---

### Post by sofasurfer on 2008-11-08
I am able to get analog and digital in my area.

The program schedule shows the station numbers but there is no listing information. Where is the file which stores the channels?

When I scan for channels, even though it appears to be finding channels, the channel signal strength shoulds 0 percent.

I tuned to a channel (all channels just show static) and then disconnected my antenna cable from the card. It made no differance in the appearance of the static.

---

### Post by sofasurfer on 2008-11-08
I just went back in and changed the card type back to V4L for the anaolg tuner. I then rescanned channels. Surprise! The signal strength meter registered while scanning. I then opened the frontend and I saw images. However, they were distorted, pixelated and would freeze on and off.

Do you understand why this would have happened? Or was it just a fluke?

Now I went and deleted all the cards with the intention of reconffiguring from scratch. Woops! I am getting nothing now.

So even though I screwed up, I have proof that I am recieving a signal and it is viewable and the problem IS in my settings.

I'm on the right track.

---

### Post by sofasurfer on 2008-11-09
Ok, I'm using mpeg2 as card type again. I have not got a clue why I am now getting an image, but I am. I am not getting a digital image. I am only getting analog.

I am getting only channel 66. It is very gainy but watchable. I can change channels and the display number changes but the image stays on channel 66.

One small step for Ubuntu, one giant leap for me.

---

### Post by bawilson2 on 2008-11-09
Why don't you run "dmesg" from the terminal and attach the output here. It kind of sounds like the card still isn't being recognized by the system correctly.  Another thing to watch out for is that you have it scanning the correct frequencies.  If you're using cable make sure you set that.  If you're using over the air broadcast select that.

---

### Post by sofasurfer on 2008-11-09
I am using antenna and Myth is set for us-broadcast.

Following is my dmesg | grep cx18 (followed by my complete dmesg)...

```

test@test-desktop:~$ dmesg | grep cx18
[    9.499929] cx18:  Start initialization, version 1.0.0
[    9.499970] cx18-0: Initializing card #0
[    9.499973] cx18-0: Autodetected Hauppauge card
[    9.500365] cx18 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    9.500373] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[    9.502265] cx18-0: cx23418 revision 01010000 (B)
[    9.718467] cx18-0: Autodetected Hauppauge HVR-1600
[    9.718469] cx18-0: VBI is not yet supported
[   10.063544] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.063569] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.252020] cx18-0: Disabled encoder IDX device
[   10.252155] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.252158] DVB: registering new adapter (cx18)
[   10.466219] cx18-0: DVB Frontend registered
[   10.466253] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.466284] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.466287] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   10.466369] cx18:  End initialization
[   23.841558] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.417564] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.423721] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.607551] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
test@test-desktop:~$ 

```



Here is my complete dmesg...

```

test@test-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 377b1000 - 37fef4aa
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F6370, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 3FFF3000, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: DSDT 3FFF30C0, 45BD (r1 GBT    NVDAACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: SSDT 3FFF7740, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 3FFF7980, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 3FFF79C0, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 3FFF7680, 0098 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [00377b1000 - 0037fef4aa]          RAMDISK ==> [00377b1000 - 0037fef4aa]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f49b0] 000f49b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262031
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32464 pages, LIFO batch:7
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259727
[    0.000000] Kernel command line: root=UUID=4b1065a4-7c1e-4c32-9ccc-ed73ccf25941 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2210.035 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024228k/1048512k available (2572k kernel code, 23552k reserved, 1160k data, 424k init, 131008k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.07 BogoMIPS (lpj=8840140)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017397] ACPI: Core revision 20080609
[    0.018719] ACPI: Checking initramfs for custom DSDT
[    0.343144] ENABLING IO-APIC IRQs
[    0.343344] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.383038] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.384024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4420.03 BogoMIPS (lpj=8840079)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.468164] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.468189] Brought up 2 CPUs
[    0.468192] Total of 2 processors activated (8840.10 BogoMIPS).
[    0.468214] CPU0 attaching sched-domain:
[    0.468217]  domain 0: span 0-1 level CPU
[    0.468219]   groups: 0 1
[    0.468225] CPU1 attaching sched-domain:
[    0.468227]  domain 0: span 0-1 level CPU
[    0.468229]   groups: 1 0
[    0.468287] net_namespace: 840 bytes
[    0.468287] Booting paravirtualized kernel on bare hardware
[    0.468287] Time:  3:27:20  Date: 11/09/08
[    0.468291] NET: Registered protocol family 16
[    0.468310] EISA bus registered
[    0.468310] ACPI: bus type pci registered
[    0.468310] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 127
[    0.468310] PCI: MCFG area at e0000000 reserved in E820
[    0.468310] PCI: Using MMCONFIG for extended config space
[    0.468310] PCI: Using configuration type 1 for base access
[    0.468794] ACPI: EC: Look up EC in DSDT
[    0.478732] ACPI: Interpreter enabled
[    0.478735] ACPI: (supports S0 S1 S4 S5)
[    0.478750] ACPI: Using IOAPIC for interrupt routing
[    0.488176] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.488192] PCI: 0000:00:01.1 reg 10 io port: [c000, c03f]
[    0.488203] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
[    0.488207] PCI: 0000:00:01.1 reg 24 io port: [c800, c83f]
[    0.488223] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.488228] pci 0000:00:01.1: PME# disabled
[    0.488269] PCI: 0000:00:02.0 reg 10 32bit mmio: [f3006000, f3006fff]
[    0.488289] pci 0000:00:02.0: supports D1
[    0.488291] pci 0000:00:02.0: supports D2
[    0.488293] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488296] pci 0000:00:02.0: PME# disabled
[    0.488315] PCI: 0000:00:02.1 reg 10 32bit mmio: [f3007000, f30070ff]
[    0.488339] pci 0000:00:02.1: supports D1
[    0.488340] pci 0000:00:02.1: supports D2
[    0.488342] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488345] pci 0000:00:02.1: PME# disabled
[    0.488396] PCI: 0000:00:05.0 reg 10 32bit mmio: [f3000000, f3003fff]
[    0.488418] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.488421] pci 0000:00:05.0: PME# disabled
[    0.488449] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
[    0.488480] PCI: 0000:00:07.0 reg 10 32bit mmio: [f3004000, f3004fff]
[    0.488484] PCI: 0000:00:07.0 reg 14 io port: [cc00, cc07]
[    0.488502] pci 0000:00:07.0: supports D1
[    0.488504] pci 0000:00:07.0: supports D2
[    0.488506] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488510] pci 0000:00:07.0: PME# disabled
[    0.488526] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
[    0.488529] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
[    0.488533] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
[    0.488537] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
[    0.488540] PCI: 0000:00:08.0 reg 20 io port: [e000, e00f]
[    0.488544] PCI: 0000:00:08.0 reg 24 32bit mmio: [f3005000, f3005fff]
[    0.488583] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488586] pci 0000:00:09.0: PME# disabled
[    0.488691] PCI: 0000:01:06.0 reg 10 32bit mmio: [e8000000, ebffffff]
[    0.488739] PCI: 0000:01:07.0 reg 10 32bit mmio: [ec000000, ec007fff]
[    0.488791] pci 0000:00:04.0: transparent bridge
[    0.488795] PCI: bridge 0000:00:04.0 32bit mmio: [e8000000, efffffff]
[    0.488817] PCI: 0000:02:00.0 reg 10 32bit mmio: [f0000000, f0ffffff]
[    0.488822] PCI: 0000:02:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.488831] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f1000000, f1ffffff]
[    0.488838] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.488879] PCI: bridge 0000:00:09.0 32bit mmio: [f0000000, f2ffffff]
[    0.488883] PCI: bridge 0000:00:09.0 64bit mmio pref: [d0000000, dfffffff]
[    0.488889] bus 00 -> node 0
[    0.488895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.489222] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.524182] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.524348] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[    0.524511] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.524675] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.524839] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525002] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525166] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525330] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.test@test-desktop:~$ dmesg | grep cx18
[    9.499929] cx18:  Start initialization, version 1.0.0
[    9.499970] cx18-0: Initializing card #0
[    9.499973] cx18-0: Autodetected Hauppauge card
[    9.500365] cx18 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    9.500373] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[    9.502265] cx18-0: cx23418 revision 01010000 (B)
[    9.718467] cx18-0: Autodetected Hauppauge HVR-1600
[    9.718469] cx18-0: VBI is not yet supported
[   10.063544] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.063569] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.252020] cx18-0: Disabled encoder IDX device
[   10.252155] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.252158] DVB: registering new adapter (cx18)
[   10.466219] cx18-0: DVB Frontend registered
[   10.466253] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.466284] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.466287] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   10.466369] cx18:  End initialization
[   23.841558] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.417564] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.423721] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.607551] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
test@test-desktop:~$ 


[    0.525498] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525663] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.525829] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.525994] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.526160] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.526324] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.526491] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.526656] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.526820] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.526986] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.527149] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.527366] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.527574] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.527782] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.528175] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.528384] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.528593] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.528802] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.529011] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.529219] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[    0.529429] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.529642] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.529852] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.530062] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.530271] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.530481] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.530690] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.530900] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.531110] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.531320] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.531378] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.531378] pnp: PnP ACPI init
[    0.531378] ACPI: bus type pnp registered
[    0.536438] pnp: PnP ACPI: found 15 devices
[    0.536438] ACPI: ACPI bus type pnp unregistered
[    0.536438] PnPBIOS: Disabled by ACPI PNP
[    0.536438] PCI: Using ACPI for IRQ routing
[    0.544041] NET: Registered protocol family 8
[    0.544043] NET: Registered protocol family 20
[    0.544056] NetLabel: Initializing
[    0.544057] NetLabel:  domain hash size = 128
[    0.544059] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.544073] NetLabel:  unlabeled traffic allowed by default
[    0.544080] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.544085] hpet0: 3 32-bit timers, 250test@test-desktop:~$ dmesg | grep cx18
[    9.499929] cx18:  Start initialization, version 1.0.0
[    9.499970] cx18-0: Initializing card #0
[    9.499973] cx18-0: Autodetected Hauppauge card
[    9.500365] cx18 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    9.500373] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[    9.502265] cx18-0: cx23418 revision 01010000 (B)
[    9.718467] cx18-0: Autodetected Hauppauge HVR-1600
[    9.718469] cx18-0: VBI is not yet supported
[   10.063544] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.063569] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.252020] cx18-0: Disabled encoder IDX device
[   10.252155] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.252158] DVB: registering new adapter (cx18)
[   10.466219] cx18-0: DVB Frontend registered
[   10.466253] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.466284] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.466287] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   10.466369] cx18:  End initialization
[   23.841558] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.417564] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.423721] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.607551] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
test@test-desktop:~$ 

00000 Hz
[    0.546132] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.546134]    actual entries 65620
[    0.546264] AppArmor: AppArmor Filesystem Enabled
[    0.546291] ACPI: RTC can wake from S4
[    0.548044] Switched to high resolution mode on CPU 0
[    0.548203] Switched to high resolution mode on CPU 1
[    0.552031] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.552034] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.552037] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.552040] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.552043] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.552045] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.552049] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.552052] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.552059] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.552062] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.552065] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.552068] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.552079] system 00:0d: iomem range 0xe0000000-0xe7ffffff could not be reserved
[    0.552086] system 00:0e: iomem range 0xce200-0xcffff has been reserved
[    0.552088] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.552091] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.552094] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.552097] system 00:0e: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.552100] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.552103] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.552106] system 00:0e: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.552109] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.552113] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.587343] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.587346] pci 0000:00:04.0:   IO window: disabled
[    0.587350] pci 0000:00:04.0:   MEM window: 0xe8000000-0xefffffff
[    0.587353] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.587360] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.587362] pci 0000:00:09.0:   IO window: disabled
[    0.587365] pci 0000:00:09.0:   MEM window: 0xf0000000-0xf2ffffff
[    0.587368] pci 0000:00:09.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.587377] pci 0000:00:04.0: setting latency timer to 64
[    0.587382] pci 0000:00:09.0: setting latency timer to 64
[    0.587385] bus: 00 index 0 io port: [0, ffff]
[    0.587387] bus: 00 index 1 mmio: [0, ffffffff]
[    0.587390] bus: 01 index 0 mmio: [0, 0]
[    0.587392] bus: 01 index 1 mmio: [e8000000, efffffff]
[    0.587394] bus: 01 index 2 mmio: [0, 0]
[    0.587396] bus: 01 index 3 io port: [0, ffff]
[    0.587398] bus: 01 index 4 mmio: [0, ffffffff]
[    0.587400] bus: 02 index 0 mmio: [0, 0]
[    0.587402] bus: 02 index 1 mmio: [f0000000, f2ffffff]
[    0.587404] bus: 02 index 2 mmio: [d0000000, dfffffff]
[    0.587406] bus: 02 index 3 mmio: [0, 0]
[    0.587417] NET: Registered protocol family 2
[    0.600061] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.600352] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.601041] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.601405] TCP: Hash tables configured (established 131072 bind 65536)
[    0.601408] TCP reno registered
[    0.608097] NET: Registered protocol family 1
[    0.608214] checking if image is initramfs... it is
[    1.276283] Freeing initrd memory: 8441k freed
[    1.277364] audit: initializing netlink socket (disabled)
[    1.277382] type=2000 audit(1226201240.276:1): initialized
[    1.282866] highmem bounce pool size: 64 pages
[    1.282871] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.285310] VFS: Disk quotas dquot_6.5.1
[    1.285403] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.285506] msgmni has been set to 1761
[    1.285632] io scheduler noop registered
[    1.285635] io scheduler anticipatory registered
[    1.285637] io scheduler deadline registered
[    1.285647] io scheduler cfq registered (default)
[    1.285680] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.285772] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.285788] pci 0000:00:05.0: Enabling HT MSI Mapping
[    1.285815] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.285829] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.285844] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.285867] pci 0000:02:00.0: Boot video device
[    1.285970] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.285994] pcieport-driver 0000:00:09.0: found MSI capability
[    1.286015] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.286068] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.286411] isapnp: Scanning for PnP cards...
[    1.639019] isapnp: No Plug & Play device found
[    1.676018] hpet_resources: 0xfeff0000 is busy
[    1.676120] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.676256] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.676423] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.677082] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.677384] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.679445] brd: module loaded
[    1.679522] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.679659] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.680065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.680071] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.680390] mice: PS/2 mouse device common for all mice
[    1.680540] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.680571] rtc0: alarms up to one year, y3k, hpet irqs
[    1.680721] EISA: Probing bus 0 at eisa.0
[    1.680727] Cannot allocate resource for EISA slot 1
[    1.680746] EISA: Detected 0 cards.
[    1.680749] cpuidle: using governor ladder
[    1.680751] cpuidle: using governor menu
[    1.681218] TCP cubic registered
[    1.681243] Using IPI No-Shortcut mode
[    1.681446] registered taskstats version 1
[    1.681561]   Magic number: 0:946:461
[    1.681750] rtc_cmos 00:05: setting system clock to 2008-11-09 03:27:21 UTC (1226201241)
[    1.681753] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.681755] EDD information not available.
[    1.682026] Freeing unused kernel memory: 424k freed
[    1.682084] Write protecting the kernel text: 2576k
[    1.682121] Write protecting the kernel read-only data: 936k
[    1.696050] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.738513] compcache: Compressed swap size set to: 258360 KB
[    1.738960] TLSF: pool: f8820000, init_size=16384, max_size=0, grow_size=16384
[    1.951791] fuse init (API version 7.9)
[    1.976706] processor ACPI0007:00: registered as cooling_device0
[    1.976771] processor ACPI0007:01: registered as cooling_device1
[    2.485036] usbcore: registered new interface driver usbfs
[    2.485059] usbcore: registered new interface driver hub
[    2.485116] usbcore: registered new device driver usb
[    2.498776] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.499196] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    2.499204] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    2.499216] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.499219] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.499264] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.499284] ohci_hcd 0000:00:02.0: irq 23, io mem 0xf3006000
[    2.513425] No dock devices found.
[    2.526139] SCSI subsystem initialized
[    2.541028] libata version 3.00 loaded.
[    2.554742] usb usb1: configuration #1 chosen from 1 choice
[    2.554770] hub 1-0:1.0: USB hub found
[    2.554780] hub 1-0:1.0: 8 ports detected
[    2.594177] Adding 258356k swap on /dev/ramzswap0.  Priority:100 extents:1 across:258356k
[    2.657377] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.657387] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.657400] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.657403] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.657442] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    2.657470] ehci_hcd 0000:00:02.1: debug port 1
[    2.657474] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.657489] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf3007000
[    2.668021] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.668167] usb usb2: configuration #1 chosen from 1 choice
[    2.668193] hub 2-0:1.0: USB hub found
[    2.668202] hub 2-0:1.0: 8 ports detected
[    2.772465] pata_acpi 0000:00:06.0: setting latency timer to 64
[    2.772504] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.772886] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    2.772894] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    2.772898] forcedeth 0000:00:07.0: setting latency timer to 64
[    3.292728] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:7d:2b:a1:df
[    3.292733] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    3.293165] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.293172] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.293206] pata_acpi 0000:00:08.0: setting latency timer to 64
[    3.293216] pata_acpi 0000:00:08.0: PCI INT A disabled
[    3.298387] sata_nv 0000:00:08.0: version 3.5
[    3.298403] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.298443] sata_nv 0000:00:08.0: setting latency timer to 64
[    3.300443] scsi0 : sata_nv
[    3.300563] scsi1 : sata_nv
[    3.300737] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    3.300740] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    3.768036] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.789186] ata1.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[    3.789191] ata1.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.804960] ata1.00: configured for UDMA/133
[    4.272032] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.296126] ata2.00: ATAPI: PHILIPS SPD2513P, MP03, max UDMA/100
[    4.328119] ata2.00: configured for UDMA/100
[    4.328217] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[    4.329370] scsi 1:0:0:0: CD-ROM            PHILIPS  SPD2513P         MP03 PQ: 0 ANSI: 5
[    4.329874] pata_amd 0000:00:06.0: version 0.3.10
[    4.329925] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.329998] scsi2 : pata_amd
[    4.330064] scsi3 : pata_amd
[    4.330762] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.330764] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.512278] ata3.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    4.512284] ata3.00: ATA-8: WDC WD3200AAJB-22WGA0, 00.02C01, max UDMA/100
[    4.512287] ata3.00: 625142448 sectors, multi 16: LBA48 
[    4.512301] ata3: nv_mode_filter: 0x3f39f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    4.529138] ata3.00: configured for UDMA/33
[    4.529179] ata4: port disabled. ignoring.
[    4.529278] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJB-2 00.0 PQ: 0 ANSI: 5
[    4.539850] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.539885] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.539917] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.553242] Driver 'sr' needs updating - please use bus_type methods
[    4.558581] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.558586] Uniform CD-ROM driver Revision: 3.20
[    4.558678] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.567407] Driver 'sd' needs updating - please use bus_type methods
[    4.567538] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[    4.567560] sd 0:0:0:0: [sda] Write Protect is off
[    4.567563] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.567598] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.567669] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[    4.567687] sd 0:0:0:0: [sda] Write Protect is off
[    4.567690] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.567724] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.567728]  sda: sda1 sda2 < sda5 sda6 >
[    4.594505] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.594599] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    4.594621] sd 2:0:0:0: [sdb] Write Protect is off
[    4.594624] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.594659] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.595704] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    4.595732] sd 2:0:0:0: [sdb] Write Protect is off
[    4.595734] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.595761] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.595766]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 sdb9 > sdb2
[    4.646590] sd 2:0:0:0: [sdb] Attached SCSI disk
[    4.969172] PM: Starting manual resume from disk
[    4.969175] PM: Resume from partition 8:24
[    4.969177] PM: Checking hibernation image.
[    4.969449] PM: Resume from disk failed.
[    4.985671] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.985675] EXT3-fs: write access will be enabled during recovery.
[    6.428669] kjournald starting.  Commit interval 5 seconds
[    6.428691] EXT3-fs: sdb7: orphan cleanup on readonly fs
[    6.428697] ext3_orphan_cleanup: deleting unreferenced inode 16309
[    6.428724] ext3_orphan_cleanup: deleting unreferenced inode 16299
[    6.428731] ext3_orphan_cleanup: deleting unreferenced inode 16298
[    6.428737] ext3_orphan_cleanup: deleting unreferenced inode 16297
[    6.428742] ext3_orphan_cleanup: deleting unreferenced inode 16296
[    6.428759] ext3_orphan_cleanup: deleting unreferenced inode 16295
[    6.428764] EXT3-fs: sdb7: 6 orphan inodes deleted
[    6.428766] EXT3-fs: recovery complete.
[    6.438604] EXT3-fs: mounted filesystem with ordered data mode.
[    7.997503] udevd version 124 started
[    8.657281] input: PC Speaker as /devices/platform/pcspkr/input/input2
[    8.730159] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.794878] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    8.820027] ACPI: Power Button (FF) [PWRF]
[    8.820112] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[    8.852042] ACPI: Power Button (CM) [PWRB]
[    8.891367] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.946584] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.946619] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc800
[    9.190729] Linux video capture interface: v2.00
[    9.499929] cx18:  Start initialization, version 1.0.0
[    9.499970] cx18-0: Initializing card #0
[    9.499973] cx18-0: Autodetected Hauppauge card
[    9.500358] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    9.500365] cx18 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    9.500373] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[    9.502265] cx18-0: cx23418 revision 01010000 (B)
[    9.628277] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.628321] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.718446] tveeprom 2-0050: Hauppauge model 74041, rev C5B2, serial# 3013423
[    9.718450] tveeprom 2-0050: MAC address is 00-0D-FE-2D-FB-2F
[    9.718453] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[    9.718456] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[    9.718459] tveeprom 2-0050: audio processor is CX23418 (idx 38)
[    9.718461] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
[    9.718464] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[    9.718467] cx18-0: Autodetected Hauppauge HVR-1600
[    9.718469] cx18-0: VBI is not yet supported
[    9.937790] logips2pp: Detected unknown logitech mouse model 127
[   10.063544] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.063569] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.251121] tuner-simple 3-0061: creating new instance
[   10.251126] tuner-simple 3-0061: type set to 50 (TCL 2002N)
[   10.252020] cx18-0: Disabled encoder IDX device
[   10.252155] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.252158] DVB: registering new adapter (cx18)
[   10.409526] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   10.466057] MXL5005S: Attached at address 0x63
[   10.466063] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   10.466219] cx18-0: DVB Frontend registered
[   10.466253] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.466284] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.466287] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   10.466369] cx18:  End initialization
[   10.466849] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   10.466856] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   10.466879] HDA Intel 0000:00:05.0: setting latency timer to 64
[   10.539400] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   10.539409] rt61pci 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   10.545755] phy0: Selected rate control algorithm 'pid'
[   10.703142] Registered led device: rt61pci-phy0:radio
[   10.703161] Registered led device: rt61pci-phy0:assoc
[   11.843884] lp0: using parport0 (interrupt-driven).
[   12.165381] Adding 995988k swap on /dev/sdb8.  Priority:-1 extents:1 across:995988k
[   12.779008] EXT3 FS on sdb7, internal journal
[   13.646572] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   13.647957] SGI XFS Quota Management subsystem
[   13.685382] XFS mounting filesystem sdb9
[   13.905622] Starting XFS recovery on filesystem: sdb9 (logdev: internal)
[   13.963644] Ending XFS recovery on filesystem: sdb9 (logdev: internal)
[   14.570324] type=1505 audit(1226201254.835:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4202
[   14.570548] type=1505 audit(1226201254.835:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4202
[   14.609729] type=1505 audit(1226201254.875:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4206
[   14.768901] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.939785] ACPI: WMI: Mapper loaded
[   16.771175] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   17.122152] NET: Registered protocol family 10
[   17.122922] lo: Disabled Privacy Extensions
[   18.558246] ppdev: user-space parallel port driver
[   23.636523] firmware: requesting v4l-cx23418-apu.fw
[   23.841558] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.340521] firmware: requesting v4l-cx23418-cpu.fw
[   24.417564] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.423721] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   24.620517] firmware: requesting v4l-cx23418-apu.fw
[   25.168018] firmware: requesting v4l-cx23418-cpu.fw
[   25.424017] firmware: requesting v4l-cx23418-dig.fw
[   25.607551] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.252192] Bluetooth: Core ver 2.13
[   26.252819] NET: Registered protocol family 31
[   26.252824] Bluetooth: HCI device and connection manager initialized
[   26.252828] Bluetooth: HCI socket layer initialized
[   26.321575] Bluetooth: L2CAP ver 2.11
[   26.321583] Bluetooth: L2CAP socket layer initialized
[   26.351422] Bluetooth: SCO (Voice Link) ver 0.6
[   26.351429] Bluetooth: SCO socket layer initialized
[   26.411882] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.411888] Bluetooth: BNEP filters: protocol multicast
[   26.422865] Bluetooth: RFCOMM socket layer initialized
[   26.423969] Bluetooth: RFCOMM TTY layer initialized
[   26.423975] Bluetooth: RFCOMM ver 1.10
[   26.468060] Bridge firewalling registered
[   26.468730] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   30.628750] eth0: no link during initialization.
[   30.629246] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.630389] firmware: requesting rt2561s.bin
[   30.704233] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.770053] NET: Registered protocol family 17
[   74.164061] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   74.364015] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   74.564015] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   74.764018] wlan0: authentication with AP 00:17:3f:f1:1a:2c timed out
[   84.892987] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   84.893763] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   84.894498] wlan0: authenticated
[   84.894504] wlan0: associate with AP 00:17:3f:f1:1a:2c
[   84.899032] wlan0: RX AssocResp from 00:17:3f:f1:1a:2c (capab=0x431 status=0 aid=2)
[   84.899038] wlan0: associated
[   84.899682] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.235650] padlock: VIA PadLock not detected.
[   95.648513] wlan0: no IPv6 routers present
[  545.570139] DVB: frontend 0 frequency 863000000 out of range (54000000..858000000)
[  545.570978] DVB: frontend 0 frequency 869000000 out of range (54000000..858000000)
[  545.572549] DVB: frontend 0 frequency 875000000 out of range (54000000..858000000)
[  545.574088] DVB: frontend 0 frequency 881000000 out of range (54000000..858000000)
[  545.587588] DVB: frontend 0 frequency 887000000 out of range (54000000..858000000)
[ 1131.845544] DVB: frontend 0 frequency 863000000 out of range (54000000..858000000)
[ 1131.846527] DVB: frontend 0 frequency 869000000 out of range (54000000..858000000)
[ 1131.847407] DVB: frontend 0 frequency 875000000 out of range (54000000..858000000)
[ 1131.849261] DVB: frontend 0 frequency 881000000 out of range (54000000..858000000)
[ 1131.849673] DVB: frontend 0 frequency 887000000 out of range (54000000..858000000)
[ 1550.534022] DVB: frontend 0 frequency 863000000 out of range (54000000..858000000)
[ 1550.534870] DVB: frontend 0 frequency 869000000 out of range (54000000..858000000)
[ 1550.535416] DVB: frontend 0 frequency 875000000 out of range (54000000..858000000)
[ 1550.536104] DVB: frontend 0 frequency 881000000 out of range (54000000..858000000)
[ 1550.538321] DVB: frontend 0 frequency 887000000 out of range (54000000..858000000)
[ 1607.924904] mythfilldatabas[7520]: segfault at df46a63e ip 08bbc47d sp b543a80c error 7
[ 3579.061540] DVB: frontend 0 frequency 863000000 out of range (54000000..858000000)
[ 3579.061987] DVB: frontend 0 frequency 869000000 out of range (54000000..858000000)
[ 3579.062358] DVB: frontend 0 frequency 875000000 out of range (54000000..858000000)
[ 3579.062719] DVB: frontend 0 frequency 881000000 out of range (54000000..858000000)
[ 3579.063203] DVB: frontend 0 frequency 887000000 out of range (54000000..858000000)
[ 5695.658748] mythfilldatabas[11130]: segfault at df70763e ip 08e5947d sp b551a80c error 7


```

---

### Post by bawilson2 on 2008-11-09
Ok, so it looks like I was wrong.  Your tuner appears to be setup correctly.  

Do you normally get digital stations in your area?  Let's try getting that one working since the driver is a little more polished in that area.  I'm not sure what the problem is now so I'm going to try suggesting a few simple things.  Sorry if you've already gone through these.  I'm just trying to figure out what else could be wrong.  I have almost the exact same setup so thing should be working.

There are two places that you need to set the channel frequency.  First one is in the backend setup under "General"->"Locale Settings"->"Channel frequency table".  Second place is "Video sources" and then select the source you have setup.  In that menu there is also a "Channel frequecy table" that needs to be set.

What do you have set for you Video sources?  If you have digital channels available in your area you should have gotten some of those.

---

### Post by sofasurfer on 2008-11-09
>Ok, so it looks like I was wrong. Your tuner appears to be setup >correctly.

>Do you normally get digital stations in your area? 

Yes, I am viewing digital channels over the air using mplayer and vlc.

>Let's try getting that one working since the driver is a little more >polished in that area. I'm not sure what the problem is now so I'm >going to try suggesting a few simple things. Sorry if you've already >gone through these. I'm just trying to figure out what else could be >wrong. I have almost the exact same setup so thing should be working.

>There are two places that you need to set the channel frequency. First >one is in the backend setup under "General"->"Locale >Settings"->"Channel frequency table". 

This is set to "U.S. broadcast".

>Second place is "Video sources" and then select the source you have >setup. In that menu there is also a "Channel frequecy table" that needs >to be set.

This is set to "braodcast".

>What do you have set for you Video sources? If you have digital >channels available in your area you should have gotten some of those.

I have to double check this.

I just tried the digital tuner again. I setted myth and the analog tuner started. I pressed "m" and chose "digital. The screen went black for quite a while and this I was taken back to the main menu.

The "guide" shows no listings for digital or analog.

---

### Post by bawilson2 on 2008-11-11
So after you try to use the digital tuner was there anything interesting in the mythtv logs?

---

### Post by sofasurfer on 2008-11-11
When I configure the backend, it asks for a name and password. Do I use the password that is in /home/mythtv/.mythtv/mysql.txt

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

or do I use '0000'?

Where do I find the Myth logs? Is there a particular file that you want to see?

---

### Post by bawilson2 on 2008-11-11
> **sofasurfer said:**
> When I configure the backend, it asks for a name and password. Do I use the password that is in /home/mythtv/.mythtv/mysql.txt

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

or do I use '0000'?

Where do I find the Myth logs? Is there a particular file that you want to see?

Sorry, not following where you're being asked for the mysql stuff.  The '0000' is the security PIN that should be entered into the backend setup.  It just makes things easer by allowing all frontends to attach to the backend.  

The logs I was interested in are the ones in /var/log/mythtv/mythfronend and mythbackend.  When you try to use the digital tuner and it fails it should say something in there about why it failed.

---

### Post by sofasurfer on 2008-11-12
Well, hear is a complete run-down of where I am at.
I reinstalled Mythbuntu. Now I can not view anything. When I click on "watch tv" I go nowhere and I stay at that page.

Anyway, I scanned for channels with analog tuner and to results show many available channels, way more than I normally get on regular tv.
When I scanned, the signal strength bar was working which means there was good strong signals.

Hear is my backend log followed by my frontend log...

```

2008-11-12 00:24:42.121 Using runtime prefix = /usr
2008-11-12 00:24:42.150 Empty LocalHostName.
2008-11-12 00:24:42.152 Using localhost value of daryl-desktop
2008-11-12 00:24:42.159 New DB connection, total: 1
2008-11-12 00:24:42.166 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:24:42.168 Closing DB connection named 'DBManager0'
2008-11-12 00:24:42.173 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:24:42.178 New DB connection, total: 2
2008-11-12 00:24:42.181 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:24:42.186 Current Schema Version: 1214
Starting up as the master server.
2008-11-12 00:24:42.263 New DB connection, total: 3
2008-11-12 00:24:42.272 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:24:42.292 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2008-11-12 00:24:42.296 DVBChan(1:0) Error: SetChannelByString(3): Failed to initialize multiplex options
2008-11-12 00:24:42.297 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-11-12 00:24:42.436 New DB scheduler connection
2008-11-12 00:24:42.438 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-11-12 00:24:42.460 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-12 00:24:42.461 Main::Registering HttpStatus Extension
2008-11-12 00:24:42.469 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-12 00:24:42.476 Enabled verbose msgs:  important general
2008-11-12 00:24:42.485 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-12 00:24:45.454 Reschedule requested for id -1.
2008-11-12 00:24:45.488 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2008-11-12 00:24:45.492 Seem to be woken up by USER
2008-11-12 00:24:49.619 MainServer::HandleAnnounce Monitor
2008-11-12 00:24:49.630 adding: daryl-desktop as a client (events: 0)
2008-11-12 00:24:49.636 MainServer::HandleAnnounce Monitor
2008-11-12 00:24:49.637 adding: daryl-desktop as a client (events: 1)
2008-11-12 00:24:49.638 Reschedule requested for id -1.
2008-11-12 00:24:49.640 MythSocket(b2404728:-1): writeStringList: Error, socket went unconnected.
2008-11-12 00:24:49.663 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2008-11-12 00:25:22.193 MainServer::HandleAnnounce Monitor
2008-11-12 00:25:22.236 adding: daryl-desktop as a client (events: 0)
2008-11-12 00:25:22.239 MainServer::HandleAnnounce Monitor
2008-11-12 00:25:22.240 adding: daryl-desktop as a client (events: 1)
2008-11-12 00:25:22.248 MainServer::HandleAnnounce Playback
2008-11-12 00:25:22.250 adding: daryl-desktop as a client (events: 0)
2008-11-12 00:25:22.253 TVRec(1): Changing from None to WatchingLiveTV
2008-11-12 00:25:22.257 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '2'.
2008-11-12 00:25:22.260 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2008-11-12 00:25:22.267 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '2'.
2008-11-12 00:25:22.269 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2008-11-12 00:25:22.272 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-11-12 00:25:22.276 TVRec(1): HW Tuner: 1->1
2008-11-12 00:25:22.282 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2008-11-12 00:25:22.284 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2008-11-12 00:25:22.288 TVRec(1): Changing from WatchingLiveTV to None
2008-11-12 00:26:02.454 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-12 00:33:54.144 MainServer::HandleAnnounce Monitor
2008-11-12 00:33:54.149 adding: daryl-desktop as a client (events: 0)
2008-11-12 00:33:54.151 MainServer::HandleAnnounce Monitor
2008-11-12 00:33:54.152 adding: daryl-desktop as a client (events: 1)
2008-11-12 00:33:54.155 MainServer::HandleAnnounce Playback
2008-11-12 00:33:54.157 adding: daryl-desktop as a client (events: 0)
2008-11-12 00:33:54.161 TVRec(1): Changing from None to WatchingLiveTV
2008-11-12 00:33:54.171 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '2'.
2008-11-12 00:33:54.172 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2008-11-12 00:33:54.179 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '2'.
2008-11-12 00:33:54.180 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2008-11-12 00:33:54.185 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-11-12 00:33:54.188 TVRec(1): HW Tuner: 1->1
2008-11-12 00:33:54.193 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2008-11-12 00:33:54.196 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2008-11-12 00:33:54.200 TVRec(1): Changing from WatchingLiveTV to None

```

Here is the frontend log...

```

Starting mythfrontend.real..
2008-11-12 00:25:17.739 New DB connection, total: 2
2008-11-12 00:25:17.739 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:25:17.741 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-12 00:25:17.741 Enabled verbose msgs:  important general
2008-11-12 00:25:18.044 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:25:18.045 Primary screen 0.
2008-11-12 00:25:18.046 Using screen 0, 1680x1050 at 0,0
2008-11-12 00:25:18.046 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:25:18.046 Switching to square mode (Mythbuntu-8.04)
2008-11-12 00:25:18.062 Using the Qt painter
2008-11-12 00:25:18.063 JoystickMenuClient Error: Joystick disabled - Failed to read /home/daryl/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-12 00:25:18.063 lirc_init failed for mythtv, see preceding messages
2008-11-12 00:25:19.109 Specified base font 'medium' does not exist for font clock
2008-11-12 00:25:19.109 Specified base font 'medium' does not exist for font small
2008-11-12 00:25:19.109 Specified base font 'medium' does not exist for font medium
2008-11-12 00:25:19.109 Specified base font 'medium' does not exist for font large
2008-11-12 00:25:19.110 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-12 00:25:19.233 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-12 00:25:19.257 Registering Internal as a media playback plugin.
2008-11-12 00:25:19.306 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-12 00:25:19.374 MythMusic adding CD-Writer: 1,0,0 -- SPD2513P        
2008-11-12 00:25:19.403 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-12 00:25:19.463 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:25:22.192 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-12 00:25:22.193 Using protocol version 40
2008-11-12 00:25:22.247 TV: Attempting to change from None to WatchingLiveTV
2008-11-12 00:25:22.248 Using protocol version 40
2008-11-12 00:25:22.293 GetEntryAt(-1) failed.
2008-11-12 00:25:22.293 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-11-12 00:25:22.293 TV Error: LiveTV not successfully started
2008-11-12 00:25:22.294 TV Error: LiveTV not successfully started
2008-11-12 00:25:22.349 TV: Deleting TV Chain in destructor
2008-11-12 00:25:22.356 DPMS Deactivated 
2008-11-12 00:25:22.357 DPMS Reactivated.
2008-11-12 00:25:26.497 Deleting UPnP client...
Starting mythfrontend.real..
2008-11-12 00:33:21.924 New DB connection, total: 2
2008-11-12 00:33:21.924 Connected to database 'mythconverg' at host: localhost
2008-11-12 00:33:21.926 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-12 00:33:21.926 Enabled verbose msgs:  important general
2008-11-12 00:33:22.231 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:33:22.232 Primary screen 0.
2008-11-12 00:33:22.233 Using screen 0, 1680x1050 at 0,0
2008-11-12 00:33:22.233 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:33:22.233 Switching to square mode (Mythbuntu-8.04)
2008-11-12 00:33:22.249 Using the Qt painter
2008-11-12 00:33:22.249 JoystickMenuClient Error: Joystick disabled - Failed to read /home/daryl/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-11-12 00:33:22.249 lirc_init failed for mythtv, see preceding messages
2008-11-12 00:33:23.420 Specified base font 'medium' does not exist for font clock
2008-11-12 00:33:23.420 Specified base font 'medium' does not exist for font small
2008-11-12 00:33:23.420 Specified base font 'medium' does not exist for font medium
2008-11-12 00:33:23.420 Specified base font 'medium' does not exist for font large
2008-11-12 00:33:23.421 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-12 00:33:23.546 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-12 00:33:23.570 Registering Internal as a media playback plugin.
2008-11-12 00:33:23.622 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-12 00:33:23.690 MythMusic adding CD-Writer: 1,0,0 -- SPD2513P        
2008-11-12 00:33:23.718 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-12 00:33:23.780 No theme dir: /home/daryl/.mythtv/themes/Mythbuntu-8.04
2008-11-12 00:33:54.143 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-12 00:33:54.144 Using protocol version 40
2008-11-12 00:33:54.154 TV: Attempting to change from None to WatchingLiveTV
2008-11-12 00:33:54.154 Using protocol version 40
2008-11-12 00:33:54.205 GetEntryAt(-1) failed.
2008-11-12 00:33:54.205 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-11-12 00:33:54.205 TV Error: LiveTV not successfully started
2008-11-12 00:33:54.206 TV Error: LiveTV not successfully started
2008-11-12 00:33:54.256 TV: Deleting TV Chain in destructor
2008-11-12 00:33:54.263 DPMS Deactivated 
2008-11-12 00:33:54.264 DPMS Reactivated.
2008-11-12 00:33:58.761 Deleting UPnP client...

```

EDIT:::
One more thing...
When I go to "capture cards" and I choose to "add a capture card" and then select "capture card type"-"mpeg", the probe does not work and so "Hauppauge 1600" is not available. But if I choose "mjpeg" or "V4L", the probe does work. So I click "finish" and then repeat the process and change "capture card type" to "mpeg". This is the only way to get "mpeg" to "find" my card.
I think this may be a clue.

---

### Post by bawilson2 on 2008-11-12
A little bit of thinking out loud...

If you've got the card working with other programs then Ubuntu is recognizing it correctly and you should have all the drivers/firmware setup correctly. 

The error that I see in the log is that your log is that the channels aren't setup correctly.  It is very strange that you're picking up more analog channels using the tuner then you do with a normal TV.  That shouldn't matter.  I'm wondering if something might be wrong with the channel setup.

Again... no answers just throwing out ideas.

---

### Post by sofasurfer on 2008-11-12
My problem now is why I can not get past the first page of the frontend.
I am unable to view the video screen. Been racking my brains all night trying to figure out what I did differant.
I think my backend is not starting.

---

### Post by CaptainPatent on 2008-11-12
> My problem now is why I can not get past the first page of the frontend.

Do you mean when you go to "Watch Live TV" in the frontend menu it automatically shoots you back to the frontend menu screen? If that's the case you need to re-check to make sure your card is configured properly... 

Check to see if your card is set up properly again (dmesg) and then check in the backend to see if it is set up properly as an input.

I'm also having a few problems with my Hauppauge 1600 card though that I was wondering if you or anyone else had insight into. I'm getting about to the point you were at when all you were getting was static, but I never have been able to obtain any signal strength at all.

I get Comcast digital cable and I do have a converter box, but I would prefer to use the digital tuner in the card if possible (that way I can avoid using the IR blaster to change channels.)

I'm pretty sure that the signals coming in before the box are digital and after the box, they're converted to analog (let me know if that's incorrect) I've been trying to go directly from a cable splitter before the box to my MythTV box. I have the channel frequency set to US-Cable, and the TV format to NTSC. I have the card set up as an MPEG2 / DVB card as it should be. I have an XMLTV schedule setup and working and I have "Tuner 1" from the MPEG portion of the card and DVB from the digital portion of the card set to accept the XMLTV schedule as the input connection.

Is there anything I'm missing / I should try?

---

### Post by sofasurfer on 2008-11-14
CaptianPatent,bawilson2  and others... sorry I took so long to respond. Everything has fallen apart. Any progress I had made is gone.

When I was using Ubuntu 8.04 and trying to get the cx18 drivers and firmware working, in order to get my Hauppauge 1600 to work, I at first got the card to work. Then I reinstalled Ubuntu and then my card would not work anymore...It was not set up properly according to dmesg cx18. After MONTHS of trying to get this going again based on opions that I had the famous "mmio_ndelay" problem and was just about to give up when I accidently found that my problem could be fixed by removing my Hauppauge card, reinstalling Ubuntu and  then reinstall the card. Well, at this same time, Ubuntu 8.10 came out which eliminated the need to install cx18 drivers and firmware. So after wasting all that time I finally have my card working. I now can watch tv by using Mplayer or VLC.

Now I spend a week or so trying to get Mythtv working. After no success with Mythtv, Myth Desktop, Myth Frontend and Backend, etc, etc, I stumbled on The Mythbuntu 8.10 iso. I installed it on a empty partition and after a couple days some helpful people made suggestions which let me get my card working with Mythbuntu so that I could watch tv, although Mythbuntu did need some fine tuning. So I knew I was almost there and decided to finish up with a fresh, clean Mythbuntu 8.10 reinstall. 

AAAAHHHH!!!!!!!

Now I can not get Mythbuntu working again. How the hell long can I go on like this. Talk about throwing your life away on meaningless crap!!

Well, anyway. I am about done ranting.

I have now attempted ONCE AGAIN to set up mythbuntu. I have recorded ALL of my steps and settings to the best of my knowledge. 

From the number of people who have viewed this thread (over 1100), I know that I am not alone in my failures, so...

If anyone wants me to continue, I will post my settings so we can try to figure this out. 

Let me know.

---

### Post by bawilson2 on 2008-11-14
> **sofasurfer said:**
> CaptianPatent,bawilson2  and others... sorry I took so long to respond. Everything has fallen apart. Any progress I had made is gone.

When I was using Ubuntu 8.04 and trying to get the cx18 drivers and firmware working, in order to get my Hauppauge 1600 to work, I at first got the card to work. Then I reinstalled Ubuntu and then my card would not work anymore...It was not set up properly according to dmesg cx18. After MONTHS of trying to get this going again based on opions that I had the famous "mmio_ndelay" problem and was just about to give up when I accidently found that my problem could be fixed by removing my Hauppauge card, reinstalling Ubuntu and  then reinstall the card. Well, at this same time, Ubuntu 8.10 came out which eliminated the need to install cx18 drivers and firmware. So after wasting all that time I finally have my card working. I now can watch tv by using Mplayer or VLC.

Now I spend a week or so trying to get Mythtv working. After no success with Mythtv, Myth Desktop, Myth Frontend and Backend, etc, etc, I stumbled on The Mythbuntu 8.10 iso. I installed it on a empty partition and after a couple days some helpful people made suggestions which let me get my card working with Mythbuntu so that I could watch tv, although Mythbuntu did need some fine tuning. So I knew I was almost there and decided to finish up with a fresh, clean Mythbuntu 8.10 reinstall. 

AAAAHHHH!!!!!!!

Now I can not get Mythbuntu working again. How the hell long can I go on like this. Talk about throwing your life away on meaningless crap!!

Well, anyway. I am about done ranting.

I have now attempted ONCE AGAIN to set up mythbuntu. I have recorded ALL of my steps and settings to the best of my knowledge. 

From the number of people who have viewed this thread (over 1100), I know that I am not alone in my failures, so...

If anyone wants me to continue, I will post my settings so we can try to figure this out. 

Let me know.

So have you gotten things to work?  I was thinking if you still had issues I'd try doing a print screen of each of my setup windows since I have the same card and have it working to see if we could find the problem.

---

### Post by sofasurfer on 2008-11-14
If it is not a problem, your print screens would probably be a lot easier and faster than my writing everything out. Learning to do print screens is probably something I should put on my list of "things to learn".

So if you would do this for me we can quickly learn if I made a mistake in configuration.

---

### Post by bawilson2 on 2008-11-14
> **sofasurfer said:**
> If it is not a problem, your print screens would probably be a lot easier and faster than my writing everything out. Learning to do print screens is probably something I should put on my list of "things to learn".

So if you would do this for me we can quickly learn if I made a mistake in configuration.

First off... print screen is really easy.  Just press the button on the keyboard.  

I tried to attach a tar file with the screen shots but it was too big.  I've posted them to flickr instead.  Probably not the most tech savy way to do it but it was the quickest and easiest route I could come up with.  

Pictures are at:
[http://www.flickr.com/photos/32437882@N06/](http://www.flickr.com/photos/32437882@N06/)

You'll still probably have a few differences as I'm running multiple frontends on my network but it should be mostly the same.  Let me know what you find.

---

### Post by sofasurfer on 2008-11-14
Sorry to say that your screenshots were to blurry. I am going to post my screenshots to this thread. I'll do a few at first to be sure they are viewable.

---

### Post by sofasurfer on 2008-11-14
No, I quess I am not going to post screen shots. There is no screen shot function in Mythbuntu. Hmmm...

---

### Post by bawilson2 on 2008-11-14
> **sofasurfer said:**
> Sorry to say that your screenshots were to blurry. I am going to post my screenshots to this thread. I'll do a few at first to be sure they are viewable.

Were you able to click on each screen shot and enlarge it?  I'm not seeing them blurry at all.  They should all be able to be viewed at 1024 x 640.

---

### Post by sofasurfer on 2008-11-14
O crap!! I'm sorry for not thinking AGAIN.
I'll be going over them now. I'll write soon.

---

### Post by sofasurfer on 2008-11-14
It all looks good so far.
Some pages that you did not send me I will tell you what I have.

Under General...
Page 1.
Local backend
I.P. address 127.0.0.1
port 6543  status port 6544
security pin 0000 (recommended to allow for all users to access Myth)

Master backend
I.P. address 127.0.0.1
Port 6543

Page 2.
v.b.i. format none
Channel Freq table U.S. Bcast
Tmezone auto


Other than that I think everything is good.

I wonder if its possible that removing the card and restarting or reinstalling and then putting the card in would make a differance. Like I had to do to get the cx18 drivers to work in Ubuntu 8.04?

This makes no sense that the first time I installed Mythbuntu I was able to get Myth to function basically.

---

### Post by Mythgruntled on 2009-02-03
Is this thread still live? I'm having a similar issue to Sofasurfer (which I posted yesterday to [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6661388](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6661388) ) and I would be interested to hear if/how you resolved this issue.

---

