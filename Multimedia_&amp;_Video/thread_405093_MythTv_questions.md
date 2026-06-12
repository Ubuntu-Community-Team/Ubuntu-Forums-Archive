---
title: "MythTv questions"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by whein on 2007-04-09
Ok, finally got MythTv installed on a fresh Edgy box.  A few wrinkles still exist so hopefully someone here can help.

1) The computer this is installed on has no internet connection.  :(  Is there a way I can manually download TV listings (from Zap2It) every so often from another computer, transfer them over, and get MythTV to incorporate them?

2) I have a PVR-350 that came with the gray Hauppauge remote.  I'm using the lircd.conf and lircrc example files pointed to from [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy).  These are:
[https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge](https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge)
and
[http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt)
respectively.
I can change the channel if I press 5,3 or 2,2 but not if I press the channel up/down buttons.  I *think* this is just a naming problem where the lircd.conf file calls them "CH+" and "CH-" while the lircrc file calls them "Channel-UP" and "Channel-DOWN".  Anyone else run into this problem and can I fix this just by making them match?  I assume the real name is arbitrary, just so long as it is consistent?

3) Is there a way to make Myth actually display the button presses for the numbers after I've pressed them but before the channel changes?  What I mean is if I'm pressing 5,3 to change to channel 53, can I make it display the leading 5 before I press the 3 instead of waiting until the channel changes and then showing me 53?  This way I can tell if I press the wrong button.

Other than these, I'm pretty darned happy!  Kudos to all the people who worked on the tutorials, I got _much_ further this time than a six months ago....  :)
-Will

---

### Post by wjston on 2007-04-09
> **whein said:**
> Ok, finally got MythTv installed on a fresh Edgy box.  A few wrinkles still exist so hopefully someone here can help.

1) The computer this is installed on has no internet connection.  :(  Is there a way I can manually download TV listings (from Zap2It) every so often from another computer, transfer them over, and get MythTV to incorporate them?

Not sure about this (I think you have to connect to the internet), but maybe someone else can answer this more definite.

> 2) I have a PVR-350 that came with the gray Hauppauge remote.  I'm using the lircd.conf and lircrc example files pointed to from [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy).  These are:
[https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge](https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge)
and
[http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt)
respectively.
I can change the channel if I press 5,3 or 2,2 but not if I press the channel up/down buttons.  I *think* this is just a naming problem where the lircd.conf file calls them "CH+" and "CH-" while the lircrc file calls them "Channel-UP" and "Channel-DOWN".  Anyone else run into this problem and can I fix this just by making them match?  I assume the real name is arbitrary, just so long as it is consistent?

The two files have to be exact with respect to names - even the case (upper/lower) must match; otherwise, the remote button won't function. Changing the "Channel-UP" and "Channel-DOWN" to "CH+" and "CH-" will enable channel changing using these buttons on your remote.

> 3) Is there a way to make Myth actually display the button presses for the numbers after I've pressed them but before the channel changes?  What I mean is if I'm pressing 5,3 to change to channel 53, can I make it display the leading 5 before I press the 3 instead of waiting until the channel changes and then showing me 53?  This way I can tell if I press the wrong button.

Mine does display the button number when I want to change channels, so I'm not sure why yours doesn't. Maybe  there is a setting in the setup that I configured. I'll check later today and post if I find something.

---

### Post by Dubstar_04 on 2007-04-09
Whein,

With respect to the channel changing problems you have a few options, 

1. configure one of your buttons to 'jump to'' the tvguide from live tv this way you can browse the channel you want and select the program of your choice. options for this are in the Edit keys (guide button) and tv settings > tv guide > change channel with select.

2. I use the retro-osd which seems to allow what you require if i press 1 - 2 it will halt for a second and then change to channel 12.

3. you can use the channel up and down buttons to scroll through the listings on the OSD and then select the program you require (like sky does) 

The internet issue could be solved by using a dvb card (europe and OZ) so that may well be an option if available in your region.

I have attached a few screenshots to help show the changing options. 


I hope this helps.

Dubstar_04

---

### Post by whein on 2007-04-10
Ok, couple problems solved, couple new ones.

The differences between my lircd.conf and lircrc file were the cause of my channel up/down button not working (found a couple other bugs too...)  I need to do some reading on what Myth can take as arguments and maybe make it a little more customized, but for now it works well enough.

Not sure what I did, but sometimes the numbers now show up on screen as soon as I press them, sometimes not.  But I can live with it.

I messed around with the Zap2It site a bit and have come to the conclusion that while I *could* do it manually, it would be way too much headache.  I can live without a TV guide for the near future.

New problems:
When I exit the front end completely (back to the desktop) and then restart the front end, I cannot watch live tv.  I get an error saying that all available tuners (I only have one) are in use.  I've tried stopping and restarting the back end but that will not fix it.  Only fix so far is a reboot.  :(

On some of the setup screens, when there is a description of the setting at the bottom of the screen, the words are often cut off in mid sentence.  I can't find any way to scroll the description or make the font smaller so it all fits on the screen.  :(

I am getting errors when I run the front end
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```What does this mean and how do I fix it?  I tried looking it up on Google but did not get anything very helpful.  A few people said to ignore it, but I say an error is an error and should be addressed.  It also wasn't doing this previously.

So close.....
-Will

---

### Post by wjston on 2007-04-12
> **whein said:**
> 
New problems:
When I exit the front end completely (back to the desktop) and then restart the front end, I cannot watch live tv.  I get an error saying that all available tuners (I only have one) are in use.  I've tried stopping and restarting the back end but that will not fix it.  Only fix so far is a reboot.  :(

On some of the setup screens, when there is a description of the setting at the bottom of the screen, the words are often cut off in mid sentence.  I can't find any way to scroll the description or make the font smaller so it all fits on the screen.  :(

I am getting errors when I run the front end
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```What does this mean and how do I fix it?  I tried looking it up on Google but did not get anything very helpful.  A few people said to ignore it, but I say an error is an error and should be addressed.  It also wasn't doing this previously.

So close.....
-Will

The first problem sounds like you are ending up with a second frontend starting up, which isn't a good thing. I am not sure how to fix that, but maybe someone else can help.

Second issue is a common bug in Edgy. The 169 error can be fixed by altering your xorg.conf file. Remember to back it up first.

**To backup your configuration: open a terminal and write:**
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

**Edit /etc/X11/xorg.conf : open a terminal and write:**
sudo nano /etc/X11/xorg.conf

**Under _Section "ServerLayout"_ comment out:**
        InputDevice "stylus" "SendCoreEvents"
        InputDevice "cursor" "SendCoreEvents"
        InputDevice "eraser" "SendCoreEvents"
**so that it looks like this:**
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"

[COLOR="Blue"](I also deleted all reference to "wacom" under _Section "InputDevice"_ as I only use my system as a pvr).[/COLOR]

**Save the file and restart the computer.**

If you encounter any problems (the graphical interface does not load) just restore the backup with:
sudo cp -a /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

and restart the computer.

Hope this helps!

---

### Post by whein on 2007-04-12
wjston:
> The first problem sounds like you are ending up with a second front end starting up, which isn't a good thing. I am not sure how to fix that, but maybe someone else can help.

I'm not sure this is the case.  I did a little more experimentation last night and if I am in the front end, I can watch TV, but if I close the TV screen by going back to the main setup menu (Pressing Esc on the keyboard or Exit on the remote) and then try to watch TV again *with the same front end* it also fails.  I get a black screen and a bunch of output in the terminal.  I'll copy it down this evening and post it.  Given that stopping and restarting the back end does not solve the problem my only hunch is that the hardware on the PVR-350 isn't shutting down properly.  Maybe I can get around this by not using the onboard MPEG-2 encoder, but I'll be pissed if that's the fix.  The entire point of getting that card was the encoder/decoder hardware.  I'll let you know what I find out tonight.

On the bright side I was able to find the configuration menu for fonts (at least for the front end) and set them to a much smaller (and more readable) size.  Yay!

-Will

---

### Post by whein on 2007-04-13
OK, the results of last night's experimentation:
Removing the "wacom" and related references from /etc/X11/xorg.conf fixed one of the X errors.  But there is another, different one that shows up in the terminal output, copied below.

I ran the front end a couple times last night.  The first time all I did was set it to watch live TV, then exited back to the main menu, then watched live TV again.  I did NOT change the channel while watching live TV.  Doing this I was able to successfully open and close the tuner and get video out multiple times.  I even closed the frontend and restarted it and was able to watch live TV.

Next I tried changing channel just by pressing the number keys to change.  I was able to exit back to the menu and the watch live TV again a couple of times without problem.  But not every time.  The last go round I tried it had the same problem as before, where it would go to a black screen and then spew a bunch of lines like the following to the terminal.
```
2007-04-12 23:10:35.880 NVP: Prebuffer wait timed out 10 times.
```
If I close and restart the frontend I get the error that all the available sources for the channel I want to watch are busy.

I think the theme I'm using is retro or something that sounds similar.  It has a menu page that displays the status of the machine.  After the errors I tried checking the status and no errors were shown and the tuner was shown as idle.

I experimented with just restarting the X session to see if that would reset the encoder, but nothing short of a full reboot seems to fix the problem.

My terminal output for the evening follows. (in two posts cause the forms think it't too long...)
-Will


```
whein@MythTvBox:~$ sudo /etc/init.d/mythtv-backend stop
Password:
Stopping MythTV server: mythbackend .
whein@MythTvBox:~$ mythtv-setup
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-12 22:33:14.985 Using runtime prefix = /usr
2007-04-12 22:33:15.030 Gnome-Screensaver support enabled
2007-04-12 22:33:15.031 DPMS is active.
2007-04-12 22:33:15.088 New DB connection, total: 1
2007-04-12 22:33:15.126 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:33:15.129 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:33:15.149 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:33:15.186 Current Schema Version: 1160
2007-04-12 22:33:15.239 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:33:15.241 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:33:15.242 Switching to square mode (Retro)
2007-04-12 22:33:15.440 Using the OpenGL painter
2007-04-12 22:33:16.661 Joystick disabled.
2007-04-12 22:33:16.668 New DB connection, total: 2
2007-04-12 22:33:16.676 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:33:16.971 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 22:33:35.830 Using NV NPOT texture extension
2007-04-12 22:34:32.302 DiSEqCDevTree, Warning: No device tree for cardid 1
2007-04-12 22:34:32.323 DiSEqCDevTree, Warning: No device tree for cardid 1
2007-04-12 22:34:42.448 New DB connection, total: 3
2007-04-12 22:34:42.449 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:34:42.489 New DB connection, total: 4
2007-04-12 22:34:42.490 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:34:42.492 New DB connection, total: 5
2007-04-12 22:34:42.493 Connected to database 'mythconverg' at host: 192.168.0.2
whein@MythTvBox:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
whein@MythTvBox:~$ 

```

---

### Post by whein on 2007-04-13
More of the terminal output:
> whein@MythTvBox:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-12 22:35:18.657 Using runtime prefix = /usr
2007-04-12 22:35:18.691 Gnome-Screensaver support enabled
2007-04-12 22:35:18.720 DPMS is active.
2007-04-12 22:35:18.769 New DB connection, total: 1
2007-04-12 22:35:18.777 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:35:18.785 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:35:18.789 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:35:18.819 Current Schema Version: 1160
2007-04-12 22:35:18.819 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 22:35:18.819 Enabled verbose msgs:  important general
2007-04-12 22:35:19.483 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:35:19.485 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:35:19.485 Switching to square mode (Retro)
2007-04-12 22:35:19.549 Using the OpenGL painter
2007-04-12 22:35:20.497 Joystick disabled.
2007-04-12 22:35:20.712 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 22:35:21.377 Registering Internal as a media playback plugin.
2007-04-12 22:35:21.521 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-12 22:35:21.542 Mediamonitor: Adding /dev/hdd
no record for '/block/hdd/device' in database
no record for '/block/hdd/holders' in database
no record for '/block/hdd/queue' in database
no record for '/block/hdd/slaves' in database
2007-04-12 22:35:21.622 Mediamonitor: AddDevice() -- Not adding '/dev/hdd', it appears to be a duplicate.
2007-04-12 22:35:21.624 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-12 22:35:22.104 Using NV NPOT texture extension
Failed to run 'cdrecord --scanbus'
adding: ATAPI:0,1,0 -- COMBO SOHC-5236V
2007-04-12 22:35:23.759 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-12 22:35:23.760 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-12 22:35:23.760 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-04-12 22:35:24.142 Starting media monitor.
2007-04-12 22:35:24.144 NetworkControl: Listening for remote connections on port 6546
2007-04-12 22:35:24.149 Executing '/usr/bin/pmount /dev/hdd'
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0
2007-04-12 22:35:24.339 Failed to mount /dev/hdd.
2007-04-12 22:35:24.342 Media status changed...  New status is: MEDIASTAT_MOUNTED old status was MEDIASTAT_NOTMOUNTED
2007-04-12 22:35:24.342 Posting MediaEvent
2007-04-12 22:38:50.986 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2007-04-12 22:38:50.992 Using protocol version 31
2007-04-12 22:38:51.005 Received a remote 'Clear Cache' request
2007-04-12 22:39:09.479 Received a remote 'Clear Cache' request
2007-04-12 22:39:52.238 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/keyboard/en_us_ui.xml
2007-04-12 22:40:14.359 Received a remote 'Clear Cache' request
2007-04-12 22:40:40.431 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
QDateTime::fromString: Parameter out of range
2007-04-12 22:40:43.926 New DB connection, total: 2
2007-04-12 22:40:43.927 Connected to database 'mythconverg' at host: 192.168.0.2
QDateTime::fromString: Parameter out of range
2007-04-12 22:41:21.984 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 22:41:21.986 Using protocol version 31
2007-04-12 22:41:23.269 DPMS Deactivated 
2007-04-12 22:41:23.502 AFD: Opened codec 0xbc82d0, id(MPEG2VIDEO) type(Video)
2007-04-12 22:41:23.587 AFD: Opened codec 0xbc8e10, id(MP2) type(Audio)
2007-04-12 22:41:23.778 Opening OSS audio device '/dev/dsp'.
2007-04-12 22:41:23.924 VideoOutputXv: XvMCTex: Init failed
2007-04-12 22:41:23.926 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x1b6
2007-04-12 22:41:24.824 TV: Changing from None to WatchingLiveTV
2007-04-12 22:41:24.826 New DB connection, total: 3
2007-04-12 22:41:24.827 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:41:24.830 Using realtime priority.
2007-04-12 22:41:24.937 Video timing method: USleep with busy wait
2007-04-12 22:41:34.841 NVP: prebuffering pause
2007-04-12 22:41:52.433 NVP: prebuffering pause
2007-04-12 22:41:55.709 NVP: prebuffering pause
2007-04-12 22:41:59.630 NVP: prebuffering pause
2007-04-12 22:42:02.402 NVP: prebuffering pause
2007-04-12 22:42:26.119 NVP: prebuffering pause
2007-04-12 22:42:31.374 NVP: prebuffering pause
2007-04-12 22:42:39.739 NVP: prebuffering pause
2007-04-12 22:42:47.763 NVP: prebuffering pause
2007-04-12 22:42:50.275 NVP: prebuffering pause
2007-04-12 22:43:13.019 NVP: prebuffering pause
2007-04-12 22:43:15.732 NVP: prebuffering pause
2007-04-12 22:43:22.104 NVP: prebuffering pause
2007-04-12 22:43:32.433 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 22:43:32.880 TV: Changing from WatchingLiveTV to None
2007-04-12 22:43:32.900 DPMS Reactivated.
2007-04-12 22:43:35.713 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
QDateTime::fromString: Parameter out of range
2007-04-12 22:43:49.141 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 22:43:49.142 Using protocol version 31
2007-04-12 22:43:50.032 DPMS Deactivated 
2007-04-12 22:43:51.327 RingBuf(/var/lib/mythtv//1002_20070412224349.mpg): Waited 1.0 seconds for data to become available...
2007-04-12 22:43:51.327 Checking to see if there's a new livetv program to switch to..
2007-04-12 22:43:52.351 RingBuf(/var/lib/mythtv//1002_20070412224349.mpg): Waited 2.0 seconds for data to become available...
2007-04-12 22:43:52.351 Checking to see if there's a new livetv program to switch to..
2007-04-12 22:43:54.399 RingBuf(/var/lib/mythtv//1002_20070412224349.mpg): Waited 4.0 seconds for data to become available...
2007-04-12 22:43:54.399 Checking to see if there's a new livetv program to switch to..
2007-04-12 22:43:58.495 RingBuf(/var/lib/mythtv//1002_20070412224349.mpg): Waited 8.0 seconds for data to become available...
2007-04-12 22:43:58.495 Checking to see if there's a new livetv program to switch to..
2007-04-12 22:44:06.431 RingBuf(/var/lib/mythtv//1002_20070412224349.mpg) Error: Waited 16 seconds for data, aborting.
2007-04-12 22:44:06.433 AFD: Opened codec 0xc1d5e0, id(MPEG2VIDEO) type(Video)
2007-04-12 22:44:06.495 NVP: Disabling Audio, params(-1,-1,-1)
2007-04-12 22:44:06.495 NVP: Disabling Audio, params(0,-1,-1)
2007-04-12 22:44:06.504 VideoOutputXv: XvMCTex: Init failed
2007-04-12 22:44:06.505 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x1b6
2007-04-12 22:44:07.089 Using realtime priority.
2007-04-12 22:44:07.091 TV: Changing from None to WatchingLiveTV
2007-04-12 22:44:07.191 Video timing method: USleep with busy wait
2007-04-12 22:44:08.603 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:10.007 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:11.411 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:12.815 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:14.215 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:15.615 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:17.015 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:18.415 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:19.815 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:21.215 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:22.615 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:24.015 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:25.415 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:26.815 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:28.215 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:29.615 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:31.015 NVP: Prebuffer wait timed out 10 times.
2007-04-12 22:44:31.396 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 22:44:38.400 MythSocket(8f6b20:28): readStringList: Error, timeout (quick).
2007-04-12 22:44:38.400 RemoteEncoder::SendReceiveStringList(): No response.
2007-04-12 22:44:38.469 TV: Changing from WatchingLiveTV to None
2007-04-12 22:44:38.489 DPMS Reactivated.
2007-04-12 22:44:41.614 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
QDateTime::fromString: Parameter out of range
2007-04-12 22:46:07.166 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 22:46:07.168 Using protocol version 31
2007-04-12 22:46:14.181 MythSocket(9ed730:28): readStringList: Error, timeout (quick).
2007-04-12 22:46:14.182 RemoteEncoder::SendReceiveStringList(): No response.
2007-04-12 22:46:14.183 GetEntryAt(-1) failed.
2007-04-12 22:46:14.185 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2007-04-12 22:46:14.185 TV Error: LiveTV not successfully started
2007-04-12 22:46:14.185 TV Error: LiveTV not successfully started
2007-04-12 22:46:14.190 TV: Deleting TV Chain in destructor
2007-04-12 22:46:14.194 DPMS Deactivated 
2007-04-12 22:46:14.194 DPMS Reactivated.
2007-04-12 22:46:24.888 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
QDateTime::fromString: Parameter out of range
whein@MythTvBox:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-12 22:46:57.135 Using runtime prefix = /usr
2007-04-12 22:46:57.159 Gnome-Screensaver support enabled
2007-04-12 22:46:57.169 DPMS is active.
2007-04-12 22:46:57.217 New DB connection, total: 1
2007-04-12 22:46:57.227 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:46:57.233 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:46:57.237 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:46:57.261 Current Schema Version: 1160
2007-04-12 22:46:57.265 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 22:46:57.265 Enabled verbose msgs:  important general
2007-04-12 22:46:57.669 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:46:57.670 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:46:57.671 Switching to square mode (Retro)
2007-04-12 22:46:57.722 Using the OpenGL painter
2007-04-12 22:46:58.283 New DB connection, total: 2
2007-04-12 22:46:58.284 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:46:58.284 Joystick disabled.
2007-04-12 22:46:58.383 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 22:46:58.801 Registering Internal as a media playback plugin.
2007-04-12 22:46:58.825 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-12 22:46:58.826 Mediamonitor: Adding /dev/hdd
no record for '/block/hdd/device' in database
no record for '/block/hdd/holders' in database
no record for '/block/hdd/queue' in database
no record for '/block/hdd/slaves' in database
2007-04-12 22:46:58.858 Mediamonitor: AddDevice() -- Not adding '/dev/hdd', it appears to be a duplicate.
2007-04-12 22:46:58.859 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-12 22:46:58.919 Using NV NPOT texture extension
Failed to run 'cdrecord --scanbus'
adding: ATAPI:0,1,0 -- COMBO SOHC-5236V
2007-04-12 22:47:00.576 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-12 22:47:00.576 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-12 22:47:00.577 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-04-12 22:47:00.813 Starting media monitor.
2007-04-12 22:47:00.816 NetworkControl: Listening for remote connections on port 6546
2007-04-12 22:47:00.821 Executing '/usr/bin/pmount /dev/hdd'
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0
2007-04-12 22:47:00.983 Failed to mount /dev/hdd.
2007-04-12 22:47:00.987 Media status changed...  New status is: MEDIASTAT_MOUNTED old status was MEDIASTAT_NOTMOUNTED
2007-04-12 22:47:00.987 Posting MediaEvent
2007-04-12 22:47:05.877 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2007-04-12 22:47:05.883 Using protocol version 31
2007-04-12 22:47:11.734 TV: Attempting to change from None to None
2007-04-12 22:47:15.731 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
whein@MythTvBox:~$ mythfrontend
2007-04-12 22:58:01.696 Using runtime prefix = /usr
2007-04-12 22:58:01.721 Gnome-Screensaver support enabled
2007-04-12 22:58:01.722 DPMS is active.
2007-04-12 22:58:01.778 New DB connection, total: 1
2007-04-12 22:58:01.800 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:58:01.803 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:58:01.807 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:58:01.852 Current Schema Version: 1160
2007-04-12 22:58:01.853 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 22:58:01.853 Enabled verbose msgs:  important general
2007-04-12 22:58:02.587 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 22:58:02.588 Using screen 0, 1280x1024 at 0,0
2007-04-12 22:58:02.589 Switching to square mode (Retro)
2007-04-12 22:58:02.652 Using the OpenGL painter
2007-04-12 22:58:03.634 Joystick disabled.
2007-04-12 22:58:03.925 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 22:58:04.365 Registering Internal as a media playback plugin.
2007-04-12 22:58:04.487 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-12 22:58:04.488 Mediamonitor: Adding /dev/hdd
no record for '/block/hdd/device' in database
no record for '/block/hdd/holders' in database
no record for '/block/hdd/queue' in database
no record for '/block/hdd/slaves' in database
2007-04-12 22:58:04.513 Mediamonitor: AddDevice() -- Not adding '/dev/hdd', it appears to be a duplicate.
2007-04-12 22:58:04.515 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-12 22:58:05.036 Using NV NPOT texture extension
Failed to run 'cdrecord --scanbus'
adding: ATAPI:0,1,0 -- COMBO SOHC-5236V
2007-04-12 22:58:06.699 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-12 22:58:06.699 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-12 22:58:06.699 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-04-12 22:58:07.074 Starting media monitor.
2007-04-12 22:58:07.075 NetworkControl: Listening for remote connections on port 6546
2007-04-12 22:58:07.080 Executing '/usr/bin/pmount /dev/hdd'
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0
2007-04-12 22:58:07.275 Failed to mount /dev/hdd.
2007-04-12 22:58:07.277 Media status changed...  New status is: MEDIASTAT_MOUNTED old status was MEDIASTAT_NOTMOUNTED
2007-04-12 22:58:07.277 Posting MediaEvent
2007-04-12 22:58:10.539 New DB connection, total: 2
2007-04-12 22:58:10.540 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:58:10.665 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2007-04-12 22:58:10.668 Using protocol version 31
2007-04-12 22:58:10.722 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 22:58:10.723 Using protocol version 31
2007-04-12 22:58:11.855 DPMS Deactivated 
2007-04-12 22:58:12.063 AFD: Opened codec 0x91c030, id(MPEG2VIDEO) type(Video)
2007-04-12 22:58:12.155 AFD: Opened codec 0x91c400, id(MP2) type(Audio)
2007-04-12 22:58:12.173 Opening OSS audio device '/dev/dsp'.
2007-04-12 22:58:12.211 VideoOutputXv: XvMCTex: Init failed
2007-04-12 22:58:12.212 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 22:58:12.871 TV: Changing from None to WatchingLiveTV
2007-04-12 22:58:12.872 New DB connection, total: 3
2007-04-12 22:58:12.874 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 22:58:12.874 Using realtime priority.
2007-04-12 22:58:12.979 Video timing method: USleep with busy wait
2007-04-12 22:58:19.259 NVP: prebuffering pause
2007-04-12 22:58:25.223 NVP: prebuffering pause
2007-04-12 22:58:28.048 NVP: prebuffering pause
2007-04-12 22:58:37.396 NVP: prebuffering pause
2007-04-12 22:58:42.592 NVP: prebuffering pause
2007-04-12 22:58:44.708 NVP: prebuffering pause
2007-04-12 22:58:54.348 NVP: prebuffering pause
2007-04-12 22:59:04.333 NVP: prebuffering pause
2007-04-12 22:59:11.384 NVP: prebuffering pause
2007-04-12 22:59:17.864 NVP: prebuffering pause
2007-04-12 22:59:24.361 NVP: prebuffering pause
2007-04-12 22:59:30.528 NVP: prebuffering pause
2007-04-12 22:59:33.544 NVP: prebuffering pause
2007-04-12 22:59:44.590 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 22:59:45.182 TV: Changing from WatchingLiveTV to None
2007-04-12 22:59:45.205 DPMS Reactivated.
2007-04-12 23:00:30.150 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:00:30.151 Using protocol version 31
2007-04-12 23:00:31.061 DPMS Deactivated 
2007-04-12 23:00:31.088 AFD: Opened codec 0x1fda190, id(MPEG2VIDEO) type(Video)
2007-04-12 23:00:31.089 AFD: Opened codec 0x1ff0790, id(MP2) type(Audio)
2007-04-12 23:00:31.208 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:00:31.218 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:00:31.222 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:00:31.786 Using realtime priority.
2007-04-12 23:00:31.789 TV: Changing from None to WatchingLiveTV
2007-04-12 23:00:31.889 Video timing method: USleep with busy wait
2007-04-12 23:00:37.071 NVP: prebuffering pause
2007-04-12 23:00:37.934 NVP: prebuffering pause
2007-04-12 23:00:44.131 NVP: prebuffering pause
2007-04-12 23:00:45.506 NVP: prebuffering pause
2007-04-12 23:00:48.654 NVP: prebuffering pause
2007-04-12 23:00:57.466 NVP: prebuffering pause
2007-04-12 23:01:13.142 NVP: prebuffering pause
2007-04-12 23:01:24.087 NVP: prebuffering pause
2007-04-12 23:01:31.871 NVP: prebuffering pause
2007-04-12 23:01:41.879 NVP: prebuffering pause
2007-04-12 23:01:43.613 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:01:43.863 TV: Changing from WatchingLiveTV to None
2007-04-12 23:01:43.875 DPMS Reactivated.
2007-04-12 23:01:52.888 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:01:52.889 Using protocol version 31
2007-04-12 23:01:53.787 DPMS Deactivated 
2007-04-12 23:01:53.816 AFD: Opened codec 0x269c080, id(MPEG2VIDEO) type(Video)
2007-04-12 23:01:53.816 AFD: Opened codec 0x269c450, id(MP2) type(Audio)
2007-04-12 23:01:53.876 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:01:53.886 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:01:53.887 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:01:54.450 Using realtime priority.
2007-04-12 23:01:54.450 TV: Changing from None to WatchingLiveTV
2007-04-12 23:01:54.555 Video timing method: USleep with busy wait
2007-04-12 23:02:06.455 NVP: prebuffering pause
2007-04-12 23:02:12.583 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:02:13.060 TV: Changing from WatchingLiveTV to None
2007-04-12 23:02:13.067 DPMS Reactivated.
2007-04-12 23:02:19.742 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:02:19.743 Using protocol version 31
2007-04-12 23:02:20.643 DPMS Deactivated 
2007-04-12 23:02:21.747 RingBuf(/var/lib/mythtv//1056_20070412230219.mpg): Waited 1.0 seconds for data to become available...
2007-04-12 23:02:21.747 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:02:22.771 RingBuf(/var/lib/mythtv//1056_20070412230219.mpg): Waited 2.0 seconds for data to become available...
2007-04-12 23:02:22.771 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:02:24.831 RingBuf(/var/lib/mythtv//1056_20070412230219.mpg): Waited 4.0 seconds for data to become available...
2007-04-12 23:02:24.831 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:02:28.935 RingBuf(/var/lib/mythtv//1056_20070412230219.mpg): Waited 8.0 seconds for data to become available...
2007-04-12 23:02:28.935 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:02:36.875 RingBuf(/var/lib/mythtv//1056_20070412230219.mpg) Error: Waited 16 seconds for data, aborting.
2007-04-12 23:02:36.876 AFD: Opened codec 0x9cb710, id(MPEG2VIDEO) type(Video)
2007-04-12 23:02:36.935 NVP: Disabling Audio, params(-1,-1,-1)
2007-04-12 23:02:36.935 NVP: Disabling Audio, params(0,-1,-1)
2007-04-12 23:02:36.944 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:02:36.944 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:02:37.500 Using realtime priority.
2007-04-12 23:02:37.503 TV: Changing from None to WatchingLiveTV
2007-04-12 23:02:37.603 Video timing method: USleep with busy wait
2007-04-12 23:02:39.003 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:40.403 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:41.803 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:43.203 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:44.603 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:46.003 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:47.403 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:48.803 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:50.203 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:51.603 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:53.003 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:54.403 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:55.803 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:57.203 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:02:58.603 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:00.003 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:01.403 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:02.803 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:04.203 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:05.603 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:07.003 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:08.403 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:09.803 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:11.204 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:12.604 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:14.004 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:15.404 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:16.804 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:18.204 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:19.604 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:21.004 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:22.404 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:23.804 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:25.204 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:26.604 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:28.004 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:29.404 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:30.804 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:32.204 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:33.604 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:35.004 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:36.404 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:03:37.199 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:03:44.260 MythSocket(92d870:28): readStringList: Error, timeout (quick).
2007-04-12 23:03:44.260 RemoteEncoder::SendReceiveStringList(): No response.
2007-04-12 23:03:44.325 TV: Changing from WatchingLiveTV to None
2007-04-12 23:03:44.333 DPMS Reactivated.
whein@MythTvBox:~$ mythfrontend
2007-04-12 23:06:36.627 Using runtime prefix = /usr
2007-04-12 23:06:36.661 DPMS is active.
2007-04-12 23:06:36.716 New DB connection, total: 1
2007-04-12 23:06:36.733 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 23:06:36.736 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:06:36.742 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:06:36.783 Current Schema Version: 1160
2007-04-12 23:06:36.783 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 23:06:36.783 Enabled verbose msgs:  important general
2007-04-12 23:06:37.559 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:06:37.560 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:06:37.561 Switching to square mode (Retro)
2007-04-12 23:06:37.633 Using the OpenGL painter
2007-04-12 23:06:38.643 Joystick disabled.
2007-04-12 23:06:38.940 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 23:06:39.526 Registering Internal as a media playback plugin.
2007-04-12 23:06:39.650 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-12 23:06:39.651 Mediamonitor: Adding /dev/hdd
no record for '/block/hdd/device' in database
no record for '/block/hdd/holders' in database
no record for '/block/hdd/queue' in database
no record for '/block/hdd/slaves' in database
2007-04-12 23:06:39.676 Mediamonitor: AddDevice() -- Not adding '/dev/hdd', it appears to be a duplicate.
2007-04-12 23:06:39.678 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-12 23:06:40.158 Using NV NPOT texture extension
Failed to run 'cdrecord --scanbus'
adding: ATAPI:0,1,0 -- COMBO SOHC-5236V
2007-04-12 23:06:41.824 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-12 23:06:41.824 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-12 23:06:41.824 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-04-12 23:06:42.348 Starting media monitor.
2007-04-12 23:06:42.350 NetworkControl: Listening for remote connections on port 6546
2007-04-12 23:06:42.359 Executing '/usr/bin/pmount /dev/hdd'
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0
2007-04-12 23:06:42.536 Failed to mount /dev/hdd.
2007-04-12 23:06:42.539 Media status changed...  New status is: MEDIASTAT_MOUNTED old status was MEDIASTAT_NOTMOUNTED
2007-04-12 23:06:42.539 Posting MediaEvent
2007-04-12 23:06:47.144 New DB connection, total: 2
2007-04-12 23:06:47.145 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 23:06:47.202 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2007-04-12 23:06:47.205 Using protocol version 31
2007-04-12 23:06:47.241 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:06:47.242 Using protocol version 31
2007-04-12 23:06:53.945 DPMS Deactivated 
2007-04-12 23:06:54.111 AFD: Opened codec 0x92b430, id(MPEG2VIDEO) type(Video)
2007-04-12 23:06:54.211 AFD: Opened codec 0x92b800, id(MP2) type(Audio)
2007-04-12 23:06:54.270 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:06:54.318 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:06:54.319 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:06:54.960 TV: Changing from None to WatchingLiveTV
2007-04-12 23:06:54.965 Using realtime priority.
2007-04-12 23:06:55.073 Video timing method: USleep with busy wait
2007-04-12 23:06:59.966 NVP: prebuffering pause
2007-04-12 23:07:01.162 NVP: prebuffering pause
2007-04-12 23:07:02.985 NVP: prebuffering pause
2007-04-12 23:07:05.405 NVP: prebuffering pause
2007-04-12 23:07:06.985 NVP: prebuffering pause
2007-04-12 23:07:13.325 NVP: prebuffering pause
2007-04-12 23:07:17.282 NVP: prebuffering pause
2007-04-12 23:07:23.963 NVP: prebuffering pause
2007-04-12 23:07:32.378 NVP: prebuffering pause
2007-04-12 23:07:38.770 NVP: prebuffering pause
2007-04-12 23:07:43.255 NVP: prebuffering pause
2007-04-12 23:07:51.370 NVP: prebuffering pause
2007-04-12 23:07:57.090 NVP: prebuffering pause
2007-04-12 23:08:01.394 NVP: prebuffering pause
2007-04-12 23:08:03.467 NVP: prebuffering pause
2007-04-12 23:08:07.738 NVP: prebuffering pause
2007-04-12 23:08:14.455 NVP: prebuffering pause
2007-04-12 23:08:15.991 NVP: prebuffering pause
2007-04-12 23:08:17.873 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:08:18.311 TV: Changing from WatchingLiveTV to None
2007-04-12 23:08:18.318 DPMS Reactivated.
2007-04-12 23:08:32.386 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:08:32.387 Using protocol version 31
2007-04-12 23:08:33.290 DPMS Deactivated 
2007-04-12 23:08:33.313 AFD: Opened codec 0x9ba670, id(MPEG2VIDEO) type(Video)
2007-04-12 23:08:33.314 AFD: Opened codec 0x9b6a00, id(MP2) type(Audio)
2007-04-12 23:08:33.371 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:08:33.380 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:08:33.385 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:08:33.925 TV: Changing from None to WatchingLiveTV
2007-04-12 23:08:33.926 Using realtime priority.
2007-04-12 23:08:34.026 Video timing method: USleep with busy wait
2007-04-12 23:08:42.647 NVP: prebuffering pause
2007-04-12 23:09:02.455 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:09:02.872 TV: Changing from WatchingLiveTV to None
2007-04-12 23:09:02.879 DPMS Reactivated.
2007-04-12 23:09:14.263 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:09:14.263 Using protocol version 31
2007-04-12 23:09:15.151 DPMS Deactivated 
2007-04-12 23:09:15.169 AFD: Opened codec 0xa238b0, id(MPEG2VIDEO) type(Video)
2007-04-12 23:09:15.170 AFD: Opened codec 0xa250e0, id(MP2) type(Audio)
2007-04-12 23:09:15.224 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:09:15.234 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:09:15.238 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:09:15.823 TV: Changing from None to WatchingLiveTV
2007-04-12 23:09:15.823 Using realtime priority.
2007-04-12 23:09:15.923 Video timing method: USleep with busy wait
2007-04-12 23:09:21.360 NVP: prebuffering pause
2007-04-12 23:09:24.383 NVP: prebuffering pause
2007-04-12 23:09:25.575 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:09:26.044 TV: Changing from WatchingLiveTV to None
2007-04-12 23:09:26.059 DPMS Reactivated.
whein@MythTvBox:~$ mythfrontend
2007-04-12 23:09:30.550 Using runtime prefix = /usr
2007-04-12 23:09:30.566 Gnome-Screensaver support enabled
2007-04-12 23:09:30.567 DPMS is active.
2007-04-12 23:09:30.614 New DB connection, total: 1
2007-04-12 23:09:30.627 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 23:09:30.634 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:09:30.652 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:09:30.673 Current Schema Version: 1160
2007-04-12 23:09:30.674 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-12 23:09:30.674 Enabled verbose msgs:  important general
2007-04-12 23:09:31.065 Total desktop dim: 1280x1024, with 1 screen[s].
2007-04-12 23:09:31.067 Using screen 0, 1280x1024 at 0,0
2007-04-12 23:09:31.068 Switching to square mode (Retro)
2007-04-12 23:09:31.112 Using the OpenGL painter
2007-04-12 23:09:32.070 New DB connection, total: 2
2007-04-12 23:09:32.071 Joystick disabled.
2007-04-12 23:09:32.076 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 23:09:32.288 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-12 23:09:33.007 Registering Internal as a media playback plugin.
2007-04-12 23:09:33.032 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-12 23:09:33.033 Mediamonitor: Adding /dev/hdd
no record for '/block/hdd/device' in database
no record for '/block/hdd/holders' in database
no record for '/block/hdd/queue' in database
no record for '/block/hdd/slaves' in database
2007-04-12 23:09:33.062 Mediamonitor: AddDevice() -- Not adding '/dev/hdd', it appears to be a duplicate.
2007-04-12 23:09:33.063 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-12 23:09:33.122 Using NV NPOT texture extension
Failed to run 'cdrecord --scanbus'
adding: ATAPI:0,1,0 -- COMBO SOHC-5236V
2007-04-12 23:09:34.773 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-12 23:09:34.773 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-12 23:09:34.773 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2007-04-12 23:09:34.989 Starting media monitor.
2007-04-12 23:09:34.991 NetworkControl: Listening for remote connections on port 6546
2007-04-12 23:09:34.998 Executing '/usr/bin/pmount /dev/hdd'
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom0
2007-04-12 23:09:35.169 Failed to mount /dev/hdd.
2007-04-12 23:09:35.172 Media status changed...  New status is: MEDIASTAT_MOUNTED old status was MEDIASTAT_NOTMOUNTED
2007-04-12 23:09:35.172 Posting MediaEvent
2007-04-12 23:09:42.905 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2007-04-12 23:09:42.907 Using protocol version 31
2007-04-12 23:09:42.923 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:09:42.924 Using protocol version 31
2007-04-12 23:09:43.795 DPMS Deactivated 
2007-04-12 23:09:43.900 AFD: Opened codec 0xa3e260, id(MPEG2VIDEO) type(Video)
2007-04-12 23:09:43.923 AFD: Opened codec 0xa3db70, id(MP2) type(Audio)
2007-04-12 23:09:44.020 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:09:44.054 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:09:44.055 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:09:44.627 TV: Changing from None to WatchingLiveTV
2007-04-12 23:09:44.631 New DB connection, total: 3
2007-04-12 23:09:44.635 Connected to database 'mythconverg' at host: 192.168.0.2
2007-04-12 23:09:44.637 Using realtime priority.
2007-04-12 23:09:44.744 Video timing method: USleep with busy wait
2007-04-12 23:09:51.953 NVP: prebuffering pause
2007-04-12 23:09:52.784 NVP: prebuffering pause
2007-04-12 23:09:55.365 NVP: prebuffering pause
2007-04-12 23:10:00.581 NVP: prebuffering pause
2007-04-12 23:10:01.248 NVP: prebuffering pause
2007-04-12 23:10:05.036 NVP: prebuffering pause
2007-04-12 23:10:14.601 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:10:15.093 TV: Changing from WatchingLiveTV to None
2007-04-12 23:10:15.101 DPMS Reactivated.
2007-04-12 23:10:16.496 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:10:16.497 Using protocol version 31
2007-04-12 23:10:17.422 DPMS Deactivated 
2007-04-12 23:10:18.648 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 1.0 seconds for data to become available...
2007-04-12 23:10:18.648 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:19.676 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 2.0 seconds for data to become available...
2007-04-12 23:10:19.676 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:21.728 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 4.0 seconds for data to become available...
2007-04-12 23:10:21.728 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:25.824 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 8.0 seconds for data to become available...
2007-04-12 23:10:25.824 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:33.760 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg) Error: Waited 16 seconds for data, aborting.
2007-04-12 23:10:33.761 AFD: Opened codec 0xa4d240, id(MPEG2VIDEO) type(Video)
2007-04-12 23:10:33.816 NVP: Disabling Audio, params(-1,-1,-1)
2007-04-12 23:10:33.816 NVP: Disabling Audio, params(0,-1,-1)
2007-04-12 23:10:33.825 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:10:33.826 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x192
2007-04-12 23:10:34.377 Using realtime priority.
2007-04-12 23:10:34.380 TV: Changing from None to WatchingLiveTV
2007-04-12 23:10:34.480 Video timing method: USleep with busy wait
2007-04-12 23:10:35.880 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:37.280 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:38.680 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:40.080 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:41.480 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:42.880 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:44.280 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:45.680 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:46.223 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:10:53.276 MythSocket(aa7ee0:28): readStringList: Error, timeout (quick).
2007-04-12 23:10:53.277 RemoteEncoder::SendReceiveStringList(): No response.
2007-04-12 23:10:53.342 TV: Changing from WatchingLiveTV to None
2007-04-12 23:10:53.349 DPMS Reactivated.
whein@MythTvBox:~$ 

---

### Post by wjston on 2007-04-13
> **whein said:**
> 2007-04-12 23:06:54.111 AFD: Opened codec 0x92b430, id(MPEG2VIDEO) type(Video)
2007-04-12 23:06:54.211 AFD: Opened codec 0x92b800, id(MP2) type(Audio)
2007-04-12 23:06:54.270 Opening OSS audio device '/dev/dsp'.
2007-04-12 23:06:54.318 VideoOutputXv: XvMCTex: Init failed

Are you using the pvr-350 to output the signal to your tv? If so, I have read a number of reports that people were having problems getting this to work on some hardware configurations. The above error looks like the card is having a problem syncing the audio and video. If possible, I would suggest trying an nvidia fx5200 or fx6800 card to see if that resloves your issues. Also, do you have OpenGL turned on (if so, try turning that off to see if it makes a difference)?

---

### Post by whein on 2007-04-13
> Are you using the pvr-350 to output the signal to your tv? If so, I have read a number of reports that people were having problems getting this to work on some hardware configurations. The above error looks like the card is having a problem syncing the audio and video. If possible, I would suggest trying an nvidia fx5200 or fx6800 card to see if that resloves your issues. Also, do you have OpenGL turned on (if so, try turning that off to see if it makes a difference)?
Yes and no...  I ran through the part of the [tutorial]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out") up to the section titled "Configure X to use the ivtvdev_drv driver" where I stopped.  Right now I do not have a TV connected (only connected it to test, I still need to make permanent cable runs) and was under the impression that running through that section would make ALL the display output (Gnome, KDE, etc.) go through the TV instead of the LCD monitor I have connected.  Is this the case?  Right now I have all the X display still going through my monitor.

I think I did turn on the OpenGL option, so I'll try to mess with that tonight to see if it makes a difference.  I also noticed that every couple of seconds the encoded tv signal will skip when I watch it with the frontend.  I had passed this off to poor reception (I just have a weak antenna connection for testing) messing with the mpeg encoding, but maybe worth mentioning in case it's important.  The skips are not very noticeable if you don't pay attention.
-Will

---

### Post by wjston on 2007-04-13
> **whein said:**
> Yes and no...  I ran through the part of the [tutorial]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out") up to the section titled "Configure X to use the ivtvdev_drv driver" where I stopped.  Right now I do not have a TV connected (only connected it to test, I still need to make permanent cable runs) and was under the impression that running through that section would make ALL the display output (Gnome, KDE, etc.) go through the TV instead of the LCD monitor I have connected.  Is this the case?  Right now I have all the X display still going through my monitor.

There is a difference between hooking up your tv and monitor with respect to your xorg.conf settings. It will also depend on the type of tv that you have (standard analogue, lcd, or plasma).

> I think I did turn on the OpenGL option, so I'll try to mess with that tonight to see if it makes a difference.  I also noticed that every couple of seconds the encoded tv signal will skip when I watch it with the frontend.  I had passed this off to poor reception (I just have a weak antenna connection for testing) messing with the mpeg encoding, but maybe worth mentioning in case it's important.  The skips are not very noticeable if you don't pay attention.
-Will

If your signal input is poor and drops off, this can cause some of the issues you are experiencing (black screen) if mythtv can't receive a signal to process. I would ensure the cable coming into the capture card is of acceptable quality and makes a good connection at both ends. OpenGL is useful to try to keep audio/video in sync, and I would check use the video as a timeline also.

---

### Post by whein on 2007-04-16
update:

This weekend I tried a couple things with no success.  I switched the theme back to the ugly gray one that Myth installed with.  I turned off the OpenGL rendering and switched it back to Qt.  Hunted around for any settings that looked at all applicable, but nothing stood out for either the front end or the back end.

There are two sections in the terminal output that I hope someone out there can shed a little light on.
```
whein@MythTvBox:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
whein@MythTvBox:~$

``` Anyone know what the session management error is about?  This happens when I issue the restart or just the start command for the back end.

```
2007-04-12 23:10:16.496 TV: Attempting to change from None to WatchingLiveTV
2007-04-12 23:10:16.497 Using protocol version 31
2007-04-12 23:10:17.422 DPMS Deactivated
2007-04-12 23:10:18.648 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 1.0 seconds for data to become available...
2007-04-12 23:10:18.648 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:19.676 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 2.0 seconds for data to become available...
2007-04-12 23:10:19.676 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:21.728 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 4.0 seconds for data to become available...
2007-04-12 23:10:21.728 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:25.824 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg): Waited 8.0 seconds for data to become available...
2007-04-12 23:10:25.824 Checking to see if there's a new livetv program to switch to..
2007-04-12 23:10:33.760 RingBuf(/var/lib/mythtv//1055_20070412231016.mpg) Error: Waited 16 seconds for data, aborting.
2007-04-12 23:10:33.761 AFD: Opened codec 0xa4d240, id(MPEG2VIDEO) type(Video)
2007-04-12 23:10:33.816 NVP: Disabling Audio, params(-1,-1,-1)
2007-04-12 23:10:33.816 NVP: Disabling Audio, params(0,-1,-1)
2007-04-12 23:10:33.825 VideoOutputXv: XvMCTex: Init failed
2007-04-12 23:10:33.826 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
Major opcode: 140
Minor opcode: 14
Resource id: 0x192
2007-04-12 23:10:34.377 Using realtime priority.
2007-04-12 23:10:34.380 TV: Changing from None to WatchingLiveTV
2007-04-12 23:10:34.480 Video timing method: USleep with busy wait
2007-04-12 23:10:35.880 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:37.280 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:38.680 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:40.080 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:41.480 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:42.880 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:44.280 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:45.680 NVP: Prebuffer wait timed out 10 times.
2007-04-12 23:10:46.223 TV: Attempting to change from WatchingLiveTV to None
2007-04-12 23:10:53.276 MythSocket(aa7ee0:28): readStringList: Error, timeout (quick).
2007-04-12 23:10:53.277 RemoteEncoder::SendReceiveStringList(): No response.
2007-04-12 23:10:53.342 TV: Changing from WatchingLiveTV to None
2007-04-12 23:10:53.349 DPMS Reactivated.
whein@MythTvBox:~$
```  Does this bit shed any light on what is failing or why?  I understand what it is trying to do, but not why it is unable to do it.
-Will

---

### Post by msak007 on 2007-04-30
> **whein said:**
> Ok, finally got MythTv installed on a fresh Edgy box.  A few wrinkles still exist so hopefully someone here can help.

1) The computer this is installed on has no internet connection.  :(  Is there a way I can manually download TV listings (from Zap2It) every so often from another computer, transfer them over, and get MythTV to incorporate them?

2) I have a PVR-350 that came with the gray Hauppauge remote.  I'm using the lircd.conf and lircrc example files pointed to from [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy).  These are:
[https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge](https://help.ubuntu.com/community/Install_Lirc_Edgy?action=AttachFile&do=get&target=lircd.conf.hauppauge)
and
[http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt)
respectively.
I can change the channel if I press 5,3 or 2,2 but not if I press the channel up/down buttons.  I *think* this is just a naming problem where the lircd.conf file calls them "CH+" and "CH-" while the lircrc file calls them "Channel-UP" and "Channel-DOWN".  Anyone else run into this problem and can I fix this just by making them match?  I assume the real name is arbitrary, just so long as it is consistent?
I have the same issue with my 350 remote and you're right, it is a button naming issue in the file. You'll also run into a problem with the left / right buttons as well because they're labeled "LEFT" and "RIGHT" in lircrc. You have to edit your lircrc file to match the exact button names that irw registers. One note though, leave the UP / DOWN buttons the way they are - if you try to change those to "Ch+" and "Ch-" as well, every time you press those buttons it'll end up registering a button press twice so it'll skip over a menu entry. Here's the relevant section of my ~/.mythtv/lircrc file (everything else is the same):

```
begin
prog = mythtv
button = UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = DOWN
repeat = 3
config = Down
end

begin
prog = mythtv
button = Vol-
repeat = 3
config = Left
end

begin
prog = mythtv
button = Vol+
repeat = 3
config = Right
end

# Channel Up
begin
prog = mythtv
button = Ch+
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = Ch-
repeat = 3
config = Down
end
```

---

