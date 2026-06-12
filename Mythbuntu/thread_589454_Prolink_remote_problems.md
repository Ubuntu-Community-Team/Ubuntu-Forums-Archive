---
title: "Prolink remote problems"
date: 2007-10-24
forum: Mythbuntu
---

### Post by pentzol on 2007-10-24
Hi,

Mythbuntu (7.10). 
Hardware : P4 2.0ghz 512 MB ram Geforce 440 64 mb 60 hdd

All seems to be well except I cannot get the remote to work.
It's a Pixelview PlayTV MPEG2 (pv - M4900) card and remote combo.
The files /home/user1/.lircrc and /home/user1/.mythtv/lircrc is both there and they look both correct.
I started irw to see if anything comes up but no response
ps -ef  shows /usr/sbin/lircd --driver=dev/input

 I have in  /dev/input :
 ls -alrt
total 0
crw-rw----  1 root root 13, 32 2007-10-24 21:03 mouse0
crw-rw----  1 root root 13, 63 2007-10-24 21:03 mice
crw-rw----  1 root root 13, 65 2007-10-24 21:03 event1
crw-rw----  1 root root 13, 64 2007-10-24 21:03 event0
crw-rw----  1 root root 13, 33 2007-10-24 21:03 mouse1
crw-rw----  1 root root 13, 66 2007-10-24 21:03 event2
crw-rw----  1 root root 13, 67 2007-10-24 21:03 event3
drwxr-xr-x  2 root root    120 2007-10-24 21:03 by-path
crw-rw----  1 root root 13, 69 2007-10-24 21:03 event5
crw-rw----  1 root root 13, 68 2007-10-24 21:03 event4
drwxr-xr-x  3 root root    240 2007-10-24 21:03 .
drwxr-xr-x 12 root root  14120 2007-10-24 21:03 ..

I have only the following file in /dev in regards to lirc
srw-rw-rw-  1 root   root           0 2007-10-24 21:03 lircd

The layout in /etc/lirc/lircd.conf file is spot on for the remote that it is for - I don't know about the rest of the info.

Here is the hardware.conf which doesn't tell me much on where what is :
user1@user1-desktop:/etc/lirc$ more hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Pixelview PlayTV MPEG2"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="pixelview/lircd.conf.playtv_pro"
LIRCMD_CONF=""

===================================
The lircmd.conf file is unconfigured.

I cannot find any file called lircd.conf.playtv_pro - should that maybe be the file /etc/lirc/lircd.conf ?

Anybody have a few Ideas I can try.
This is by far the closest I have come to having the remote installed. I have knoppmyth and mythdora but no luck on either.

Thanks
Lourens

---

### Post by pentzol on 2007-10-25
Ok Progress....
I found some further info:
I created a entry in /etc/modules called bttv and in /etc/modprobe.d created a file called bttv with the entry :
options bttv card=139 tuner=44 radio=1 ( i also tried tuner 69 and no noticable difference)

I scanned 4 channels which is about the few free to air channels you can get here.
I can change the channel by watching tv and then selecting the channel using the numbers on the remote.
Navigation using the CH+ or CH- in the menu's or changing channel, volume, etc does not work.
Running irw I can see the numbers of the remote nothiing else.


I also had no sound - when I pulled the card to see what the tuner is ( ymec tvf88t5-b/dff) I noticed pins on the card audio out and audio in - I plugged the CD sound cable into the audio out and now I have sound although it does not stop when I exit the Watching TV menu - it keeps on playing even whilst making config changes - only stops if I reboot.


===========
There has been mention of things like alias char-major-81 i2c-dev in the modules
Anybody that can give me a easy explanation of what that means and what does that influence in regards to the tv card and or remote

I am now of to look at the remote's conf file

---

### Post by superm1 on 2007-10-26
You need to modify your DEVICE="" line as described here:
[https://blueprints.edge.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative](https://blueprints.edge.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative)

Just modify the line and restart lirc.

---

### Post by pentzol on 2007-10-29
Thanks for the reply.

I have tried as suggested but no go.
My devices files looks like this :
I: Bus=0001 Vendor=109e Product=036e Version=0001
N: Name="bttv IR (card=139)"
P: Phys=pci-0000:02:0d.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=100003
B: KEY=2c0814 100004 0 0 0 4 2008000 2090 2001 1e0000 4400 0 ffc


So the handler seems to different - I have tried /dev/input/event4, but nothing works then ( I think I just might try that agin to be doubly sure)

---

### Post by pentzol on 2007-10-29
scratch the previous post - I ran the command as is on the webiste and it seems to be working - I will have a look at the config file supplied and the new one created

Thanks heaps

---

