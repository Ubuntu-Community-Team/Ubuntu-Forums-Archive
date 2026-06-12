---
title: "Netgear N300 WNA3100"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by Silverflyer on 2013-03-21
Please someone help me out here.

The adapter is a Netgear N300 WNA3100

It will be much appreciated.

---

### Post by mörgæs on 2013-03-22
[http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989)

---

### Post by Silverflyer on 2013-03-22
ok, so I made this much easier on myself and have acquired a wired connection to use to get the wifi working.  I am on plain 12.04 Ubuntu, which now has NDIS Wrapper downloaded and is fully up to date.

---

### Post by Silverflyer on 2013-03-22
Ok, so...  I have downloaded NDISwrapper and installed it via software center.    

Then I followed the link above:  [http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989)   

and downloaded the drivers here:  [http://ubuntuforums.org/showthread.php?t=1965989&p=11879280#post11879280](http://ubuntuforums.org/showthread.php?t=1965989&p=11879280#post11879280)   

When I open NDISwrapper to install them I get this message:  FATAL: Module ndiswrapper not found.    

What is it I need to do?

---

### Post by Silverflyer on 2013-03-23
Did some googling regarding my problem and if someone could help me understand how to install the items listed here:  [http://ubuntuforums.org/showthread.php?t=1987695](http://ubuntuforums.org/showthread.php?t=1987695)  that would be great, thank you.

---

### Post by Silverflyer on 2013-03-23
you know, I am a linux noob.  I have followed every link given, googled for others, made some progress and am now against a brick wall and would really appreciate help as simple as being shown how to install what is claimed to fix my problem instead of just assuming everyone knows how as the poster of that info did...

---

### Post by mörgæs on 2013-03-24
You could also post in the thread mentioned above. A lot of knowledgeable people are gathered there.

If you do, please be very specific about your problem, your attempts at solving and their results. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Silverflyer on 2013-03-24
I followed every bit of advice I can find on this forum regarding my problem and none have worked, including the 3 "solutions" in the sticky at the top of the forum.

---

### Post by Silverflyer on 2013-03-24
Here is the output of LSUSB


```
Bus 001 Device 007: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 004: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 002 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 002 Device 003: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971/KU-0325 Keyboard
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by Silverflyer on 2013-03-24
My chip, the 43231, is not listed here:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

It says to use ndiswrapper.  Now, I am back to the fatal error...  If someone could help me fix that, that would be great.

---

### Post by Silverflyer on 2013-03-24
I just did this which is supposed to work, and again have the ndiswrapper fatral error.  [http://ubuntuforums.org/showthread.php?t=1835175](http://ubuntuforums.org/showthread.php?t=1835175)

---

### Post by Silverflyer on 2013-03-24
I tried  suggestion #2 just now, still got the ndiswrapper fatal error message...  [http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)

```
jason@jason-desktop:~$ cd /usr/src
jason@jason-desktop:/usr/src$ sudo tar -xjf ndiswrapper.tar.bz2
[sudo] password for jason: 
jason@jason-desktop:/usr/src$ cd /usr/src/modules/ndiswrapper
jason@jason-desktop:/usr/src/modules/ndiswrapper$ sudo make
make -C /usr/src/linux-headers-3.5.0-26-generic M=/usr/src/modules/ndiswrapper
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /usr/src/modules/ndiswrapper/ndis.o
/usr/src/modules/ndiswrapper/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
/usr/src/modules/ndiswrapper/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/modules/ndiswrapper/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/modules/ndiswrapper/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
make[2]: *** [/usr/src/modules/ndiswrapper/ndis.o] Error 1
make[1]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make: *** [modules] Error 2
jason@jason-desktop:/usr/src/modules/ndiswrapper$ sudo make install
make modules
make[1]: Entering directory `/usr/src/modules/ndiswrapper'
make -C /usr/src/linux-headers-3.5.0-26-generic M=/usr/src/modules/ndiswrapper
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /usr/src/modules/ndiswrapper/ndis.o
/usr/src/modules/ndiswrapper/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
/usr/src/modules/ndiswrapper/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/modules/ndiswrapper/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/usr/src/modules/ndiswrapper/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
make[3]: *** [/usr/src/modules/ndiswrapper/ndis.o] Error 1
make[2]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ndiswrapper'
make: *** [ndiswrapper.ko] Error 2
jason@jason-desktop:/usr/src/modules/ndiswrapper$ sudo modprobe ndiswrapper
**FATAL: Module ndiswrapper not found.**


```

---

### Post by mörgæs on 2013-03-24
Please stop the repeated postings. 

Again, my advice is that you post *once* in the thread I mentioned in #2, giving a complete description of the steps you have tried and their result.

---

### Post by Silverflyer on 2013-03-24
> **mörgæs said:**
> Please stop the repeated postings. 

Again, my advice is that you post *once* in the thread I mentioned in #2, giving a complete description of the steps you have tried and their result.

Have you even read any of what I wrote or just the WNA3100 part?

The solution to this problem is simple.  Stick with a mac.  Linux is free because no one in their right mind would pay for it...

[URL="http://ubuntuforums.org/showthread.php?t=1965989&page=13&p=12572305#post12572305"]http://ubuntuforums.org/showthread.php?t=1965989&page=13&p=12572305#post12572305
[/URL]

---

### Post by Silverflyer on 2013-03-24
ok, I took a deep breath and a walk, and then got it working by compiling ndis 1.58 versus the 1.57 in the software center.

---

### Post by mörgæs on 2013-03-24
Marking the thread 'solved'.

In case anyone is following: Ndiswrapper 1.58 is default in Buntu 13.04, which should make future installations easier.

---

