---
title: "ZTE MF668A Mobile Broadband?"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by jrk36 on 2012-01-02
I have a problem getting mobile broadband service to start on this device.
There is heaps of help on this forum on this matter but it all appears very techo' and doesn't make sense to me :(
I'm TOTALLY new to Ubuntu after so, so, long on Windows (upon which I'm reasonably proficient).

I have an unlocked (originally Telstra) ZTE MF668A that currently has an Amaysim SIM card in it which is on the optus network. This USB was unlocked on a Windows 7 laptop and works just fine on that.
When I plug it in to this Ubuntu 10.04 laptop the system detects it - i.e. it shows up in Computer file browser as "ZTE MMC Storage", but I cannot open it from there. 
I have set it up correctly in Network Connections under Mobile Broadband (i.e. correct network and APN).

Now, how do I start the service?

Thanks and regards,
John Kennedy

---

### Post by Brizvegan on 2012-01-05
Hi,

I have the Telstra ZTE MF668 (without the "A") working in Linux Mint 9 and 10 (based on Ubuntu 10.04 Lucid and 10.10 Meerkat).

The 668 works "out of the box" in LM10 using Network Manager, but in LM9 I had to download and install sakis3g to get it to work consistently - [http://www.sakis3g.org](http://www.sakis3g.org)

You can read about the same problem here - maybe some tips to help (see post #7 for what I did to get it working):
[http://forums.linuxmint.com/viewtopic.php?f=53&t=89232&sid=4e03921210f0afdfff163cea6c921db4](http://forums.linuxmint.com/viewtopic.php?f=53&t=89232&sid=4e03921210f0afdfff163cea6c921db4)

Maybe if you first try starting with the dongle plugged in at boot, then, wait a few minutes - be patient - for things to settle before you:

Right-click the Network Manager icon in notification tray
If "Enable Mobile Broadband" option is there , left-click it
Then left-click Network Manager icon,
click on the account you have already set up
Hopefully .... it connects.

Brizvegan

---

### Post by jrk36 on 2012-01-05
... tried all that without success.
Upgrade to Ubuntu 11.10, but the problem still exists (and is well documented in this forum).
Found a manual work around on the forum and that was successful at enabling mobile broadband. Whilst this will do for now, it does involve putting two lines of code into  "Terminal" every time I boot, which is not really a solution.
Is there a permanent patch/fix and if so how is it downloaded and installed?
Thanks,
John Kennedy

---

### Post by Brizvegan on 2012-01-05
So , you were able to get an internet connection in Network Manager with the workaround?
If so, great - progress!

As you have seen by the many threads about usb mobile broadband dongles on the forums, they can be a "hit and miss" thing in linux.  Different hardware configurations/dongles/software versions can have a bearing on connection success.

I'm still very much a newbie, so can't help you with a permanent fix - hope someone with more expertise will help out.

All I can say FWIW is that sakis3g has worked for me.  It takes less than a minute to connect in LM9 and has been rock solid.  I don't mind not being able to use NM.  With the amount of time reading/experimenting I put in with this issue, I'm happy to have a reliable connection.

Brizvegan

---

### Post by alexfish on 2012-01-05
hi jrk36

can have a look through

 [How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 


Check out post #2 with a regards to ZTE devices , and the rules (some devices only need the eject command)

Check post #1 with regards to Storage Delay

also check out post #61  , there is a script worth trying if the device is failing to switch

it will output the udev rule , + other info , read how to use carefully

alexfish

---

