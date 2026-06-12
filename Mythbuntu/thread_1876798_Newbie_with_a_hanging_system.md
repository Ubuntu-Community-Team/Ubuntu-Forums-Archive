---
title: "Newbie with a hanging system"
date: 2011-11-06
forum: Mythbuntu
---

### Post by RideMan on 2011-11-06
Greetings! 

I recently built a beast of a system specifically to run Mythbuntu. So far it seems to be working pretty well, but not good enough to call it an appliance just yet...

From time to time, the system just seems to hang for no apparent reason, and I don't even know where to look. I'm an OS-X guy, so I'm not familiar with either Ubuntu or MythTV. I am not sure what is crashing, but when it happens, frontend is idle. The first thing I notice is the stalled clock on frontend. Then I try to log in via SSH from another computer and get no response. Likewise, MythWeb is unresponsive. A hardware reset brings the machine back up, and everything works fine. At that point, an examination of syslog, mythbackend.log, and mythfrontend.log reveal nothing out of the ordinary except for a gap in log entries between the hang and the reboot.

The system is a beast, as noted...
Asus M5A78L-M LX board, AMD Phenom II X4 840 CPU
NVIDIA based MSI N8400GS graphics card
4 Gb RAM, 1.5Tb HDD
Hauppauge WinTV HVR-2250
Built fresh from Mythbuntu 11.10 distribution and updated with update manager
(incidentally, if anyone has figured out how to get the MCE remote to work with that card...I know, it isn't supported yet.)

All four tuners work, and I have had success with simultaneous recording on different combinations of both tuners (QAM/Analog, Analog/Analog, haven't tried QAM/QAM yet). Earlier tonight I had it recording two analog shows and playing back a third without a hiccup. 

At this point, I'm looking for advice. Any suggestions as to where should I start looking to figure out what is causing these hangs would be tremendously helpful. 

Thanks!

--Dave Althoff, Jr.

---

### Post by hansdown on 2011-11-06
Welcome to the forum, RideMan.

What driver are you using, for your graphics card?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by RideMan on 2011-11-06
I'm using the NVIDIA driver.  Hmmm..Not sure how to get much more specific...it's the Ubuntu-supplied proprietary driver. 

dmesg | NVIDIA says:
nvidia: module license 'NVIDIA' taints kernel.
NVRM: loading NVIDIA UNIX x86_64 Kernel Module 280.13 Wed Jul 27 16:53:56 PDT 2011

--Dave Althoff, Jr.

---

### Post by nhtrader on 2011-11-11
> **RideMan said:**
> 
All four tuners work, and I have had success with simultaneous recording on different combinations of both tuners (QAM/Analog, Analog/Analog, haven't tried QAM/QAM yet). Earlier tonight I had it recording two analog shows and playing back a third without a hiccup. 


Very cool - 4 tuners. I'm sorry that I can't offer a solution to your problem. But I can just add that I've experienced intermittent problems such as yours b4 and tossed my hands into the air. It still happens, however infrequently.

In my case, I have one tuner but record 5 channels simultaneously. I can do this b/c my cable company multiplexes 12 stations on the same frequency and so I am recording up to 5 of them which is the maximum limit of MythTV. And naturally hiccups occur occasionally.

Now if I wanted to record 5 channels in HD using Over-The-Air channels, then I would need 5 tuners. That's for a future project.

---

### Post by RideMan on 2011-11-11
On the advice of everything I have read regarding the Hauppauge HVR-2250, I set the maximum number of streams on the digital side of the card to 1, and while I assume that it is a hybrid tuner and therefore incapable of simultaneously recording analog and digital on the same tuner (and I have set up the sources accordingly), I don't think I have seen that as a stated limit.

Anyway, as for additional information on my problem...I ran the Seagate drive test tool on the HDD, both the short test and the long test, and it passed both.  I have reduced the allowable jobs count to 1, and I have disabled all the power saving settings I can in the system BIOS.  I checked the logs at the last system hang, and found out that while the system had been simultaneously recording two programs just before the hang, and had successfully run commercial scans on both programs, later when the machine was doing *nothing*, it became unresponsive.  The clock on mythfrontend stopped at 10:37 AM, but the last backend log entry was at something like 10:17, and it was a call to run the hourly cleanup job.  That seems to have finished properly, but sometime when the machine was doing absolutely nothing, it became non-responsive.

Last night I learned that Asus had a BIOS upgrade available for my motherboard, so I applied that, and I added a user job that should export to MP4 for me. There are several recordings scheduled for tonight, so I'm watching to see if it hangs again.  Last night I was watching a recording while recording two other shows, and the machine was perfectly happy with me.  Still watching; it wil be interesting to see if the BIOS update makes a difference.

--Dave Althoff, Jr.

---

