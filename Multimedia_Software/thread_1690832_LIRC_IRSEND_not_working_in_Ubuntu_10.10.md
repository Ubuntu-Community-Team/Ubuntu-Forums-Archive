---
title: "LIRC IRSEND not working in Ubuntu 10.10"
date: 2011-02-19
forum: Multimedia Software
---

### Post by Gadgetman on 2011-02-19
I have recently built a new Ubuntu 10.10 (64bit) and installed MythTV and LIRC.
I have correctly (?) configured LIRC for my specific IR Blaster on the serial port. Using the test send (see below), nothing happens - ie none of the pins on the serial port change state, and hence my IR Blaster hardware does nothing. No errors are produced and the log output looks good (?) - see below.
# irsend  SEND_ONCE DSTV9110 1 2 3

tail -f /var/log/syslog
Feb 15 00:56:56 MalutiPVR2 lircd-0.8.7-pre3[10127]: lircd(default) ready, using /var/run/lirc/lircd
Feb 15 00:57:04 MalutiPVR2 lircd-0.8.7-pre3[10127]: accepted new client on /var/run/lirc/lircd
Feb 15 00:57:04 MalutiPVR2 lircd-0.8.7-pre3[10127]: removed client

root@MalutiPVR2:/etc/lirc# ls -l /dev/lirc*
crw------- 1 root root 250, 0 2011-02-13 07:42 /dev/lirc0
lrwxrwxrwx 1 root root     19 2011-02-15 00:56 /dev/lircd -> /var/run/lirc/lircd

I also re-enabled /dev/ttyS0 (as it has to be disabled for LIRC) and sent data to the port (echo hello > /dev/ttyS0), and found data on TX pin & DTR pin (using scope) just to prove to myself that the com port is working!

All of this works perfectly on my 10.04 installation. I still have the 10.04 installation so have been able to compare configs etc.

I note that on 10.04 ***lirc 0.8.6-0ubuntu4.2*** is installed, whereas on 10.10 ***lirc 0.8.7~pre3-0ubuntu1*** is installed.

Some configs:-
**/etc/lirc/lircd.conf** 
#Configuration for the Home-brew (16x50 UART Hauppauge PVR-150 RC) remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

#Configuration for the Home-brew (16x50 Serial Port UART] : DSTV Satellite Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dstv/dstv9110.conf"

[B]/etc/lirc/hardware.conf
[/B]REMOTE="Home-brew (16x50 UART Hauppauge PVR-150 RC)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Home-brew (16x50 Serial Port UART] : DSTV Satellite Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="dstv/dstv9110.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

What could be wrong?
Do others have this working?

---

### Post by bogustrumper on 2011-03-02
I'll give this thread a bump, since I'm having a similar issue.  I'm running an IR receiver off of a Hauppauge PVR 350 card, and a serial IR transmitter to talk to a Comcast Digital Transport Adapter.  I had this same setup/same hardware running smoothly for quite awhile in Mythdora 10 (using the transmitter configuration file that I got here:
[http://regx.dgswa.com/html/Comacast_DTA-and_MythTV](http://regx.dgswa.com/html/Comacast_DTA-and_MythTV)), but I moved and got a new HDTV, decided I'd do a software update so that I could work in hulu in HD.

If I do a default install of Mythbuntu 10.10, the remote works great.  But since I need to control a cable box to record anything meaningful, that is not enough.  Once I try to enable the serial ir blaster, I run into the same wall -- the transmitter never blinks when I run ir_send.  Furthermore, I seem to lose my remote.  It's quite frustrating, as is the fact that people are still having this issue.  

I've tried running all the obvious things:
I ruled out the hardware by getting the IR blaster to blink using the python script found in post 13 at this page: [http://ubuntuforums.org/showthread.php?p=5417214](http://ubuntuforums.org/showthread.php?p=5417214)
I've tried reconfiguring lirc using dpkg-reconfigure, with no success.
I've tried installing lirc-modules-source, with no success.
I've tried running Mythbuntu's IR configuration gui, with no success.

It certainly seems like something out of the lirc box may be helpful to a lot of people at this point.  I tried coding something up in Python to send the raw codes, based on the script I found above.  I haven't entirely given up on that idea, honestly.  Toggling the pin up and down is going to be way too slow... but it seems somewhat plausible that I should be able to send some data at 1152000 and get sub-millisecond accuracy, right?

---

