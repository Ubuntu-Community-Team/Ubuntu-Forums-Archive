---
title: "Update on status of Hauppauge 1213 WinTV HVR 2255"
date: 2015-02-06
forum: Multimedia Software
---

### Post by AFriendlyNerd on 2015-02-06
UPDATE: According to the LinuxTV people, it's now merged and can be compiled from mediatree.  [http://linuxtv.org/wiki](http://linuxtv.org/wiki) I am still a struggling n00b with these things, but will endeavor to install as soon as I have time. Any guidance would be appreciated! I will report my experience.

Previous message:

----------

FYI, here is the status of this TV Tuner card from Hauppauge.

First of all, even if you order a 2250, they are now shipping the boxes with 2255's inside.

There is no public driver for the 2255 as of this posting.

However, Hauppauge has a beta driver if you bug them, and are wiling to sign a NDA. The driver is reportedly not just ready to install. Supposedly, it requires some advanced Linux skills to compile it.

Steven Toth told me it should be weeks (not months) before he releases a public driver for the 2255.

---

### Post by tominto on 2015-04-02
Any further update on this?  I purchased this thinking I was getting a 2250.  A the moment its just doing nothing sitting in my computer.  Anxiously awaiting working drivers so I can use it

---

### Post by AFriendlyNerd on 2015-04-03
I was just going to check in!

Steven Toth has submitted a driver to the LinuxTV.org brains. But it is not merged into the official driver package yet.

If you are something of a whiz, you can head over to their media_build tree and compile it yourself. But this process requires using an experimental kernel, I'm told. I like my nice, stable media center so I'm waiting until they merge with the new driver. I'm told this is a couple of weeks away, because they are still finalizing some things with Mr. Toth.

I will update this thread when I become aware of the new drivers being merged.

---

### Post by mrtisoy on 2015-04-03
I just successfully patched and recompiled my kernel so that I was able to use this card. My last tuner card had failed so I didn't have the luxury of waiting. The directions weren't too bad, and I submitted a couple of suggested clarifications. I had trouble getting mythtv-setup to properly scan for channels but the command line tools for channel scanning worked flawlessly. I eventually found a work around to get the channels in MythTV.

---

### Post by tominto on 2015-04-08
thanks for the info.  Recompiling the kernel looks tricky, so Ill just wait until the drivers are released.

---

### Post by sblack55 on 2015-04-24
> **AFriendlyNerd said:**
> I was just going to check in!

Steven Toth has submitted a driver to the LinuxTV.org brains. But it is not merged into the official driver package yet.

If you are something of a whiz, you can head over to their media_build tree and compile it yourself. But this process requires using an experimental kernel, I'm told. I like my nice, stable media center so I'm waiting until they merge with the new driver. I'm told this is a couple of weeks away, because they are still finalizing some things with Mr. Toth.

I will update this thread when I become aware of the new drivers being merged.

I have a few questions as I breathlessly await the availability of this driver:

[LIST=1]
[*]Any updates (as it closes in on three weeks since the "couple of weeks" prognostication)?
[*]When you say "merged into the official driver package", is that different than merging into a new kernel?
[LIST=1]
[*]If so, how would I obtain the driver package and install it on my 14.04 LTS system?
[/LIST]

[*]Once a new kernel is released how to I obtain it and install it on my 14.04 LTS system?
[/LIST]

(You can tell that my Linux experience is quite limited!)

---

### Post by AFriendlyNerd on 2015-04-26
Same here, Sblack555.

I was told today, April 26th, "not quite there yet....likely merged next week". 

I am Linux-challenged to be sure. I believe that the model number will be listed on one of these pages, though I'm not 100% sure. I've just been bugging people with emails and chat messages:
[http://git.linuxtv.org/cgit.cgi/media_tree.git/](http://git.linuxtv.org/cgit.cgi/media_tree.git/)
[http://git.linuxtv.org/cgit.cgi/mchehab/media-next.git/](http://git.linuxtv.org/cgit.cgi/mchehab/media-next.git/)

I'm not sure about the best way to install, but when it's released, I intend to ask. It might be this: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by sblack55 on 2015-04-26
Thanks AFriendlyNerd.  I'll keep holding my breath.  I might decide to pursue that build/install process since I also have a 955Q for which the driver IS available.  One tuner would be better than none!  I'll let you know how it goes... if I can overcome the jitters.

---

### Post by sblack55 on 2015-04-26
Just screwed up my courage and went through the build/install process.  All was very straightforward and trouble-free.  Just didn't get anything new for either 2255 OR 955.  Back to breath-holding.  One note for future reference.  On the build instructions page it says you will need the kernel-source or kernel-headers packages.  This actually translates to linux-headers-$(uname -r): 'sudo apt-get install linux-headers-$(uname -r)'

---

### Post by AFriendlyNerd on 2015-05-11
According to the LinuxTV people, it's now merged and can be compiled from mediatree.  [http://linuxtv.org/wiki](http://linuxtv.org/wiki) I am still a struggling n00b with these things, but will endeavor to install as soon as I have time. Any guidance would be appreciated! I will report my experience.

---

### Post by sblack55 on 2015-05-11
I've just obtained and built the tree without any problems.  It is not loading the driver for me though.  I think I've got something screwed up and I'll have to figure out how to get back to square one before I can move forward.

I followed the basic obtain & build instructions to the letter and the process was perfectly smooth, so I don't anticipate you having any problems.  The only caveat is what I noted previously about getting the headers/source.

---

### Post by sblack55 on 2015-05-14
I've gotten a clean Kodibuntu installed on a separate machine, and I hope to get the drivers built there soon (tonight?).  This machine only has the 955Q device, but getting that to work will be a good sign that all is go for the 2255.

One thing I noticed in the log after my earlier builds was a number of messages about "experimental media stack" being back-ported to an older kernel and not being good enough for production use.  I suspect that may be a standard result of building directly from the git tree.  I have found that both of the new devices seem to be supported in the 5/11 driver tarball at [http://www.linuxtv.org/downloads/drivers/]("http://www.linuxtv.org/downloads/drivers/linux-media-2015-05-11-4c0a65a.tar.bz2")[linux-media-2015-05-11-4c0a65a.tar.bz2]("http://www.linuxtv.org/downloads/drivers/"), so I intend to play around with building from that instead of directly from git.  That might slow me down.

Please advise if you have any thoughts on the subject.

---

### Post by sblack55 on 2015-05-15
> **sblack55 said:**
> I've gotten a clean Kodibuntu installed on a separate machine, and I hope to get the drivers built there soon (tonight?).  This machine only has the 955Q device, but getting that to work will be a good sign that all is go for the 2255.

One thing I noticed in the log after my earlier builds was a number of messages about "experimental media stack" being back-ported to an older kernel and not being good enough for production use.  I suspect that may be a standard result of building directly from the git tree.  I have found that both of the new devices seem to be supported in the 5/11 driver tarball at [http://www.linuxtv.org/downloads/drivers/]("http://www.linuxtv.org/downloads/drivers/linux-media-2015-05-11-4c0a65a.tar.bz2")[linux-media-2015-05-11-4c0a65a.tar.bz2]("http://www.linuxtv.org/downloads/drivers/"), so I intend to play around with building from that instead of directly from git.  That might slow me down.

Please advise if you have any thoughts on the subject.
Success, sorta...

I built from the git tree on the new Kodibuntu box according to the instructions.  (There seemed to be some pieces missing from the downloaded tarball so I couldn't figure out how to build that.)  The drivers built fine, and the log included messages indicating correct identification and initialization of my 955Q device.  The "experimental" messages remain, but I didn't notice anything that looked like a problem.

Unfortunately I'm having trouble getting tvheadend configured, so I can't actually connect to and configure the device.  I also went through the whole process on the production htpc with the 2255, but it still fails to recognize the device.  I'm going to have to reinstall from scratch there, but it will take a while to get to that.

---

### Post by sblack55 on 2015-05-15
> **sblack55 said:**
> Success, sorta...
Unfortunately I'm having trouble getting tvheadend configured, so I can't actually connect to and configure the device.  I also went through the whole process on the production htpc with the 2255, but it still fails to recognize the device.  I'm going to have to reinstall from scratch there, but it will take a while to get to that.
Got tvheadend working after getting it from the correct repository instead of the one bundled in kodibunu.  Attached the 955Q to usb and it was automatically recognized and configured.  Had to restart kodibuntu (or, more accurately, tvheadend) before the adapter was seen there though.  Now all appears to be normal in the new kodibuntu install.  The production box will have to wait until later next week as this weekend is already jam packed.

---

### Post by sblack55 on 2015-05-18
Got the production box rebuilt with the latest driver tree.  The log looks cleaner than before, and it does include messages identifying the 2255 card.  However, errors are reported in loading the firmware and tvheadend is unable to see the card.  I need to review the log messages in more detail to see if I can identify the specific firmware problem.

---

### Post by sblack55 on 2015-05-18
Found these messages in my log:
```

[   12.412911] saa7164_downloadfirmware() no first image
[   12.412921] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   12.422726] device-mapper: multipath: version 1.6.0 loaded
[   12.480209] saa7164 0000:03:00.0: Direct firmware load failed with error -2
[   12.480212] saa7164 0000:03:00.0: Falling back to user helper
[   13.079859] saa7164_downloadfirmware() Upload failed. (file not found?)
[   13.079863] Failed to boot firmware, no features registered

```

Found the following statements (regarding 2250 in 2013) in [http://ubuntuforums.org/showthread.php?t=2113099](http://ubuntuforums.org/showthread.php?t=2113099):
> 
I am having problem to fully load the firmware of Hauppauge  2250 card. I have compiled the driver for both firmware:  v4l-saa7164-1.0.3-3.fw and NXP7164-2010-03-10.1.fw. Both firmware files  are in /lib/firmware.

 dmesg only shows it was loading NXP7164-2010-03-10.1.fw.


I cannot find either of these firmware files, or anything like, anywhere on my filesystem, or in the linuxtv.org firmware download.  I've no idea where to turn at this point.

---

### Post by Keith_Helms on 2015-05-19
Try

[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

and

[http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/)

---

### Post by sblack55 on 2015-05-19
> **Keith_Helms said:**
> Try

[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

and

[http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/)

Oh, excellent... that's the best forum response performance I've ever seen!  Thank you Keith_Helms.  

Now I'll have to get sick so I can go home and try it out.  <cough/> <cough/>

---

### Post by sblack55 on 2015-05-19
Bingo!

Now getting the following messages in the log (though not all contiguous):
```
[   14.130375] saa7164 driver loaded
[   14.131230] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
[   14.131234] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[   14.131264] saa7164 0000:03:00.0: irq 47 for MSI/MSI-X
[   14.288601] saa7164_downloadfirmware() no first image
[   14.288613] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   15.013692] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   15.013695] saa7164_downloadfirmware() firmware loaded.
[   15.013697] Firmware file header part 1:
[   15.013698]  .FirmwareSize = 0x0
[   15.013700]  .BSLSize = 0x0
[   15.013701]  .Reserved = 0x3d538
[   15.013702]  .Version = 0x3
[   15.013703] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   15.013710] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   15.013711] saa7164_downloadfirmware() BSLSize = 0x0
[   15.013712] saa7164_downloadfirmware() Reserved = 0x0
[   15.013713] saa7164_downloadfirmware() Version = 0x1661c00
[   21.874400] saa7164_downloadimage() Image downloaded, booting...
[   21.978369] saa7164_downloadimage() Image booted successfully.
[   21.978386] starting firmware download(2)
[   24.705562] saa7164_downloadimage() Image downloaded, booting...
[   26.473048] saa7164_downloadimage() Image booted successfully.
[   26.473061] firmware download complete.
[   26.518164] tveeprom 6-0000: Hauppauge model 151061, rev B2I6, serial# 4035657296
[   26.518166] tveeprom 6-0000: MAC address is 00:0d:fe:8b:3e:50
[   26.518167] tveeprom 6-0000: tuner model is SiLabs Si2157 (idx 186, type 4)
[   26.518169] tveeprom 6-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   26.518170] tveeprom 6-0000: audio processor is SAA7164 (idx 43)
[   26.518171] tveeprom 6-0000: decoder processor is SAA7164 (idx 40)
[   26.518172] tveeprom 6-0000: has radio, has IR receiver, has no IR transmitter
[   26.518173] saa7164[0]: Hauppauge eeprom: model=151061
[   26.674797] si2157 6-0060: Silicon Labs Si2147/2148/2157/2158 successfully attached
[   26.675176] DVB: registering new adapter (saa7164)
[   26.675179] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   26.712973] si2157 7-0060: Silicon Labs Si2147/2148/2157/2158 successfully attached
[   26.713354] DVB: registering new adapter (saa7164)
[   26.713358] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   26.713697] saa7164[0]: registered device video0 [mpeg]
[   26.948257] saa7164[0]: registered device video1 [mpeg]
[   27.159258] saa7164[0]: registered device vbi0 [vbi]
[   27.159303] saa7164[0]: registered device vbi1 [vbi]
[   78.407952] si2157 6-0060: found a 'Silicon Labs Si2157-A30'
[   78.437615] si2157 6-0060: firmware version: 3.0.5

```

tvheadend sees the card and successfully scans muxes and finds services.  Haven't gotten as far as actually seeing video as tvheadend seems to be a bear with very outdated documentation.  But as far as I can tell the driver is working just fine.

Here are the complete instructions I followed:
```

In any folder:
[LIST]
[*]sudo apt-get install linux-source-$(uname –r)
[*]sudo apt-get install libdigest-sha-perl
[*]sudo apt-get install make gcc git patch patchutils
[*]sudo apt-get install libproc-processtable-perl
[/LIST]

In ~ folder:
[LIST]
[*]git clone –depth=1 git://linuxtv.org/media_build.git
[*]cd media_build
[*]./build
[*]sudo make install
[/LIST]

In /lib/firmware folder:
[LIST]
[*]sudo wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
[*]sudo wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
[/LIST]

```

---

### Post by AFriendlyNerd on 2015-05-24
I'm grateful for your reports, all.

I mimicked your instructions with two exceptions:
1:
```

[LIST]
[*]git clone &#8211;depth=1 git://linuxtv.org/media_build.git
[/LIST]

```

changed to:

```

[LIST]
[*]git clone git://linuxtv.org/media_build.git --depth=1
[/LIST]

```

(not sure if the fix was moving depth to the end or using two short dashes -- instead of the long dash [COLOR=#000000][FONT=Ubuntu Mono]&#8211;[/FONT][/COLOR] in your code

2. Reboot was necessary for TVHeadend to see my card.

Now I just have to test it. I guess I need to attach an antenna and hope :p

---

### Post by AFriendlyNerd on 2015-05-24
I have a question. I went from having nothing available in the TVHeadend input box to having 4 things:

[ATTACH=CONFIG]262195[/ATTACH]
Well, which of these four options should I use? I guess I can experiment...

---

### Post by sblack55 on 2015-05-25
A) The long dash was the problem - I think Word converted it without my noticing
B) Yes, a reboot is required.  Sorry I left that bit out.
C) TVH is a BEAR to configure.  And version 3.4, which is pre-installed with Kodibuntu, is completely unusable as far as I am concerned.  We probably need another thread to discuss that in, but let me get you started with this:

[LIST]
[*]sudo apt-add-repository -r [http://ppa.launchpad.net/adamsutton/tvheadend](http://ppa.launchpad.net/adamsutton/tvheadend)
[*]curl [http://apt.tvheadend.org/repo.gpg.key](http://apt.tvheadend.org/repo.gpg.key) | sudo apt-key add -
[*]sudo apt-add-repository [http://apt.tvheadend.org/unstable](http://apt.tvheadend.org/unstable)
[*]sudo apt-get update
[*]sudo apt-get install tvheadend
[/LIST]

That will get 3.9 installed.  I need some time to record the lengthy configuration instructions I've worked out.  I'll get them to you soon.

---

### Post by sblack55 on 2015-05-25
Here is my procedure for TVH configuration, minus EPG.  Give this a try and see how it works for you.  I've gone through it several times and often had varying results.  This is as close as my memory can get me to what I did the last time through (last night and this morning) that seems to be working.  EPG introduces a few more wrinkles, so hopefully this will get you started and we can add the rest later.

Connect to tvheadend service with url [http://<server-ip-addr>:9981]("http://%3cserver-ip-addr%3e:9981/")

[LIST=1]
[*]Select Configuration (top tab row)
[LIST=1]
[*]Select General (second tab row)
[LIST=1]
[*]Highlight language in Available list
[*]Double-click language or click right-arrow button to add to Selected list
[*]Press Save configuration
[/LIST]

[*]Select Access Entries (second tab row)
[LIST=1]
[*]Click add
[LIST=1]
[*]Enter username & password
[*]Set network prefix to your private network (192.168.0.0/12)
[*]Check all access levels
[*]Set Streaming Profile to htsp
[*]Press Save
[/LIST]
[/LIST]

[*]Select DVB Inputs (second tab row)
[LIST=1]
[*]Select Networks (third tab row)
[LIST=1]
[*]Click Add
[LIST=1]
[*]Select the type of network to add
[*]Enter a name for the network
[*]Set Pre-defined Muxes to the appropriate value (us-ATSC-center-frequencies-8VSB)
[*]Set Character Set to AUTO
[*]Leave all others as default
[*]Press Create
[/LIST]
[/LIST]

[*]Select TV adapters (third tab row)
[LIST=1]
[*]Select a tuner frontend (In the adapter tree, the bottom level represents the tuner frontends to be configured)
[LIST=1]
[*]Check Enabled
[*]Uncheck Over-the-air EPG if you have another source of EPG information  (tvheadend doesn’t handle ATSC OTA EPG very well, if at all)
[*]Select the desired network(s) from the Networks drop-down
[*]***Select another frontend from the same card in the Linked Input drop-down (Uncertain how to use this.  It is supposed to ensure paired tuners are powered on together.)
[*]Press Save
[/LIST]

[*]Repeat for remaining tuners until all tuners are configured
[/LIST]
[/LIST]
[/LIST]

[*][COLOR=#696969][EDIT: ignore this step as it applies to channel mapping, not mux scanning]Select Status (top tab row)[/COLOR]
[LIST=1]
[*][COLOR=#696969]Monitor progress until all muxes have completed scanning[/COLOR]
[/LIST]
[COLOR=#696969][/COLOR]
[*]Select Configuration
[LIST=1]
[*]Select DVB Inputs (second tab row)
[LIST=1]
[*]Select Services
[LIST=1]
[*]Press Map All
[/LIST]
[/LIST]

[*]Select Channel / EPG (second tab row)
[LIST=1]
[*]Select Channels (third tab row)
[LIST=1]
[*]Review available channels
[/LIST]
[/LIST]
[/LIST]
[/LIST]
Hopefully you will now see your channels listed here.  At this point, configuring the TVH addon for Kodi should allow you to tune your channels and watch TV on Kodi.  The episode guide will not be populated yet, unless you chose OTA EPG on you tuners for a non-ATSC implementation.  Configuring the episode guide with non-OTA information may require several additional steps and will be described separately.

---

### Post by sblack55 on 2015-05-27
There's a very good guide here: [http://forum.kodi.tv/showthread.php?tid=182556](http://forum.kodi.tv/showthread.php?tid=182556), including EPG instructions.  It's a little old and HDHomeRun-specific, but if your starting somewhere it the TVH portion, it should be helpful.

---

### Post by tominto on 2015-12-09
I haven't checked on this thread in a while.  I have a 2255 installed, but unable to use it.  I thought I'd wait and look for official installation instructions.  Hauppauge website now has this [http://www.hauppauge.com/site/support/install_ubuntu14_04_2-kernel-3.16.txt](http://www.hauppauge.com/site/support/install_ubuntu14_04_2-kernel-3.16.txt)  Does this work well?  Can I apply this to a more recent kernel?

---

### Post by singogli on 2016-01-02
It did not work well for me.  After following all the instructions everything appears to work fine for a while.  Soon the entire system will hang, sometimes minutes sometimes hours, always overnight.  var/log/kern.log will reveal a continuous stream of the following errors:  
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.304121] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368110] saa7164_cmd_send() No free sequences
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368121] saa7164_api_i2c_write() error, ret(1) = 0xc
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368127] i2c_write_bytes: i2c_write_bytes(): i2c transfer failed
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368132] silabs_tercab_get_signal: [4-0060] Si2177_L1_TUNER_STATUS() failed (err=3)
I used all of the versions of patches and firmware indicated in the document.  I have filed two support tickets with Hauppauge but not received any response.  They may be backlogged due to weather and the holidays.  Does anyone actually have an HVR-2255 working reliably with both tuners on Mythbuntu 14.04.3 ? Any suggestions to fix this?  If I get a response from Hauppauge I will post it here.

Update: iso labelled mythbuntu 14.04-2 installed as 14.04-3.  Checksum  does not verify as any known mythbuntu 14.04 release. This image was  originally downloaded from mythbuntu.org/downloads some time ago.  The  new links on that page currently download an iso whose checksum  verifies.  So I am starting over with a fresh mythbuntu install  and  will report results here.

---

### Post by tominto on 2016-01-03
I had other probblems with my last version of Ubuntu so I finally decided to upgrade to 15.10 with the newest kernel and it works perfectly.  Can't get fm though and analog (which would be nice, since I have vhs tapes I want to convert to .mpg's)

---

### Post by redmcg2 on 2016-01-29
> **singogli said:**
> It did not work well for me.  After following all the instructions everything appears to work fine for a while.  Soon the entire system will hang, sometimes minutes sometimes hours, always overnight.  var/log/kern.log will reveal a continuous stream of the following errors:  
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.304121] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368110] saa7164_cmd_send() No free sequences
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368121] saa7164_api_i2c_write() error, ret(1) = 0xc
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368127] i2c_write_bytes: i2c_write_bytes(): i2c transfer failed
Jan  2 11:09:52 mythbuntu64-2 kernel: [46900.368132] silabs_tercab_get_signal: [4-0060] Si2177_L1_TUNER_STATUS() failed (err=3)
I used all of the versions of patches and firmware indicated in the document.  I have filed two support tickets with Hauppauge but not received any response.  They may be backlogged due to weather and the holidays.  Does anyone actually have an HVR-2255 working reliably with both tuners on Mythbuntu 14.04.3 ? Any suggestions to fix this?  If I get a response from Hauppauge I will post it here.

Update: iso labelled mythbuntu 14.04-2 installed as 14.04-3.  Checksum  does not verify as any known mythbuntu 14.04 release. This image was  originally downloaded from mythbuntu.org/downloads some time ago.  The  new links on that page currently download an iso whose checksum  verifies.  So I am starting over with a fresh mythbuntu install  and  will report results here.

I had a very similar problem to this - it could be the same root cause. I found a solution for my problem and submitted a patch to linux-media which is now included within Kernel v4.2. The patch can be found here: [https://github.com/torvalds/linux/commit/77978089ddc90347644cc057e6b6cd169ac9abd4](https://github.com/torvalds/linux/commit/77978089ddc90347644cc057e6b6cd169ac9abd4)

Mythbuntu 14.04.3 runs Kernel v3.19 - so with this version you'd need to manually apply this patch and rebuild the saa7164 driver. I run Ubuntu 14.04.3 so that's the solution I take. 

The good news is Ubuntu 14.04.4 (and presumably Mythbuntu 14.04.4) will run Kernel v4.2. According to [https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule) - the release date is February 18th. However - the LTS package appears to already be available.

So I guess you have three options:
1. Rebuild the driver (as I do - and can confirm works)
2. Wait for Mythbuntu 14.04.4 (not sure how long Mythbuntu takes to follow a Ubuntu release - but Ubuntu 14.04.4 is due Feb 18)
3. Or try upgrading the Wily LTS package with Mythbuntu 14.04.3 ([FONT=courier new]apt-get install linux-generic-lts-wily[/FONT])

Keep in mind with option 3 that this package is not yet officially supported and that the [FONT=courier new]xserver-xorg-core-lts-wily package[/FONT] (and friends) do not appear to be available yet. However - if you do choose this option - the following link provides some good instructions for upgrading the LTS stack: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by reubenbrown13 on 2016-02-19
I just tried to setup a Hauppauge 1255 using the wily 4.2 kernel on Trusty 14.04.3 and it didn't recognize it after reboot.  I have the drives in the /lib/firmware folder.  I have followed the steps to patch the 3.16 kernel but am waiting to reboot till my shows are done recording for tonight.  If anyone has gotten this device to work w/ the 4.2 kernel, I would be VERY interested to hear what else needs to be done.

---

### Post by bilkay on 2016-04-24
According to this:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255)
[h=1]Hauppauge WinTV-HVR-2255[/h] 			 								 								 												 					Jump to:					[navigation]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255#mw-navigation"), 					[search]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255#p-search") 				
 				An [ATSC]("http://www.linuxtv.org/wiki/index.php/ATSC") [PCIe card]("http://www.linuxtv.org/wiki/index.php/ATSC_PCIe_Cards") from [Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge"). Also supports ClearQAM cable TV. 
It is supported under Linux since kernel 4.2. (Note: Analog support is not implemented yet).

---

### Post by bilkay on 2016-04-24
> **bilkay said:**
> 

It is supported under Linux since kernel 4.2. (Note: Analog support is not implemented yet).

Running Mythbuntu 14.04.4 and kernel 3.16.0 (patched) (3.13.0-83 supported), what's the procedure for switching to the 4.2 series kernels and getting automatic updates?

---

