---
title: "Hauppauge HVR-1600 Analog Tuner Issues"
date: 2010-06-01
forum: Mythbuntu
---

### Post by TwiztedMatt1007 on 2010-06-01
Before I get started, I want to say I have already confirmed the hardware and current setup are good by installing Windows 7 and the default software that came with the card. Both the analog and digital tuners worked perfectly. This issue only comes up in Linux and MythTV. I will go into what I have already tried at the later. Also, my experience with Linux is extremely limited so, if you do decide to help me, and I sure hope you do, I will need the special ed version of it. Aka, step by step or codes I can just copy and paste. The only reason I care about the Analog side is we only have Extended Basic Cable so, most of my channels are analog.

My issue is the analog tuner of my Hauppauge HVR-1600 is not working in MythTV. I have followed the complete instructions [**_here_**]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") yet the issue still persists. I also tried to follow the remote guide linked to on that page but was lost on part 3 nor did I understand what he meant by "update your kernel" in part 2 however, that is not something I am concerned with at the moment.

What happens is the screen displays either a red or black screen when I try to view an analog channel with "Watch Live TV." I have done channel scans and do not receive a lock on any analog channel either. I manually put in the channel as I am not a subscriber to Schedules Direct. I don't know the frequencies so I just put in the channel number. Remember, this EXACT same set up works in Windows with the default software. I have also moved the system to a different room just to be sure that somehow my current setup affected MythTV differently than it effected Windows and the default software but, it made no difference. In the other room it ran from the wall, to one splitter, then to my system.

What I have done to try and remedy this problem has been multiple reinstalls of Ubuntu 10.04 64-bit, I believe I have also installed the 32-bit versions but, as I have been doing a lot over this week, I do not recall. I have also tried Mythbuntu but, it lacks the audio settings I need to get audio over HDMI unless I install the Ubuntu Desktop as well. I also tried installing some other variants of bundled MythTV with an OS to no avail. I have done many Google searches and tried many different "solutions" to this problem. Most of which resulted in nothing good happening and needing to reformat since I had no idea how to undo what I had done. As it currently stands, I have downgraded from MythTV .23 and Ubuntu 10.04 to MythTV .21 and Ubuntu 8.04 and still no change to this issue. Please help!



My System:

Motherboard: GIGABYTE GA-MA785GM-US2H Version 1.1 Using the integrated graphics with ATI proprietary drivers. The integrated graphics is a Radeon HD 4200.

Tuner Card: Hauppauge HVR-1600

Ram: 2GB A-DATA AD2U800B1G5-DRH

Processor: 2.9GHz Athlon II X3 ADX435WFGIBOX

New Current OS: Mythbuntu 10.04 64-bit with MythTV .23

Old Current OS: Ubuntu 8.04 (Hardy) with MythTV .21

Prior OS (That I would like to get back to): Ubuntu 10.04 with MythTV .23

I thank those of you for your help ahead of time. I have been struggling with this myself for over a week and I hope someone with more knowledge can help me solve this issue.

---

### Post by klc5555 on 2010-06-01
One main problem is the cx18 driver that the HVR-1600 uses.

Support with a reasonably functional version of this driver was  added to the Linux 2.6.26 and subsequent kernels. So Mythbuntu 8.04 with kernel 2.6.24-16 is simply too old, unless you want to compile the driver yourself. You'll need a 9.04 release or later to get usable analog support for this card out-of-the box. 

The digital side of this card has some signal-strength issues with the cx18 driver. A patched version of the cx18 driver correcting much of this has reportedly begun to be incorporated with 2.6.33 kernels. Unfortunately Ubuntu 10.04 was back-leveled to 2.6.32, so if you eventually find 1600 digital not quite satisfactory on 10.04, you may still be compelled to do a bit of compiling/upgrading work.

Another potential problem that you may run into are the ATI Radeon graphics. Proprietary driver support from ATI for their cards for Linux is simply not as good as NVidia's is, which is why NVidia is more popular for Mythtv users. Moreover, there is a Radeon display bug on Mythfrontend that specifically bites default 9.10 installs, so when choosing a more contemporary version of Mythbuntu than 8.04 for your HVR-1600/ATI system, you may have fewer initial headaches with either 9.04 or 10.04.

Third, when setting up the analog side of your HVR-1600 card in the mythbackend setup Capture Cards, there is one trick you may need to be aware of. The analog side of the card is a MPEG2 encoder card. However, if you initially try to set up the card as type "MPEG2" the card will not be detected properly and you'll generally get a "failed to open card" error message. You need to _first_ configure the card as a regular "V4L Analog" and save this. Then, immediately reopen the analog card settings that you just saved, and change the card type to "MPEG2". _Now_ the card will be correctly detected as MPEG2, you can save this, proceed to scanning, etc.

If you have left your analog 1600 as a standard "V4L Analog", it will not scan or work properly. Has to be MPEG2. 

Once the channels have been added, by scan or manually from channel editor (your way should have worked), and the backend has been started you should be able to fire up "Watch Live TV", if there are analog channels to watch.

If the analog video works fine, but the audio is missing or degraded, that's a small problem that can be dealt with later.

---

### Post by LowSky on 2010-06-01
ATI graphics are fine on 9.10...  I'm currently using 9.10 with an ATI HD4550

---

### Post by klc5555 on 2010-06-01
> **LowSky said:**
> ATI graphics are fine on 9.10...  I'm currently using 9.10 with an ATI HD4550

My bad, faulty memory. The famous Radeon bug was a feature of 9.04. 

9.10 and 10.04 should be OK. TwiztedMatt1007 should go with one of these two versions to properly support his HVR1600 analog in the presence of ATI Radeon graphics.

---

### Post by ryry46d9 on 2010-06-01
I just picked up a hvr-1600 (just the card) and got it going by doing the following:

```
* Configure the analog half of the card like a supported MPEG-2 Encoder PVR-150 card. Treating the analog half of the card as an ivtv based card in MythTV works as the cx18 driver is heavily based on (i.e. cut and pasted from) the ivtv driver. 

   1. Under Card type, choose IVTV MPEG-2 encoder (or MPEG-2 encoder card (PVR-x50, PVR-500)). Do not select Analog V4L capture
   2. Choose the correct video device (usually /dev/video0 unless there is more than one card). Note: if the video device is not listed and a could not open to probe its inputs message appears, add /dev/video0 manually
   3. Probed info should populate with Hauppauge HVR-1600 [cx18]
   4. To use NTSC RF from an antenna or cable TV provider, choose 'Tuner 1' under Default input
   5. Select Finish.
```

This worked with Mythbuntu 8.10 and currently under Ubuntu 10.04

I set up the digital side of the card under Mythbuntu, but I have no real use for it at this time since I'm using a cable box.

---

### Post by klc5555 on 2010-06-02
> **ryry46d9 said:**
> I just picked up a hvr-1600 (just the card) and got it going by doing the following:

```
* Configure the analog half of the card like a supported MPEG-2 Encoder PVR-150 card. Treating the analog half of the card as an ivtv based card in MythTV works as the cx18 driver is heavily based on (i.e. cut and pasted from) the ivtv driver. 

   1. Under Card type, choose IVTV MPEG-2 encoder (or MPEG-2 encoder card (PVR-x50, PVR-500)). Do not select Analog V4L capture
   2. Choose the correct video device (usually /dev/video0 unless there is more than one card). Note: if the video device is not listed and a could not open to probe its inputs message appears, add /dev/video0 manually
   3. Probed info should populate with Hauppauge HVR-1600 [cx18]
   4. To use NTSC RF from an antenna or cable TV provider, choose 'Tuner 1' under Default input
   5. Select Finish.
```

This worked with Mythbuntu 8.10 and currently under Ubuntu 10.04

I set up the digital side of the card under Mythbuntu, but I have no real use for it at this time since I'm using a cable box.

8.10 came with the cx18 driver, but the version it had still suffered from the the "corrupted first analog capture after boot" bug (described in the wiki page), which wasn't patched at V4L until sometime in Jan 2009. The version in 10.04 doesn't particularly suffer from this, but may not include the latest digital patches. 

The trick I described earlier for adding the analog 1600 was a substitute for needing to add /dev/video0 manually in your note to step 2 above.

---

### Post by ryry46d9 on 2010-06-02
yeah like the OP I just needed analog so far she's good. even had a few reboots,  but I am sad that I can't stream to 2 or more devices like I could with windows MCE.

---

### Post by TwiztedMatt1007 on 2010-06-02
**Current Status** I have no idea what is causing this issue to be honest. The DVR worked fine this morning, I just changed from loading AMD graphics to using open source and that seemed to do it, but, now, later in the day, it is not working. Only difference between then and now is everyone is using the internet. I will try to test later on if this is indeed the case. Suffice it to say, from being elated this morning and having it work to it dieing and now no longer working, yeah, not exactly happy.

All the configuration data has been correct since the beginning. Also, to clarify, the digital side works perfectly and I have no complaints. I also do not have a set top box so the IR blaster is not a concern at the moment. Only extended basic cable here which is why I need the analog side to work. I have started looking into getting a different card as well so I could test to see if I would have better results. Below is what I had to do to get everything working in MythTV when the DVR worked this morning. I also signed up for a trial of Schedules Direct to see if that would make any difference, answer, not really. The analog scanner somewhat works though. It picked up most of my channels even though it said it failed. A final note, I am now running Mythbuntu 10.04 64-bit with MythTV .23 as per basically everyones suggestion.

**Getting ATI Drivers working:** NOW, to get the proprietary ATI drivers working that can be download from the hardware drivers link. I had to go into my MythTV Front End and follow these instructions from a fellow MythTV user who also bought this motherboard on Newegg:

MythTV Frontend Utilities/Setup->Setup->TV Settings->Playback-> then to the third page and set the "Current Video Playback Profile" to "Normal."

Gukin, as he is called, was running an older setup though, I have found I can either run Normal, High Quality, or Slim. If I try to run any of the CPU types, I get a double vision thing going on with the screen. The screen gets split in half from left to right and the show is played in its entirety on both the top and bottom half. While I love my shows, I have no desire to watch them in stereo.

**HDMI Audio:**Thanks to an awesome guide from Nick (foxbuntu) I was able to get the HDMI audio working for MythTV. The guide is as follows:

From a terminal: ```
aplay -l
```
      - This will provide several audio playback devices, one will be easily be the HDMI port, similar to this:
         -
         - *card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]*
         - The important parts are the card and device numbers, keep track of these
      - Test audio out on the device like this: ```
speaker-test -Dplughw:0,3
``` (notice the format <card number>,<device number>)
      - If the HDMI port is plugged in and working, you should get a static noise, you can press CTRL+C to stop it
         - In the event this does not work, you need to make sure the HDMI port is not muted
            - At a terminal: ```
alsamixer
```
            - Use the Left/Right arrows to navigate across the bottom of the screen, ensure any devices label S/PDIF or IEE* show a "00"  and not "MM", if they show "MM" you can type M to unmute them. To save and exit, use the ESC key. At this point retry your testing above.
         - In the MythTV Frontend, navigate the menus below:
         - Utilities / Setup > Setup > General > Page 4 (Audio System)
            - Audio output device: ALSA:plughw:0,3 (in the case of my system, the device and/or card numbers could be different
in your case)
            - Click Next/Finish until you exit the menu. This will allow HDMI audio to work on your MythTV system.


I still need to get the remote working however. Once again, I tried following this guide that was linked to on the MythTV wiki:  [http://www.uluga.ubuntuforums.org/showpost.php?p=8257616&postcount=27](http://www.uluga.ubuntuforums.org/showpost.php?p=8257616&postcount=27) but I am lost at step 1 and 3. I have already updated to the newest drivers already so, I don't have to redo step 2.

Also, I am having the known audio issue that causes there to be no audio playback on analog channels. I have tried "sudo rmmod cx18" and "sudo modprobe cx18" however, every time I "sudo rmmod cx18" it tells me something else is using it and it cannot be terminated at this time. How would I go about disabling

Last thing I need to get set up in the system is get audio over HDMI for the entire system. That way I can stream videos from Firefox and such and have all audio through HDMI. I know I can do this in Ubuntu by simply right clicking the speaker icon in the system tray and changing the preferences but, I cannot do that in Mythbuntu. How would I go about setting this up?

---

### Post by TwiztedMatt1007 on 2010-06-03
Alright, the issue is the cx18 driver itself. If I have no picture I can  rmmod modprobe it. The other part of it was indeed the AMD graphics  drivers I could have installed at startup so, first, I install the open  source drivers, then if I have no picture I just rmmod then modprobe  cx18.

I have an issue with that however. Since updating to the newest drivers  via the tutorial on  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers) every time I "sudo  rmmod cx18" I get this error: "ERROR: Module cx18 is in use by  cx18_alsa" How do I stop alsa from using the driver so I can rmmod it?  Also still failing at getting the remote to work and hdmi audio for the  system as a whole in Mythbuntu 10.04.

---

### Post by klc5555 on 2010-06-04
Usually if you're stuck on a dependent module, you have to rmmod that one first, then rmmod the main module, i.e. rmmod cx18_alsa then rmmod cx18. When you then modprobe cx18, the dependent module loads as well.

If you find that the cx18 non-function issue only happens after a boot, and that one time through the rmmod/modprobe ritual always enables cx18 functionality, then you may wish to consider incorporating the rmmod/modprobe commands (without sudo) into the /etc/rc.local file which executes at boot. I have a secondary backend that uses two of these HVR1600 cards to capture analog from a pair of Comcast DTAs, and I ended up using this method to get the cards to start up reliably at boot.

Can't help you with the remote issue, since of the about forty eleven versions of the 1600 card extant, mine don't include reliable blaster support for the DTAs, so I use a 3rd-party blaster from Iguanaworks.

---

### Post by lglenn on 2010-06-06
Hi all:

I am having trouble somewhat along the same lines; I can't get the analog half of my new Hauppauge PVR 1600 to work -- I am just getting static in the picture. The digital (ATSC) input works fine.  

I am running Mythbuntu 10.04, the output of uname -a is "Linux myth 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:17:36 UTC 2010 i686 GNU/Linux". Analog capture had been working on the system before, with an aging, ailing PVR 150 which I intended to replace with the 1600 (there were other, unrelated issues with the 150 which drove the replacement, and which are neither interesting nor funny, so I won't go into them here).  

When setting up the new card, I followed the instructions on the MythTV Wiki's [PVR 1600 page]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600"), including downloading, building, and installing the latest V4L drivers. I configured the analog half of the capture card as an IVTV MPEG-2 encoder card, using Tuner 1 as the default input. I have tried presetting the tuner to channels 3 and 4 in the Input Connection config, to no avail -- I just get static. I have removed every other capture card from the box, so there's no chance that I just stuck the cable in the wrong hole (and no, the cable is not in the ATSC input; it's in the top one, the analog input). I also tried taking Myth out of the picture entirely by stopping mythbackend and then running: 

mplayer -cache 8192 /dev/video0

...to play whatever the encoder card is recieving, and using:

ivtv-tune -t us-cable -c 3

...to set the channel. I tried various frequency tables with ivtv-tune (us-cable-hrc, us-cable-irc, us-bcast), and both channels 3 and 4 (the card is connected to cable-out on my set top box, and with my old analog enoder card, channel 3 worked, so there's no reason to think it'd be different, but I am trying everything). Same thing, just static.  

I am noticing, however, that when I change to a channel on the analog input in MythTV, I see the following message in mythbackend.log: 

```
Not ivtv or pvrusb2 or hdpvr driver

```

...which must be significant. The output of dmesg | grep cx shows this: 

```
[   26.791182] cx18:  Start initialization, version 1.4.0
[   26.791232] cx18-0: Initializing card 0
[   26.791238] cx18-0: Autodetected Hauppauge card
[   26.791381] cx18 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   26.791393] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   26.793069] cx18-0: cx23418 revision 01010000 (B)
[   27.037266] cx18-0: Autodetected Hauppauge HVR-1600
[   27.037268] cx18-0: tveeprom cannot autodetect tuner!
[   27.037270] cx18-0: Simultaneous Digital and Analog TV capture supported
[   27.146413] IRQ 20/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   27.650392] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   27.876755] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   28.130690] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   28.133691] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   28.133695] DVB: registering new adapter (cx18)
[   28.524562] cx18-0: DVB Frontend registered
[   28.524565] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   28.524599] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   28.524632] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   28.524660] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   28.524663] cx18-0: Initialized card: Hauppauge HVR-1600
[   28.524691] cx18:  End initialization
[   28.644036] cx18 0000:03:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   28.738818] cx18-alsa: module loading...
[   28.939765] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   28.978164] cx18 0000:03:06.0: firmware: requesting v4l-cx23418-apu.fw
[   29.219393] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   29.225765] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   29.432569] cx18 0000:03:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   29.646162] cx18 0000:03:06.0: firmware: requesting v4l-cx23418-apu.fw
[   30.013767] cx18 0000:03:06.0: firmware: requesting v4l-cx23418-dig.fw
[   30.228480] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   30.262183] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[ 8274.982150] cx18-0: Skipped encoder MPEG, MDL 61, 62 times - it must have dropped out of rotation
[ 9051.918618] cx18-0: Skipped encoder MPEG, MDL 15, 62 times - it must have dropped out of rotation

```

I believe this shows that the 1600 is being detected properly. I've found [some discussion]("http://www.gossamer-threads.com/lists/ivtv/devel/40944") about those last two messages about skipping the encoder, and I don't believe that they are related to my problem. But who knows. 

Can anyone shed any light on what might be happening here? I have a feeling that I am doing something mind-numbingly stupid, causing me to miss the glaringly obvious.  

Thanks!

---

### Post by matt06 on 2010-06-06
> **lglenn said:**
> I am running Mythbuntu 10.04, the output of uname -a is "Linux myth 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:17:36 UTC 2010 i686 GNU/Linux". Analog capture had been working on the system before, with an aging, ailing PVR 150 which I intended to replace with the 1600 (there were other, unrelated issues with the 150 which drove the replacement, and which are neither interesting nor funny, so I won't go into them here).
9.10 here ("Linux mythtv 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux") with Mythtv 0.22-fixes ("2010-06-06 16:27:46.088 mythbackend version: branches/release-0-22-fixes [23893] www.mythtv.org").  I have 2 PVR-1600s in my single backend.

> **lglenn said:**
> (the card is connected to cable-out on my set top box, and with my old analog enoder card, channel 3 worked, so there's no reason to think it'd be different, but I am trying everything). Same thing, just static.
I wouldn't think so either.  This is some type of analog STB I take it?  Static is a least *something*.  I'm not familiar with using ivtv-tune, but does the static flicker or change at all when changing channels?

> **lglenn said:**
> ```
Not ivtv or pvrusb2 or hdpvr driver

```

...which must be significant.
I don't remember seeing that message regularly in my backend logs, but since upgrading to -fixes I've been keeping a closer eye on them and now I see it all the time.  Live analog TV works fine on both tuners for me.

```
2010-06-06 18:44:00.264 adding: mythtv-bs as a client (events: 0)
2010-06-06 18:44:00.267 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-06-06 18:44:00.273 TVRec(1): HW Tuner: 1->1
2010-06-06 18:44:00.357

Not ivtv or pvrusb2 or hdpvr driver


2010-06-06 18:44:00.362 AutoExpire: CalcParams(): Max required Free Space: 5.0 GB w/freq: 15 min
2010-06-06 18:44:19.285 MainServer::ANN Playback
2010-06-06 18:44:19.286 adding: mythtv-bs as a client (events: 0)
2010-06-06 18:44:19.288 MainServer::HandleAnnounce FileTransfer
2010-06-06 18:44:19.291 adding: mythtv-bs as a remote file transfer
2010-06-06 18:44:19.798 RecBase(1:/dev/video0): GetKeyframePositions(376,9223372036854775807,#10) out of 36
2010-06-06 18:44:49.349 TVRec(1): Changing from Watching WatchingLiveTV to None
```

> **lglenn said:**
> ```
[   27.037268] cx18-0: tveeprom cannot autodetect tuner!
```

Your dmesg looks ok except here, I'm not seeing that line on my system.  The "Skipped encoder MPEG" message I *think* is just dropping frames or such?  More expertise needed than I have.

BTW, thanks for making me check my dmesg..it seems I'm now running v1.2.0 for some reason since my last batch of updates and reboot!? Arrrgggh!!  It could be the last kernel update and having to recompile the v4l drivers again.  Anyway, here's dmesg for both cards (no "tveeprom cannot autodetect tuner!").

```
[   15.893130] cx18:  Start initialization, version 1.2.0
[   15.893199] cx18-0: Initializing card 0
[   15.893205] cx18-0: Autodetected Hauppauge card
[   15.894314] cx18 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.894328] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[B][   15.896288] cx18-0: cx23418 revision 01010000 (B)
[   16.113935] cx18-0: Autodetected Hauppauge HVR-1600
[   16.113939] cx18-0: Simultaneous Digital and Analog TV capture supported[/B]
[   16.208420] IRQ 20/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.065752] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   17.528468] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   17.699505] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   18.172085] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   18.172092] DVB: registering new adapter (cx18)
[   18.331318] cx18-0: DVB Frontend registered
[   18.331324] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   18.331380] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   18.331428] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   18.331476] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   18.331523] cx18-0: Registered device radio0 for encoder radio
[   18.331528] cx18-0: Initialized card: Hauppauge HVR-1600
[   18.331563] cx18-1: Initializing card 1
[   18.331569] cx18-1: Autodetected Hauppauge card
[   18.335210] cx18 0000:02:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.335221] cx18-1: Unreasonably low latency timer, setting to 64 (was 32)
**[   18.336313] cx18-1: cx23418 revision 01010000 (B)**
[   18.356116] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-cpu.fw
[B][   18.552168] cx18-1: Autodetected Hauppauge HVR-1600
[   18.552171] cx18-1: Simultaneous Digital and Analog TV capture supported[/B]
[   18.644493] IRQ 22/cx18-1: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.654139] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #1-1)
[   18.657202] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #1-1)
[   18.659298] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #1-0)
[   18.663475] cx18-1: Registered device video1 for encoder MPEG (64 x 32 kB)
[   18.663482] DVB: registering new adapter (cx18)
[   18.707786] cx18-1: DVB Frontend registered
[   18.707792] cx18-1: Registered DVB adapter1 for TS (32 x 32 kB)
[   18.707848] cx18-1: Registered device video33 for encoder YUV (16 x 128 kB)
[   18.707898] cx18-1: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   18.707954] cx18-1: Registered device video25 for encoder PCM audio (256 x 4 kB)
[   18.708006] cx18-1: Registered device radio1 for encoder radio
[   18.708010] cx18-1: Initialized card: Hauppauge HVR-1600
[   18.708049] cx18:  End initialization
[   18.713211] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   19.469794] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.481666] cx18-1: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.506100] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-apu.fw
[   19.513488] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-apu.fw
[   19.852477] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   19.858656] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   20.069033] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   20.073952] cx18-1: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   20.080311] cx18-1: FW version: 0.0.74.0 (Release 2007/03/12)
[   20.202702] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-apu.fw
[   20.289033] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   20.426102] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-apu.fw
[   20.517745] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-dig.fw
[   20.738672] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-dig.fw
[   21.352504] cx18-1 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   21.371355] cx18-1 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   21.561753] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   21.580922] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
```

HTH.

---

### Post by TwiztedMatt1007 on 2010-06-06
> **klc5555 said:**
> Usually if you're stuck on a dependent module, you have to rmmod that one first, then rmmod the main module, i.e. rmmod cx18_alsa then rmmod cx18. When you then modprobe cx18, the dependent module loads as well.

If you find that the cx18 non-function issue only happens after a boot, and that one time through the rmmod/modprobe ritual always enables cx18 functionality, then you may wish to consider incorporating the rmmod/modprobe commands (without sudo) into the /etc/rc.local file which executes at boot. I have a secondary backend that uses two of these HVR1600 cards to capture analog from a pair of Comcast DTAs, and I ended up using this method to get the cards to start up reliably at boot.

Can't help you with the remote issue, since of the about forty eleven versions of the 1600 card extant, mine don't include reliable blaster support for the DTAs, so I use a 3rd-party blaster from Iguanaworks.

Ha, thanks. I feel kind of daft though. I tried to do just that on a prior install. I would stop the backend, rmmod cx18_alsa and it would not allow me, even with a sudo. Finally tried to force it out and, well, that wasn't the best idea. I also could still not rmmod cx18 as it would give me "ERROR: Module cx18 is in use by" but not say what it was being used by. Which is why I now have this install and, well, it works now so that is all that matters. Only difference between this install and the last, I didn't reinstall the firmware so, that may have something to do with it. I only updated the cx18 driver. As a note, alsa does not seem to use cx18 until AFTER I update it, but not before.

I wouldn't know how to add it to run at start up and the machine will not allow me to rmmod/modprobe either cx18 or cx18_alsa without sudo so, I guess I'm SoL in that regard. My startup ritual with this card is as follows:

1.) Turn on DVR.
2.) Make sure the TV is on or I will get no display.
3.) See if cx18 loaded properly.
4.) When it doesn't, shutdown the backend.
5.) rmmod cx18_alsa then cx18, then modprobe both in reverse order. (just to be sure)
6.) Check the frontend to see if I now have picture.
7.) When I don't have sound, I have to power off/on my TV so I can get sound.
8.) Finally start watching TV.

Might sound like a lot just to watch TV but, after the headache I've had the past two weeks trying to just get it to work, this is nothing. I'm sure in time it will get old but, for now, I'm just happy it works. One thing I was not happy about was in the [http://www.mythtv.org/wiki/File_storage](http://www.mythtv.org/wiki/File_storage) guide saying MythTV saved its files to /home/mythtv/tvstore which, for .23 at least, is no longer true. I have since moved it to the /home folder since I already have the HDD partitioned to give the bulk of my space to /home and XFS formatted. The default area .23 saves TV files to is /var/lib/mythtv Not a big deal to change the directories though. Just had to ensure the permissions for the folders were correct and I was in business.

As it currently stands, this is my status:

1.) Get system working at all. [OK] (Had to install opensource graphical drivers when I first installed Mythbuntu instead of the AMD ones.)

2.) Get audio for MythTV over HDMI. [OK] (Followed guide I posted earlier.)

3.) Be able to rmmod/modprobe cx18_alsa and cx18. [OK] (If I couldn't do this, the system would not work period.)

4.) Get the proprietary ATI drivers to work in MythTV [OKish] (I'm not using it at the moment because the screen will still have issues. I will get a horizontal split on the screen during fast movement scenes and the top half will lag behind the bottom half. Aka, if someone is moving their head from the left side of the screen to the right, the bottom half will move before the top half will. Only issue I have with the opensource driver is the screens outer edges are cut off as it seems to think my display is larger than it really is. I tried to find a scaling tool to make it fit but cannot. I just used the Wizard in MythTV to get it to fit properly. Doesn't help for watching full screen videos on YouTube though.)

Last things I need to accomplish to say I am completely done:

1.) Get HDMI audio for the entire system. I have set the mixer to HDA ATI HDMI (Alsa mixer), which I had to do to get audio for MythTV, but, still no audio for the rest of the system. I know I can easily do so in Ubuntu via right clicking the speaker icon and changing the preferences but, don't know of a way to do so in Mythbuntu as there is not speaker icon in the system tray. I assume there is some roundabout way to do so in the terminal but, have yet to find a guide on it.

2.) Get the remote working. I've tried the tutorial linked to at [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) and the other tutorials in the thread. But, I can either not understand them, they do not seem to work in Mythbuntu, or are not intended for 10.04.

---

### Post by klc5555 on 2010-06-08
> **TwiztedMatt1007 said:**
> H

I wouldn't know how to add it to run at start up and the machine will not allow me to rmmod/modprobe either cx18 or cx18_alsa without sudo so, I guess I'm SoL in that regard. My startup ritual with this card is as follows:

1.) Turn on DVR.
2.) Make sure the TV is on or I will get no display.
3.) See if cx18 loaded properly.
4.) When it doesn't, shutdown the backend.
5.) rmmod cx18_alsa then cx18, then modprobe both in reverse order. (just to be sure)
6.) Check the frontend to see if I now have picture.
7.) When I don't have sound, I have to power off/on my TV so I can get sound.
8.) Finally start watching TV.







The way I get the cx18 to work reliably on the machine where I have two 1600 cards is to have the following sequence at the end of my rc.local file (in mythbuntu at /etc/rc.local ; which doesn't use "sudo" or the equivalent as it executes with root privileges). I just assume the cx18 has misloaded at boot (which it would have done at least one time in three or four anyway).

rmmod cx18
sleep 5
modprobe cx18

and the cards work pretty much 100% of the time. If I had had a problem with a dependent module like cx18_alsa, I would have preceded the above with rmmod cx18_alsa (and maybe ended the sequence with modprobe cx18_alsa )

Now by way of full disclosure my machine having the two 1600s is a Slackware machine, which distro doesn't give a bleep if the backend is running or not when you do something like this, and where the backend loads after rc.local in a standard myth installation anyway. This may not work as well off the top in a mythbuntu box, where the backend appears possibly to load before rc.local, and which is more restrictive in what it allows the user to do without interference. Wouldn't take but five minutes to try though.

---

### Post by klc5555 on 2010-06-08
> **lglenn said:**
> Hi all:

I am having trouble somewhat along the same lines; I can't get the analog half of my new Hauppauge PVR 1600 to work -- I am just getting static in the picture. The digital (ATSC) input works fine.  

...[dmesg}

[   27.037266] cx18-0: Autodetected Hauppauge HVR-1600
[   27.037268] cx18-0: tveeprom cannot autodetect tuner!
[   27.037270] cx18-0: Simultaneous Digital and Analog TV capture supported



There are many flavors of the 1600. On the ivtv developers list there was some discussion a year ago about this particular error occurring with certain analog tuner assemblies that the cx18 wasn't detecting properly (in that instance Philips NTSC MK3 (FM1236MK3 or FM1236/F). (See here for starters: [http://webcache.googleusercontent.com/search?q=cache:WpEUYCvxCFgJ:ivtvdriver.org/pipermail/ivtv-users/2009-May/009392.html+%22tveeprom+cannot+autodetect+tuner!%22&cd=6&hl=en&ct=clnk&gl=us&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:WpEUYCvxCFgJ:ivtvdriver.org/pipermail/ivtv-users/2009-May/009392.html+%22tveeprom+cannot+autodetect+tuner!%22&cd=6&hl=en&ct=clnk&gl=us&client=firefox-a)  )

The cx18 developer (Andy Walls) as a workaround try in that particular instance a year ago recommended unloading the cx18 module and then modprobing it with the following parameters:

modprobe cx18 tuner=43 radio=0

And if this exact tuner parameter didn't load the module in usable fashion, to replace "43" with other compatible NTSC tuner numbers from (inter alia) the list ( [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner) ) in the hope of hitting the right one.

This may not be your problem, and I'd think that the particular tuner would have been added to the kernel tree by now, but nevertheless it might be worth a try to see whether loading the cx18 with the particular parameters for the tuner will correct your problem.

---

### Post by lglenn on 2010-06-08
OK, I have fixed the problem that I was having -- where I was just getting static on the screen on the 1600's analog input. 

Matt06 pointed out that this line from the dmesg output was probably worth paying attention to: 

```
[   27.037268] cx18-0: tveeprom cannot autodetect tuner!
```

That led me to some quality time with Google, which led me to the ivtv-users mailing list. The full exchange is [here]("http://ivtvdriver.org/pipermail/ivtv-users/2010-June/010026.html"), but the gist of it is that my card contains an analog tuner chip that is not yet autodetected by v4l. Because the system doesn't know what kind of tuner is on the card, it can't tell it how to tune, so no tuning happens, so all you see on the screen is static, aka snow. This is what klc5555 was alluding to in his post. 

Here's what I did to fix it, it may be useful to someone with the same problem who stumbles upon this post. 

There is a workaround where you can force the cx18 module to use a given tuner by loading it with the tuner=n parameter, where n is a tuner ID, as specified in the [v4l-dvb tuner.h header file]("http://linuxtv.org/hg/v4l-dvb/file/24ea80f2631f/linux/include/media/tuner.h#l29"). E.g., if you wanted to use tuner id 34: 

```
sudo modprobe cx18 tuner=34

```

Rather than manually try all 84 tuners id's to see if any worked, I wrote a small shell script that unloads the cx18 module, reloads it with tuner=1, prints the signal strength, then reloads with tuner 2, and so on, with all 84. I watched the output for signals stronger than 0%. Here's sample output, showing one successful tuner, number 71: 

```
Tuner type 68:  Signal strength/AFC  : 0%/-12500
Tuner type 69:  Signal strength/AFC  : 0%/-187500
Tuner type 70:  Signal strength/AFC  : 0%/187500
Tuner type 71:  Signal strength/AFC  : 99%/-12500
Tuner type 72:  Signal strength/AFC  : 0%/187500

```

I found three tuners that showed solid signal, so I went and tried to watch TV using each of them in turn, using the mplayer/ivtv-tune combination in my first post. Only one of the tuners, XC2028, number 71, worked. 

So, pending a new release of v4l-dvb, I'll just be forcing the tuner to type 71 like this: 

```
sudo modprobe cx18 tuner=71
```

I confess that I don't know how to make that persist after a reboot. 

Here is the shell script. You may need to change the values of VIDEO_DEVICE, CHANNEL, and/or FREQUENCY_TABLE. Caveat: I wrote this script in about ten minutes, it is as quick and dirty as quick and dirty gets. Use it at your own risk. It may not work 100%, but it got me what I needed. Don't forget to shut off anything that may be using the cx18 module, such as mythtv-backend, first. And run it as root -- it's loading and unloading kernel modules. 

```
#!/bin/bash

VIDEO_DEVICE=/dev/video0
CHANNEL=3
FREQUENCY_TABLE=us-bcast

let start=1
let end=84

for ((i=$start; i <= $end; i++))
do
    echo -n "Tuner type $i: "
    modprobe -r cx18_alsa
    modprobe -r cx18
    modprobe cx18 tuner=$i debug=3
    ivtv-tune -t $FREQUENCY_TABLE -c $CHANNEL -d $VIDEO_DEVICE > /dev/null
    v4l2-ctl -T -d $VIDEO_DEVICE | grep 'Signal strength'
    sleep 1
done
```

Hope this helps someone sometime!

---

### Post by klc5555 on 2010-06-09
There are at least two ways to make this persist.

The first way would be to set up a .conf file under /etc/modprobe.d that would include a line something like

options cx18 tuner=71


And you may be OK.

However, I've discovered that some other Phillips tuner cards (in my case Avermedia A180s) cheerfully ignore configuration files under modprobe.d and continue to load their driver defaults. In these cases, I've been compelled to add their driver module to the blacklist under modprobe.d, so that it doesn't automatically load with the wrong parameters, and to put a modprobe line with the correct parameters in the /etc/rc.local (not sudo of course). In this case:

modprobe cx18 tuner=71


One way or the other should take care of it.

---

### Post by eslio on 2010-06-17
**lgleen**, thanks a lot for your script. It helped me finding that my tuner is 71 and not 43 (the one that the module loads).

My problem is that when I use MythTV frontend, it doesn't change to other channels. It gets stuck in the initial channel.

It's strange because the first time that I tried this card, I was able to change channels, but the image was very bad. Then I removed the card and yesterday I tried again. Is it possible that the ivtv-tune has blocked the tuner to one channel.

EDIT

One information that I forgot to say. After running modprobe cx18 tuner=71 and running MythTV, the module complained about the firmware cx3038-v27. I downloaded this firmware. Now it loads it, but it gives another error (I don't have the message here) but I think that it's something about the version).

---

