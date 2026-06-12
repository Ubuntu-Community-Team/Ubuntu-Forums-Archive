---
title: "DVB USB tuner, device recognised but not registered"
date: 2010-01-30
forum: Mythbuntu
---

### Post by hoontune on 2010-01-30
Hi,

Trying to install a LifeView TV Walker Twin DVB-T USB2.0 on Mythbuntu 9.1 (details below)

[SIZE=3]**Summary:**[/SIZE]

dsmesg tells me that it can see the device, but it doesn't seem to want to install it as a tuner

:~$ dmesg | grep dvb
[  145.725987] dvb-usb: found a 'LifeView TV Walker Twin DVB-T USB2.0' in cold state, will try to load a firmware
[  145.725996] usb 2-2: firmware: requesting dvb-usb-tvwalkert.fw
[  145.805190] dvb-usb: downloading firmware from file 'dvb-usb-tvwalkert.fw'
[  146.233190] usbcore: registered new interface driver dvb_usb_m920x


[SIZE=3]**How I got this far:**[/SIZE]

I modified the workflow I found here :
[http://thejungleonline.wordpress.com/2009/08/09/setup-avlabs-avl680hd-dvb-t-usb-tuner-on-ubuntu-9-04/](http://thejungleonline.wordpress.com/2009/08/09/setup-avlabs-avl680hd-dvb-t-usb-tuner-on-ubuntu-9-04/)
[INDENT][I][B]sudo apt-get install mercurial
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd ./v4l-dvb/
make
sudo make install
sudo reboot[/B][/I]
 *After your PC reboots you need to check if your hardware is now recognised with the following :-*
 [I][B]
dmesg | grep dvb[/B][/I]
 *This should advise that the hardware has been detected but needs to load the firmware. *

[/INDENT]This was correct


I found the firmware from a post here: [http://www.mythtv.org/pipermail/mythtv-users/2007-November/203709.html](http://www.mythtv.org/pipermail/mythtv-users/2007-November/203709.html)
[INDENT]

*So we now need to install the frmware for the chipset. Do this with the following :-*
 [I][B]cd /lib/firmware
[/B][/I]


 ***sudo wget ***[SIZE=2]**[http://www.nick-andrew.net/LifeView/dvb-usb-tvwalkert.fw](http://www.nick-andrew.net/LifeView/dvb-usb-tvwalkert.fw)**[/SIZE]
 

*** sudo reboot***

[/INDENT]so I reboot and look at dmesg again

dmesg | grep dvb

[INDENT][  145.725987] dvb-usb: found a 'LifeView TV Walker Twin DVB-T USB2.0' in cold state, will try to load a firmware
[  145.725996] usb 2-2: firmware: requesting dvb-usb-tvwalkert.fw
[  145.805190] dvb-usb: downloading firmware from file 'dvb-usb-tvwalkert.fw'
[  146.233190] usbcore: registered new interface driver dvb_usb_m920x
[/INDENT]
[SIZE=1]I don't see a line stating that "dvb-usb will pass the complete MPEG2 transport stream[SIZE=2][SIZE=1]"[/SIZE][SIZE=1] etc[/SIZE]

Any help would be appreciated

Thanks
H


[/SIZE][/SIZE][B][SIZE=3]
Versions etc[/SIZE][/B]
MythBuntu 9.1

:~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.22.0+fixes22594-0ubuntu1
  Candidate: 0.22.0+fixes22594-0ubuntu1
  Version table:
 *** 0.22.0+fixes22594-0ubuntu1 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Packages
        100 /var/lib/dpkg/status

---

### Post by hoontune on 2010-01-31
I was testing this on a dev machine, and had used a normal usb to mini-usb cable.  When I looked at the pc the tuner was normally connected to, I remembered that the device uses a weird double usb plug to mini-usb cable.
 
Use the right cable and it works!

---

