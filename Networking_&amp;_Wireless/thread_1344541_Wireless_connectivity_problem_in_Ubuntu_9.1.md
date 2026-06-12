---
title: "Wireless connectivity problem in Ubuntu 9.1"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Jtech13 on 2009-12-03
Hi... I have a dual boot with windows XP and ubuntu.  I had installed ubuntu (jaunty) on a separate partition.  I had absolutely no problem connecting to the wireless internet.  Then I upgraded to ubuntu 9.1.  But after this, the internet connectivity thro wi-fi gets disconnected after some time.  Then it asks for passwd and does not connect at all even on giving the password.  I like using ubuntu and prefer it over windows.  Its so frustrating to keep connecting and I finally end up with windows for net.  

I read this is a bug in the new version.  I even tried disabling IPV6 but not much of a help.  Is there a solution.. Should I reinstall the earlier version of ubuntu????

Can someone help me out... I have seen many facing this problem.. has anyone rectified this?????

---

### Post by mörgæs on 2009-12-03
Was there any particular reason for upgrading from Jaunty?

---

### Post by ingenoiusengine on 2009-12-09
I have the same exact problem, since I updated to 9.1 my wireless stops working every few minutes, though the Network manager applet shows the network to be connected. On restarting, my wireless starts working.

This works a few times but after a few times I have to restart: 
$sudo ifconfig wlan0 down

I notice that the wireless doesn't drop right away, and I still see my wireless connected. Anyway, it auto-reconnects and works. 

Is there any way to roll back to 9.0 without losing files and programs?

---

### Post by ingenoiusengine on 2009-12-09
anyone?

---

### Post by Colonel Forbin on 2009-12-09
I'm having a similar problem. In Windows 7 my connection is excellent, but in Karmic it drops out every few minutes. I'd love an answer to this. Would much rather be using Karmic.

---

### Post by linux6994 on 2009-12-10
I had wireless problems after a fresh install of 9.1 also and with many problems that you see now. I ended up going to Linux Mint8 which is Karmic based and all is well. The b43-fwcutter hardware driver was available and kicked in well. Copy out you /home/user directory and then bring it back in after the install,works great.

Good Luck.

---

### Post by soseihin on 2009-12-16
Hi!

I'm having this issue as well. I connect (automatically) just fine after login. Then the connection will intermittently drop out and ask for the security key (WEP in my case). Even after re-entering it I fail to connect. This problem only began after an update from 9.04. I just did a clean install of 9.1 (64-bit) and the problem persists.

I'm on a Gateway NV52 with an Atheros (AR928X) wireless adapter. 

I came across [this post]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1911481.html") and it looks like the bug has been reported already:
[https://bugs.launchpad.net/bugs/493342](https://bugs.launchpad.net/bugs/493342)

But launchpad isn't playing nice with me today and I can't find anything further. (-_- )

---

### Post by billybag on 2009-12-16
upgraded from linux mint 7 to linux mint 8

now the wireless internet on that laptop does not work

have no idea how to fix it and various "solutions" online have done nothing.

my girlfriend is going to be pissed.


whoops

---

### Post by kecker on 2009-12-16
Same problem after the upgrade 9.10

Was using b43-wcutter but after the upgrade to 9.10 had to go to ndiswrapper.

With that I can get it to connect for about 2 seconds and then it immediately drops it and "loses" the security key.  If I try to reenter the security key it fails.

I've been asking for answers to this problem for awhile and so far no responses.

I hate to say it but on my laptop Windows works better apparently.

---

### Post by kevjames3 on 2009-12-21
So, I am having trouble too and I am on an HP Pavilion dv3.  However, I was surfing the web and I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/493342/](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/493342/)

This sounds a lot like the issue we have all been having, so I have subscribed to that bug report, hoping that something will happen soon.  Windows is looking more enticing every day it seems.  Someone help us, please!

---

### Post by Kevinlittleton on 2009-12-23
Anyone have any fixes for this problem?

---

