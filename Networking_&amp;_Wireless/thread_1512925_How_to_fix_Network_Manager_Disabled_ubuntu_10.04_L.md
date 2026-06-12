---
title: "How to fix Network Manager Disabled ubuntu 10.04 Lucid"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by Bobbybudz on 2010-06-18
This one was really giving me a hard time but I finally have an answer for you all. 

If your network manager is not working, and says unmanaged, or Networking disabled, open your terminal and enter:

sudo rm /var/lib/NetworkManager/NetworkManager.state

Then reboot your system. 

Good luck.

---

### Post by Iowan on 2010-06-18
There are a couple of [threads]("http://ubuntuforums.org/showthread.php?t=1505217") that mention:>  service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start
**sudo** won't hurt... :)

---

### Post by LeslieL on 2010-06-23
Thanks for that. I knew there had to be some command-line fix for it. Can't figure out why it happens sometimes when I open up my laptop and at other times the network re-connects smoothly.

---

### Post by dkintheuk on 2010-06-26
So this fix works lovely but...

Why does the network manager get stuck in a state like this?

Is it a bug?

Cheers for posting this... saved me from throwing my pc out the window.

---

### Post by carusoswi on 2010-06-26
> **dkintheuk said:**
> So this fix works lovely but...

Why does the network manager get stuck in a state like this?

Is it a bug?

Cheers for posting this... saved me from throwing my pc out the window.

Of which state are we speaking?  I installed 10.04 Studio, and have had nothing but problems with my wireless connection since (and it worked fine in 9.10 Studio).  First, of course, I had to discover that network manager isn't automatically installed in Studio.  Ok, reasoning seems sound, installed, fine.

Now, when I reboot, more times than not, there is no attempt by Ubuntu to connect to my router.  I have to go into the 'windows wireless drivers' area and reconfigure - basically re-enter my WEP key in order for Ubuntu to initialize my wireless adapter.

Even more annoying, and I don't know if this is Ubuntu or what, but while browsing, the entire computer locks up.  No mouse, no keyboard, and no solution except to reboot.  This is truly annoying.  I have tried Opera and Firefox, suspect that other browsers would begave similarly.  I can boot into windows xp and no problems browsing there, so the problem is definitely confined to the Ubuntu side of my system.

Is this the sort of problem addressed by this thread or should I post elsewhere?

Thanks.

Caruso

---

### Post by ginsong on 2010-06-26
Just had this problem; thanks for the fix, guys.

---

### Post by LeslieL on 2010-06-28
Tried this fix but it didn't work - I had to reboot. 

Seems like I had this problem in 9.04 as well, but it fixed itself through some update or other. Hope it happens again!

---

### Post by macoto on 2010-08-02
I had same problem. Thank you for this info.

I think this is an initialization bug of Network Manager.
Hope to fix this!

---

### Post by Iowan on 2010-08-02
Although not to the "necromantic" stage, this thread is getting a bit old. If you have problems, start a new thread, and link to this one. :)

---

### Post by Phezz on 2010-09-30
Thanks - this thread is VERY useful as google knows about it.

---

### Post by mnharrisburg on 2010-11-07
Thanks for keeping this post up since it comes up nicely in a Google search! :KS 

Got access to the internet up and running after running the command 'sudo rm/var/lib/NetworkManager/NetworkManager.state' in terminal and re-booted However, I no longer get them same nice message in the 'tray' that verifies the network is running at 100M like I used to (simply says 'unavailable' under the grayed icon for networks).

Following some previous threads earlier, I went into hardware system settings (Network Manager Backend), and moved 'Wicd' up in front of 'NetworkManager 0.7' since there was some discussion about being this being better. Trying to run the application 'KNetworkManager' doesn't open up any window, either before or after the move with Wicd.

Anyone have any knowledge of a thread that addresses this particular issue? That tray verification message is a nice 'warm and fuzzy' that everything is working right.

---

### Post by nicklcarey on 2011-01-16
I had several problems in 10.04 on  my toshiba laptop.  I've tried several fixes over the past 2 weeks and  no resolution.  Tonight, I upgraded to 10.10.  Issues are gone. Some  pages take 1 second longer to load than other pages but most/all pages  seem to load in under 2 seconds. Takes an 1 hour and a half to upgrade  but so far its been worth it. I also suggest backing up before/after  upgrade.  To upgrade to 10.10 go to System>Administration>Update  manager.  Click on upgrade to 10.10.  I'm not sure why/what fixed the  problem but it did. 
  I also had a problem with 10.04 network disabled on boot.  It resolved this issue as well. Hope this helps someone....:D

---

### Post by pramod_mb on 2011-12-06
saved me from a lot of trouble.

---

### Post by 2burke on 2012-01-22
Hi,
Was allways getting Network manager disabled and really do not know what it means so had a hunt to find out what is all about. Came across this fix on the first search..
Have ubuntu 10.10 Maverick and Network Manager now fixed.
Many Thanks
2burke

---

