---
title: "Cannot Scan for Digital Channel using HVR-1600"
date: 2010-10-21
forum: Mythbuntu
---

### Post by prof3205 on 2010-10-21
I know this has been asked before, but I've tried most of everything I have read and still am having the following problem.

Using an HVR-1600 card, Mythbuntu 10.04 (but I've tried every version since 9.04) and an OTA digital cable antenna (which works on when connected directly to a LCD TV).

The installation seems to detect the hardware by setting it to ITV MPEG2, and then manually entering in /dev/video0.

I have a Schedule's Direct account with the other the air stations set for the Orange County area (where I live).

When I scan for channels, no channels are scanned.  I'm using US-Broadcast as the frequencies (should I have used US-Cable??)

This is making me nuts!!!

Any suggestions?

Thanks in advance

---

### Post by klc5555 on 2010-10-21
Gosh I'm starting to hate these cards, or at least Hauppauge's failure to support them on Linux.

At any rate, IVTV, MPEG-2 encoding and /dev/video0 refer to the setup for the analog tuner (which has it's own port separate from the digital one in the back of the card).

The digital tuner should be detected generally as a Samsung something-or-other (I'm not at my machines at the moment) and will set up its device node under .../DVB/ The Mythtv backend card setup will generally detect this tuner as DVB0 (unless it's the second or subsequent digital tuner) 

The 1600's digital tuner, which is reported to work flawlessly on Windows, is all kinds of quirky on Linux with the cx18 driver. Most of this quirkiness settles around the the high signal strength requirements for this tuner on Linux with the Linux cx18 driver. You may (or may not) need to compile and install the current daily snapshot of the dvb drivers from linuxtv.org, since certain driver patches were merged with the kernel tree along about 2.6.33.x. You probably will need to use a good line-drop amp (Motorola or equivalent) on the cable input to the card to overcome it's Linux digital deafness. And you may or may not be able to get the card to scan for signals properly in the backend setup in certain versions of mythtv, which may then necessitate setting up and loading a channels.conf file using a utility like dvbscan (or w_scan)

For my own part, I find other cards like the pchdtv-hd-5500 (and even the new AverMedia A180) much less of a pain in the tookis for digital than the 1600. Particularly the 5500, which works essentially out-of-the-box on just about all contemporary Linux systems.

Myth's wiki on the 1600 is available at:  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)  

The mythtv page for dvbscan is here: [http://www.mythtv.org/wiki/Dvbscan](http://www.mythtv.org/wiki/Dvbscan) while linuxtv's more informative one is here: [http://www.linuxtv.org/wiki/index.php/Dvbscan](http://www.linuxtv.org/wiki/index.php/Dvbscan)

Good luck.

---

### Post by prof3205 on 2010-10-21
Thanks for the info.  I'll give it a try and report back.

---

### Post by majorw00dy on 2010-11-03
Take a look at this post, hopefully it help you out..

[http://ubuntuforums.org/showthread.php?t=1572837]("http://ubuntuforums.org/showthread.php?t=1572837")

---

### Post by stratoscape on 2010-11-03
OK, I just stumbled across this post after posting my own request. and klc5555 is right, in the backend setup , capture cards I set mine up DVB DTV capture cards (v3.x) and one appears as 

/dev/dvb/adapter0/frontend0
/dev/dvb/adapter1/frontend1

hear is what the cx18 info looks like -> cx18_info
[http://pastebin.com/Cy5UuBZ4](http://pastebin.com/Cy5UuBZ4) strangeness was I could only scan when plugged into digital port, but never got a picture, well once, for few seconds but when I plugged the cable into it I got nothing. then I remember something I read in a thread about this on ATI HDTV Wonder cards, rescan

Frq Table: Cable-High
Modulation: Cable (QAM-256)
Scanning range (I left alone, qam-256 channel 78 -> qam-256 channel 159, 77

as I told most the qam-256 unencrypted in in this range also see whats avail in your area here [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

I also wish we had bought pcHD-5500 cards cause I have heard nothing but positive stuff about them as well as the HDHomerun devices

these 1600 are the pits so far, am looking forward to trying to "amp" the cable feed to possible see if that works.

---

### Post by klc5555 on 2010-11-04
> **stratoscape said:**
> 
Frq Table: Cable-High
Modulation: Cable (QAM-256)
Scanning range (I left alone, qam-256 channel 78 -> qam-256 channel 159, 77

as I told most the qam-256 unencrypted in in this range also see whats avail in your area here [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)



Not quite as true as it perhaps was before last year's big digital cut-over kerfluffle. In my own area I find that since June 2009 most of the surviving QAM has landed in the low channel 70s, with a couple down in the 30s. Comcast is low-level encrypting more in my area all the time, however, and two weeks ago even a QAM long-time mainstay like the History Channel was sucked into the set top box. 

Also I'm not quite sure how reliable the silicondust listings are going to be for you. The silicondust listings for my area seem to be infrequently updated, and seldom correspond very well to the limited offerings actually available in my area beyond the OTA local channels. But perhaps they're better where you are.

---

### Post by stratoscape on 2010-11-04
By no means am I a subject matter expert on this, I found some of it in another thread and was turned on to the silicondust site just as reference. In our area this is how we scanned for the available QAM channels and should have mentioned that this could be very different in your area :)

Also wondering if you are still with the hvr-1600 you mention a preference for other cards but I didn't get from you reply if you were still using the 1600's my question was if you needed a amp as saw mentioned in another post as well as is it necessary to cofigure the analog side of the tuner in myth backend if you intend to only use the digital qam channels. In my situation I was getting signal (as displayed on signal meter) when I scanned on the digital side but afterwards I just could not see a picture for whatever reason (p.s. Not meaning to hijack this thread, just thought the symptoms were the same)

Thanks

---

### Post by klc5555 on 2010-11-04
There is no need to configure the analog if you only use the digital port. 

I found that the digital on the 1600 was nearly useless without a drop amp. I absolutely needed an amp. I also had to compile my own dvb drivers off the linuxtv.org daily snapshot. I could never get scans to produce any signal strength at all in the mythtv backend setup, so I had to formulate and load a channels.conf file using the dvbscan tools.

You say you're getting signal strength; are you getting channel locks? Do you have the v4l-cx23418 firmware (in addition to the driver)for the 1600 card (available, in the unlikely event you don't have it, at [http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html](http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html) ) and did the firmware load at boot? Failure to get locks in the presence of decent (say 70%) QAM signal strength is sometimes a firmware problem.

Under the best of circumstances I could only ever get satisfactory reception with the 1600 on about 2/3 of the QAM stations I had available to at the time (about a year ago). So I soon relegated the 1600s to analog capture off of my cable box and DTAs (at which service they are excellent), and moved to three Pchdtv hd5500s and an AverMedia A180 for QAM. Either of which being vastly superior for this purpose to the Hauppauge 1600. Especially the 5500 which requires essentially no setup, no firmware, and no special drivers beyond what is in the standard kernel tree.

Sorry, can't help you with this card beyond this and what the wiki on linuxtv.org has to say about it.

---

### Post by stratoscape on 2010-11-04
> **klc5555 said:**
> You say you're getting signal strength; are you getting channel locks? Do you have the v4l-cx23418 firmware (in addition to the driver)for the 1600 card (available, in the unlikely event you don't have it, at [http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html](http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html) ) and did the firmware load at boot? Failure to get locks in the presence of decent (say 70%) QAM signal strength is sometimes a firmware problem.

Yes, was seeing metered signal strength while scanning QAM-256 (Both Locked, Unlocked) and we just saved the information from the unlocked to our channel list (have not had to use a scan utility, we can scan and lock them we so far just can't view them, no lockup just times out on "Please Wait" then drops back to selection menu) I am hoping we can correct this when I install this Radio Shack 15-1169 Bidirectional Cable Amplifier this evening.

Here are the results from dmesg | grep cx18

```
mfamdvr@mfamdvr-desktop:~$ dmesg | grep cx18
[    7.076511] cx18:  Start initialization, version 1.2.0
[    7.076543] cx18-0: Initializing card 0
[    7.076545] cx18-0: Autodetected Hauppauge card
[    7.076617] cx18 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.077247] cx18-0: cx23418 revision 01010000 (B)
[    7.298267] cx18-0: Autodetected Hauppauge HVR-1600
[    7.298269] cx18-0: Simultaneous Digital and Analog TV capture supported
[    7.394156] IRQ 19/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.825832] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[    7.902793] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    8.159096] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[    8.159099] DVB: registering new adapter (cx18)
[    8.264022] cx18 0000:03:01.0: firmware: requesting v4l-cx23418-cpu.fw
[    8.707496] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[    8.733665] cx18 0000:03:01.0: firmware: requesting v4l-cx23418-apu.fw
[    8.912207] cx18-0: DVB Frontend registered
[    8.912209] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[    8.912237] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[    8.912259] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    8.912283] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[    8.912285] cx18-0: Initialized card: Hauppauge HVR-1600
[    8.912308] cx18-1: Initializing card 1
[    8.912311] cx18-1: Autodetected Hauppauge card
[    8.913689] cx18 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.914328] cx18-1: cx23418 revision 01010000 (B)
[    9.119128] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[    9.126891] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[    9.147750] cx18-1: Autodetected Hauppauge HVR-1600
[    9.147752] cx18-1: Simultaneous Digital and Analog TV capture supported
[    9.241996] IRQ 18/cx18-1: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.246709] tuner 4-0061: chip found @ 0xc2 (cx18 i2c driver #1-1)
[    9.248183] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #1-0)
[    9.251872] cx18-1: Registered device video1 for encoder MPEG (64 x 32 kB)
[    9.251874] DVB: registering new adapter (cx18)
[    9.298162] cx18-1: DVB Frontend registered
[    9.298164] cx18-1: Registered DVB adapter1 for TS (32 x 32 kB)
[    9.298188] cx18-1: Registered device video33 for encoder YUV (16 x 128 kB)
[    9.298237] cx18-1: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[    9.298285] cx18-1: Registered device video25 for encoder PCM audio (256 x 4 kB)
[    9.298287] cx18-1: Initialized card: Hauppauge HVR-1600
[    9.298326] cx18:  End initialization
[    9.304530] cx18 0000:03:02.0: firmware: requesting v4l-cx23418-cpu.fw
[    9.336525] cx18 0000:03:01.0: firmware: requesting v4l-cx23418-cpu.fw
[    9.485369] cx18-1: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[    9.536904] cx18 0000:03:02.0: firmware: requesting v4l-cx23418-apu.fw
[    9.589046] cx18 0000:03:01.0: firmware: requesting v4l-cx23418-apu.fw
[    9.716239] cx18-1: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[    9.723670] cx18-1: FW version: 0.0.74.0 (Release 2007/03/12)
[    9.932024] cx18 0000:03:02.0: firmware: requesting v4l-cx23418-cpu.fw
[    9.958253] cx18 0000:03:01.0: firmware: requesting v4l-cx23418-dig.fw
[   10.072214] cx18 0000:03:02.0: firmware: requesting v4l-cx23418-apu.fw
[   10.385674] cx18 0000:03:02.0: firmware: requesting v4l-cx23418-dig.fw
[   10.474609] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   10.496867] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   10.572851] cx18-1 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   10.592571] cx18-1 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
mfamdvr@mfamdvr-desktop:~$ 

```

If the amp does not do it, I've already braced my friend for the news that we're going to abandon the HVR-1600's and in-lieu of the pcHD-5500's

thanks for reply's, they were indeed helpful and I will post results from amp installation so anyone stagering across this later can save the trouble and just punt now!

Strato

---

### Post by stratoscape on 2010-11-04
@prof3205, first, sorry for hijacking your thread but hopfully you can get what you need from it to resolve your issue. I weighed in here in the first place cause I have the same issue with a setup same version same tuner and was bangin my head on the walls as well. 

Next, @klc5555 you were spot on with the HVR-1600 requiring a in-line amp to get enough signal for it to display. I can't imagine how you came by that important piece of information but it really should be sticky'd somewhere cause we have been on this for weeks now (my friend and I) researching this card all over the net and never found anything on that - Thank You, for the idea 

@prof3205, read my previous post for info on the amp becuase i do not believe this 1600 will even work without it (Digital that is) but in regards to the scanning, I have no idea for your area but try starting with cable then cable high fequencies QAM-256 but you will probably need to find a post from someone in your area to succesfully complete this - good luck

Another very important piece I ran into relates to either multiple HVR-1600's and/or NVIDIA video cards in the same system. If you find "__VMALLOC_RESERVE in page.h" appearing in the logs this comes from a addressing issue between the drivers and kernel. you can find more on this by just doing a google search but the fix is VERY simple in that there is a file that needs to be appended with "vmalloc=192M" which allocate more space to load the drivers (pittyful explanation but finding fix for this was simple as well)

---

### Post by klc5555 on 2010-11-12
Just as a follow-up on this thread: the cx18 driver situation with this card and digital is still getting better over time, thanks to the continuing work of Andy Walls, Hans Verkuil, and others over at linuxtv. 

Since I was moving up to a newly-compiled 2.6.35. series kernel on a machine that I happen to have two 1600 cards on for analog capture from DTAs, I decided to grab a current dvb driver snapshot from linuxtv. The one I had been using was over 10 months old.

After compiling and installing the drivers, as an experiment, I hooked up the digital halves of the two 1600s, set up video sources for them, and tried a scan. These cards are downstream from a very good amplified splitter, but I'd always had to make a channels.conf file for them before (last experiment about a year ago).

Though they still register 0% signal strength in scanning (and tuning), nevertheless, one of the two cards easily got locks and later tuned all the available Standard Digital channels available to me on QAM. (Oddly, it couldn't find any of the HD QAMs at all.) The second card in the next slot, however, got locks on all available SD and HD QAMs. And, with some fiddling on several of the HDs, it could tune them all, so far without noticeable artifacting or pixellation.

I've never had even close to this level of success on digital with the 1600 before, and I may start scheduling digital recordings on them for a while as a further test.

But over time, life does seem to be getting better with digital on this card in Linux. Thanks to the crew who continues to labor over the cx18 driver.

---

### Post by tpham3783 on 2010-11-13
[klc5555]("http://start.ubuntuforums.org/member.php?u=533176"),

I use ubuntu 10.10 and i can't seem to be able to scan clear QAM channels from comcast.  I can only watch ATSC channels.  Do you know what driver version you had to end updating?

---

### Post by klc5555 on 2010-11-13
The machine with the two 1600s ended up with the dvb drivers compiled from linuxtv.org's  26th October snapshot v4l-dvb-abd3aac6644e, compiled against a 2.6.35.7 kernel on gcc 4.4.4 

The mythtv version on this particular machine, however, is old: still 0.21. Users of more current versions of mythtv have occasionally reported scanning difficulties on this card. But the dvb side of this card always requires a good line amp, and even when scanning and tuning correctly it never reports signal strength at greater than 0%.

If your card doesn't want to scan at all with current drivers on a current version of mythtv, you might still need to compose and load a channels.conf file using non-mythtv command-line scanning tools like scan or dvbscan. See [http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan)

---

### Post by CoximusPrime on 2011-02-22
are you still having issues here?? I've got a HVR 4000 which had issues scanning channels, which I think (think being the highlighted word here) Ive now got working.

---

