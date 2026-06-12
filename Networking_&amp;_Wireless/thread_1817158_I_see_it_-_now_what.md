---
title: "I see it - now what?"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by freebird54 on 2011-08-03
Perhaps one of the most foolish conceptual failures I have experienced on a computer, but this wireless stuff is something I have avoided with great success up to this time.  I have been away from my systems for 3 years, and find myself needing wireless to set up in this (temporary) location.

As you can see from this:

```
freebird@eyrie:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:83:BF:1F
                    ESSID:"MYKELLE-HP_Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 1C:7E:E5:2E:A1:46
                    ESSID:"Prince-Smokey-net"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:26:5A:CA:EE:D1
                    ESSID:"CLAPTOP"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

I have figured out how to get ndiswrapper going, located and successfully installed a Win2K driver for my USB wireless access, and found several networks to hook up to *number 2 is the intended target).  What I have YET to figure out is what next - how do I make it actually connect/work?  Chasing answers has been frustrating because I have to switch keyboards between 2 machines everytime I need to get info - so any pointers will be appreciated!  What did I miss???

Thanks in advance.

---

### Post by bkratz on 2011-08-03
[QUOTE=freebird54;11113268

I have figured out how to get ndiswrapper going, located and successfully installed a Win2K driver for my USB wireless access, and found several networks to hook up to *number 2 is the intended target).  What I have YET to figure out is what next - how do I make it actually connect/work?  Chasing answers has been frustrating because I have to switch keyboards between 2 machines everytime I need to get info - so any pointers will be appreciated!  What did I miss???

Thanks in advance.[/QUOTE]



You have done the hard part well. Just go to the network icon (in 10.04) right click on it and finish setting up the ssid and password. You should be go to go!

---

### Post by freebird54 on 2011-08-03
I have been away too long.  I just upgraded to 10.04 from 8.04, and a few things broke along the way (like Evolution!) - but I am not familiar with a net work icon - nor can I see one on my system now.  There is a network connection device that can be put on the top panel - but if that is it it isn't apparently a solution.  It does not acknowledge the existence of wlan0, as everything else seems to.

```
freebird@eyrie:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:a2:10:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.3-0 ip=192.168.0.102 latency=0 multicast=yes
       resources: irq:29 memory:e0380000-e039ffff memory:e03a4000-e03a4fff ioport:20e0(size=32)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:02:72:8e:33:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
```

Any further ideas as to what - probably n00b - thing I have left out or not found?  suggestions as to other commands to lead me on the right trail?  As was commented, the part that was SUPPOSED to be difficult went OK - perhaps just a pointer to a (reasonably current) how-to would highlight my missing steps..

Thanks again

---

### Post by freebird54 on 2011-08-03
I think this may come down to how much got 'lost' in upgrading from 8.04 to 10.04.  I have now identified other missing items - such as System/Administration/Networking - access to my VFAT drives - access to my NTFS drives - Evolution - Opera.... to me this means either I find and rebuild a menu.lst with some of the alternatives that should be here, OR I install an ISO of 11.04 and get all the new stuff at once (then set things up - if I remember how!).

I'll be back with an answer if this effort succeeds..

Thanks!

---

### Post by bkratz on 2011-08-04
Just try right clicking on your upper panel and select add to panel and select notification area. That is probably what you are missing.

---

### Post by freebird54 on 2011-08-04
Well - you helpers certainly zeroed in on the problem - now if only that Network item had EXISTED on my system!!  The whole episode shows that while some of my thinking is OK, laziness will get you every time!

1.  Good Thought - upgrade and maybe it'll work out of the box

2.  Bad thought  - upgrades usually work, so I won't ensure everything is safely stored before I start (I run a system with / and /home on separate partitions, with other data partitions too, so it wasn't totally stupid - just lazy!)

3.  Good thought - it didn't work, nothing I could see helped, so assume (!) that it'll be an ndiswrapper case.

4,  Bad thought  - Don't need to spend an hour on research, just dive in.  Seemed to work - got it going with ndiswrapper, no conflicts, no foolishness - but also - no results!

5.  Bad thought  - maybe installing 11.04 will do the job!

6.  Good thought - specify own partitioning, and reformat all the stuff that wasn't working right off the computer.

Finally - good result - Fresh new 11.04 install with Unity, wireless working without problems (AND without ndiswrapper!) and all I have to do is customize everything again, while adding in all my 'extra' programs.  Maybe I should have STARTED there - based on the FIRST good thought...


Anyway, thanks to all who pointed out what SHOULD have worked - I couldn't tell what was missing because of 3 years in a Windows wasteland away from my own systems!  Everything looks good now - at least until I start customizing!

---

### Post by bkratz on 2011-08-04
Glad to see you finally got it working ( I think!!??).

---

### Post by freebird54 on 2011-08-05
Too wordy? :) Yes, everything is seemingly functional except my desktop (compiz) effects and Wanda the Fish.  Now I have to wander the forums and see what's worth adding, as well as rebuilding the environment I used 'til mid 2008.

Thanks for your input - it helped steer me to the real problems - and allow me to give a shout out for the developers, who have made even MORE giant strides in usability with this latest release.  Easier than Win 7 from what I can see so far,,,

Thanks

---

