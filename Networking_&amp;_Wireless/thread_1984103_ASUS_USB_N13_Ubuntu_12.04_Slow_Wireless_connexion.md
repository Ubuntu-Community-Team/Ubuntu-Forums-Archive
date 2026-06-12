---
title: "ASUS USB N13 Ubuntu 12.04 Slow Wireless connexion"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by add1kt on 2012-05-21
I just installed Ubuntu 12.04.
Using the default modules rt2800usb,rt2x00lib...
I can't get any internet speed above 50KB/s. 
The chipset is RT3072
Previously I have been able to compile the ralink drivers from source, but now I run into some errors that I can't seem to work around. I can post the output if needed....but I had to switch to my Debian box to type this because the Ubuntu internet is painfully slow. 

I tried disabling ipv6 within Ubuntu and in firefox, that seemed to help a little, because initially I had pretty much no internet.

The old module that was compiled prior to linux 3.X was called rt2870sta worked great.  I understand that isn't used anymore, but this new crap doesn't work well at all. I hope I am just missing something easy.  I am a pretty big fan of the Ubuntu movement, 12.04 was a leap for Ubuntu and I think it looks and feels great.

I used to say I would use Ubuntu more but there always seemed to be one thing that held me back, a glitchy kernel module, random crashes, a program I just couldn't get to work.  At 10.10 I was 100% ubuntu, now I found myself back to my stable Debian box, saying Ubuntu is almost there, again!

Anyway sorry for the rant, and thanks in advance for any help.

---

### Post by add1kt on 2012-05-22
I apologize, as I thought this was an Ubuntu specific problem, it is most certainly a Linux kernel problem.  The new modules suck the big one for rt2870 and rt3070 support.

This link did the trick for compiling official ralink drivers from source:
> [http://en.gentoo-wiki.com/wiki/Ralink_RT2870](http://en.gentoo-wiki.com/wiki/Ralink_RT2870)
Go straight to the Troubleshooting section.

I did this with the DPO_RT3070_LinuxSTA_V2.3.0.2_20100422 driver available from ralink.  So if anyone tries this with the ASUS USB N13 and driver V2.3.0.2, follow all the steps in the link that apply except when it says go to line 1077 substitute 1014; for 1078 sub 1015.

---

