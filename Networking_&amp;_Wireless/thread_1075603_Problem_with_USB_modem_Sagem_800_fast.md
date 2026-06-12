---
title: "Problem with USB modem Sagem 800 fast"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by dragoslav_zaric on 2009-02-20
Hello All,

I have problem to connect to the internet with usb modem Sagem 800 Fast. I have Ubuntu 8.10 on Lenovo laptop. 

I followed few instructions on the internet and finally I came to the point to try to connect to the internet. When I type

pon ueagle-atm

and look with plog what is going on, I get this message all the time:

-------------------------------------------------------------
Feb 20 18:30:33 ubuntu pppd[6885]: Plugin pppoatm.so loaded.
Feb 20 18:30:33 ubuntu pppd[6887]: pppd 2.4.4 started by root, uid 0
Feb 20 18:30:33 ubuntu pppd[6887]: Using interface ppp0
Feb 20 18:30:33 ubuntu pppd[6887]: Connect: ppp0 <--> 8.35
Feb 20 18:31:03 ubuntu pppd[6887]: LCP: timeout sending Config-Requests 
Feb 20 18:31:03 ubuntu pppd[6887]: Connection terminated.
Feb 20 18:31:03 ubuntu pppd[6887]: Modem hangup 
-------------------------------------------------------------

The numbers 8.35 (<VP>.<VC>) I saw from config in windows xp for this modem, where it works ok.

Maybe I should also tell this, when I installed everything and modem still didn't work, it complained during boot time that it cannot find file DSP4.bin in folder /lib/firmware/ueagle-atm
so I looked on internet and I found ueagle4-data-1.0.tar.gz file that contained file DSP4.bin .After this, it booted normally and I have just problem to connect.

Kind regards and tnx in advance

---

