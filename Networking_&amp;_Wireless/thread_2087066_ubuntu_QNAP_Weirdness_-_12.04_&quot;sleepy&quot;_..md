---
title: "ubuntu QNAP Weirdness - 12.04 &quot;sleepy&quot; ..."
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by ytene on 2012-11-22
All, my [mis]adventures with my QNAP TS-459 Pro II NAS continue apace...

The latest is a good one... Starting about 6 weeks ago, I noticed that when I booted my Core i7 Quad machine with 12.04 64-bit, it would often fail to mount it's CIFS connection to my QNAP NAS. Not 100% of the time, but perhaps a little over 50% of the time. Here's some more data for you:-

1. Windows 7 64-Bit on the same harware is fine. I have Win7 for running Photoshop CS5 and X3:Reunion, but Windows seems to work just perfectly.

2. ubuntu 12.04 32-bit is fine. I run this on a Shuttle X35 Atom-based machine, and it works just peachy. 

3. Mac OS/X is also just fine. I have a latest-generation Mac Mini, and that also connects on boot, without issue.

4. I did a little investigation, and I initially noticed that if I rebooted the NAS and then re-started my machine, it would work perfectly. I refined this ever so slightly, and now find that the QNAP goes into a "sleep" mode if allowed to idle. 

For reasons I don't pretend to understand, the 64-bit version of ubuntu not only cannot "wake" the QNAP when it tries to perform a CIFS mount, that failure also prevents it from CIFS-mounting my Time Capsule [the connection string for which follows the QNAP string in my fstab file]. 

For the curious, I enclose a copy of my QNAP and time Capsule mount strings below. 

I would be really keen to know if anyone has had similar experience with the combination of 12.04 64-bit and QNAP. for what it's worth, the QNAP is currently running Firmware: 3.7.3 Build 20120801. 

Here are the fstab entries:

[FONT="Courier New"]//192.168.1.41/Public                           /media/nas      cifs    defaults,rw,username=######,password=######,file_mode=0777,dir_mode=0777

//192.168.1.40/Data                             /media/capsule  cifs    username=#####,password=######,rw,iocharset=utf8,file_mode=0777,dir_mode=0777[/FONT]

I've posted the same information on the QNAP web site, but the general consensus of opinion seems to be that if this works fine with ubuntu 12.04 32-bit and not with 64-bit; and if it works fine with Windows 7 but not ubuntu on the same hardware, there is more chance that this is a 12.04 64-bit issue, not a QNAP issue. 

I also tried upgrading to the latest QNAP Firmware, but that made no difference. 

Can anyone think of a reason why a 32-bit edition of 12.04 has the ability to "wake" a sleeping QNAP, but the 64-bit edition does not? 

I'm honestly not expecting anyone to bust a gut on this one. I have a work-around and I can live with it; it's just annoying. I'd be happy to cooperate with any triage activities that anyone might want me to experiment with. 

Any guidance or suggestions would be gratefully received. 

Thanks in advance,

C

---

