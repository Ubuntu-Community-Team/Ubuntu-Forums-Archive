---
title: "Audio stopped working after upgrade to 7.04"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by vishalsethia on 2007-04-21
I installed Fiesty Fawn and my sound card seemed to be working. But for some reason it didn;t detect my Wireless card. But once I played around installing a few things for my wireless, my wireless card was installed but now sound is not working.
To list a few details

 Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


It seems that the sound card is detected, but doesn't work for some reason. On booting with a live CD, the sound works but wireless doesn't. I installed Wireless using ndiswrapper with bcmwl5.inf driver. 

Any tips would be greatly appreciated. 

Thanks
-V

---

### Post by James Paige on 2007-04-25
I had a similar problem. After upgrading from edgy to feisty, sound appeared to work fine, but after the first reboot, it stopped working, and nothing I can do will get it back. I am using a Thinkpad which also has an intel ICH6 sound chip.

I never had any wireless problems.

---

### Post by viz_e on 2007-04-26
> **James Paige said:**
> I had a similar problem. After upgrading from edgy to feisty, sound appeared to work fine, but after the first reboot, it stopped working, and nothing I can do will get it back. I am using a Thinkpad which also has an intel ICH6 sound chip.


Very same here. Ideas?

---

### Post by James Paige on 2007-04-26
I worked around the problem by booting with the old kernel 2.6.17 that came with edgy instead of the 2.6.20 kernel that came with feisty. Sound works fine with the older kernel.

The only disadvantage I can see so far of running the older kernel is that "Roaming" mode for my wireless is now broken, so I have to configure wireless manually (I'm not sure if that was the same problem vishalsethia was having or not)

---

### Post by rrwo on 2007-04-26
Check [http://ubuntuforums.org/showthread.php?t=424354](http://ubuntuforums.org/showthread.php?t=424354)

---

### Post by James Paige on 2007-04-26
> **rrwo said:**
> Check [http://ubuntuforums.org/showthread.php?t=424354](http://ubuntuforums.org/showthread.php?t=424354)

No, that thread does not describe my problem. If I boot using kernel 2.6.20, sound does not work, no matter whether I cold boot, warm boot, or resume-from-hybernate

---

### Post by samuliri on 2007-04-27
check this:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by James Paige on 2007-04-27
> **samuliri said:**
> check this:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

Nope. That has no effect on my problem either.

(Incidentaly, vishalsethia, I sincerely apologize for hijacking your thread. I hope some of this is useful/relevant to your problem)

I realized that after a cold boot with kernel 2.6.20, my sound DOES in fact come back. I could swear I tried that at least twice earlier this week and it didn't work, but now it does.

That lead me to [http://ubuntuforums.org/showthread.php?t=418082](http://ubuntuforums.org/showthread.php?t=418082) which lead me to something fascinating. After my sound fails, it returns for a fraction of a second if I disconnect or reconnect my laptop's power supply.

That lead me to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98605](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98605) which gave me the idea to try suspending... and after resuming from a suspend, my sound returns. For my own purposes, suspending/resuming is a much better workaround for this problem that shutting down and cold booting.

---

### Post by mority on 2007-04-30
James Paige, I have exactly the same problem on my Thinkpad T30 after upgrading from 6.10 to 7.04.

Sound works after cold start, after reboot or hibernating it stops working, and after suspending it does work again. Pretty strange.

I would be very thankful for a proper solution to this bug if you know any.

---

### Post by maicua on 2007-04-30
similar problem with my presario 2825ea, 
sound works at starting, after reboot 
but stops working after suspending ... :|

---

### Post by neilrizo on 2007-05-02
> **mority said:**
> James Paige, I have exactly the same problem on my Thinkpad T30 after upgrading from 6.10 to 7.04.

Sound works after cold start, after reboot or hibernating it stops working, and after suspending it does work again. Pretty strange.

I would be very thankful for a proper solution to this bug if you know any.


you're right! my audio stopped working after hibernation. i suspended my system just now and after reviving it the audio was back.

what gives?

---

### Post by scarabaeus on 2007-05-04
I had a similar problem on my T43 (either no sound at all, or loosing sound after hibernate...) 
I solved the problem by installing an unpatched kernel:

the bug report
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

the kernel:
[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/)

hope that helps

cheers

---

### Post by viz_e on 2007-05-04
After the sound problem, I have noticed that either the Master Volume was muted, or the Head Jack. Sense (if I remember right) was *not* muted. By correcting one of these issues, the sound was back again.

---

