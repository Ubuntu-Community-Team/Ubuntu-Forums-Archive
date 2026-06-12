---
title: "Trying to get Hauppauge 1250 card to work"
date: 2009-08-29
forum: Multimedia Software
---

### Post by &lt;Danny&gt; on 2009-08-29
Hello everyone. First off, I'm a linux noob - I know just enough to be dangerous :-) I inherited my brother's PC when he left for college. It has ubuntu 9.04 on it. I thought I would put in a TV card so I could watch shows on the monitor. I bought a Hauppauge WinTV-HVR-1250 card. Well...I didn't realize how hard this would be. 2 days ago I put the card in, and here is where I've been:

I started with "The Google" and went here and started following the advice in the thread:

[http://ubuntuforums.org/showthread.php?t=974366](http://ubuntuforums.org/showthread.php?t=974366)

installed "xawtv" - launched it - NOTHING HAPPENED - No errors, just NOTHING.
installed Me TV - launched it - Scan Wizard popped up. Selected By Location, but "country" and "region" were both greyed out and NOT selectable. "Help" was NOT helpful (only contained "about"). Scan said scanning is only available for dvb-c or dvb-t. I pretty sure we do ATSC.

Following the thread I typed in "sudo lshw -C multimedia" and got:

danielle@media:~$ sudo lshw -C multimedia
[sudo] password for danielle: 
  *-multimedia            
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0 module=cx23885
  *-multimedia
       description: Multimedia audio controller
       product: MCP04 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 13
       bus info: pci@0000:00:13.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

Following further, I installed "Kaffeine". I launched Kaffeine and a pop-up window said "DVB-Device...Ok".

Scanned for channels - found 47-1, 47-2, 53-1 53-2 (didn't find 6,8,10,12,17,18,23,66 and a host of smaller religious stations in the area).

I actually could see these 4 channels through Kaffeine :-) So, I'm making some progress WOO HOO!!

I continue to follow the thread because I still can't see all the stations that I can on the TV in my room, so somthing's not right.

Ran "lspci | grep Conexant" and got:

02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)

Followed a link to here: [http://ubuntuforums.org/showthread.php?t=1234274](http://ubuntuforums.org/showthread.php?t=1234274)
which lead me to one here: [http://ubuntuforums.org/showthread.php?t=1014551](http://ubuntuforums.org/showthread.php?t=1014551)

"dmesg" produced this (snippet) just like the thread starter:

[   12.896297] cx23885 driver version 0.0.1 loaded
[   12.897985] cx23885 0000:02:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   12.898104] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   13.025756] tveeprom 2-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   13.025760] cx23885[0]: warning: unknown hauppauge model #0
[   13.025762] cx23885[0]: hauppauge eeprom: model=0
[   13.025765] cx23885_dvb_register() allocating 1 frontend(s)
[   13.025844] cx23885[0]: cx23885 based dvb card
[   13.173484] MT2131: successfully identified at address 0x61
[   13.173491] DVB: registering new adapter (cx23885[0])
[   13.173495] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   13.173900] cx23885_dev_checkrevision() Hardware revision = 0xc0
[   13.173910] cx23885[0]/0: found at 0000:02:00.0, rev: 3, irq: 16, latency: 0, mmio: 0xd3000000
[   13.173917] cx23885 0000:02:00.0: setting latency timer to 64

Following the thread, I clicked a link which took me here: [http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10](http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10). I realize this was an earlier version (8.10), but after jumping around the internet for a couple of hours and making little or no progress, I decided I had little to lose.

I followed their instructions:

1. Load up a terminal window if you are in the graphic interface.
2. Type in the following to install gcc, mercurial and the kernel headers:
sudo apt-get install build-essential mercurial linux-headers-`uname -r`
3. Move to the /usr/src/ folder with:
cd /usr/src
4. Download the latest V4L drivers with:
sudo hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
5. Move into the newly created folder with
cd v4l-dvb
6. Now start the building process with:
sudo make

This will take a while.

7. And finally we install these drivers with:
sudo make install
8. Reboot your computer and the newer V4L drivers will be used. 

dmesg produced the same (snippet)

[   12.804345] Linux video capture interface: v2.00
[   12.873197] cx23885 driver version 0.0.2 loaded
[   12.873250] cx23885 0000:02:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   12.873372] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   12.999362] tveeprom 2-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   12.999366] cx23885[0]: warning: unknown hauppauge model #0
[   12.999368] cx23885[0]: hauppauge eeprom: model=0
[   12.999370] cx23885_dvb_register() allocating 1 frontend(s)
[   12.999513] cx23885[0]: cx23885 based dvb card
[   13.219722] MT2131: successfully identified at address 0x61
[   13.219728] DVB: registering new adapter (cx23885[0])
[   13.219731] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   13.226310] cx23885_dev_checkrevision() Hardware revision = 0xa4
[   13.226319] cx23885[0]/0: found at 0000:02:00.0, rev: 3, irq: 16, latency: 0, mmio: 0xd3000000
[   13.226326] cx23885 0000:02:00.0: setting latency timer to 64

So...that didn't change anything.

according to to peeps on the web, the above shows my card isn't being recognized correctly. I followed a couple of other threads that said to set the tuner with ivtv-tune, but doing:

ivtv-tune -c6

gives me: Failed to open /dev/video0

AAAAAARRRRRGGGGGGHHHH!!!

Can anyone out there help me get this thing going? I'm so close with Kaffeine. If I run ivtv-tune like this:

ivtv-tune -l - it gives me a list, but none of the frequencies are close to what is reported in Kaffeine for the 4 channels I got.

Well, I went back in to Kaffeine and did another scan and now I get:

TSID:1527-SID:3
TSID:1527-SID:4

in the found column, but when I try to move them to the channels column, they disappear :-(

I feel like I'm chasing all over the internet and getting nowhere!  I hope this isn't too long of a post, but I tried to list everything I did before asking for help.

Thank you - Danny

---

### Post by &lt;Danny&gt; on 2009-08-31
Help!!

---

### Post by mathieulj on 2009-09-01
I have had this card for a year or so and have given up trying to get it working. The main problem for me is the lack or analog support for this card in all linux drivers (Digital is supported in the V4L drivers). My region has very poor OTA reception due to terrain and my cable company only sends analog unencrypted so when i'm under linux, this card is of no use to me. Perhaps you have run into a similar hurdle.

---

### Post by Tomlin on 2009-09-03
I've had limited success with this card under Linux. I'm not at home right now, but will report back later today on how I got Mythbuntu to work.

Long story short - I still haven't gotten the remote to work (keyboard works, but I'd like to use in a HTPC setup).

Later.

Tomlin

---

### Post by HappyFeet on 2009-09-03
See [this]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)").

---

### Post by Tomlin on 2009-09-04
When setting up Mythbuntu, under "Capture card", the 1250 was recognized as a:

Samsung S5H1409.

Before starting the installation, I signed up at Schedules Direct ([http://www.schedulesdirect.org]("http://www.schedulesdirect.org")) for their free 7-day trial and set up a profile. In MythTV setup under "Input Connect" you can scan for channels by typing in your username and password for Schedules Direct.

When setting up Storage directories, I followed a thread where the poster had set up different directories for "Recordings", "LiveTV", and "DB backup", so I did the same. I had to manually add  the latter 2 and change the owner to mythtv and permissions to 755. I have a feeling if you let EVERYTHING go to the "Default", you don't need to do that, as it's already done for you.

Having said all this, I'm still having some minor problems with freezing after it's been running for a while. It is not responsive to mouse or keyboard. I've been reading posts here and a few people are having the same issue. They seem to say it stores up keystrokes and then, maybe a minute later, executes them all. I'll have to wait until it feezes up again to try it. It seems random.

Good luck. Let me know how it works.

---

### Post by Creideamh on 2010-05-31
Any progress on any of this? I realize driver development is too much to ask for, since the problem is analog reception and the trend is digital. However, I still want my 1250 to receive analog from a STB, but it finds no channels on scan.

In my case the dmseg output is almost the same as Danny's near the top of this thread - the difference is that it shows the tveeprom not a valid Hauppauge eeprom. I gather from another forum thread that this means the analog isn't working.

I downloaded and compiled the latest linuxtv drivers via hg, with a huge FAIL. Following the same steps Danny listed, I got errors on compile, though not in the driver for this card. Tried make install, which appeared to complete properly, but the drivers have unresolved symbols after reboot.

Unfortunately this is one of the few cards that fits in the low-profile case, and came with the system, so it would be nice to be able to get it working.

---

### Post by WinterRain on 2010-05-31
I think the only thing you can do is go out and buy a usb tuner that is known to work in linux.

---

### Post by Creideamh on 2010-06-02
Thanks - not what I had hoped to hear, but looking like the best choice at this point.

---

### Post by the_pod on 2010-11-26
fwiw, I had this card working like a champ in 9.04.  Just recently decided to do some upgrading and wish I hadn't.  

First, 10.10 lirc doesn't seem to work, or it's just not worth the hassle.

Beyond that, the reception on the 1250 is now noticeably worse than it was and doing a v4l upgrade just breaks my system.

Bonus points - some clown deleted the 1250 help page on the Mythtv wiki.  For added humor, I noticed that the "installation manual" linked to from the MythBuntu installation screens doesn't exist either.  That's just rich.

After 4 days of nonsense I am very bitter.  And I just use the digital side.

In other news, my 1600 now works native in myth but not as well as it used to using Devin's drivers.

Happy Thanksgiving.

---

### Post by poe503 on 2010-11-26
I am also currently struggling with this 1250 card.  Actually 2 cards. 

I have two 1250 cards set up with a 9.04 system that I had mocked up a year ago and they work great.  The new cards are also recognized on this system.  I had used the usual v4l-dvb setup at that time, everything had gone smoothly and the card were recognized right off the bat by Myth.

I am trying to get these cards to work on a new system with 10.04 with not much luck.  The v4l-dvb setup went smoothly after using "make config" to remove the Firedtv entry to avoid a failed "make".  Install went smoothly but dmesg shows the cards as unrecognized after a reboot.

I can get one card recognized by making a file in modprobe.d to set the card at "card=20" but have no luck getting the second card recognized.

I read that someone had updated 9.04 and also lost their 1250 setup.

What gives here?

---

### Post by the_pod on 2010-11-26
> **poe503 said:**
> I am also currently struggling with this 1250 card.  Actually 2 cards. 

I have two 1250 cards set up with a 9.04 system that I had mocked up a year ago and they work great.  The new cards are also recognized on this system.  I had used the usual v4l-dvb setup at that time, everything had gone smoothly and the card were recognized right off the bat by Myth.

I am trying to get these cards to work on a new system with 10.04 with not much luck.  The v4l-dvb setup went smoothly after using "make config" to remove the Firedtv entry to avoid a failed "make".  Install went smoothly but dmesg shows the cards as unrecognized after a reboot.

I can get one card recognized by making a file in modprobe.d to set the card at "card=20" but have no luck getting the second card recognized.

I read that someone had updated 9.04 and also lost their 1250 setup.

What gives here?

fwiw, I found that doing the old v4l update like you did on the 9.04 version to break things. Based on your description, we had similar paths previously.  At this point, I've done a clean install of 10.04 and the card is recognized fine.  If that works for you, I'd discourage the v4l updates since that's been a disaster on my end.  Your mileage may very.

---

### Post by poe503 on 2010-11-27
Thanks for the reply.

Well, this is an new system with a fresh install of 10.04.  

The card was "recognized" in lspci but the /dev/dvb file was not installed and so I would get the list of "card=n" in demesg.  

I then went the v4l-dvb route which did nothing.  

As I had previously stated, the v4l-dvb installation in last year's 9.04 Myth system was a big success and continues to be so.

---

### Post by Daibhi on 2011-10-09
I understand Danny's plight. I am a Ubuntu virgin, well maybe slightly tried, however I'm having similar problems with Kaffiene and others to pick up my signal from my cable box. Then I hear this about VL4 and I'm lost. Can someone please help direct this ultranoob out of wonderland?

Thanks!

---

### Post by poe503 on 2011-10-09
If you are having trouble getting your Hauppauge 1250 TV card to work, check out my tutorial: [*http://ubuntuforums.org/showthread.php?t=1648472*]("http://ubuntuforums.org/showthread.php?t=1648472")

---

### Post by Daibhi on 2011-10-16
Hey Poe! Went through the tutorial, still no luck. TVTime said that there is nothing found at /dev/video 0. 

I dislike having to drop out of Linux to go over to the Windows side to get this card to work but right now it's the only way unless someone can give me a heads up on how to get Myth or the system to recognize a card that is usuable in Windows, is plugged into a PCI-E slot, and is otherwise fully functional.

BTW Poe, excellent tutorial, it got me closer but there's obviously one thing out there I'm missing and I don't know how to get to it.

---

### Post by poe503 on 2011-10-16
I had replied to your post on the tutorial thread.  I am willing to help but need you to supply information.  We can discuss this on this thread or the other, your choice.  

I would point out that the tutorial is almost a year old and things change quickly in the world of linux so the tutorial may not be as accurate as it used to be.  

The tutorial gets lots of hits each week and not much for commentary so I assume it's still pretty good.  When I wrote the tutorial, I tried to include a howto for both the old and new versions of Ubuntu that were available at the time.

Someone has subsequently commented on the tutorial thread that newer versions of Ubuntu need Git instead of Hg to install the drivers properly.  I don't know if this is true.

---

