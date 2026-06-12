---
title: "cant watch .iso videos (dvd) from frontend +more problems"
date: 2007-11-06
forum: Mythbuntu
---

### Post by gsrcrxsi on 2007-11-06
i turned all my saved DVD's from VIDEO_TS directories to .iso files. mythtv now recognizes them and plays them fine on the backend/frontend machine. however i cant seem to get anything to play on the remote frontend. if i go to

Media Library -> watch video

i can see my movies, but the covers from IMDB are gone, info is still there. but when i try to play them, it says that the file does not exist. does the frontend have to mount the backends /var/lib/ partition (thats where all the recordings and movie files are) to be able to watch them? i can see and watch the recordings (which are also on /var/lib, but its slow and glitchy like is explained below) on the remote frontend, which doesnt really make sense that it can see those files but not the videos. i have the video directory set to the default /var/lib/mythtv/videos (same as the backend/frontend) but it doesnt work on the frontend only box. if i have to mount the partition, how do i do that? and how do i make it so that the front end does that automatically?

im also having a problem where if i try to watch live tv on the frontend only box, the playback it very glitches and its like the processor cant handle it, but its SDTV on a 1.8GHz processor and a a good video card (nvidia 7300GT + nvidia drivers +video out via svid). the backend is wireless and the frontend is wired to the router, do you think its getting hung up through the network? the backend is just in the other room, and its wireless G, so i igure it can handle the mpeg-2 stream, but maybe not? maybe up it to a wireless-N setup? in addition, i cant seem to get a static IP address setup on the wireless. if i try manua config, it will no longer conntect and im sure all the settings are correct.

and the other problem im having is the audio on the frontend. its VERY low. if i try to turn it up with the tv, i have to turn it up very loud and i get a buzzing/humming as a result.

Backend/Frontend machine:
asus p4g8x delux MB
p4 2.4 GHz
1 GB ram
320 GB HD - winxp
500 GB HD - myth (15 GB for "/", 2 GB for swap, rest on "/var/lib")
ati 9600 vid card - open source drivers
hauppage pvr-150 tuner card

Frontend machine
intel dg965pz MB
celeron 1.8 GHz processor
1 GB ram
40 GB HD
nvidia 7300GT + nvidia drivers

any help on any or all of this is much appreciated :)

---

### Post by superm1 on 2007-11-06
Yes, you do have to mount the videos on the frontend.  You can enable NFS in MCC.  Be sure to put in the Mythbuntu CD before you open up and his the apply button though.  It pulls a few for the packages off of the CD.

As for your video stuttering, consider enabling the options for caching the audio under the general settings page on the frontend.

Audio stuff: same thing here, turn the default mixers on that same page up a bit.

---

### Post by gsrcrxsi on 2007-11-06
thanks. i enabled NFS, but i dont know how to use it. i want to have the drive mounted on startup so that i can access the videos on startup. someone on another forum mentioned that i would have to make some changes to /etc/fstab but i dont exactly know how to do that from within mythbuntu. 

i know ill have to excecute a code similar to this: (make changes as necessary!)

```
 mount -t nfs 192.168.2.101:/var/lib /var/lib
```

and then what would i have to point mythtv front end to? the same default location?

---

### Post by superm1 on 2007-11-07
Okay so after you enabled NFS in mcc, if you look at /etc/exports, you can see what shares are already being exported.

On your frontend machine, you will then add something to /etc/fstab like this:

```
mythdell://var/lib/mythtv  /var/lib/mythtv   nfs     defaults,user,soft,nointr 0 0
```
This is for my setup (with a machine called mythdell)

Hopefully you can make sense of it.

After you do that, it will automount upon reboot.

Do a test mount by mounting like this (before reboot)

```
mount /var/lib/mythtv
```

---

### Post by gsrcrxsi on 2007-11-07
ok i did (used the IP address of the backend because it couldnt find it from the hostname) that and when i try to mount it, it says "failed, reason given by server: Permission denied"

 from the frontend i typed this in /etc/fstab

```
192.168.2.101://var/lib/mythtv  /var/lib/mythtv   nfs     defaults,user,soft,nointr 0 0
```

where '192.168.2.101' is the IP for my backend named 'MythTVBackend'

---

### Post by superm1 on 2007-11-07
> **gsrcrxsi said:**
> ok i did (used the IP address of the backend because it couldnt find it from the hostname) that and when i try to mount it, it says "failed, reason given by server: Permission denied"

 from the frontend i typed this in /etc/fstab

```
192.168.2.101l://var/lib/mythtv  /var/lib/mythtv   nfs     defaults,user,soft,nointr 0 0
```where '192.168.2.101' is the IP for my backend named 'MythTVBackend'
You appear to have typed your ip address wrong in that.  It looks like you have 192.168.2.101l rather than 192.168.2.101.

Also, make sure that is the correct path that you want to export, it may not be identical.

---

### Post by gsrcrxsi on 2007-11-07
i typed it wrong here, not in the terminal. 

that path is correct. to be clear im doing all this from the frontend right? not the backend? when i try to mount, it says the backend is denying me permission, so wouldnt i have to change something there?

---

### Post by superm1 on 2007-11-07
> **gsrcrxsi said:**
> i typed it wrong here, not in the terminal. 

that path is correct. to be clear im doing all this from the frontend right? not the backend? when i try to mount, it says the backend is denying me permission, so wouldnt i have to change something there?
Make sure its the same exported path on the backend.  You can try to update the exported filesystems on the backend by typing.

```
exportfs -a
```

---

### Post by gsrcrxsi on 2007-11-07
ok im starting to get a little confused now.

do i have to type anything in the /etc/exports? 

i know it seems like you are telling me the same thing over and over, but im a n00b and dont really understand how all this stuff works. 

ill try to provide as much info about my system as i can

backend:
hostname: MythTVBackend
IP: 192.168.2.101 ( for now. DHCP wireless, i still cant make this static, it wont work for some reason)

frontend
hostname: MythTVFrontend
IP: 192.168.2.102 (DHCP wired)

what exactly do i have to do on the backend and the frontend to do what i want to do? 

my /etc/exports on the backend looks like:

```
/var/lib/mythtv/videos    *(-some options-)
/var/lib/mythtv/recordings    *(-some options-)
/var/lib/mythtv/pictures    *(-some options-)
/var/lib/mythtv/games   *(-some options-)
```

and on the frontend

```
/var/lib/mythtv/videos    *(-some options-)
/var/lib/mythtv/pictures    *(-some options-)
/var/lib/mythtv/games   *(-some options-)
```

---

### Post by gsrcrxsi on 2007-11-07
note : -some options- just represents that there are options listed there. im not at the terminal so i cant see for sure and i dont remmeber exactly what they are.

---

### Post by laga on 2007-11-09
Hi,

can you try to mount "/var/lib/mythtv/video" to "/var/lib/mythtv/video" instead of just using "/var/lib/mythtv"?

---

### Post by gsrcrxsi on 2007-11-09
i got it figured out. but the stream is all glitchy. im thinking its because of the backend being wireless though. same for tv, video, and recordings. im gonna try running a wire and seeing if tha helps.

but now im having issues ripping DVD's. it says that there are no jobs. even though the dvd will play.

---

### Post by gsrcrxsi on 2007-11-10
ok i think my wireless netowrk is causing lag in the stream. i hard wired it all and tv and recorded tv streams were fine. movies were still a little slow, but i think its because my wireless router only hass 100 ports so its getting limited there (both backend and frontends have gigabit lan) so im gonna check out some wireless N routers and see if that will fix my issues with that.

but i need to find a solution for my DVDs. dvd shrink is inconsistent and it sucks having to transfer them all over manually. i would like to use mythtv to rip the dvd's to .iso's and then put them in the correct directory. but MythDVD doesnt work. it tells me that there are no jobs. but it will play the dvd. how do i fix this?

---

### Post by superm1 on 2007-11-10
Press the '1' key to start the mtd daemon.

---

### Post by gsrcrxsi on 2007-11-10
at the no jobs screen?

---

### Post by superm1 on 2007-11-10
yes.

Alternatively, you can start mtd manually in a terminal if you want to see if there is any error messages.

---

### Post by gsrcrxsi on 2007-11-11
ok well it seems to be dependent on the dvd. some dvd's ill put in, it plays(studering playback...) but wont rip, and some wont play(it just goes black screen then back to the menu) , and it will go to the transcoding screen. it selects the main title for ripping to an iso image. i press 0 to rip, the progress screen comes up it works for like a second and then says nothing left to do. whats going on here?

and typing mtd in the terminal will just say its already running. 

everything i explained happens on both the frontend and frontend/backend. any ideas?

---

### Post by superm1 on 2007-11-11
> **gsrcrxsi said:**
> ok well it seems to be dependent on the dvd. some dvd's ill put in, it plays(studering playback...) but wont rip, and some wont play(it just goes black screen then back to the menu) , and it will go to the transcoding screen. it selects the main title for ripping to an iso image. i press 0 to rip, the progress screen comes up it works for like a second and then says nothing left to do. whats going on here?

and typing mtd in the terminal will just say its already running. 

everything i explained happens on both the frontend and frontend/backend. any ideas?
The best thing to do is see what /var/log/mythtv/mythfrontend.log is saying while you are trying to rip.   It should be pretty friendly to the exact issue happening...

---

### Post by gsrcrxsi on 2007-11-11
ok this is the output of the /var/log/mythtv/mythfrontend.log

```
Starting mythfrontend.real..
2007-11-11 12:27:13.485 Current Schema Version: 1160
2007-11-11 12:27:13.512 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-11-11 12:27:13.513 Enabled verbose msgs:  important general
2007-11-11 12:27:15.324 Total desktop dim: 1600x1200, with 1 screen[s].
2007-11-11 12:27:15.326 Using screen 0, 1600x1200 at 0,0
2007-11-11 12:27:15.327 Switching to square mode (Retro)
2007-11-11 12:27:15.363 Using the Qt painter
2007-11-11 12:27:15.809 Joystick disabled.
2007-11-11 12:27:18.003 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-11 12:27:18.320 Registering Internal as a media playback plugin.
2007-11-11 12:27:18.459 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-11 12:27:18.477 Mediamonitor: Adding /dev/scd0
2007-11-11 12:27:18.478 Mediamonitor: Adding /dev/scd1
2007-11-11 12:27:18.483 Mediamonitor: Adding /dev/fd0
2007-11-11 12:27:18.535 Mediamonitor: AddDevice() -- Not adding '/dev/scd0', it appears to be a duplicate.
2007-11-11 12:27:18.541 Mediamonitor: AddDevice() -- Not adding '/dev/scd1', it appears to be a duplicate.
2007-11-11 12:27:18.542 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-11 12:27:18.628 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-11 12:27:18.628 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2007-11-11 12:27:18.628 MonitorRegisterExtensions(0x100, gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-11 12:27:18.965 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-11 12:27:18.965 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-11-11 12:27:18.965 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.104:5060 NAT address 192.168.2.104
SIP: Cannot register; proxy, username or password not set
2007-11-11 12:27:19.207 Starting media monitor.
2007-11-11 12:27:23.526 New DB connection, total: 2
2007-11-11 12:27:23.529 Connected to database 'mythconverg' at host: 192.168.2.104
2007-11-11 12:27:23.578 Connecting to backend server: 192.168.2.104:6543 (try 1 of 5)
2007-11-11 12:27:23.580 Using protocol version 31
2007-11-11 12:27:23.612 TV: Attempting to change from None to WatchingLiveTV
2007-11-11 12:27:23.613 Using protocol version 31
2007-11-11 12:27:24.894 DPMS Deactivated
2007-11-11 12:27:25.040 AFD: Opened codec 0x831ebd0, id(MPEG2VIDEO) type(Video)
2007-11-11 12:27:25.062 AFD: Opened codec 0x8322bc0, id(MP2) type(Audio)
2007-11-11 12:27:25.090 Opening ALSA audio device 'default'.
2007-11-11 12:27:25.292 VideoOutputXv: XvMCTex: Init failed
2007-11-11 12:27:25.311 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2007-11-11 12:27:26.171 TV: Changing from None to WatchingLiveTV
2007-11-11 12:27:26.205 Realtime priority would require SUID as root.
2007-11-11 12:27:26.450 Video timing method: DRM
2007-11-11 12:27:30.309 TV: Attempting to change from WatchingLiveTV to None
2007-11-11 12:27:30.519 TV: Changing from WatchingLiveTV to None
2007-11-11 12:27:30.525 DPMS Reactivated.
2007-11-11 12:27:35.922 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml
Destroying SipFsm object
Starting mythfrontend.real..
2007-11-11 12:28:12.983 Current Schema Version: 1160
2007-11-11 12:28:12.985 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-11-11 12:28:12.985 Enabled verbose msgs:  important general
2007-11-11 12:28:14.858 Total desktop dim: 1600x1200, with 1 screen[s].
2007-11-11 12:28:14.860 Using screen 0, 1600x1200 at 0,0
2007-11-11 12:28:14.861 Switching to square mode (Retro)
2007-11-11 12:28:14.873 Using the Qt painter
2007-11-11 12:28:15.281 Joystick disabled.
2007-11-11 12:28:17.201 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-11 12:28:17.503 Registering Internal as a media playback plugin.
2007-11-11 12:28:17.561 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-11 12:28:17.562 Mediamonitor: Adding /dev/scd0
2007-11-11 12:28:17.563 Mediamonitor: Adding /dev/scd1
2007-11-11 12:28:17.569 Mediamonitor: Adding /dev/fd0
2007-11-11 12:28:17.581 Mediamonitor: AddDevice() -- Not adding '/dev/scd0', it appears to be a duplicate.
2007-11-11 12:28:17.588 Mediamonitor: AddDevice() -- Not adding '/dev/scd1', it appears to be a duplicate.
2007-11-11 12:28:17.589 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-11 12:28:17.628 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-11 12:28:17.628 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2007-11-11 12:28:17.629 MonitorRegisterExtensions(0x100, gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-11 12:28:17.762 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-11 12:28:17.762 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-11-11 12:28:17.762 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-11-11 12:28:17.890 New DB connection, total: 2
2007-11-11 12:28:17.902 Starting media monitor.
2007-11-11 12:28:17.948 Connected to database 'mythconverg' at host: 192.168.2.104
SIP listening on IP Address 192.168.2.104:5060 NAT address 192.168.2.104
SIP: Cannot register; proxy, username or password not set
2007-11-11 12:29:01.054 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml
2007-11-11 12:29:15.334 Connecting to backend server: 192.168.2.104:6543 (try 1 of 5)
2007-11-11 12:29:15.339 Using protocol version 31
Destroying SipFsm object
Starting mythfrontend.real..
2007-11-11 12:29:52.364 Current Schema Version: 1160
2007-11-11 12:29:52.366 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-11-11 12:29:52.366 Enabled verbose msgs:  important general
2007-11-11 12:29:54.188 Total desktop dim: 1600x1200, with 1 screen[s].
2007-11-11 12:29:54.190 Using screen 0, 1600x1200 at 0,0
2007-11-11 12:29:54.191 Switching to square mode (Retro)
2007-11-11 12:29:54.204 Using the Qt painter
2007-11-11 12:29:54.633 Joystick disabled.
2007-11-11 12:29:56.517 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-11 12:29:56.822 Registering Internal as a media playback plugin.
2007-11-11 12:29:56.882 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-11 12:29:56.883 Mediamonitor: Adding /dev/scd0
2007-11-11 12:29:56.884 Mediamonitor: Adding /dev/scd1
2007-11-11 12:29:56.900 Mediamonitor: AddDevice() -- Not adding '/dev/scd0', it appears to be a duplicate.
2007-11-11 12:29:56.906 Mediamonitor: AddDevice() -- Not adding '/dev/scd1', it appears to be a duplicate.
2007-11-11 12:29:56.907 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-11 12:29:56.946 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-11 12:29:56.947 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2007-11-11 12:29:56.947 MonitorRegisterExtensions(0x100, gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-11 12:29:57.068 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-11 12:29:57.068 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-11-11 12:29:57.068 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.104:5060 NAT address 192.168.2.104
2007-11-11 12:29:57.202 Starting media monitor.
SIP: Cannot register; proxy, username or password not set
2007-11-11 12:30:02.710 New DB connection, total: 2
2007-11-11 12:30:02.712 Connected to database 'mythconverg' at host: 192.168.2.104
QDate::fromString: Parameter out of range
2007-11-11 12:30:02.754 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Encrypted DVD support unavailable.
*** Zero check failed in ifo_read.c:1727
    for pgci_ut->zero_1 = 0xbab5

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1729 ***
*** for pgci_ut->nr_of_lus < 100 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1772 ***
*** for (pgci_ut->lu[i].exists & 0x07) == 0 ***

libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: PI
libdvdnav: DVD Serial Number: 256a9477
libdvdnav: DVD Title (Alternative): PI
libdvdnav: Unable to find map file '/home/icrum/.dvdnav/PI.map'
libdvdnav: vm: ifoRead_PGCI_UT failed
2007-11-11 12:30:04.818 Failed to open DVD device at //dev/scd0
2007-11-11 12:30:09.628 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml
2007-11-11 12:30:21.620 Connecting to backend server: 192.168.2.104:6543 (try 1 of 5)
2007-11-11 12:30:21.621 Using protocol version 31
Destroying SipFsm object

```

---

### Post by gsrcrxsi on 2007-11-12
bump, i dont know what that output means. what should i do?

---

### Post by Prefader on 2007-11-26
> Encrypted DVD support unavailable
You may need to install the libdvdcss2 package, if you haven't already.  Search the forums for help with that, and keep in mind that this may not be legal depending on which country you live in.

---

