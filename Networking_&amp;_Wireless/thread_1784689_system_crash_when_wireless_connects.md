---
title: "system crash when wireless connects"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by benbo on 2011-06-17
Hi I've recently installed release 11.04 and am trying to get wireless networking operational. I'm using a netgear wg111t usb wireless adapter. I've installed ndiswrapper and have got the netgear windows drivers installed ok. My problem is when I try to connect wirelessly I get a system crash, think it tends to be called a kernel panic in linux. The network connection is confirmed and about 5-10 seconds later the crash happens. I've updated the linux kernel to 2.6.39-0-generic but thats not helped.

Would be grateful for any ideas on what else to try, I can connect with a cable but that is somewhat limiting.

thanks

---

### Post by dargaud on 2011-06-17
I'm not going to be of great help when I tell you that since 11.04 one of my oldish laptop would behave very badly with 4 different wireless cards (different drivers too): crashes, random freezes, disconnections, refusal to connect after sleep, etc... After weeks of trying to diagnose the problem, purchasing a recent card solved the problem.

---

### Post by benbo on 2011-06-17
So does that mean I either need to get a new card or is it likely anolder version of ubuntu may work?

---

### Post by phz_swe on 2011-06-17
May be one of many issues, but I solved one of these problems today with my laptop: [http://ubuntuforums.org/showthread.php?p=10950523#post10950523](http://ubuntuforums.org/showthread.php?p=10950523#post10950523)

---

### Post by superduperlinuxperson on 2011-06-17
if you have any other drivers other than the one you are using, it will crash. you must blacklist it like this:
gksudo gedit etc/modprobe.d/blacklist.conf/

---

### Post by xavi787 on 2011-06-17
> **superduperlinuxperson said:**
> if you have any other drivers other than the one you are using, it will crash. you must blacklist it like this:
gksudo gedit etc/modprobe.d/blacklist.conf/

What is the difference between gksudo and sudo?

---

### Post by superduperlinuxperson on 2011-06-17
its for running gui applications in sudo/root
thanks

---

### Post by benbo on 2011-06-18
Thanks but as this is a new install I think I've only got one driver for the usb adapter, I only loaded one and can find that. Is there a command i should use to check for other drivers. Sorry if this sounds nuts but I've never tried this sort of thing before.

---

### Post by squigles1 on 2011-06-23
Im not sure if Im having the same problem. But:
 
I find that when I connect My Packard Bell Easynote, running Ubuntu 11.4 to the wireless, while on battery power it causes a system "crash."  It drops out of Ubuntu shows a screen of text behind for about 10-20seconds then loses screen imagery and shows lines across the screen.  Only solution then seems to be to power off the Note Book.  
 
I find if I have the power supply connected (ie battery charging/running off mains electricity) that the system is stable and the wireless works fine.
 
Has anyone else noticed this? Or have a solution to this?

---

### Post by squigles1 on 2011-09-14
@ Benbo,
Did you find a workable solution to your problem?
Am still suffering with mine.

---

