---
title: "Networking disabled, HP DV7-1025nr 10.4 Lucid Lynx"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by Dan Lyke on 2010-05-23
My wife has an HP Pavilion DV7-1025nr laptop. She recently upgraded to 10.4 Lucid Lynx, and decided to see if Hibernate worked yet (I know: aiiigh!). When the machine didn't come back she rebooted, and now networking doesn't work.

At first I thought it was just a wireless issue, when I click on the network icon in the upper right hand corner I see "Networking Disabled", but I can't even bring up a GUI interface to get the wired hardware working.

I was able to bring up the wired interface manually using ```
sudo dhclient eth0
```, but I can't find the magic incantations to bring up the wireless one, ```
sudo iwconfig wlan0 essid Flutterby1 key
``` gives me:

> wlan0     IEEE 802.11abgn  ESSID:"Flutterby1"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0D92-D7D4-EB33-CA37-EFC3-905B-61
          Power Management:off


I can't figure out the formatting to do those nice scrollbarred embedded listings, so "lspci -v" is attached as "lspci.txt", "lsmod" is attached as "lsmod.txt", uname -a:

```
Linux charlene-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

I've tried rebooting into Vista and turning on the network then rebooting back into Ubuntu, but no joy.

Thanks.

Dan

---

### Post by wolfhouse on 2010-05-23
Hello, 

I am having the exact same issue on a Macbook Pro.  I had to restart from a failed sleep session, and no networking available...

---

### Post by Dan Lyke on 2010-05-23
So currently I have two potential avenues:

1. The PRO/Wireless 5100 AGN chip uses the firmware-iwlwifi firmware package on Debian, I'm still looking for this on Ubuntu.

2. Weirdly, when I plug the machine in I still have to manually use "dhclient eth0" because I can't find the interface in the network manager GUI. Further, Firefox starts up in offline mode, and that has to be manually unchecked. So whatever Firefox is polling to see about network configuration is screwed up.

Suggestions gratefully received.

---

### Post by Dan Lyke on 2010-05-23
Aaaargh!

Okay: *Right*-click on the little networking icon. Make sure that networking is enabled.

Ya know, I remember back in the days when we had APM for suspend/resume, and had to type in "dhclient" manually, and, yeah, we had to know all that crap, but dang it, it just freakin' worked.

Grrr.

---

### Post by Iowan on 2010-05-24
Sometimes it's the simple things...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ? :)

---

### Post by Dan Lyke on 2010-05-24
thank you, that was the link to the button I was looking for. Yes: Solved.

---

### Post by naomiyaki on 2010-05-25
> **Dan Lyke said:**
> Aaaargh!

Okay: *Right*-click on the little networking icon. Make sure that networking is enabled.

Ya know, I remember back in the days when we had APM for suspend/resume, and had to type in "dhclient" manually, and, yeah, we had to know all that crap, but dang it, it just freakin' worked.

Grrr.

It's true! I had the same problem on my MacBook Pro after a recent package update and couldn't figure out how to fix it -- all I had to do was right-click! .: facepalm #-o:.

---

### Post by gordontytler on 2010-05-29
Thanks. This saved me a lot of time. My problem also occurred after hibernate.

The icons in the top right all do different things when you right click. I would never have guessed. Unfortunately, if you are disconnected, and you don't know this, the network icon does nothing when you left click. If would be good if the reconnect option was on the left click. Oh well, now I know.

---

### Post by DavorC on 2010-05-31
Does anyone know how to solve this without the Gnome GUI? (I'm running KUbuntu, but a command line solution would be fine, too.)

---

### Post by nalcomis on 2010-06-02
> **naomiyaki said:**
> It's true! I had the same problem on my MacBook Pro after a recent package update and couldn't figure out how to fix it -- all I had to do was right-click! .: facepalm #-o:.

Thank you very much for this post.  Solved my problem.  I feel like an idiot, but it solved my problem :)

I wonder why the software update disabled networking?

---

### Post by zahanm on 2010-08-19
Oh man, wow.
I was expecting to spend hours fixing this. If anyone has access to it, 'right click on networking icon' really should be a part of the [Ubuntu wired network troubleshooting guide]("https://help.ubuntu.com/9.10/internet/C/troubleshooting-lan.html").

---

### Post by ponzoj on 2012-07-09
service network-manager stop

rm /var/lib/NetworkManager/NetworkManager.state

service network-manager start

That worked for me

---

### Post by wildmanne39 on 2012-07-09
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

