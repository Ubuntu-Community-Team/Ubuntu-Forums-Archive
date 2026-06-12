---
title: "DSL internet not connecting in new ubuntu  9.10 after upgrade!"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Raik.48 on 2009-10-30
hi
i had a ubuntu 9.04 and that was fine with the DSL internet connection. Then i upgraded to Karmic Koala and now the internet connection is not working at all. I did every step that worked in 9.04 but does not give any solution. Can anyone tell me what is wrong and how to fix it?

Thanks.

---

### Post by C++buntu on 2009-10-30
Hi, I have exactly the same problem. I've no clue yet on how to resolve this, but i'm still looking.

---

### Post by Orbegoso on 2009-10-31
I'm having that same problem and I also had it during the beta, but I thought it was a beta problem. Windows 7  VM doesn't connect either, I'm on the 9.04 live CD, right now.  Any ideas?

---

### Post by Raik.48 on 2009-10-31
hi guys
please let me know if any of you find the solution and i too am searching for the solution, if this problem persists than i have to choose other measures. 

Please do help!

---

### Post by dafdaf on 2009-10-31
Can I add a ME TOO!

---

### Post by cryptichorizon on 2009-10-31
I had the same issue, but the following works for me:

1) Click on the network icon in the top panel. This brings up a drop-down menu that looks something like this:

[B]Wired Networks
    ifupdown (ham0)[/B]
    *Disconnect*
------- Available -------
    Auto eth0
.
.
.

2) Click on "Disconnect". 
3) Click on the network icon again. The menu now looks something like:

[B]Wired Networks
[/B]     disconnected------- Available -------
     ifupdown (ham0)
     *Auto eth0*
.
.
.

4) Click on "Auto eth0" and it should now connect without a problem.

It looks like the problem returns after every reboot and I have to do the whole thing again.

Hope that helps.

---

### Post by abyzek on 2009-10-31
I am going thru the same problem.
I cannot log onto the internet from the 9.10 live cd too (could do that from 9.04 live cd).

I could not even hear the audio after the update last nite. 
Changed the entry in menu.lst in the grub folder to the latest kernel & got it back.


*It is OK if anything else is not working. You can search for the solution on the forums. Its damn boring when i cannot connect to the internet itself..:(

Please Help...Thanx!

---

### Post by trustno1. on 2009-10-31
Same problem here,
I've tried with pppoe, but doesn't work either. I'm trying to connect trough DSL, and it doesn't work... Any suggestions, I don't want to switch to 9.10 until I have fully working internet connection, cuz I need it 24/7 for both my work and university...

---

### Post by Iowan on 2009-10-31
[Another]("http://ubuntuforums.org/showthread.php?p=8204222#post8204222") one to check...

---

### Post by Onesimus on 2009-10-31
I got my DSL working with this:

[https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo]("https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo")

alternatively, you could try these:
[https://help.ubuntu.com/community/UsbAdslModem]("https://help.ubuntu.com/community/UsbAdslModem")

Hope these help

---

### Post by SunfireSSR on 2009-10-31
I have ATT Fast-Access DSL with a Netopia Modem/Router. In 9.04 it worked great. Under 9.10 it hangs for a long time before getting to any website. But when I do a speed test, transfer rates look good telling me it's a connection issue to the modem ?
Tried Automatic and Static both with no luck...

---

### Post by Raik.48 on 2009-10-31
the solutions posted couldnt solve my problem.

---

### Post by faical117 on 2009-10-31
Try with ->sudo pppoeconf

---

### Post by Raik.48 on 2009-10-31
hey guys

I just did "sudo pppoeconf" in terminal then i followed the guided instruction where i was asked to enter username, password, then automatically it connected me to the internet after reboot and is working fine without having to configure any other settings. 

This indeed worked for me. Hope that is works for you too!

Thanks for the help and support.

---

### Post by demonashes on 2009-10-31
I updated to 9.10 today. I have the same issue.. None of the resolutions here have worked for me. And its a little weird kind of issue that I'm facing. When I ping for sites on terminal, I can see a response. When I play a streaming radio on VLC, even that plays fine. But firefox won't connect to the internet nor the software update package!! Does someone face similar issue?

---

### Post by faical117 on 2009-10-31
I think that the problem is in /etc/resolv.conf 

(try this->chmod a+r /etc/resolv.conf)

if you edit /etc/resolv.conf you must find the DNS of your FAI
like this 
nameserver xx.xx.xx.xx
nameserver yy.yy.yy.yy 
you can create one /etc/resolv.conf

---

### Post by VladimirCZ on 2009-11-01
Network Manager has a bug effecting DSL connections.
It is fixed in daily builds available from PPA's at launchpad.
Also connecting via pppoeconf and pon dsl-provider works.

For more, please, read:

[http://ubuntuforums.org/showthread.php?t=1307560]("http://ubuntuforums.org/showthread.php?t=1307560")

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205")

---

### Post by su5555 on 2009-11-01
i also can not connect my dsl router. when i try to connect it, it search something and then back to auto eth0 connection.
if anybody solve this problem, then please inform me............:KS

---

### Post by vmkr on 2009-11-12
Hi Sir

In my case, no network connection is appearing and hence no options are available.

---

### Post by vmkr on 2009-11-12
> **Raik.48 said:**
> the solutions posted couldnt solve my problem.

Sir
I have suffered for the last one week with this problem.  
  	 	 	 	 	 	  However, the following two commands worked for me.

[COLOR=#000000][FONT=Courier New, monospace][SIZE=2]sudo apt-get update[/SIZE][/FONT][/COLOR]
    	 	 	 	 	 	   [COLOR=#000000][FONT=Courier New, monospace][SIZE=2]sudo apt-get upgrade[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New, monospace][SIZE=2]Now net connection is working fine
[/SIZE][/FONT][/COLOR]

---

### Post by vmkr on 2009-11-12
> **su5555 said:**
> i also can not connect my dsl router. when i try to connect it, it search something and then back to auto eth0 connection.
if anybody solve this problem, then please inform me............:KS
Sir
I have suffered for the last one week with this problem.  
  	 	 	 	 	 	  However, the following two commands worked for me.

[COLOR=#000000][FONT=Courier New, monospace][SIZE=2]sudo apt-get update[/SIZE][/FONT][/COLOR]
    	 	 	 	 	 	   [COLOR=#000000][FONT=Courier New, monospace][SIZE=2]sudo apt-get upgrade[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New, monospace][SIZE=2]Now net connection is working fine[/SIZE][/FONT][/COLOR]

---

