---
title: "Program Guides only flashes in Live TV"
date: 2010-09-04
forum: Mythbuntu
---

### Post by KCC-Tech on 2010-09-04
While watching Live TV, if I press M on the keyboard, the Program Guide flashes up for a millisecond and then disappears. Anyone seen this issue and know how to deal with it?

Thanks for the help.

My specs are:

Mythbuntu 10.4

Processor: AMD Athlon X2 7850 Black Edition Kuma 2.8GHz Socket AM2+ 95W Dual-Core
    with ARCTIC COOLING ACALP64 Pro 92mm CPU Cooler

Mobo: ASRock K10N78 AM2+/AM2 NVIDIA GeForce 8200 ATX

RAM: Kingston HyperX 4GB 240-Pin DDR2 SDRAM DDR2 1066

Video: ASUS ENGT240/DI/1GD3/A GeForce GT 240 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready

TV Tuner: Hauppauge WinTV-HVR-1600 ATSC/ClearQAM/NTSC

Monitor: ASUS VW266H Black 25.5" 2ms(GTG) HDMI Widescreen LCD

---

### Post by KCC-Tech on 2010-09-05
Is this an obscure problem or did I neglect to provide some of the details necessary to diagnose this issue?

Thanks

---

### Post by ian dobson on 2010-09-05
Hi,

Looks as if noone knows what the problem is. The only thing I can think of is what OSD painter are you using (OpenGL or Qt)? Which ever one your using try the other.

Also do you see any messages in the frontend log file (/var/log/mythtv).

also have a look here:- [http://www.gossamer-threads.com/lists/mythtv/commits/449719](http://www.gossamer-threads.com/lists/mythtv/commits/449719)

Regards
Ian Dobson

---

### Post by KCC-Tech on 2010-09-05
Ian:

Thanks for the response.


> **ian dobson said:**
> 
also have a look here:- [http://www.gossamer-threads.com/lists/mythtv/commits/449719](http://www.gossamer-threads.com/lists/mythtv/commits/449719)


If I understand the info in this link properly, I may have to live with this.

Your suggestion on OSD got me playing with the settings. I did find a crude work-around.  In the OSD Menu Editor I set Live TV Browse Mode. It's a two step process but at least I can get the Guide up now.

Thanks

---

