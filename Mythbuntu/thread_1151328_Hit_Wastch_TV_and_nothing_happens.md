---
title: "Hit Wastch TV and nothing happens"
date: 2009-05-06
forum: Mythbuntu
---

### Post by bgolpmp on 2009-05-06
Hello and thanks for reading. I just reinstalled mythbuntu 9.04 and am having the same trouble. When I hit watch tv, the screen goes blank for about 30 sec and then I Am right back where I started. Here is my log file.

2009-05-06 22:13:17.588 New DB connection, total: 2
2009-05-06 22:13:17.589 Connected to database 'mythconverg' at host: localhost
2009-05-06 22:13:17.591 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-05-06 22:13:17.591 Enabled verbose msgs:  important general
2009-05-06 22:13:18.056 No theme dir: /home/andy/.mythtv/themes/Mythbuntu-8.04
2009-05-06 22:13:18.059 Primary screen 0.
2009-05-06 22:13:18.059 Using screen 0, 1024x768 at 0,0
2009-05-06 22:13:18.060 No theme dir: /home/andy/.mythtv/themes/Mythbuntu-8.04
2009-05-06 22:13:18.060 Switching to square mode (Mythbuntu-8.04)
2009-05-06 22:13:18.073 Using the Qt painter
2009-05-06 22:13:18.074 JoystickMenuClient Error: Joystick disabled - Failed to read /home/andy/.mythtv/joystickmenurc
2009-05-06 22:13:18.075 lirc init success using configuration file: /home/andy/.mythtv/lircrc
2009-05-06 22:13:19.137 Specified base font 'medium' does not exist for font clock
2009-05-06 22:13:19.137 Specified base font 'medium' does not exist for font small
2009-05-06 22:13:19.137 Specified base font 'medium' does not exist for font medium
2009-05-06 22:13:19.138 Specified base font 'medium' does not exist for font large
2009-05-06 22:13:19.139 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-06 22:13:19.214 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-06 22:13:19.330 Registering Internal as a media playback plugin.
2009-05-06 22:13:19.486 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-06 22:13:19.520 Failed to run 'cdrecord --scanbus'
2009-05-06 22:13:19.530 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-05-06 22:13:19.534 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-05-06 22:13:19.583 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.105:5060 NAT address 192.168.1.105
SIP: Cannot register; proxy, username or password not set
2009-05-06 22:13:19.723 No theme dir: /home/andy/.mythtv/themes/Mythbuntu-8.04
2009-05-06 22:13:21.904 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-05-06 22:13:21.905 Using protocol version 40
2009-05-06 22:13:21.922 TV: Attempting to change from None to WatchingLiveTV
2009-05-06 22:13:21.923 Using protocol version 40
2009-05-06 22:13:23.128 DPMS Deactivated 
2009-05-06 22:14:03.097 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-05-06 22:14:03.097 TV Error: LiveTV not successfully started
2009-05-06 22:14:03.183 TV: Deleting TV Chain in destructor
2009-05-06 22:14:03.185 DPMS Reactivated.


This is driving me nuts!!!!!!!!!!!!!!!!!!!!!!! Please help!!!
I am running a hauppauge 500 card.

Thanks

---

### Post by nickrout on 2009-05-06
What is your TV card?

---

### Post by bgolpmp on 2009-05-06
it is a hauppauge 500

---

### Post by nickrout on 2009-05-06
sorry yes I see that now from your 1st post!

Is it a PVR-500? (or some other model with 500 in the name?)

What did you set it up as in mythtv-setup.

I assume you have set up (in this order)

capture card
video source
input connection
channel editor

---

### Post by bgolpmp on 2009-05-06
I would have answered them in the order they asked them. I am going to go through the configuration again and make sure I did not miss anything, but I am sure that will not work.
 
Thanks
Andy

---

### Post by nickrout on 2009-05-06
do make sure you set it up as an ivtv card (i think thats what the option is called these days), not as a frame grabber.

---

### Post by bgolpmp on 2009-05-07
Nickrout YOU ARE THE MAN!!!!!!!!!
 
All I did was choose the wrong type of card!!!!!
 
THANKS
 
Now I have to figure the rest out!!!
 
THANKS AGAIN 
Now I can go to sleep!!

---

### Post by ktmom on 2009-05-19
Yes, thank you.

---

