---
title: "Windows 7 coexistence issue"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by andyparker55 on 2010-01-31
Searched high and low through various forums for a match on this issue without success.  Leads me to think that it's something simple so please help me out!

I run Ubuntu 9.10 on my laptop and connect to the internet via a wireless connection to a D-Link DSL 2640R router.  Works like a dream - absolutely no problems at all.  Where it all starts to go wrong is when my partner starts up her laptop running Windows 7 and starts to browse the internet herself.  Even though my wireless network connection is still showing as active, I cannot connect to any internet sites.

It gets even weirder - if I then left click on my wireless icon and reselect my wireless network, the connection disconnects and then reconnects as I would expect.  The internet then springs to life and I can reload pages successfully but only for 5-10 seconds.  I then lose the connectivity again.  I can repeat this over and over again.

As soon as my partner shuts down her laptop, full service is resumed and the problem goes away.

So is her Windows 7 machine causing the router to do something strange that Ubuntu doesn't like?

thanks in advance.

---

### Post by quixote on 2010-02-02
Erm... is the solution to tell your partner to stop using such a rude OS that interrupts everyone else? :D

More seriously, I haven't heard of this problem before, so Win7 machines don't have to do that, which implies it's a Win7 setting on her machine and not something the ubuntu setup could do anything about.  All I can suggest is to carefully go through the win7 settings, especially looking for anything that retries or re-broadcasts every few seconds.

---

### Post by dmizer on 2010-02-02
This is most probably a router problem. Your router is probably handing the same IP address to both your partner's laptop and to yours. To check your IP address, look for "inet addr" in the output of this command (ignore the "lo" section):
```
ifconfig
```
You could probably solve this problem by rebooting the router, or checking the router settings to make sure that you have more than one DHCP address leased.

---

### Post by andyparker55 on 2010-03-13
Thanks for the responses.

I posted the problem on the TalkTalk forum and got exactly the same responses so was quite hopeful that I could fix it.  Unfortunately not.  I've configured the router to give my machine a static IP and the problem persists.

Looking through daemon.log I see the following (see attachment).  All ok until Michelle boots up win 7 at 16:34.  Can anyone diagnose what goes wrong from there? 

tia
Andy

---

### Post by dmizer on 2010-03-13
Something is misconfigured in your router. This is a router problem, not an operaiting system problem.

Double check the IP address on Michelle's computer. Make sure it's not 192.168.1.10.

Double check the DHCP lease settings in the router, and make sure you have the DHCP range set to allow more than one computer.

Double check the MAC address settings on the Win7 machine, and make sure it's not the same as the MAC address on your Ubuntu computer.

---

### Post by ajgreeny on 2010-03-21
Also check the MTU size in your router setup dialog, if that's possible in that router.  TalkTalk say it should be 1432, I think, but their site will confirm this.

Yes, I've just checked this.  It should be 1432.

How is the connection and support from TalkTalk, as I'm considering moving to them from my current more expensive ISP?

---

