---
title: "Help with scanning channels with HVR-1250"
date: 2009-11-06
forum: Mythbuntu
---

### Post by hvanzile on 2009-11-06
Hi all,

I've found a huge number of posts about the Hauppauge HVR-1250, but I don't think I've seen any about my specific problem.  I'm fairly sure that the card is being recognized.  I can set it as my capture card in mythtv-setup.  I can't, however, get it to scan channels.  I can't get the Myth GUI to do it, I can't get *scan* to work.  I added a channel manually with the information available from SchedulesDirect, and was able to get some guide data, but I've read that I need frequency information, etc.

I guess my biggest problem is that I really don't understand all the digital cable stuff.  (My former Myth box was a few years ago, all analog...)  I have a Motorola DCT700 that, when plugged directly into my TV (via coax) works just fine (additionally, I've tried the HVR-1250 in WinXP and was able to get reception just fine).  I know I'll need to figure out how to get it to change channels, get the IR blaster stuff sorted out, but for now I kind of think I need a channel list to get started. :)

My setup is as follows:
[FONT=Courier New]
[FONT=Verdana]**Motherboard**:    ASUS M3N78-EMH HDMI 
**CPU**:            AMD Athlon X2 5200 2.7 GHz 
**RAM**:            2 x 1GB Crucial Rendition DDR2-800
**Video Card**:     NVIDIA GeForce 8200 (Onboard)
**Sound Card**:     VIA VT1708B (Onboard)
**HDD1**:           Western Digital Caviar Blue 80GB SATA
**HDD2**:           Western Digital Caviar Green 1TB SATA 
**Remote**:         Microsoft MCE with USB IR Blaster
**Tuners**:         Hauppauge HVR-1250 (rev 4)
**Country**:        Canada
**TV provider**:    Shaw Cable
**TV signal type**: Not sure - I have a Motorola DCT700
**Mythbuntu**:      9.10[/FONT][/FONT]

My dmesg output says the following about it:```

[    6.718016] cx23885 driver version 0.0.2 loaded
[    6.718232] cx23885 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    6.718305] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[    6.845941] cx23885[0]: warning: unknown hauppauge model #0
[    6.845943] cx23885[0]: hauppauge eeprom: model=0
[    6.845945] cx23885_dvb_register() allocating 1 frontend(s)
[    6.845948] cx23885[0]: cx23885 based dvb card
[    7.303522] DVB: registering new adapter (cx23885[0])
[    7.303525] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    7.303804] cx23885_dev_checkrevision() New hardware revision found 0x0
[    7.303807] cx23885_dev_checkrevision() Hardware revision unknown 0x0
[    7.303814] cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfea00000
[    7.303819] cx23885 0000:04:00.0: setting latency timer to 64
[    7.303824] IRQ 18/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
```lspci -vvnn
```
04:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder [14f1:8852] (rev 04)
        Subsystem: Hauppauge computer works Inc. Device [0070:7911]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: <access denied>
        Kernel driver in use: cx23885
        Kernel modules: cx23885
```modprobe -l | grep cx23885
```
kernel/drivers/media/video/cx23885/cx23885.ko
```Thanks in advance for any help. :)

---

### Post by hvanzile on 2009-11-07
On a lark, I tried doing a fresh reinstall with 9.04 (since a lot of people seem to be reporting problems with capture cards after upgrading to 9.10), but that didn't help.  I'm still having the same problem.

I'm pretty lost here.  Can someone please help me out?

---

### Post by epi 1:10,000 on 2009-11-07
What are your scan parameters?
 

 Cable high?   QAM 256?
 

   What is The DVB-C broadcast standard in Canada? I believe your DVB-T standard is ATSC ([8VSB]("http://en.wikipedia.org/wiki/8VSB"))  like it is here in the United States so I believe the cable company would just pass the ATSC signal via QAM 250 or  [16VSB]("http://en.wikipedia.org/wiki/16VSB").

---

### Post by hvanzile on 2009-11-07
> **epi 1:10,000 said:**
> What are your scan parameters?
 

 Cable high?   QAM 256?
 

   What is The DVB-C broadcast standard in Canada? I believe your DVB-T standard is ATSC ([8VSB]("http://en.wikipedia.org/wiki/8VSB"))  like it is here in the United States so I believe the cable company would just pass the ATSC signal via QAM 250 or  [16VSB]("http://en.wikipedia.org/wiki/16VSB").

Hi - thanks for replying.  I've tried pretty much every combination I can think of.  Cable, HRC, IRC, high and full on all, at all three QAM settings.  I know Canada is ATSC, but I don't know how to find out the DVB-C standard.  I've googled around and found mentions of Shaw (my cable company) using QAM 64, but some others of them upgrading to QAM256, but I'm not sure how to verify that.

One other thing that I found very confusing - someone mentioned that once the signal comes out of the DCT700, it's no longer QAM.  I don't know what this means for scanning with my HVR-1250, though.

Have I mentioned I really don't understand digital cable? :)

---

### Post by epi 1:10,000 on 2009-11-08
How is your HVR-1250 connected? Coax via splitter, Coax routed through the cable box, audio/video cables from your cable box? 

Is your connection routed through your cable box?  Try using a line splitter and hooking one cable directly to the hvr-1250 and the other to the cable box. the most common standard in my area is Cable high QAM256.  If the channels you are trying to record are encrypted (they can only be seen on the cable box) then you need an analog capture device like the HD-PVR to control and record off your cable box.

As for the remotes the remotes that plug into my HVR-1250 are not supported in linux.  I have to have a separate MCE remote where the IR blaster plugs into a USB port.

Here is a tutorial on using the diagnostics menu on your cable box

[http://www.broadbandreports.com/forum/r20389024-Digital-Adapter-DCT700-Diagnostics-Menu](http://www.broadbandreports.com/forum/r20389024-Digital-Adapter-DCT700-Diagnostics-Menu)

---

### Post by hvanzile on 2009-11-10
Sorry for the delay&#8230; I had to take a bit of a break from the project before someone found a very reasonably price HTPC for sale on my local Craigslist. :)

Okay, I think I might be half a step closer.  I've removed the DCT700 from the picture for the time being.  (Getting MythTV to work is much higher priority than anything the cable box provides.)  My set up is now the coax coming from the wall and plugged directly into my HVR-1250.  (I did plug it in to the TV first, just to ensure I got channels.  No problems there.)

I performed a dvbscan and actually got some output, but that's about the only thing I've gotten to work.

What I did:

Used this command:```
scan -a 0 /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > channels.conf
```Got the following unfriendly and ugly output (snippet): ```
[0001]:381012500:QAM_256:0:1985:1
[0003]:381012500:QAM_256:0:2049:3
[0001]:387012500:QAM_256:0:1985:1
[0002]:387012500:QAM_256:0:2049:2
[0003]:387012500:QAM_256:0:2113:3
```I had previously read the [DVB search (http://www.mythtv.org/wiki/DVB_search)]("http://www.mythtv.org/wiki/DVB_search") page on the MythTV wiki, so I went there and followed the steps for people who get no usable names.

Running the perl script went just fine.  My channels.conf.new file now read (snippet):```
1:381012500:QAM_256:0:1985:1
2:381012500:QAM_256:0:2049:3
3:387012500:QAM_256:0:1985:1
4:387012500:QAM_256:0:2049:2
5:387012500:QAM_256:0:2113:3
```From there, I installed the scan.sh script and set it to run overnight.  It seems to have timed out at 1 AM, but it did go through 233 of the 383 listings in channels.conf.new and found absolutely nothing.  Every channel says; ```
Tue Nov 10 00:57:29 PST 2009 | 233 start scan..
Tue Nov 10 00:57:59 PST 2009 | 233 ended! 
Tue Nov 10 00:57:59 PST 2009 | 233 end scan..
Tue Nov 10 00:57:59 PST 2009 | We gots nothin!
```Additionally, the "found" directory (which is where it was supposed to put a bunch of MPGs) is empty. 

I am, again, stumped.  (FWIW, I also tried scte65scan, but that didn't provide any output at all.)

---

### Post by The Odometer on 2009-11-10
Have you tried to import your channels.conf into Myth's scanner after creating it? I did that and had to slow down the scan in the settings--and I was able to find the channels when I had a similar problem on QAM 256.

---

### Post by hvanzile on 2009-11-10
> **The Odometer said:**
> Have you tried to import your channels.conf into Myth's scanner after creating it? I did that and had to slow down the scan in the settings--and I was able to find the channels when I had a similar problem on QAM 256.

i just gave that a try and strangely, it only went from 1-40 (in a very short amount of time) and then said that no channels were found.

This seems strange because, as I mentioned above, there are 380-something lines in my channels.conf.

I tried using channels.conf.new and it did the exact same thing.

---

### Post by The Odometer on 2009-11-12
It is doing that because QAM puts multiple channels on the same frequency. (I have as many as 8 on one frequency) Go into your settings and slow the scan way down--and select the option for: Ignore signal timeout.

Also--you might want to try to view your channels.conf using mplayer. To do so, put your channels.conf into your home/.mplayer directory and then bring it up by typing:
mplayer dvb:// at the command prompt. See if you can get channels that way. If so, then its a myth issue--but can be fixed.

I'm doing all of this by memory--so I could be a bit off--but I had a similar issue and that was how I resolved it. You can change mplayer's channels using the keyboard, but I don't remember what keys to hit.

---

