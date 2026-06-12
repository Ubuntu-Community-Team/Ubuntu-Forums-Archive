---
title: "DELL Laptops Wireless not working after update to 9.10"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Yazwho on 2010-01-10
I recently had a problem with my Dell laptop (XPS M1330), where the wireless was no longer working after upgrading to 9.10.

My network applet was showing that the wireless was disabled, as was 'lshw -C network'.

Thank you to **Chilli555**, who found the problem. There is a bug which is causing rfkill to see the wireless as turned off via the kill switch when in fact it is not. The bug has been reported here: [http://bugzilla.kernel.org/show_bug.cgi?id=14098](http://bugzilla.kernel.org/show_bug.cgi?id=14098)

To see if you suffer the same problem as I did, try this. If your wireless springs to life then you do!

```
sudo rmmod -f dell_laptop
```To fix add 'blacklist dell_lapto' to /etc/modprobe.d/blacklist.conf

Original thread here: [http://ubuntuforums.org/showthread.php?t=1375942](http://ubuntuforums.org/showthread.php?t=1375942)

---

### Post by homeuser1 on 2010-01-10
I have the same problem with a dell laptop, but your fix isn't  working.  Here's what I got.

[HTML]dell@dell-laptop:~$ sudo rmmod -f dell_laptop
[sudo] password for dell: 
ERROR: Removing 'dell_laptop': No such file or directory
dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

---

### Post by Yazwho on 2010-01-10
Sorry to hear that. First thing make sure the kill switch is actually off!

Secondly I suggest you start a new thread with the name of the driver\wireless nic in the title, along with the output of:

```

iwconfig
lshw -C network
rfkill

```

---

### Post by dj_akasha on 2010-04-30
Worked wonders for me, thanks! Just did a clean install into Lucid Lynx and the wireless was just not working. Your fix fixed it nicely.

Cheers! :)

---

### Post by Oggoman on 2010-05-02
Just want to report that this fix works fine with my Dell XPS M1530 with Ubuntu 10.04LTS.

THANK YOU :)

---

### Post by nastelroy on 2010-07-08
thanks brooo...nice inpoh gan...

Network Manager work like charmmmmm........







-------------------------------------------------------------
dell vostro 1320
Ubuntu 10.04 Lucid
wireless bcm4312 with b43 driver
kernel 2.6.34-020634-generic

---

### Post by BigBlue802 on 2010-10-14
Fix worked for me too.  Thanks.  However, I have to enter it every time I turn the computer on now.  Any idea how to make the change permanent?

---

### Post by blue900 on 2010-10-16
thanks for the above posts:
Dell Studio 1558 this just fixed the wireless Intel Centrino N 6200 in Ubuntu 10.10 
According to dmesg the kernel Module was loaded and ready to go.

I guess the button gets in the way (it seems like the switch was turned off and in dmesg you can see its not turning it on, stays off each time its pressed)

to FIX-Add "blacklist dell_laptop" to your modprobe config (e.g. on Ubuntu
/etc/modprobe.d/blacklist.conf

found here:[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)

Nice Machine

---

### Post by lrios on 2010-10-19
Tanks fot the above post,  works on my dell ispiron 1764, i3. 

Tanks and best regard

Luis Ríos

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

