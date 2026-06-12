---
title: "HOWTO: Linux Hulu Desktop integration"
date: 2009-10-08
forum: Mythbuntu
---

### Post by tgm4883 on 2009-10-08
Ok, Hulu has released their desktop client for Linux. I've documented what I have done to get it working and accessible from the MythTV frontend

**Disclaimer:** I am not responsible for you destroying your box. These instructions may not work for everyone. Follow these instructions at your own risk.

There are 32-bit and 64-bit DEBs (and RPMs) that you can download on the following site

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

**Requirements:** See the website above. You will need the same architecture of flash installed as the package you have installed. I've only tested 64-bit package with 64-bit flash on a 64-bit system.

Download and install the .deb for your architecture. Make sure you have flash installed as well. It looks like it looks for the flash library at ~/.mozilla/plugins/libflashplugin.so

You will need a mouse for initial setup, as it will require you to accept the EULA and you will probably want to maximize the Hulu desktop. You will only have to do this once, as it saves your settings when you exit.


**Remote support:**
You will need to make a small change to your hardware.conf file and restart lirc. I've tested this with my MCEUSB2 remote and MythTV and Hulu both appear to work fine. If you do not make this change, Hulu Desktop will only receive a few of your remote button presses.

Edit your hardware.conf
```
sudo nano /etc/lirc/hardware.conf
```

Find 
```
REMOTE_LIRCD_ARGS=""
```
and change it to
```
REMOTE_LIRCD_ARGS="--release"
```

Then restart lirc

```
sudo /etc/init.d/lirc restart
```


**Frontend Menu:**

We will need to manually edit the frontend menu. I chose to place the Hulu link in the Media Library, but you can place it where you wish.

Edit the Media Library XML file
```
sudo nano /usr/share/mythtv/themes/defaultmenu/library.xml
```

Add the following code before </mythmenu> (modified from the Boxee thread)

```

    <button>
        <type>TV_WATCH_RECORDINGS</type>
        <text>Hulu</text>
        <action>EXEC /usr/bin/huludesktop</action>
    </button>

```

:EDIT:

Also, please reply here if you have issues with LIRC in any other applications after making this change.

---

### Post by Dr_Willis on 2009-10-09
Having several issues here with this. but i am testing 9.10 right now.   Using the 64bit version , on 64bit ubuntu. It never seems to want to 'find' the flash plugin 

> Hulu Desktop could not locate the Flash plugin.

If you do not have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so

Been trying various  locations in the .huludesktop config file.
and even redownloaded the tar.gz from the flash site and pointed the file to the file in my home dir. Still dosent like it.

Tried the 64bit flash file/version from adobe it 'saw' it - but then core dumped.

I will keep trying, and try this out on a 9.04 machine when i get the chance.

---

### Post by tgm4883 on 2009-10-09
> **Dr_Willis said:**
> Having several issues here with this. but i am testing 9.10 right now.   Using the 64bit version , on 64bit ubuntu. It never seems to want to 'find' the flash plugin 



Been trying various  locations in the .huludesktop config file.
and even redownloaded the tar.gz from the flash site and pointed the file to the file in my home dir. Still dosent like it.

Tried the 64bit flash file/version from adobe it 'saw' it - but then core dumped.

I will keep trying, and try this out on a 9.04 machine when i get the chance.

try puting the libflashplugin.so file at
```
~/.mozilla/plugins/libflashplugin.so
```

And in the .huludesktop file, make the flash plugin location

```
.mozilla/plugins/libflashplugin.so
```

note the missing ~/

---

### Post by circushair on 2009-10-09
The first time I launched Hulu Desktop it was unable to find the Flash plugin.

Modifying the ~./huludesktop as follows resolved the issue.

```

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```

...Sorry, guess I missed the last bit of your post. :)

---

### Post by elgordo123 on 2009-10-09
Thanks for the write-up! 

My Flash plugin is located here (Another place for you to look):

```
/usr/lib/firefox-addons/plugins/libflashplayer.so
```

---

### Post by ub-newbie on 2009-10-09
using ```
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
``` worked for me on Jaunty 64.  Still a little "jumpy", but better.  It helped the playback for me to lock my CPU at max.

---

### Post by r0dzilla on 2009-10-09
I'm having problems getting Hulu Desktop to use my StreamZap remote.  I've implemented the "--release" switch already.  I've tried adding a section to to the /etc/huludesktop/hd_keymap.ini file, but it is not working...

Here is the output of irw with me pushing the buttons I want to use with Hulu Desktop:
```
00000000000028d4 00 DOWN Streamzap_PC_Remote
00000000000028d4 00 DOWN_UP Streamzap_PC_Remote
00000000000028d0 00 UP Streamzap_PC_Remote
00000000000028d0 00 UP_UP Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT_UP Streamzap_PC_Remote
00000000000028d3 00 RIGHT Streamzap_PC_Remote
00000000000028d3 01 RIGHT Streamzap_PC_Remote
00000000000028d3 00 RIGHT_UP Streamzap_PC_Remote
00000000000028d2 00 OK Streamzap_PC_Remote
00000000000028d2 00 OK_UP Streamzap_PC_Remote
00000000000028d5 00 MENU Streamzap_PC_Remote
00000000000028d5 01 MENU Streamzap_PC_Remote
00000000000028d5 00 MENU_UP Streamzap_PC_Remote
00000000000028d6 00 EXIT Streamzap_PC_Remote
00000000000028d6 01 EXIT Streamzap_PC_Remote
00000000000028d6 00 EXIT_UP Streamzap_PC_Remote
00000000000028ce 00 CH_DOWN Streamzap_PC_Remote
00000000000028ce 01 CH_DOWN Streamzap_PC_Remote
00000000000028ce 00 CH_DOWN_UP Streamzap_PC_Remote
00000000000028cc 00 CH_UP Streamzap_PC_Remote
00000000000028cc 01 CH_UP Streamzap_PC_Remote
00000000000028cc 00 CH_UP_UP Streamzap_PC_Remote
00000000000028cd 00 VOL_UP Streamzap_PC_Remote
00000000000028cd 01 VOL_UP Streamzap_PC_Remote
00000000000028cd 00 VOL_UP_UP Streamzap_PC_Remote
00000000000028cf 00 VOL_DOWN Streamzap_PC_Remote
00000000000028cf 01 VOL_DOWN Streamzap_PC_Remote
00000000000028cf 00 VOL_DOWN_UP Streamzap_PC_Remote
```
Here is a sample of the mceusb config section from hd_keymap.ini:
```
[mceusb]
Up=0
Down=1
Left=2
Right=3
OK=4
Home=5
ChanUp=0
ChanDown=1
VolUp=0
VolDown=1
Back=5

```

What values would I put in there for the StreamZap?  The readme in /usr/share/doc/huludesktop says to use the numbers irw gives you but it still doesn't seem to work...

---

### Post by Dr_Willis on 2009-10-09
All righty - fininally got it with the following lines in the .huludesktop

(2 lines, the 2nd one is real long and may get wrapped)

```
[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 
```


This is on Ubuntu 9.10 64bit.

I see theres all ready some updates to  the player. Perhaps they will fix a few of the quirks.

---

### Post by mythding on 2009-10-10
I could not get my remote to work until I did this step from the mythtv wiki over here...
[http://www.mythtv.org/wiki/Hulu_Desktop_Integration](http://www.mythtv.org/wiki/Hulu_Desktop_Integration)

> First, open ~/.huludesktop in your favorite editor and find the lirc_remote_identifier line. Replace mceusb with your remote. If you don't know it, exit the editor and run irw. Hit a few buttons on your remote, and you'll get output similar to the following:
squeaker@myth:~$ irw
0000000000001795 00 Down Hauppauge_350
0000000000001797 00 Right Hauppauge_350
Whatever is in the place of Hauppauge_350 on your system is your remote. Edit ~/.huludesktop accordingly.

---

### Post by dmfrey on 2009-10-10
Anyone know how to keep the screen saver from kicking in a blanking the screen when hulu desktop is running?

---

### Post by teet on 2009-10-10
Thanks for the guide.  I'm using a MCEUSB2 remote as well and it worked perfectly.  

I've been looking for a good way to get hulu integrated into mythtv for a while now.  I tried mythvodka some time ago but it never really worked right.

-teet

---

### Post by slamhound on 2009-10-10
Do get the streamzap remote working at had to change a few entries in the .huludesktop file (mainly changing the remote identifier and changing the button names to all caps):


[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Streamzap_PC_Remote
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = UP
button_name_down = DOWN
button_name_left = LEFT
button_name_right = RIGHT
button_name_select = OK
button_name_menu = MENU


After this, it works (though it lags a bit).

---

### Post by r0dzilla on 2009-10-10
> **mythding said:**
> I could not get my remote to work until I did this step from the mythtv wiki over here...
[http://www.mythtv.org/wiki/Hulu_Desktop_Integration](http://www.mythtv.org/wiki/Hulu_Desktop_Integration)

Thanks, I also had to change the name of the buttons in ~/.huludesktop, as they were all upper case as reported by irw (see my earlier post)```
[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Streamzap_PC_Remote
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = UP
button_name_down = DOWN
button_name_left = LEFT
button_name_right = RIGHT
button_name_select = OK
button_name_menu = MENU
```

---

### Post by r0dzilla on 2009-10-10
now that I have this working, is there a utility that would allow for launching programs upon pressing a button on the remote?

I have a streamzap remote and it has 4 buttons on the bottom (red/green/yellow/blue), like if I pressed the green button, it would launch huludesktop?

---

### Post by teet on 2009-10-11
> **r0dzilla said:**
> now that I have this working, is there a utility that would allow for launching programs upon pressing a button on the remote?

I have a streamzap remote and it has 4 buttons on the bottom (red/green/yellow/blue), like if I pressed the green button, it would launch huludesktop?

You might be able to use the plugin 'mythcontrols' to do this.  Just a thought.

-teet

---

### Post by bapoumba on 2009-10-11
Two posts removed from this thread.

---

### Post by cj100570 on 2009-10-11
> **circushair said:**
> The first time I launched Hulu Desktop it was unable to find the Flash plugin.

Modifying the ~./huludesktop as follows resolved the issue.

```

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```

...Sorry, guess I missed the last bit of your post. :)

I was having the same issue but that worked for me. :popcorn:

---

### Post by r0dzilla on 2009-10-11
> **slamhound said:**
> Do get the streamzap remote working at had to change a few entries in the .huludesktop file (mainly changing the remote identifier and changing the button names to all caps):


[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Streamzap_PC_Remote
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = UP
button_name_down = DOWN
button_name_left = LEFT
button_name_right = RIGHT
button_name_select = OK
button_name_menu = MENU


After this, it works (though it lags a bit).

Same here, it works but not very responsive, better than nothing I guess...

---

### Post by bcg30506 on 2009-10-12
> **tgm4883 said:**
> Ok, Hulu has released their desktop client for Linux. I've documented what I have done to get it working and accessible from the MythTV frontend

**Disclaimer:** I am not responsible for you destroying your box. These instructions may not work for everyone. Follow these instructions at your own risk.

There are 32-bit and 64-bit DEBs (and RPMs) that you can download on the following site

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

**Requirements:** See the website above. You will need the same architecture of flash installed as the package you have installed. I've only tested 64-bit package with 64-bit flash on a 64-bit system.

Download and install the .deb for your architecture. Make sure you have flash installed as well. It looks like it looks for the flash library at ~/.mozilla/plugins/libflashplugin.so

You will need a mouse for initial setup, as it will require you to accept the EULA and you will probably want to maximize the Hulu desktop. You will only have to do this once, as it saves your settings when you exit.


**Remote support:**
You will need to make a small change to your hardware.conf file and restart lirc. I've tested this with my MCEUSB2 remote and MythTV and Hulu both appear to work fine. If you do not make this change, Hulu Desktop will only receive a few of your remote button presses.

Edit your hardware.conf
```
sudo nano /etc/lirc/hardware.conf
```

Find 
```
REMOTE_LIRCD_ARGS=""
```
and change it to
```
REMOTE_LIRCD_ARGS="--release"
```

Then restart lirc

```
sudo /etc/init.d/lirc restart
```


**Frontend Menu:**

We will need to manually edit the frontend menu. I chose to place the Hulu link in the Media Library, but you can place it where you wish.

Edit the Media Library XML file
```
sudo nano /usr/share/mythtv/themes/defaultmenu/library.xml
```

Add the following code before </mythmenu> (modified from the Boxee thread)

```

    <button>
        <type>TV_WATCH_RECORDINGS</type>
        <text>Hulu</text>
        <action>EXEC /usr/bin/huludesktop</action>
    </button>

```

:EDIT:

Also, please reply here if you have issues with LIRC in any other applications after making this change.

Thank you for posting this!  This is great news and I was not aware of Hulu releasing a Linux desktop player.  I'm looking forward to setting this up and trying it out.

---

### Post by bcg30506 on 2009-10-12
This works beautifully!  Hulu rocks from mythfrontend.  The HD quality videos play perfectly and the interface is very nice in the new Desktop app.

The only question I have is how do I control the volume with my remote?  I've seen no references to the lines to put in the file or if it is even possible.

EDIT:  I have one more question.  The remote control use in Hulu Desktop skips a lot.  By this, I mean when I press the right button once, for example, it will scroll 2, 3 or more times to the right instead of once.  This behavior happens for all buttons.  It does not happen every time.  It works fine in mythfrontend.  Anyone got a clue if there is a setting for this?

---

### Post by lindend on 2009-10-13
For those with iMon IR devices, these modifications work (I'm using a harmony remote so the repeat setttings may not be optimal for everyone)

```

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = iMON-PAD
lirc_release_suffix = _UP
lirc_repeat_threshold = 5
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = Enter
button_name_menu = Menu

```

---

### Post by colinnwn on 2009-10-15
Hi,

I am running 64 bit Mythbuntu. I tried to install 64 bit Hulu and was told I was running 32 bit architecture. Out of morbid curiosity I tried installing 32 bit Hulu and it worked (though playback is choppy with Adobe Flash 10.x). Does anyone know why this could be, or the best place to report what I assume is a bug?

Thanks.

```
colin@myth-1:~/Desktop$ sudo dpkg --install huludesktop_amd64.deb
[sudo] password for colin: 
dpkg: error processing huludesktop_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 huludesktop_amd64.deb
colin@myth-1:~/Desktop$ uname -a
Linux myth-1 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
colin@myth-1:~/Desktop$ sudo dpkg --install huludesktop_i386.deb
Selecting previously deselected package huludesktop.
(Reading database ... 182526 files and directories currently installed.)
Unpacking huludesktop (from huludesktop_i386.deb) ...
Setting up huludesktop (0.9.3-1) ...
colin@myth-1:~/Desktop$ 

```

---

### Post by tgm4883 on 2009-10-15
> **colinnwn said:**
> Hi,

I am running 64 bit Mythbuntu. I tried to install 64 bit Hulu and was told I was running 32 bit architecture. Out of morbid curiosity I tried installing 32 bit Hulu and it worked (though playback is choppy with Adobe Flash 10.x). Does anyone know why this could be, or the best place to report what I assume is a bug?

Thanks.

```
colin@myth-1:~/Desktop$ sudo dpkg --install huludesktop_amd64.deb
[sudo] password for colin: 
dpkg: error processing huludesktop_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 huludesktop_amd64.deb
colin@myth-1:~/Desktop$ uname -a
Linux myth-1 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 **i686** GNU/Linux
colin@myth-1:~/Desktop$ sudo dpkg --install huludesktop_i386.deb
Selecting previously deselected package huludesktop.
(Reading database ... 182526 files and directories currently installed.)
Unpacking huludesktop (from huludesktop_i386.deb) ...
Setting up huludesktop (0.9.3-1) ...
colin@myth-1:~/Desktop$ 

```

No, you are not running 64-bit Mythbuntu

```
thomas@alpha:~$ uname -a
Linux alpha 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 **x86_64** GNU/Linux
thomas@alpha:~$
```

---

### Post by colinnwn on 2009-10-15
> **tgm4883 said:**
> No, you are not running 64-bit Mythbuntu

```
thomas@alpha:~$ uname -a
Linux alpha 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 **x86_64** GNU/Linux
thomas@alpha:~$
```

Hummm. I definitely am running 64 bit on my laptop. I thought I installed 64 bit Myth to standardize. And I thought I tried to install Boxee and couldn't get it to work due to wrong architecture. I guess I am getting the 2 machines confused. Oh well, thanks.

---

### Post by korgman on 2009-10-16
Got it working on Mythbuntu 9.04 x64 pretty quickly.  Its launching from the Myth menu.  Now, how do I get the mouse cursor to disapear when Hulu runs?

---

### Post by novellahub on 2009-10-19
I got it to work in Mythbuntu 9.04 using the directions for the Streamzap remote. I had a issue at first not getting sound over HDMI.   I changed my asound.conf file from:

```

pcm.!default {
    type hw
    card 0
    device 3
}

```

To:

```

pcm.!default {
    type hw
    card 0
    device 3
}


pcm.!default {
   type plug
   slave.pcm "hdmi"
}

```

Sound now works great.

---

### Post by williammanda on 2009-10-20
My remote Gyration GYR3101US ,doesn't seem to function correctly in Hulu desktop. I can press a button and it will react normally or it may do nothing or it may move several selections in one direction. Example: I press the down arrow, it may move one selection or not move or it may move several positions. Here is my huludesktop:

```
[display]
fullscreen = FALSE
width = 1024
height = 576
pos_x = 232
pos_y = 73

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = gyration
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = Enter
button_name_menu = Guide

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1
```

Also I have the same result using either using the key mapping or not. 

```
[Apple_IR]
VOLUP=0
VOLDOWN=1
BACKWARD=2
FORWARD=3
PLAY=4
MENU=5
[mceusb]
Up=0
Down=1
Left=2
Right=3
OK=4
Home=5
ChanUp=0
ChanDown=1
VolUp=0
VolDown=1
Back=5
[gyration]
Up=0
Down=1
Left=2
Right=3
Enter=4
Guide=5
```

I have also tried the lirc_repeat_threshold = to 0 and 1 but change.

---

### Post by tgm4883 on 2009-10-20
> **williammanda said:**
> My remote Gyration GYR3101US ,doesn't seem to function correctly in Hulu desktop. I can press a button and it will react normally or it may do nothing or it may move several selections in one direction. Example: I press the down arrow, it may move one selection or not move or it may move several positions. Here is my huludesktop:

```
[display]
fullscreen = FALSE
width = 1024
height = 576
pos_x = 232
pos_y = 73

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = gyration
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = Enter
button_name_menu = Guide

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1
```

Also I have the same result using either using the key mapping or not. 

```
[Apple_IR]
VOLUP=0
VOLDOWN=1
BACKWARD=2
FORWARD=3
PLAY=4
MENU=5
[mceusb]
Up=0
Down=1
Left=2
Right=3
OK=4
Home=5
ChanUp=0
ChanDown=1
VolUp=0
VolDown=1
Back=5
[gyration]
Up=0
Down=1
Left=2
Right=3
Enter=4
Guide=5
```

I have also tried the lirc_repeat_threshold = to 0 and 1 but change.

Did you add --release to your lirc args?

---

### Post by johnnyjboss on 2009-10-20
The only problem I'm having is that when I exit HuluDesktop after launching it from within MythTv it often seems to respawn itself one time, forcing me to exit twice to get back to MythTv.

I am considering trying to call it from a shell wrapper but I was curious if I'm the only one having this issue.


UPDATE: I believe the issue was duplicate entires in lircrc. This was because mythbuntu had created the .lirc/mythtv script in my home and then also .mythtv/lircrc was symlinked back to it again. So every ENTER press was being registered twice. I didn't find the issue until I started really fine tuning the response from my remote. (soundgraph imon pad - beware)

---

### Post by tgm4883 on 2009-10-20
> **johnnyjboss said:**
> The only problem I'm having is that when I exit HuluDesktop after launching it from within MythTv it often seems to respawn itself one time, forcing me to exit twice to get back to MythTv.

I am considering trying to call it from a shell wrapper but I was curious if I'm the only one having this issue.

I don't see that happening here.

---

### Post by williammanda on 2009-10-20
> **tgm4883 said:**
> Did you add --release to your lirc args?

Yes, see the following:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="gyration"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd"
REMOTE_LIRCD_CONF="/usr/share/lirc/remotes"
**REMOTE_LIRCD_ARGS="--release"**

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

```

---

### Post by onemyndseye on 2009-10-23
I put together a small script to launch HuluDesktop amd solve alot of the issue discussed here such as making sure the screensaver is inhibited, stoping double launches, hiding the mouse and enhancing performance by using elevated privledges.

I also had the issue with HuluDesktop that sometimes, for seemingly no reason the config file (~/.huludesktop) gets overwritten causing the remote to cease to work. So I have the config file written to my liking at start.

mythhulu.sh
```

#!/bin/bash

################################  Write Config File to disk #################################
cat <<EOF >~/.huludesktop
[display]
fullscreen = TRUE
width = 1024
height = 746
pos_x = 0
pos_y = 22

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Harmony_550
lirc_release_suffix = _UP
lirc_repeat_threshold = 3
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = OK
button_name_menu = Menu/i

[flash]
flash_location = /usr/lib/flashplugin-installer/libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1
EOF
####################################  END Config File #######################################

nosaver() {
# Make sure the screensaver is stoped
gnome-screensaver-command --inhibit --application-name HuluDesktop --reason "Watching Internet TV" &
PID=$!
echo "$PID" >"$LOCK"
}


do_cleanup() {
# Simple cleanup function
kill -9 $(cat "$LOCK")
rm -f "$LOCK"
}

## Trap exit signals for cleanup
trap "{ do_cleanup ; exit 0; }" EXIT

##  Lets create/check a lockfile
LOCK=/tmp/mythhulu.lock
if [ -f "$LOCK" ]; then
  # Another instance is running. Lets confirm
  # Start with a short sleep incase a instance is still being loaded
  sleep 3
  HULU="$(ps ax |grep hulu |grep -v "grep")"
  if [ -n "$HULU" ]; then
    # A Hulu process was detected
    exit 0
  else
    # Stale lock file. Retouch
    rm -f "$LOCK"
    touch "$LOCK"
  fi
else
  touch "$LOCK"
fi


## Nope - Dont blank my TV shows ;-)
nosaver


## If xautomation tools are installed use then to 
## move mouse far far off screen
CHECK_XTE=$(which xte)
[ -n "$CHECK_XTE" ] && xte 'mousemove 1000 1000'


##  Start HuluDesktop with elevated priority then exit 
##  with its status
HULU_PRIO=0
nice -n $HULU_PRIO /usr/bin/huludesktop
exit $?


```


Also, I have a small unsigned repo that I use for my personal machines. So I fashioned a small script to check the hulu website for package updates and store the package away if a newer version is found.  This is probably by no means the best way to do this but it suits my purposes.  I wouldnt mind posting the details for my repo here but I am unsure how Hulu Labs would feel about this.  

check-hulu.sh
```

#!/bin/bash


HULU_URL=http://download.hulu.com/huludesktop_i386.deb
HULU_OUTPUT=/myth

cd /tmp
wget -q "$HULU_URL" -O ./temp-hulu.deb

CHECK_HULU=$(dpkg --info ./temp-hulu.deb  |grep Version: |awk '{print $2}')
CURRENT_HULU=$(dpkg -l |grep huludesktop  |awk '{print $3}')


if [ "$CHECK_HULU" = "$CURRENT_HULU" ]; then
  # Package doesnt need updating. Cleanup
  echo "No update found."
  rm -f ./temp-hulu.deb
else
  # New Package available
  echo "Found update!"
  mv temp-hulu.deb $HULU_OUTPUT/.
  cd $HULU_OUTPUT
  dpkg-name ./temp-hulu.deb
fi


```



Hope this helps someone,
-onemyndseye

---

### Post by williammanda on 2009-11-02
Anyone make any headway in getting the remotes to work better (other than the 2 supplied - apple and mce)?

---

### Post by onemyndseye on 2009-11-03
as far as I can tell, any remote that is supported by lirc should work just fine.. provided you add the --release arg to lircd's startup.

I am using a Logitech Harmony 550 /w a serial reciever without any issues at all.


Does the command ` irw ` show your key presses ok?  If lircd is configured correctly all your events should be shown as well as the Key-UP events:
```

onemyndseye@mythtv:~$ irw
0000000000001795 00 Down Harmony_550
0000000000001795 01 Down Harmony_550
0000000000001795 02 Down Harmony_550
0000000000001795 00 Down_UP Harmony_550
0000000000001797 00 Right Harmony_550
0000000000001797 01 Right Harmony_550
0000000000001797 02 Right Harmony_550
0000000000001797 00 Right_UP Harmony_550
0000000000001796 00 Left Harmony_550
0000000000001796 01 Left Harmony_550
0000000000001796 02 Left Harmony_550
0000000000001796 00 Left_UP Harmony_550


```

---

### Post by williammanda on 2009-11-03
My remote is fully functional in mythtv...no problems at all. I did make the --release entry:

[http://ubuntuforums.org/showpost.php?p=8137081&postcount=31]("http://ubuntuforums.org/showpost.php?p=8137081&postcount=31")

---

### Post by onemyndseye on 2009-11-04
yes I saw that you added.. But are they showing up in lircd's output?

If not verify that the --release arg is in-fact being passed to lircd:
```

onemyndseye@mythtv:/usr/share/mythtv/themes$ ps ax |grep lircd
 1604 ?        S<s    0:05 /usr/sbin/lircd --output=/var/run/lirc/lircd --device=/dev/lirc0 --release

```

Your REMOTE_DEVICE= line:
```

REMOTE_DEVICE="/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd"

```

looks funny to me..  is this something specific to that remote?  Normaly this would be the device node for lirc and not the event device itself.  Maybe its fine as I ahve never toyed with the devinput driver but it just struck me as out of place.

Mine:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="--release"

```

---

### Post by williammanda on 2009-11-04
It looks as though it is OK. Here is the output:

```
william@C2Q:~$ ps ax |grep lircd
 6664 pts/4    S+     0:00 grep --color=auto lircd
16925 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd --release
```

Also the gyration remote is setup alittle different than the standard remote. Here is the wiki for gyration:

[http://www.mythtv.org/wiki/Gyration-based_MCE_Remotes]("http://www.mythtv.org/wiki/Gyration-based_MCE_Remotes")

Also I have emailed Hulu about the issue I'm having.

---

### Post by tube013 on 2009-11-18
This has been a great help in getting hulu integrated with myth.

But I've run into a sound problem, where when I launch huludesktop (or boxee) I don't get any sound from the flash videos.  However if I alt-tab to a terminal while myth is running (sitting at a menu) and launch huludesktop or boxee I get sound fine.

Not sure if this is a pulseaudio issue or not.  I've got a usb sound card, which I'm using, and pulseaudio is set up to use it as the default sink.  mythtv seems to suspend pulse audio on start up though. in mythtv I have my sound device as ```
ALSA:plughw:1,0
``` and I've also created an asound.conf with:

```
pcm.!default {
    type hw
    card 1
    device 0
}

```

any tips or ideas appreciated.

---

### Post by greg963 on 2009-11-19
> **tube013 said:**
> This has been a great help in getting hulu integrated with myth.

But I've run into a sound problem, where when I launch huludesktop (or boxee) I don't get any sound from the flash videos.  However if I alt-tab to a terminal while myth is running (sitting at a menu) and launch huludesktop or boxee I get sound fine.

Not sure if this is a pulseaudio issue or not.  I've got a usb sound card, which I'm using, and pulseaudio is set up to use it as the default sink.  mythtv seems to suspend pulse audio on start up though. in mythtv I have my sound device as ```
ALSA:plughw:1,0
``` and I've also created an asound.conf with:

```
pcm.!default {
    type hw
    card 1
    device 0
}

```

any tips or ideas appreciated.

make sure you have the correct card and device number by running aplay -l like this:

```

mythuser@gmythtv0:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mythuser@gmythtv0:~$ 

```

you may have additional outputs.

If the device is the correct one make sure you asound.conf is located in /etc (/etc/asound.conf), otherwise to configure it per user, name the file .asoundrc and put in your home directory (~/.asoundrc).

---

### Post by heartburnkid on 2009-12-08
Is anybody else experiencing painfully slow video playback in Hulu Desktop?  I'm running it on an Athlon x2 4850e, and it drops frames left and right.  As well, remote response is sluggish while video is playing.  Admittedly, my graphic card is a little anemic (GeForce 6200TC) but that shouldn't really matter too much, should it?

---

### Post by uncle hammy on 2009-12-08
> **heartburnkid said:**
> Is anybody else experiencing painfully slow video playback in Hulu Desktop?  I'm running it on an Athlon x2 4850e, and it drops frames left and right.  As well, remote response is sluggish while video is playing.  Admittedly, my graphic card is a little anemic (GeForce 6200TC) but that shouldn't really matter too much, should it?
Hulu Desktop is a joke, possible some of the worst software I have ever dealt with.  I can watch a Blu-Ray rip at full 1080p STREAMING from my backend with MythTV, and my CPU load runs between 5% and 10%.  Fire up Hulu Desktop, and their CRAPPY quality video pegs my CPU at 95%.

I try to use Boxee at all costs when I want to watch online TV.

---

### Post by heartburnkid on 2009-12-08
> **uncle hammy said:**
> Hulu Desktop is a joke, possible some of the worst software I have ever dealt with.  I can watch a Blu-Ray rip at full 1080p STREAMING from my backend with MythTV, and my CPU load runs between 5% and 10%.  Fire up Hulu Desktop, and their CRAPPY quality video pegs my CPU at 95%.

I try to use Boxee at all costs when I want to watch online TV.

All well and good, but I use Karmic, and I'm not in the Boxee beta yet.  I was hoping to use Hulu Desktop as a stopgap, but... well... I don't think that's going to work out.

---

### Post by colinnwn on 2009-12-08
> **uncle hammy said:**
> Hulu Desktop is a joke... I can watch a Blu-Ray rip at full 1080p STREAMING ... CPU load runs between 5% and 10%.  Fire up Hulu Desktop ...pegs my CPU at 95%.

I don't have an opinion on the quality of Hulu Desktop code, but I can say in this case, I don't think it is their fault. Blame Adobe Flash. If you are running Myth 0.22 and you can play HD Bluray at that low of CPU load, you are probably running VDPAU. 

I get choppy playback on my Mythbox (approx 2 year old Celeron running VDPAU) when I play Flash videos in the browser, or when running Hulu Desktop. It also ramps my processor up to 85%. Hulu uses Flash to stream the video in the Desktop software, and on their website. When watching Myth recordings through MPlayer, the CPU is hardly utilized. 

I am considering buying a Core2Duo to see if it can manage clean Flash playback, but I really don't want to spend $100 without knowing for sure it will work.

Adobe has very poor Linux support. There is no excuse for requiring so much CPU when decoding SD. On Windows, Flash requires half or less CPU resources. 

It has not been advertised by Adobe, but there is some speculation on the web that Flash 10.1 may support VDPAU. They are saying the beta 10.1 version supports GPU accelerated playback in Windows.

---

### Post by matt06 on 2009-12-08
> **heartburnkid said:**
> Is anybody else experiencing painfully slow video playback in Hulu Desktop?  I'm running it on an Athlon x2 4850e, and it drops frames left and right.  As well, remote response is sluggish while video is playing.  Admittedly, my graphic card is a little anemic (GeForce 6200TC) but that shouldn't really matter too much, should it?
I run Hulu Desktop with my P4 3.0 with a Geforce4 AGP card.  It's watchable, but I can tell it's struggling sometimes.  Performance is virtually identical running it from the command line or integrated into MythTV's menu as a button (Myth still running in the background).  I suspenct that you *should* be able to run it acceptably with your particular CPU and video card.

I tried Hulu before on 9.04 with a Celeron 2.0GHz CPU and Asus EN8400GS PCI-express card, but it was unusable.  Maybe I could have tweaked performance here and there to get it running better, but it seemed like a loosing battle with that CPU.

---

### Post by uncle hammy on 2009-12-09
> **colinnwn said:**
> I don't have an opinion on the quality of Hulu Desktop code, but I can say in this case, I don't think it is their fault. Blame Adobe Flash.
It's still their fault.  They CHOSE to USE Flash for a stand alone application.

---

### Post by uncle hammy on 2009-12-09
> **heartburnkid said:**
> All well and good, but I use Karmic, and I'm not in the Boxee beta yet.  I was hoping to use Hulu Desktop as a stopgap, but... well... I don't think that's going to work out.
I have Boxee Alpha installed on Karmic....64 bit Karmic...on 3 different machines.

---

### Post by colinnwn on 2009-12-09
> **uncle hammy said:**
> It's still their fault.  They CHOSE to USE Flash for a stand alone application.

It is their fault they chose a product with poor code quality on at least minority operating systems. 

But given the TV studios would insist on strong DRM, the options to be both in-browser and multiplatform were very limited, perhaps Flash was their only option until and if Moonlight supports Sliverlight DRM.

With their pre-existing flash based browser product, from a business case, it would have been ignorant not to reuse Flash in the desktop client. It just makes life hard for Linux users.

---

### Post by diskmaster23 on 2010-01-29
I am running 9.04 Mythbuntu with the Hulu Desktop intergration, but my remote isn't working. I am using Huppauge PVR-150.

It is also choppy.

I am running a AMD Athlon 64 3000+ Winchester 1.8GHz with 2.5Gigs of ram. I've made the dri and glx modifications to my xorg.conf without much Hulu performance improvement.

Please advise.

---------------
Solution

I followed the Slow Performance instructions at the bottom of this wiki entry.
[http://www.mythtv.org/wiki/Hulu_Desktop_Integration](http://www.mythtv.org/wiki/Hulu_Desktop_Integration)

---

### Post by zane131 on 2010-02-05
Everything seems to be working fine for me except that when I run Hulu Desktop from MythTV I get absolutely no sound. If I exit MythTV and launch Hulu Desktop as a stand alone application the sound works just fine. Any suggestions?

---

### Post by 4dognight on 2010-02-06
I had this happen too.
I had to open alsa mixer and turn on and up the slider for 'digital-1'.
My TV is connected via HDMI.

---

### Post by zane131 on 2010-02-06
I am also using HDMI audio, but the only option I have in alsamixer is IEC958 mute or unmute.

---

### Post by zane131 on 2010-02-06
It seems that running Hulu Desktop from the myth frontend is making the application slowly deteriorate. First there was no sound, but the video worked fine. Then while I was checking the blog-o-sphere for a solution, I let a video continue to run. Once it got to one of the commercial breaks it played the commercial, but never resumed to the video. The whole application seized up and I ultimately had to reboot. I tried one more time to load Hulu Desktop from the myth frontend. I could navigate the menu just fine until I tried to play a video, which caused it to seize once again. 

Again, when I close the myth frontend and launch Hulu Desktop as a standalone application, everything works perfectly fine.

---

### Post by murbanci on 2010-02-10
I keep getting the error:
```
Hulu Desktop could not locate the Flash plugin.

If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so.
```

I have tried editing .huludesktop with several positions of libflashplayer.so but nothing seems to work.  Any ideas?

---

### Post by sr_guy on 2010-02-15
9.04 Jaunty running Mythtv 0.21:

I have my Streamzap remote working with this code:

```

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Streamzap_PC_Remote
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = UP
button_name_down = DOWN
button_name_left = LEFT
button_name_right = RIGHT
button_name_select = OK
button_name_menu = MENU

```

My only issue, what about an iwr command that allows a remote control to close the hulu desktop and ends back at the main menu of mythtv?

---

### Post by TheMiz on 2010-02-15
> **williammanda said:**
> My remote ... doesn't seem to function correctly in Hulu desktop. I can press a button and it will react normally or it may do nothing or it may move several selections in one direction. Example: I press the down arrow, it may move one selection or not move or it may move several positions.

I am having this issue, and I've read through these pages, but I can not see if there was ever a good solution found.

I am using a DViCO Fusion Remote (which works great everywhere else)

Here is my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event3"
#REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS="--release"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```Here is the information at ~/.huludesktop
```
[display]
fullscreen = TRUE
width = 1024
height = 746
pos_x = 0
pos_y = 22

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = new-lircd.conf.conf
lirc_release_suffix = _UP
lirc_repeat_threshold = 3
button_name_up = up
button_name_down = down
button_name_left = left
button_name_right = right
button_name_select = ok
button_name_menu = dvdmenu

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1

```Here is the result of ps ax |grep lircd:
```
 1072 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/event3 --release
 6952 pts/0    S+     0:00 grep --color=auto lircd

```Like the quote above, I can get hulu desktop to recognize key presses, but it will take one key press, do 4 or 5 actions, then fail to respond again.  

When I run irw, I see this:
```
0000000000010067 00 up new-lircd.conf.conf
0000000000010067 00 up_UP new-lircd.conf.conf

```Any ideas?  I 've heard the adding the --release argument solves this, but not for me.

---

### Post by TheMiz on 2010-02-17
I should also mention that the keyboard controls work perfectly.  For now I need to VNC into the Mythbox from my Macbook to control it.  When I'm doing that, I might as well just watch HULU on my laptop.

---

### Post by klc5555 on 2010-02-17
> **sr_guy said:**
> 9.04 Jaunty running Mythtv 0.21:

I have my Streamzap remote working with this code:

```

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = Streamzap_PC_Remote
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = UP
button_name_down = DOWN
button_name_left = LEFT
button_name_right = RIGHT
button_name_select = OK
button_name_menu = MENU

```

My only issue, what about an iwr command that allows a remote control to close the hulu desktop and ends back at the main menu of mythtv?

Just maneuvering the menu within the Hulu desktop by remote control and exiting Hulu desktop from there, as the app was designed, dumps me back to the point in the Mythtv menu from which I entered Hulu desktop. Or is something more complicated  necessary?

---

### Post by D3mon_Spawn on 2010-02-18
I am currently running Ubuntu 9.10 x64, and I'm using the third party flash script maintained by the Ubuntu community: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) I decided one day to install Hulu Desktop since hulu.com hasn't been working for me lately (I think its most likely because of the version of flash I'm using). Anyway, whenever I start Hulu Desktop I get this error message: 

Hulu Desktop could not locate the Flash plugin.

If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so.

I found the libflashplayer.so but I don't know how to modify it. Also I don't seem to even have (or at least i couldn't find) the ~/.huludesktop folder. Any ideas???

---

### Post by williammanda on 2010-02-18
> **TheMiz said:**
> I am having this issue, and I've read through these pages, but I can not see if there was ever a good solution found.

I am using a DViCO Fusion Remote (which works great everywhere else)

Here is my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event3"
#REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS="--release"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```Here is the information at ~/.huludesktop
```
[display]
fullscreen = TRUE
width = 1024
height = 746
pos_x = 0
pos_y = 22

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = new-lircd.conf.conf
lirc_release_suffix = _UP
lirc_repeat_threshold = 3
button_name_up = up
button_name_down = down
button_name_left = left
button_name_right = right
button_name_select = ok
button_name_menu = dvdmenu

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1

```Here is the result of ps ax |grep lircd:
```
 1072 ?        Ss     0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/event3 --release
 6952 pts/0    S+     0:00 grep --color=auto lircd

```Like the quote above, I can get hulu desktop to recognize key presses, but it will take one key press, do 4 or 5 actions, then fail to respond again.  

When I run irw, I see this:
```
0000000000010067 00 up new-lircd.conf.conf
0000000000010067 00 up_UP new-lircd.conf.conf

```Any ideas?  I 've heard the adding the --release argument solves this, but not for me.

There never was a solution for this problem. I can get around the issue because my remote has a gyro mouse built in.

---

### Post by tgm4883 on 2010-02-18
> **D3mon_Spawn said:**
> I am currently running Ubuntu 9.10 x64, and I'm using the third party flash script maintained by the Ubuntu community: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) I decided one day to install Hulu Desktop since hulu.com hasn't been working for me lately (I think its most likely because of the version of flash I'm using). Anyway, whenever I start Hulu Desktop I get this error message: 

Hulu Desktop could not locate the Flash plugin.

If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so.

I found the libflashplayer.so but I don't know how to modify it. Also I don't seem to even have (or at least i couldn't find) the ~/.huludesktop folder. Any ideas???

~/.huludesktop is a hidden file. Use ctrl+h to view hidden files in nautilus

---

### Post by D3mon_Spawn on 2010-02-19
> **tgm4883 said:**
> ~/.huludesktop is a hidden file. Use ctrl+h to view hidden files in nautilus

I've done that and its not there...

---

### Post by TheMiz on 2010-02-20
> **williammanda said:**
> There never was a solution for this problem. I can get around the issue because my remote has a gyro mouse built in.

Oh.  Well thanks for the reply!

---

### Post by LowSky on 2010-02-24
> **D3mon_Spawn said:**
> I've done that and its not there...

.huludesktop is in the /home folder


in the file just list where flash file is located, or delete the .huludesktop file and reboot, it might find it

---

### Post by dragonborn on 2010-02-26
You're correct the .huludesktop is located in your home folder if it isn't then reinstall, open a terminal and type ls -a should show the .huludesktop , in side of this file you will see a line "flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so" or some such line indicating where your flash.so file is located.


another problem that could cause this is left over flash garbage from previous installs or upgrades, cleaning your system of any and all flash and reinstalling clean will fix this. then just reinstall hulu and it should work fine.

---

### Post by Kepesk on 2010-03-17
This tutorial is great.  It let me install and run Hulu just fine, and the remote works perfectly.  One problem though: the videos don't play at all.

Whenever I open Hulu and play any video, it loads for a minute or two and then displays the message "This request is taking longer than expected.  Would you like to cancel it and do something else?"

I know it's not my network, because Hulu Desktop runs on my other Ubuntu machine just fine.  I don't think it's flash because I can close out of MythTV and open up Firefox to play Hulu videos there just fine.  What else could this be?

Any ideas?

---

### Post by zane131 on 2010-03-18
> **Kepesk said:**
> This tutorial is great.  It let me install and run Hulu just fine, and the remote works perfectly.  One problem though: the videos don't play at all.

Whenever I open Hulu and play any video, it loads for a minute or two and then displays the message "This request is taking longer than expected.  Would you like to cancel it and do something else?"

I know it's not my network, because Hulu Desktop runs on my other Ubuntu machine just fine.  I don't think it's flash because I can close out of MythTV and open up Firefox to play Hulu videos there just fine.  What else could this be?

Any ideas?

I have run into the same problem. I did find out that I only have the problem when I launch Hulu Desktop from within the mythfrontend. Hulu Desktop works perfectly fine when launched as a standalone application.

---

### Post by Kepesk on 2010-03-18
Confirmed.  It works just fine when I open it through the main menu and not through MythTV.

I investigated it and discovered that as long as the MythTV fromtend is running, Hulu throws this error no matter how I start it (from Myth, from the menu, from the command line).  How could the Myth frontend be interfering with Hulu Desktop?

---

### Post by colinnwn on 2010-03-18
> **Kepesk said:**
> as long as the MythTV fromtend is running, Hulu throws this error no matter how I start it... How could the Myth frontend be interfering with Hulu Desktop?

I don't know, but out of morbid curiosity did you try to launch MythFE while Hulu was running? If so, did it mess up up Hulu, or did Myth not launch and run correctly?

---

### Post by Kepesk on 2010-03-19
Hah, I figured it out!  What I had to do is open Hulu Desktop from the menu, right click on the video, go to the Flash settings, and disable hardware acceleration.  After that, it launched and played videos just fine from MythTV.  I hope that helps anyone else with the same issue.

One last annoying problem though: I don't have the bandwidth to handle high quality videos.  However, the program automatically sets my video quality to high every time I run Hulu Desktop.  I have to go plug a mouse into the box to set my quality to low every time I run it (the low quality doesn't bother me since it's an old TV).

Is there any way to get it to automatically play videos on low quality from the start?

Thanks!

---

### Post by tgm4883 on 2010-03-19
> **Kepesk said:**
> Hah, I figured it out!  What I had to do is open Hulu Desktop from the menu, right click on the video, go to the Flash settings, and disable hardware acceleration.  After that, it launched and played videos just fine from MythTV.  I hope that helps anyone else with the same issue.

One last annoying problem though: I don't have the bandwidth to handle high quality videos.  However, the program automatically sets my video quality to high every time I run Hulu Desktop.  I have to go plug a mouse into the box to set my quality to low every time I run it (the low quality doesn't bother me since it's an old TV).

Is there any way to get it to automatically play videos on low quality from the start?

Thanks!

I think you have to register with Hulu for that and then set it as your default in the web interface.

---

### Post by zane131 on 2010-03-19
> **Kepesk said:**
> Hah, I figured it out!  What I had to do is open Hulu Desktop from the menu, right click on the video, go to the Flash settings, and disable hardware acceleration.  After that, it launched and played videos just fine from MythTV.  I hope that helps anyone else with the same issue.

Thanks! This fixed the video issue, however, I still have no sound. Everything else works perfectly fine within MythTV and the sound works when I launch Hulu Desktop as a standalone application. Any suggestions?

---

### Post by oobe-feisty on 2010-04-02
> **williammanda said:**
> My remote Gyration GYR3101US ,doesn't seem to function correctly in Hulu desktop. I can press a button and it will react normally or it may do nothing or it may move several selections in one direction. Example: I press the down arrow, it may move one selection or not move or it may move several positions.


I had the exact same problem upgradeing to flash 10.1 beta fixed this for me hope this helps btw it worked perfect with a common mceusb remote but on my pc i use the most i use a different remote with /dev/input device this is the one i had troubles with and upgrading to 10.1 flash fixed it.

---

### Post by williammanda on 2010-04-03
Please specify how you upgraded to flash 10.1 beta and which beta? Beta 3 is out.

---

### Post by oobe-feisty on 2010-04-04
i don't use ubuntu anymore i don't use a package for flash plugin i just downloaded the generic tar ball from the adobe site and overwrote my old one 

flashplayer10_1_p3_linux_022310.tar.gz  is the name of the file 

here is a direct link [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz)

p.s if you overwrite libflashplayer.so while firefox is running it will probably crash not a huge problem as it restores all tabs

p.p.s if you don't know where libflashplayer.so is use locate its probably somewhere like /usr/lib/mozilla/plugins/

p.p.p.s if it works for you i would suggest removing the flash package or locking it to prevent it from being overwritten

---

### Post by the_pod on 2010-05-04
Anybody get volume and the pause/play feature to work with their remote?  I don't see an option to change in the /.huludesktop file so I'm not sure where to look.

On a separate note Unclutter looks cool. How do I make this load from startup?  I'm kinda clueless there.

THanks.

---

### Post by the_pod on 2010-05-06
> **the_pod said:**
> Anybody get volume and the pause/play feature to work with their remote?  I don't see an option to change in the /.huludesktop file so I'm not sure where to look.

On a separate note Unclutter looks cool. How do I make this load from startup?  I'm kinda clueless there.

THanks.

Err... never mind on the volume and pause.  For those who haven't figured it out, up and down control volume; OK / Go or whatever the main button is toggles the pause/play.

---

### Post by azmyth on 2010-06-10
Does anyone know what the lirc_repeat_threshold does? Say I move to the right with one key press the cursor moves two spots. From looking at irw output, I'm not surprised as I see multiple key presses in the terminal on one key press. I've seen others in this thread posting their irw output with the same behavior so I figure someone has a solution.

---

### Post by colinnwn on 2010-06-10
> **azmyth said:**
> Does anyone know what the lirc_repeat_threshold does?

One of my irritations trying to set up Hulu, was that no good documentation exists of all the configuration options in Hulu, and the LIRC documentation is cursory and out of date. To make up for this, some options that should be in Hulu aren't. 

As I vaguely recall, I discovered the lirc_repeat_threshold is the amount of time before Hulu would recognize a LIRC continuing button press (or hold down), as a new independent button press instead.

In my not so humble opinion, this option is stupid and unnecessary. As you have discovered, for some reason LIRC will register a single button press (under one second duration) as multiple independent button presses, and Hulu will respond by jumping 2 or 3 menus in either direction. I guess LIRC doesn't have its own internal button debounce, which is bog standard for most hardware and software button implementations.

What this should have been was a debounce setting, where it is the number of milliseconds after a button press, before Hulu would act on another new button press. That way you could get Hulu to ignore all those rapid button presses that cause you to blow right by the option you want.

---

### Post by tgm4883 on 2010-06-10
> **colinnwn said:**
> One of my irritations trying to set up Hulu, was that no good documentation exists of all the configuration options in Hulu, and the LIRC documentation is cursory and out of date. To make up for this, some options that should be in Hulu aren't. 

As I vaguely recall, I discovered the lirc_repeat_threshold is the amount of time before Hulu would recognize a LIRC continuing button press (or hold down), as a new independent button press instead.

In my not so humble opinion, this option is stupid and unnecessary. As you have discovered, for some reason LIRC will register a single button press (under one second duration) as multiple independent button presses, and Hulu will respond by jumping 2 or 3 menus in either direction. I guess LIRC doesn't have its own internal button debounce, which is bog standard for most hardware and software button implementations.

What this should have been was a debounce setting, where it is the number of milliseconds after a button press, before Hulu would act on another new button press. That way you could get Hulu to ignore all those rapid button presses that cause you to blow right by the option you want.

Unless it has changed in recent builds, hulu desktop requires that you set the release option in lirc. Then it doesn't matter if you hold the button for 1 second or for 1,000,000 seconds it's still a single button press until you let go. IMO, that is more elegant that x amount of time after a button press.

---

### Post by colinnwn on 2010-06-10
> **tgm4883 said:**
> Unless it has changed in recent builds, hulu desktop requires that you set the release option in lirc. Then it doesn't matter if you hold the button for 1 second or for 1,000,000 seconds it's still a single button press until you let go. IMO, that is more elegant that x amount of time after a button press.

I didn't change anything in Lirc to not screw up Myth, so I might have it configured sub-prime. But it is hard to tell since Lirc documentation is so bad.

I only mapped the Hulu codes to the Lirc codes. As I recall, release was set. I watched IRW to see what was going on. I could see for example in less than a second (even though I pressed the right button only once)...

right
right_up
right
right_up
right
right_up

And Hulu of course would jump 3 menus to the right. Since Lirc either has such poor debounce, or my remote acts wierd, or I have Lirc set up poorly, it would be nice if there was a Hulu setting that said ignore button presses if they come less than x milliseconds since the last button_up command.

---

### Post by azmyth on 2010-06-10
I'm running into the same problem as collinnwn. I hit a button and irw shows multiple say right_UP thus the cursor moves multiple places to the right. Myth or lirc handles this without issue. 

Guess there isn't a way to add huludesktop to the lircrc file with prog = huludesktop. On my searches, I saw that someone added _DISABLED to the end of the lirc_remote_identifier name and then ran everything through the lircrc file but this was for prog irexevent so I'm not sure if this would work.

---

### Post by tgm4883 on 2010-06-10
> **colinnwn said:**
> I didn't change anything in Lirc to not screw up Myth, so I might have it configured sub-prime. But it is hard to tell since Lirc documentation is so bad.

I only mapped the Hulu codes to the Lirc codes. As I recall, release was set. I watched IRW to see what was going on. I could see for example in less than a second (even though I pressed the right button only once)...

right
right_up
right
right_up
right
right_up

And Hulu of course would jump 3 menus to the right. Since Lirc either has such poor debounce, or my remote acts wierd, or I have Lirc set up poorly, it would be nice if there was a Hulu setting that said ignore button presses if they come less than x milliseconds since the last button_up command.

Something is wonky there as the _up should only show up once for every release.  Do you have multiple lirc daemons running?

---

### Post by tgm4883 on 2010-06-10
It's also possible that something has changed in lirc to cause this. I don't use huludesktop anymore, instead I use MythNetVision.

What version of mythbuntu are you using?

---

### Post by colinnwn on 2010-06-10
> **tgm4883 said:**
> It's also possible that something has changed in lirc to cause this. I don't use huludesktop anymore, instead I use MythNetVision.

What version of mythbuntu are you using?

I haven't set Lirc up to run multiple daemons, and I don't see it when looking in the process list.

This was all happening on MythBuntu 9.10/0.22. I am now on Mythbuntu 10.04/0.23, but it is screwed up so badly, I still need to try a fresh install rather than an upgrade, and if it doesn't get better, try downgrading to 9.10/0.23 autobuilds.

---

### Post by azmyth on 2010-06-10
I have another daemon running for my blaster. I assume that wouldn't interfere with the receiver.

I'm running MB 10.04. I see there's a lirc option of --repeat-max=limit. I have a homebrew USB receiver and for unknown reasons the latest version of lirc doesn't work so I'm running 8.4a compiled. The latest version of lirc worked with my hw on 32 bit home PC but not 64 bit MB go figure. 8.4a doesn't have the repeat-max option. Guess I could retry lirc since this was on 9.10 I had the problem. Maybe someone else can try since it'll be easier for them.

---

### Post by ali_williams on 2010-06-12
my issue is that it stuck on loading.. its quite odd because i gave it the location of the flash file but it still says loading.

---

### Post by Nausser on 2010-06-23
After following this post to get Hulu Desktop working on my Mythbuntu 10.04 machine, I needed to stop the screensaver from popping up as well. 
Here is a link to a post on how to do this:
Click>[Screensaver suspend/resume config]("http://forum.nerdsonstandby.com/viewtopic.php?f=5&t=3")

There is also a sister post to that one on getting your Menu button to work in Hulu Desktop (will work for any button that is not working in Hulu Desktop)
Click>[Button Config]("http://forum.nerdsonstandby.com/viewtopic.php?f=5&t=4")

****Please note that these posts are very elementry. It is a great forum for beginners/noobs to hang out.

I hope this helps someone!

---

### Post by w1ll1am on 2012-07-03
Hello I am having an issue with hulu desktop in general when I try to make the player full screen it crashes. Is anyone else having this problem?

If there is a fix for this does anyone know how to make it start full screen? Thanks

---

### Post by nickrout on 2012-07-03
> **w1ll1am said:**
> Hello I am having an issue with hulu desktop in general when I try to make the player full screen it crashes. Is anyone else having this problem?

If there is a fix for this does anyone know how to make it start full screen? Thanks

Please open a new thread, this one is 2 years old.

---

### Post by wildmanne39 on 2012-07-04
Hi, this is an old thread so it has been closed, please start a new thread.
Thanks

---

