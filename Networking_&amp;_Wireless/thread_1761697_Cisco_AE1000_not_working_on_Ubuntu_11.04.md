---
title: "Cisco AE1000 not working on Ubuntu 11.04"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by Golevel on 2011-05-18
lsusb:

> Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I tried this guide:

[http://ubuntuforums.org/showpost.php?p=10629871&postcount=4](http://ubuntuforums.org/showpost.php?p=10629871&postcount=4)

With this driver:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
RT2870USB(RT2870/RT2770) 	07/09/2010 	2.4.0.1


Any ideas?

---

### Post by jasonuscg on 2011-05-18
Similar situation here...

I tried to apply this guide using 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO.bz2

[http://www.youtube.com/watch?v=cwMiHiaWtPI](http://www.youtube.com/watch?v=cwMiHiaWtPI)

All was good I could see all available access points, but the APs refuse the pass phrase.

My main AP is a Cisci/Linksys E3000 running 'DD-WRT v24-sp2 (04/11/11) mega - build 16773M NEWD-2 K2.6 Eko' On both 2.4GHz and 5GHz I am using WPA2 Personal AES, I even switched to WPA2 Personal Mixed TKIP+AES, no joy.

I'll try to grab a "uname -a" and "lsusb" and post the here ASAP.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

uname -a
Linux Nix 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0caf:2317 Buslink 
Bus 001 Device 006: ID 06e6:c200 Tiger Jet Network, Inc. Internet Phone
Bus 001 Device 005: ID 0caf:2315 Buslink 
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 003: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Golevel on 2011-05-18
Thanks, I hope someone can help :)

---

### Post by jjmilburn on 2011-05-18
Just upgraded to 11.04 and had working RT2870 (Linksys AE1000) before but didn't after upgrade.  I tried compiling and installing the RT2870 driver, but that didnt work.  I installed a modified RT3572 driver that I came across previously trying to get this to work, and it works like a charm!  270Mb/s negotiated, seems good :).

Output from iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"Vheissu"  Nickname:"RT3572STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:1D:7E:4F:1E:DD   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-65 dBm  Noise level:-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Output from lsusb:
```
josh@Frost:~$ lsusb
Bus 002 Device 002: ID 099a:7202 Zippy Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 001 Device 002: ID 08ec:0020 M-Systems Flash Disk Pioneers TravelDrive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have linked the driver install folder (compressed) exactly as I had it 10 minutes ago after I got this working.  Maybe it will be of use to someone.  
[URL="http://www.qfpost.com/download.do?get=885eb1bd56cc65595f8daaf41326b2da"]
[/URL][http://www.qfpost.com/download.do?get=885eb1bd56cc65595f8daaf41326b2da](http://www.qfpost.com/download.do?get=885eb1bd56cc65595f8daaf41326b2da)

---

### Post by chili555 on 2011-05-18
I think you will all need to blacklist rt2800usb:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot.

---

### Post by Golevel on 2011-05-19
I just tried that and it didn't work.

iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jjmilburn on 2011-05-19
For some reason, blacklisting rt2870sta doesn't work.  It keeps loading on bootup.  I ram update-initramfs -u to no avail.

To get my wireless to work, I have to unplug the adapter, then type the following:
```
sudo modprobe -r rt2870sta
```
(I may have also had to force something, trying to recall from memory from last night).

Then I believe I had to type

```
sudo modprobe rt3572
```

I have rt2800 and rt2870sta blacklisted.

Any thoughts on how to make Ubuntu actually blacklist the rt2870sta driver?  I thought the blacklist.conf file was supposed to do that....

---

### Post by chili555 on 2011-05-19
> I thought the blacklist.conf file was supposed to do that....Show us yours, please, as well as:```
cat /etc/modules
```Thanks.

---

### Post by Golevel on 2011-05-19
My lsusb listed mine as a 2870, doesn't that mean that the 2870 driver should be correct? Do I need a different driver?

---

### Post by chili555 on 2011-05-19
> Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] You need rt3572sta and it needs to be amended. Please carefully read posts 7 through 12 here: [http://ubuntuforums.org/showthread.php?t=1630358](http://ubuntuforums.org/showthread.php?t=1630358)

---

### Post by jjmilburn on 2011-05-19
> **chili555 said:**
> Show us yours, please, as well as:```
cat /etc/modules
```Thanks.

/etc/modprobe.d/blacklist.conf below:
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2870sta

#FOR AE1000
blacklist rt2800usb

#FOR AE1000
blacklist rt2870sta

#FOR AE1000
blacklist rt2870
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```And cat/etc/modules:
```
josh@Frost:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

rt2870sta
lp
rtc

```Didn't know about that second file, I bet removing it from there should work.  I wish that was mentioned more frequently in correlation with blacklisting, didn't see that until your post. Going to remove it and try/report back.

EDIT: Works fine now.  Had to blacklist rt2800usb and rt2870sta, and also remove rt2870sta from /etc/modules

---

### Post by Golevel on 2011-05-23
> **jjmilburn said:**
> /etc/modprobe.d/blacklist.conf below:
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2870sta

#FOR AE1000
blacklist rt2800usb

#FOR AE1000
blacklist rt2870sta

#FOR AE1000
blacklist rt2870
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```And cat/etc/modules:
```
josh@Frost:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

rt2870sta
lp
rtc

```Didn't know about that second file, I bet removing it from there should work.  I wish that was mentioned more frequently in correlation with blacklisting, didn't see that until your post. Going to remove it and try/report back.

EDIT: Works fine now.  Had to blacklist rt2800usb and rt2870sta, and also remove rt2870sta from /etc/modules
Can you post a step by step for how you successfully blacklisted those?

---

### Post by jjmilburn on 2011-05-23
To blacklist, just type the following into terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and provide the password when asked.

Then, go to the bottom of the blacklist.conf file that is now open, and add the following lines:

```

blacklist rt2800usb
blacklist rt2870sta
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```

Save and close the file.

Then, go into another terminal and type

```
sudo gedit /etc/modules
```

If you see an entry for "rt2870sta" in here, remove it.  Save and close the file.  Reboot.

---

### Post by Golevel on 2011-05-23
> **jjmilburn said:**
> To blacklist, just type the following into terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and provide the password when asked.

Then, go to the bottom of the blacklist.conf file that is now open, and add the following lines:

```

blacklist rt2800usb
blacklist rt2870sta
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```

Save and close the file.

Then, go into another terminal and type

```
sudo gedit /etc/modules
```

If you see an entry for "rt2870sta" in here, remove it.  Save and close the file.  Reboot.

Thanks, I just tried that and no luck. What guide did you follow to install the actual driver? I'm thinking that I must have goofed something up there.

---

### Post by bubba911 on 2011-06-10
[http://www.youtube.com/watch?v=cwMiHiaWtPI](http://www.youtube.com/watch?v=cwMiHiaWtPI)

In the description I put in a link for rt3572 2.4.0.2 (took me forever to find it myself when I first went looking for it), I also believe this to be a lot less buggy than 2.5.0.0.

It seems to work better and doesn't have the you issue where you can see the AP but can't write in a Pass-phrase it accepts.

---

### Post by gershy on 2011-10-15
> **chili555 said:**
> I think you will all need to blacklist rt2800usb:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot.

I tried this with no avail; however, after editing the code to:
```
blacklist rt2870lib
             blacklist rt2870usb
             blacklist rt28xxusb
             blacklist rt28xxlib
```I was able to connect to my router. I'm new to linux and don't know if this will be a viable solution for anyone else but it worked for me.

---

### Post by bearcatrp on 2011-11-28
I upgraded to 11.4 after reading on these forums that the AE1000 should work without doing allot of editing to get it working. Still not working after doing everything posted on these forums.
  Is there a correct way of enabling the AE1000 yet or are there still issues? Looking for the correct directions for a semi ubuntu noob. I did see the link for i2productions for there way to get this to work. Not sure if I want to try another maybe it will work solution.

---

### Post by alain1988 on 2012-07-30
hy i got this fixed this way 

i downloaded 2010_0915_RT3572_Linux_STA_v2.4.0.2
and executed these commands

sudo apt-get install build-essential linux-headers-generic 
unzip 2010_0915_RT3572_Linux_STA_v2.4.0.2.zip 
cd 2010_0915_RT3572_Linux_STA_v2.4.0.2/ 
make 
sudo make install 
sudo modprobe rt3572sta
sudo reboot

and it worked

---

