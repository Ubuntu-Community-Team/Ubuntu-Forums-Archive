---
title: "ATI Remote Wonder II not working in Myth"
date: 2009-10-10
forum: Mythbuntu
---

### Post by usmcstitch on 2009-10-10
I'm posing this question in direct correlation with another post:
[http://ubuntuforums.org/showthread.php?t=1220383]("http://ubuntuforums.org/showthread.php?t=1220383").  I haven't gotten any replies to that one, so i'll dedicate one here.

I've spent a good part of 3 months studying, configuring testing etc.  trying to get this gdm ATI Remote Wonder II (Sapphire 5000024400) to work in Myth.  As described in the linked post above, the controler works in Mythbuntu and Myth F/E, sort of.  Only a few buttons work.  I cannot for the life of me get it to work fully.  

I installed lirc via Synaptic 
I uninstalled lirc via synaptic
I tried to install the latest lirc from source (make, make install) but I think i f-ed it up and my system to boot and I don't know how to go back.  Now the USB receiver isn't recognised in my test box.
I've reinstalled lirc via Synaptic
I've created/modified the 2 files: lircrc and lircd.conf (attached).  
I've put the lircd.conf under /etc/lirc/ 
I followed the directions in the above link and copied my lircrc to ~/.lircrc and made a symbolic link inside ~/.myth/
I've also made all lircrc files into my configured one 
I've poured over this link and studied it and tried doing it [http://www.mythtv.org/wiki/ATI_Remote_Wonder_II]("http://www.mythtv.org/wiki/ATI_Remote_Wonder_II")
I'm using both Ubuntu Jaunty (test b4 i put it on the mythbuntu) and Mythbuntu Jaunty (the system that i want to go live)
At one point I didn't even have a lirc0 file in /dev, only a lircd.  and no folder of the such
I've put my modified lircd.conf in /etc/lirc/
I've tried modifying the hardware.conf file a few times, using the link above and the default.
Nothing is working

[I]<snip> crap </snip?
[/I]
Let me know what i need to include or do or put in here.  I'm desperate to get this project done.  


Hardware.config (1)
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia X10 RF (kernel)"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

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

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Hardware.config (2)
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES="lirc_i2c lirc_dev"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

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

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

---

### Post by usmcstitch on 2009-10-11
Please...:(

---

### Post by usmcstitch on 2009-10-12
Hoping for a little help....

---

### Post by cybermatthieu on 2009-10-13
I have the same issue... Does anyone had ANY success with this remote on an ubuntu box??

---

### Post by cybermatthieu on 2009-10-13
Have you tried this:
[http://ubuntuforums.org/archive/index.php/t-316278.html](http://ubuntuforums.org/archive/index.php/t-316278.html)

---

### Post by usmcstitch on 2009-10-13
<snip> all crap </snip>

OK.  I've made headway.  Still have an issue though.

So far: 
[I]
bedroom@bedroom:~$ lsmod | grep lirc
lirc_atiusb            26032  0 
lirc_i2c               18948  0 
lirc_dev               22088  2 lirc_atiusb,lirc_i2c[/I]

[I]bedroom@bedroom:~$ ls -l /dev/ | grep lirc
crw-rw----  1 root   root     61,   0 2009-10-16 19:32 lirc0
srw-rw-rw-  1 root   root           0 2009-10-16 19:32 lircd
[/I]

[I]bedroom@bedroom:~$ dmesg | grep lirc
[   20.304161] lirc_dev: IR Remote Control driver registered, major 61 
[   90.548284] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[   90.548292] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   90.565527] lirc_dev: lirc_register_plugin: sample_rate: 0
[   90.565662] lirc_atiusb[3]:  on usb3:3
[   90.565733] usbcore: registered new interface driver lirc_atiusb
[/I]

[I]bedroom@bedroom:~$ cat /etc/modprobe.d/lirc-blacklist.conf 
#blacklist lirc_atiusb
blacklist ati_remote
blacklist ati_remote2[/I]

IRW sees the remote and translates the buttons.
[SIZE="2"][I]bedroom@bedroom:~$ irw
00000000000012ff 00 mouse_cursor_downright 5000024400
00000000000021ff 00 mouse_cursor_upleft 5000024400
00000000000021ff 00 mouse_cursor_upleft 5000024400
00000000000021ff 01 mouse_cursor_upleft 5000024400
00000000000021ff 02 mouse_cursor_upleft 5000024400
00000000000021ff 03 mouse_cursor_upleft 5000024400
00000000000022ff 00 mouse_cursor_downleft 5000024400
00000000000022ff 01 mouse_cursor_downleft 5000024400
00000000000022ff 02 mouse_cursor_downleft 5000024400
0000000000000206 00 6 5000024400
0000000000000206 01 6 5000024400
0000000000000204 00 4 5000024400
0000000000000204 01 4 5000024400
0000000000000202 00 2 5000024400
00000000000002d5 00 resize 5000024400
00000000000002d5 01 resize 5000024400
[/I][/SIZE]
I've set my lircrc files with the .conf extension

[I]bedroom@bedroom:~$ ls -l /etc/lirc/
total 24
-rw-r--r-- 1 root root 1081 2009-10-10 18:22 hardware.conf
-rw-r--r-- 1 root root 1053 2009-09-19 13:50 hardware.conf.old
-rwxr-xr-x 1 root root 2100 2009-10-10 17:55 lircd.conf
-rw-r--r-- 1 root root  422 2009-04-20 11:29 lircd.conf.dpkg-old
-rw-r--r-- 1 root root  540 2009-10-10 17:54 lircd.conf.org
-rw-r--r-- 1 root root  121 2009-04-20 03:40 lircmd.conf[/I]

My /etc/lirc/hardware.conf:
[SIZE="2"]```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES="lirc_i2c lirc_dev"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

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

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```[/SIZE]

The problem is that the remote isn't moving the mouse or recognizing commands, like it used to, in either Mythbuntu or MythTV, except with irw.  

It used to work.  How can i get it moving again?

---

### Post by usmcstitch on 2009-10-16
Bump cause i put more info and am making headway. (post above)

---

### Post by muffinito on 2009-10-20
I have been using the ati remote since 8.04. 
DO NOT USE LIRC!!

blacklist lirc module at boot and un-blacklist the atiremote module.

That should fix the mouse issue. 

Then choose to dont use a remote in the mythcontrol centre and you will need to use xmodmap to be able to play / pause, etc.

Hope this helps.

---

### Post by usmcstitch on 2009-10-27
Despite nobody but Muffinito and cybermatthieu trying to help, i'm going to update this post in the hopes that I can help someone else.

I got the remote to work fine and dandy in Mythtv. There was one key element missing, between the LIRCD.conf and Lircrc.conf file;

**Lircd.conf:** (/etc/lirc/lircd.conf)
[I]begin remote
name ATI_Remote_Wonder_II
bits 24
eps 30
aeps 100
one 0 0
zero 0 0
gap 203970[/I]

**Lircrc.conf**: ~/.lircrc.conf and/or ~/.lirc/insertconffilehere
[I]begin
prog = mythtv
remote = ATI_Remote_Wonder_II [/I]<-- THIS HAS TO MATCH UP w/ [I]LIRCD
button = stop
repeat = 2
config = T
end[/I]

Because i was using various sources, copying/pasting from each one, the remotes were not matching up. My lircd was using ATI_Remote_Wonder_II and my lircrc was using 5000024400.

To get only Myth to work i followed one link, namely: [http://ubuntuforums.org/showthread.php?t=1220383]("http://ubuntuforums.org/showthread.php?t=1220383")  

Then, from what i can gather, i just need to add entries to the lircrc file for the various other programs.

To solve my particular problem, i just nuked the entire box and started over.  I'm sure, in hindsight, that i could have just restored a backuped pre-tamper copy of the needed files.  My mouse stopped moving b/c i borked up my hardware file.  Confg files all discombobulated. 

Anyway, i hope this helps someone.

---

