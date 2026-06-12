---
title: "General MythTV questions + HW question."
date: 2007-12-07
forum: Mythbuntu
---

### Post by LBadvance on 2007-12-07
Hello all,

I have several questions I would like to ask before I start my HTPC project. I'm at the planning stage of building a HTPC to do the following. Stream xvid,divx, x264 (.mkv container) from my media server to a HDTV 720p. Watch live Digital TV and be able to pause and resume and record from a EPG (like a PVR). On top of that a nice and friendly user interface that everyone can use.  

I'll have been researching on the net and this is what let to mythTV. I've used ubuntu in the past and hence why I am here. However there are still some unanswered questions.

I really like what XBMC has done. I have one that does a fine job of streaming videos, and would like some aspects of XMBC compared to mythTV. 

A1.) Does mythTV have a page scraper to scrape imdb poster cover + info tags?
A2.) Does it have the ability to combine 2 discs to one, such that when you play a movie it automatically plays disc 2 of the movie instead of you having to manually queue it up. I know its kind of hard to explain this feature but those of you whom has used XBMC knows what I am talking about.
A3.) Is there a 3rd party skin made to look like appleTV's front row? I use xTV on the XBMC and would like something similiar on mythTV

OK here comes the hardware questions.
I plan to build the following.

CPU: AMD Athlon 64 X2 BE 2350
Mobo: ASUS M2A-VM HDMI 690G
Ram: Super Talent DDR2 800 2x1GB
HDD: 2.5" (size/brand unsure)
Remote control: Unsure
TV Tuner: Unsure

B1.) I would need the AMD 64 build of Mythbuntu right?
B2.) What remote control works best with mythTV?
B3.) What Digital tuner works best with mythTV AND freeview?
B4.) Are there any issues using HDMI and the coax digital out from that motherboard with mythTV?

Thanks thats all for now.

---

### Post by ntetreau on 2007-12-07
The A questions!:

A1: yes!
A2: It does.  It uses a automatic queue system in the sense that once you told mythtv that cd2 has to be played right after cd1 then it will always automatically queue cd2 when you play cd1
A3:  There are very few skins available, none that I know look like AppleTV.

as for the B questions:

B1: I have a AMD 64 proc. but I use the 32 bit version of mythbuntu without problems.  I does seem that video encoding (especially x264) would benefit the most from your 64 bit proc though, so it might be worth installing the 64 bit version if you'll do lots of it.

B2: I use the MCE remote that came with my Hauppauge PVR-150 card and it works flawlessly

B3: From the Mythtv website: 
> HDTV.

There are a number of HDTV cards with Linux drivers which are known to operate in the United States; a complete list of cards with DVB drivers can be found at [http://www.linuxtv.org/wiki/index.php/ATSC_devices](http://www.linuxtv.org/wiki/index.php/ATSC_devices) Some cards support capture of unencrypted digital cable TV (utilizing QAM256), others will only work with Over The Air signals captured with an antenna (with 8VSB).

Cards that have been reported to work include:

    * pcHDTV HD-2000, Air2PC PCI rev 1-3 (8VSB only)
    * SiliconDust HDHomeRun (8VSB, QAM256)
    * pcHDTV HD-3000/5500 (8VSB, QAM256)
    * Air2PC HD-5000 (8VSB, QAM256)
    * DViCO Fusion HDTV Lite/Gold 5 (8VSB, QAM256)

NOTE: There are no known consumer-level capture devices which will allow you to capture the HDTV output (DVI, HDMI, VGA, YPbPr / Component) from a set-top box commonly found with digital cable systems or satellite systems. None of the capture devices listed above perform any encoding; they merely allow your computer to save a copy of a HDTV stream which has already been converted to MPEG-2 at the broadcast facility.

NOTE:: All of the cards listed above (except for the HD-2000 and HDHomeRun) should be configured as DVB cards. The HD-2000 can be configured as a pcHDTV card if you use the V4L drivers from [http://www.pchdtv.com](http://www.pchdtv.com) and use Linux kernel 2.6.9 or earlier. With kernel 2.6.10 and higher it must be configured as a DVB card, but you lose access to the second antenna input in ATSC mode. The HDHomeRun should be configured as two HDHomeRun cards, one for each tuner.

To playback HDTV content, plan on a powerful CPU. "How powerful?" depends on a number of factors, such as the capture resolution, whether the video is progressive or interlaced, and whether your display card has hardware-assist support for Linux.

The Simple Answer: Once you are in the 3.2 Ghz P4-class of CPU you should have no issues with viewing HDTV.

The Complicated Answer:

For 720p content (1280x720), a 2.4GHz P4 should be sufficient.

For 1920x1080i->1920x1080p with the better deinterlacing methods done in real time a 2.4GHz CPU is taxed, but should work if you use "Bob and Weave" deinterlacing, or if you have an NVIDIA card with MPEG-2 hardware acceleration. If you enable the hardware acceleration, you may be able to use a 1.8GHz processor. 

Also note:

> Hardware known NOT to work and other issues

    * Hauppauge WinTV-D or -HD (no driver)
    * Hauppauge WinTV-USB series
    * Hauppauge WinTV-PVR-usb (model 602), or WinTV-PVR-PCI (model 880) cards (no driver - this is not the PVR-250/350 series of cards supported by the IvyTV driver)
    * Hauppauge HVR-1600. (no driver). NOTE: There have been reports (2006-12 timeframe) that Hauppauge is putting the HVR-1600 inside of the PVR-150 box; if you're purchasing a retail PVR-150, carefully examine the packaging - there should be some indication that the hardware inside is actually a HVR-1600 and not a PVR-150. Check the Supported Hardware ( [http://www.ivtvdriver.org/index.php/Supported_hardware](http://www.ivtvdriver.org/index.php/Supported_hardware)) page of the ivtv driver for updated support information.
    * ATI All-in-Wonder series


Other in the forum might be able to tell you more precisely which HDTV card they have used.

B4: no idea

---

### Post by .nedberg on 2007-12-07
A3: I think there is

Have a look at PearTV

[http://www.mythtv.org/wiki/index.php/Category:Themes](http://www.mythtv.org/wiki/index.php/Category:Themes)

I have never used appleTV so I cannot compare them, but PearTV is made to look like appelTV

---

### Post by LBadvance on 2007-12-07
wow there are so many themes to choose from and they all look so good.

As for the motherboard is the new AMD/ATI chipset supported well in mythTV? The 690G? It has on-board       x1250 graphics card. I know linux prefers nvidia, but are there any issues with that on-board?

Thanks.

---

### Post by LBadvance on 2007-12-10
Also is there an option to sort ur movie library in terms of last modified?

---

