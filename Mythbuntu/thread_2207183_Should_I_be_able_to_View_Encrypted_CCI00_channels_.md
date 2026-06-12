---
title: "Should I be able to View Encrypted CCI00 channels i.e. Weather Ch with ceton infiniTV"
date: 2014-02-22
forum: Mythbuntu
---

### Post by purza on 2014-02-22
I am rather new to Linux, but learning quickly
I've purchased an Ceton InfiniTV4 before thoroughly researching Linux tuner card solutions.
I have been able to build and install the drivers for the infiniTV4.  I can view TV on channels that are un-encrypted, but I can't view channels that are encrypted (i.e. Weather Channel, etc), but are flagged view copy freely or 00 ([COLOR=#000000][FONT=sans-serif]CCI 0x00)[/FONT][/COLOR].
I've been through the setup from these webpages and can't get any further.
[http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)
[http://www.bsmdevelopment.com/Reference/Sections/InstallNotes-MythTV_section-1.15.html](http://www.bsmdevelopment.com/Reference/Sections/InstallNotes-MythTV_section-1.15.html)
Can someone tell me if this is a Comcast card setup issue (i.e. card activation issue) or a ceton infiniTV4 issue?  My neighbor has a Silicon Dust ethernet card tuner running with a Comcast card and has now issues viewing encrypted channels.

Thanks in advance.

Hardware/ Software list as accurate as I can get it.
MB:    ASUS A88X-PRO Socket FM2+ ATX AMD Motherboard
CPU:      A6 6400K Black Edition 3.9GHz Dual-Core Socket FM2     Boxed     
Processor
RAM:     8GB, Kingston 240-pin DIMM, DDR3 PC3-12800 memory          module 
KHX1600C9D3K2/8GX
CASE:     SILVERSTONE Black Aluminum / Steel Grandia Series SST-          GD07B 
ATX Media Center
KYBRD:  Logitech K400 WRLS
PWRSUP: CORSAIR 600W CXMOD 80+BRZ ATX PSU
HD:     BOOT DISK: SanDisk SDSSDX-120G-G25
    HARDDISK 1:  1 TB WD Green WD20EZRX
    HARDDISK 2:  1 TB WD Green WD20EZRX
TUNER:  Ceton InfiniTV 4 PCIe - 4-channel Internal Cable              TV Tuner 
Card for CableCARD
TVProv:    Comcast/ Xfinity
Region:    Philadelphia
Country:USA
Remote: None
CD:      Pioneer BDR-208DBK 15x Internal Blu-ray             Burner
ACCY:     Sabrent 7 slot 75 in 1 Int Card Reader
LINUX: Installed XBUNTU
KERNEL: Linux version 3.2.0-58-generic (buildd@allspice) (gcc         version 
4.6.3 
    (Ubuntu/Linaro 4.6.3-1ubuntu5)     ) #88-Ubuntu SMP Tue         
Dec 3 17:37:58 UTC 2013
DISTRO:    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 12.04.4 LTS
    Release:        12.04
    Codename:       precise
Mythbuntu/ MythTV: apt-cache policy mythtv
mythtv:
  Installed: (none)
  Candidate: 2:0.27.0+fixes.20140219.ab18cb1-0ubuntu0mythbuntu2
  Version table:
     2:0.27.0+fixes.20140219.ab18cb1-0ubuntu0mythbuntu2 0
        500 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/) precise/main amd64 
Packages
     2:0.25.2+fixes.20120802.46cab93-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse 
amd64 Packages
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages

---

### Post by purza on 2014-03-06
I solved this with some help from Ceton [FONT=arial]linux@cetoncorp.com  .  Comcast Philadelphia screwed up the cable card first time around and picked up a new one which they were able to set up correctly.
I posted some instructions under troubleshooting on the wiki guide [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)[/FONT]

---

