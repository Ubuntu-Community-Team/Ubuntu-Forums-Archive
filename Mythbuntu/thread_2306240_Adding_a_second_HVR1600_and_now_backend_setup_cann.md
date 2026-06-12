---
title: "Adding a second HVR1600 and now backend setup cannot access cards"
date: 2015-12-13
forum: Mythbuntu
---

### Post by JimLS on 2015-12-13
Running Mythbuntu 0.27.5 that has been solid for a very long time.  Picked up a second HVR1600 for cheap on ebay thinking it would be easy to add.  Don't need the NTSC part - just doing OTA ATSC.  I put the card in and the first time it found the card and reported the same or similar to what's in the wiki:  Samsung S5H1409 QAM/Subtype: ATSC
both cards show up in /dev/dvb...  The cards work individually - I can put in either one and recordings and live tv work.  But the front end status shows 4 tuners (even though I have only tried to set up the ATSC portions and reports errors on the last two.  In the backend setup I can't get a channel scan for the second card.  The card setup page states " Frontend ID:  Could not get card info for card /dev/dvb/adapter0/frontend0"
In fact it now does that for either card, together or separately.  Have tried removing both cards, restarting and shutting down and then putting only one in.  Still shows 4 tuners with 2 having errors and the message above is the same.  I am afraid to delete all the cards and try re-setup as my system is working (although obviously it has issues).
 
dmesg | grep cx18 seems to give reasonable output:

```
myth@myth-14:~$ dmesg | grep cx18
[   18.121375] cx18:  Start initialization, version 1.5.1
[   18.121689] cx18-0: Initializing card 0
[   18.121693] cx18-0: Autodetected Hauppauge card
[   18.124326] cx18-0: cx23418 revision 01010000 (B)
[   18.337631] cx18-0: Autodetected Hauppauge HVR-1600
[   18.337632] cx18-0: Simultaneous Digital and Analog TV capture supported
[   18.561674] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   18.622005] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   18.622009] DVB: registering new adapter (cx18)
[   18.698574] cx18 0000:01:07.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   18.698668] cx18-0: DVB Frontend registered
[   18.698670] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   18.698699] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   18.698717] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   18.699248] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   18.699331] cx18-0: Registered device radio0 for encoder radio
[   18.699333] cx18-0: Initialized card: Hauppauge HVR-1600
[   18.699381] cx18:  End initialization
[   18.707393] cx18-alsa: module loading...
[   19.123840] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.395902] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   19.402247] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   20.245063] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   20.264202] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
myth@myth-14:~$

```

When I exit the backend setup I get the following error message:

Card 3 (type DVBInput) is set to start on channel 2_1, which does not exist.
Card 4 (type DVBInput) is set to start on channel 2_1, which does not exist.

With the selection buttons of:
 "Yes please" (the default.  This makes no sense given the error.  Perhaps some of the message isn't visible?   It isn't obvious but it puts you back into setup)
"No, I know what I am doing"

The only way to get out is to select the second option even though I don't really know much about what I am doing.  :)

I did notice that the cards run hot, especially with the two right next to each other and I only have two slots.  Need to position a fan to force air between them somehow.  But I don't think that has anything to do with the problem above.

Any suggestions?

---

### Post by JimLS on 2015-12-13
I updated my system and deleted all tuners.  The setup screen was able to get the tuner info "Samsung...".  It no longer gives me error message when exiting backend setup.  But now front end status reports Tuner 5 and Tuner 6 have errors and live tv does not work.  I did this with only 1 tuner card installed.  The lower number tuners don't exist within Mythtv as far as I can tell but must still exist somewhere...???  I restored the database from earlier and now it reports tuners 1 - 4 have errors and the tuner is non-operative.  Seems like something within Myth is confused.  Is there some way to recover without completely starting fresh on setup?

---

### Post by aelfric55 on 2015-12-14
Added tuners always count up, until tuner "99", even if you delete earlier tuners. Unless you choose the option to delete all tuners on all backends, which is generally unnecessary. The myth-assigned tuner number is not an issue. My database has been continuous since the end of 2007, and my first tuner is now "71".  Every year or two I mean to clean it up, but never bother.

I currently run 4 of these obsolete HVR-1600 cards. Just as well you don't use NTSC: the analog half of these cards doesn't work at present on the combination of kernels 4.x.x (most 3.x.x is fine) and mythtv 0.27.x.  A ticket exists; a patch may come into existence for a future myth 0.27.6.

The way this upgrade should have happened was to plug the second card into the second slot. Boot. Check dmesg | grep cx18 output. There should be TWO stanzas in the output for the 1600 cards: one for "card 0" and one for "card 1". (Your file printout only indicated 1 card present at that particular boot.) If you have both cards initializing at boot according to dmesg, you should be in business for ATSC. 

In the backend setup, you should have needed to add a tuner for a second card's DVB half. You would have checked the drop-down menu to make sure the card's setup did not automatically add 2 DVB tuners instead of 1 (various iterations of mythtv setup have assumed everyone was using multirec, which the 1600 doesn't support anyway) This new tuner would have been bound in Input Connections to the same Video Source that the first dvb tuner was bound to. Therefore there would have been no need to scan for channels on the second card --myth already knew all the tuning frequencies and channels since they're the same as for the first card. You would have set the second card to start up on a channel that the mythtv database actually knows about (from the drop-down menu in Input Connections) and not a channel that "doesn't exist". You would have then exited setup, restarted the backend (or both the master backend and the secondary backend if this is the type of setup you have) and checked in the frontend's "System Status" to make sure that the new tuner was "available".  (Sometimes it may take one ot two  "sudo killall mythbackend"  get the mythbackend process stopped; I've occasionally found just restarting the service sometimes doesn't get the backend process closed cleanly.) Total upgrade time expenditure about 10 minutes.

The trouble is, after all the unnecessary card plugging and swapping, scanning (which would modify previously set up channel numbers in your digital Video Source), and database deleting and restoring, I don't know what the actual current state of your setup is to advise you further.

So for the first step, put the two cards in the machine and leave them there. See if at boot dmesg says that cx18 has initialized both card 0 and card 1 and has registered both DVB Adapter 0 and DVB Adapter 1. If DVB Adapter 0 and DVB Adapter 1 are both there, then you're good to proceed further. But if the cx18 driver doesn't initialize the second card at boot, then there are a couple of possibilities. Each iteration cx18 driver arrogates some portion of the same virtual memory space to itself that, inter alia, the NVIDIA proprietary driver uses. If the second cx18 doesn't load, or if it does load and you have, say, problems with the graphics driver loading, then you may need to up vmalloc at boot to 128M or 256M or even 512M to get all your drivers loading correctly.

---

### Post by JimLS on 2015-12-14
Thanks for the explanation of the numbering - now I know I don't need to worry about that.

Yes, the printout was for one card installed.  I can and will do for both.  They show up as expected under /dev/...

I think you may be on to something about multirec and adding 2 tuners for each card - that seems to be what is happening.  How do I avoid this?  Do I need to revert to a previous version of myth backend?  Is there a patch?  I guess I should not have updated my software as I had no trouble setting this up several years ago.    At this point I can't even get the original tuner to work by itself.

The "unnecessary card plugging..." was because the basic steps (which you outlined very well, thank you) didn't work and I was trying to troubleshoot.

The vmalloc is not the issue.  I already have that and it was working with one card.  Now I can't even install one card.

---

### Post by aelfric55 on 2015-12-14
The setting you're missing is "max recordings" which is under "recording options" in the "Tuning Cards" setup. "Max recordings" should equal "1" 

Two or three cards requires higher vmalloc than one. With NVIDIA usually 256M or 512M. Check dmesg in case there's a vmalloc error message in it.

You don't need any backend patching for ATSC. Just set up and save your 2 cards as DVB-T/S/C ATSC cards, and then bind each of the cards to your current digital Video Source in Input Connections. Unless your Video Source was compromised in all the deleting, adding, and restoring you don't need to scan channels; you do however need to make sure the "Starting Channel" drop down menu is set to one of the actual digital channels mythtv knows about. If the "Starting Channel" is set to "add channel" or to an unknown channel, LiveTV won't start up on that card.

Save and exit the backend setup. Kill and restart the backend(s) or simply restart the machine. If there are problems, start looking at the logs: dmesg, and mythbackend.log If there are spurious, unknown, missing, or no tuners, mythbackend likely did not start and will have registered the issues in the log. If the backend is running, but can't open the tuner when livetv is requested or a show is supposed to begin recording, it will also register these problems in the mythbackend.log




[LIST]
[*][[IMG]https://community.freescale.com/2015.3.0.971481a/resources/images/palette-1004/customNavLogoImage-1443117325982-community-logo.png[/IMG]]("https://community.freescale.com/") 
[*][Home]("https://community.freescale.com/welcome") 
[*][Content]("https://community.freescale.com/content") 
[*][People]("https://community.freescale.com/people") 
[*][Places]("https://community.freescale.com/places") 
[/LIST]

[LIST]
[*]
[LIST]
[*][Log in]("https://community.freescale.com/thread/360089#") 
[/LIST]
  
[*]Search 
[/LIST]

---

### Post by JimLS on 2015-12-14
I deleted all tuner cards and was able to load 1 tuner card (started with only one to minimize issues since I knew that worked before ).  My video source with channels is intact.  That worked so shut down and put in second card.  Ran myth backend setup and it recognized second card (a big improvement).  In the front end I have now have 4 tuners.  It appears each ATSC tuner can handle two streams as long as they are subchannels of the same channel.  I tried recording two programs on same channel and that seems to work.  But tuners 3 and 4 shows errors in the front end status screen (I am not using the analog tuners and haven't set them up).  These appear to be two possible streams from the second card.  I checked dmesg and both cards are detected without errors (previous posting was when only one card was installed).   Tuners 1 and 2 are ok, 3 and 4 have errors according to status in front panel.  I looked at the back end log but had trouble wading through it with much of an idea what I was looking for.  I did see several "get signal strength failed" and "get signal/noise ratio failed" messages but it appeared to be on the card that is working.  I also saw several places "unknown encoder 3" and "unknown encoder 4".  

At least I have one tuner back in operation.  I can post some specific output but don't want to post a bunch of stuff that isn't related to the issue.

---

### Post by JimLS on 2015-12-15
One tuner is working the other isn't.  They were detected the first time through in the backend setup.  But when I go back into the backend setup the card setup page for one tuner states " Frontend ID:  Could not get card info for card /dev/dvb/adapter0/frontend0"  I went into options and turned off eit scan but that didn't seem to make any difference.  I also noticed on the "interaction between inputs page that the input group 1 was changed for both cards.
The first tuner input group 1 is:  DVB_/dev/dvb/adapter0/frontend0     Input group 2 is Generic
The second tuner input group 1 is:  DVB_/dev/dvb/adapter1/frontend0     Input group 2 is Generic

Not sure if this is as it should be or not.

How do I increase the backend logging for the capture card?  I see dvbcam is one of the options - is this the one?

---

### Post by aelfric55 on 2015-12-15
> **JimLS said:**
> One tuner is working the other isn't.  They were detected the first time through in the backend setup.  But when I go back into the backend setup the card setup page for one tuner states " Frontend ID:  Could not get card info for card /dev/dvb/adapter0/frontend0"  I went into options and turned off eit scan but that didn't seem to make any difference.  I also noticed on the "interaction between inputs page that the input group 1 was changed for both cards.
The first tuner input group 1 is:  DVB_/dev/dvb/adapter0/frontend0     Input group 2 is Generic
The second tuner input group 1 is:  DVB_/dev/dvb/adapter1/frontend0     Input group 2 is Generic

Not sure if this is as it should be or not.

How do I increase the backend logging for the capture card?  I see dvbcam is one of the options - is this the one?

I still suspect the vmalloc setting. From the hvr-1600 page on the mythtv wiki (note the underlined):
**Common Problems**

 **Driver refuses to load with mysterious errors**

 Under certain memory configurations on 32-bit platforms, using this  card's driver and some other drivers (usually but not exclusively  nVidia's proprietary driver) at the same time requires more of a  particular type of address space allocated than the kernel will allocate  by default.  If you experience the driver refusing to load for no  obvious reason, check the output of `dmesg`.  If you see either of the  two following messages appear, you will need to go to [Common Problem: vmalloc too small]("https://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small") to learn how to apply a very small kernel configuration change which requires one reboot. 
[U][B]The above problem can also be what is causing a second HVR-1600  to not mount.  Increasing vmalloc will allow more than one card to start  on some system configurations. 
[/B][/U]
_**The messages to look for: **_
[U][B]allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
cx18-1: ioremap failed, perhaps increasing __VMALLOC_RESERVE in page.h


[/B][/U]You probably should check for this before proceeding further.

---

### Post by JimLS on 2015-12-15
I don't see any indication but worth a try.  Maybe loading the second card drivers clobber the first one(?).  I had some trouble with this when I first got started with Myth (different PC, similar cards) and had to add a grub option to increase it.

First see what is in /proc/meminfo:

```
VmallocTotal:   34359738367 kB
VmallocUsed:      437764 kB
VmallocChunk:   34359293436 kB
```


The first number is huge which suggests something funny is going on.  This system has 2 G of memory.

Check memory:
```
myth@myth-14:~$ free
             total       used       free     shared    buffers     cached
Mem:       2049068    1945304     103764      12736      20152    1024300
-/+ buffers/cache:     900852    1148216
Swap:      2095100     146544    1948556
```

Linux version:
```
myth@myth-14:~$ cat /proc/version
Linux version 3.13.0-71-generic (buildd@lgw01-09) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #114-Ubuntu SMP Tue Dec 1 02:34:22 UTC 2015
```

System is Ubuntu 14.04 64 bit.

Added vmalloc=512MB to boot line and both tuners now work!  :)  No errors in front end status screen and I can record two shows at the same time on different main channels.  Guess I should try 256 as that might be enough, then make it permanent.

The /proc/meminfo still looks goofy though:
```
VmallocTotal:   34359738367 kB
VmallocUsed:      437732 kB
VmallocChunk:   34359292412 kB

```
When recording on one tuner and trying to watch live tv I can only view the subchannels that are on the same channel as the one recording.  Didn't try to switch tuners but I hardly use that so not a big deal.

Thinking it may be a good idea to add some more RAM?

---

### Post by aelfric55 on 2015-12-15
Glad you've got it working! Go ahead and try 256M It may work. If not, split the difference with 320M -- vmalloc should be happy incrementing in 64M chunks. Eventually you'll find the sweet spot. 

Re: livetv channels. You can prioritize your tuners in Input Connections so that one is prioritized higher for recordings, while the other is prioritized higher for livetv. The subchannels thing is the limitation of multirec. You still only have 2 physical tuners, even if a tuner is scooping up more than 1 mpeg stream at a time on a channel.

Re: RAM. I very rarely run a frontend on a machine running a backend. This is partly because the requirements for frontends and backends are so different. For frontends I prefer to have reasonably fast core duo or better processor with about 4 Gig or more of RAM and a good NVIDIA card with 1024M -ish of GPU memory. For a dedicated backend, about any running piece of junk will do, as long as the motherboard is new enough to handle SATA. I re-motherboarded an old 2004-vintage machine a couple of weeks ago to use as a backend with a "super-modern" 2006 Celeron board I happened to have lying around the shop. Only had a single 500M DDR module floating around, so that's what it uses. It does fine simultaneously recording on an HVR-1600 and a PCHDTV-5500. Just as long as I never, ever allow commflagging on this machine. Streams livetv OK to the dedicated frontends too. But generally a dedicated backend runs best on about 1.5 to 2 Gigs RAM. More is a waste.

My preferred type of setup actually has the master backend with no tuners at all --just the database and the time and UPN servers for the network. This way, the master mythbackend process can die and restart repeatedly without interfering with any of the running recordings or streaming happening on the slave backends.  The slave backends (currently 3) do all the recording, while every screen and device in the house constitute the frontends, some running mythfrontend, some running Kodi, some running just a UPNP client (which works suprisingly well for prerecorded stuff).

All the best.

---

