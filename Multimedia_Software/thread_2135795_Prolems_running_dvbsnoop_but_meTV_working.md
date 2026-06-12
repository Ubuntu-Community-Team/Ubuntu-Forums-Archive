---
title: "Prolems running dvbsnoop but meTV working"
date: 2013-04-15
forum: Multimedia Software
---

### Post by vivandjacqui on 2013-04-15
Hi DVB Guru’s
 
I am having problems interpreting the output of dvbsnoop, I will try and explain the problem I see and the processes I have followed so far.
 
I am running Ubuntu 3.5.0-27-generic #46~precise1-Ubuntu SMP
 
The machine is a Fujitsu Siemens 2.8 GHz P4 with 1Gbyte RAM and lots of disk space (SATA II)
 
The machine has a PCI Terrestrial WinTV-HVR-1100 installed.
 
I have meTV 1.3.6 installed, tuned and running on Freeview in the UK.
 
I have dvbtune installed and running I believe this is the latest version, but am not certain how to check this.
 
I have dvbsnoop 1.4.50 /api-3  installed and running but with bad output.
 
I can watch the received Freeview channels no problem so I know I have meTV and the hardware installed correctly and running, the signal is nice and clean with no pixelation apparent.
 
I can run dvbtune and I get feedback to the screen showing that it has found the card and tuned it to the desired frequency (I took the frequency from the meTV channel list).
 
When I run dvbsnoop I get what I believe to be random data, it synchs on any 0x47 byte and see I hundreds of PIDs (too many), bad flags in the header etc.  and for instance PID 0x0000 (PAT) is absolute garbage when I study the detailed format. I gathered this data using –s ts –tsraw.
 
If I try other settings with CRC checking on then I get nothing at all captured, hardly surprising if it is random data.
 
I believe that the buffers are random data not synched with the received signal in any way. I also believe that the hardware and driver are correctly installed as I can view any of the channels using meTV.
 
My only thought is that dvbsnoop is somehow mis-configured with the drivers for the card, this is probably a self induced problem as I am a beginner and probably not the fault of dvbsnoop or the card.
 
Can anyone please give me some guidance as I am very new to Ubuntu, Linux and DVB and am fast running out of ideas.
 
Thanking you in advance for any advice that can be given.
 
Best regards
vivand jacqui

---

