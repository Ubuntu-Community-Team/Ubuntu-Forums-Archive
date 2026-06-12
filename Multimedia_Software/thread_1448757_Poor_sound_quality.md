---
title: "Poor sound quality"
date: 2010-04-07
forum: Multimedia Software
---

### Post by alienjon on 2010-04-07
I just got my hands on an [MSI E7235-295US]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834152159") and slapped Ubuntu 9.10 on it.  So far everything's worked great, but I am beginning to get a bit concerned about my sound quality.  The laptop itself has 5 speakers + subwoofer so I should be getting 5.1 sound, if I understand things correctly (the newegg link should provide more details) and when I play anything (music, flash, videos, games, etc...) the sound comes out 'muffled'.  Almost as if it is in a concert hall, maybe.  I initially wondered if the problem is related to the 5 speakers and if the sound is initially only setup for two.  If that is the case, nothing I've done has seemed to made any real difference.  I've tried changing the master/pci channels, but it only hides it a little, and doesn't solve the problem.

[This]("https://help.ubuntu.com/community/HdaIntelSoundHowto") seemed to be on the right track, but the laptop is still really new and not listed in the alsa file.

Some info:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7220
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8ef8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by lidex on 2010-04-08
> **alienjon said:**
> I just got my hands on an [MSI E7235-295US]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834152159") and slapped Ubuntu 9.10 on it.  So far everything's worked great, but I am beginning to get a bit concerned about my sound quality.  The laptop itself has 5 speakers + subwoofer so I should be getting 5.1 sound, if I understand things correctly (the newegg link should provide more details) and when I play anything (music, flash, videos, games, etc...) the sound comes out 'muffled'.  Almost as if it is in a concert hall, maybe.  I initially wondered if the problem is related to the 5 speakers and if the sound is initially only setup for two.  If that is the case, nothing I've done has seemed to made any real difference.  I've tried changing the master/pci channels, but it only hides it a little, and doesn't solve the problem.

[This]("https://help.ubuntu.com/community/HdaIntelSoundHowto") seemed to be on the right track, but the laptop is still really new and not listed in the alsa file.



Doesn't really matter. What's important is the codec. Can you post output of this command:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by alienjon on 2010-04-08
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP78 HDMI

---

### Post by lidex on 2010-04-08
Seeing that is a newer codec, and lucid comes with alsa 1.0.21, karmic version is probably even older. I would suggest upgrading to 1.0.22. Click on the alsa-upgrade-script link in my sig.

---

### Post by alienjon on 2010-04-08
That seems to have made the difference, thanks!

---

### Post by lidex on 2010-04-08
You're welcome! If you get a chance please mark the thread as solved using "Thread Tools" near the top.

---

### Post by alienjon on 2010-04-08
I hate to say it, but I'm afraid I posted a bit too early.  This morning I did a comparison between audio in Ubuntu and Windows (the laptop came with Windows 7 pre-installed).  I still feel that the sound has improved in linux because the voices sound clearer (not as muffled) but sound is only coming out of the subwoofer.  I did a websearch and found [this]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml") how to for multi-channeled sound, but this seems to have had no effect.

I tried using the 5 channel sound (sound tests, for example) and here are some results:

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr  8 2010 for kernel 2.6.31-20-generic (SMP).

```
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
aplay -Dplughw:0,0 -fcd /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```
The following speaker-test only outputs static, is it supposed to?
```
speaker-test -Dplughw:0,0 -c2

speaker-test 1.0.22

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.632858
 0 - Front Left
 1 - Front Right

```
```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output

```
```
speaker-test -D surround51 -c6

speaker-test 1.0.22

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

```

Linux just REALLY doesn't seem to want to use more than 2 channels, for some reason.  This is confirmed in the PuleAudio Manager (padevchooser) which lists the default sample type as 's16le 2ch 44100Hz'.

---

### Post by alienjon on 2010-04-08
Ok, thanks to [this how to]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/") pulse audio now reads as 6 channels.  Running the speaker test command from earlier now works and it reports that it is in 5.1 sound (6 channels) but I'm still only getting sound out of the subwoofer and only for front left/front right.  All the other channels don't output sound in the test.  Could this be a problem with linux seeing my speakers?

Also, I wanted to note that all mixer programs (alsamixer and the pulse audio volume displays) only show stereo channels at best (alsa mixer only shows front, not left/right/front/back/center/surround/etc...)

*** Update ***
Ok, last post for the moment (I promise!)  I found that adding 'model=targa-dig' to my 'options snd-hda-intel ...' in /etc/modprobe.d/alsa-base.conf will now allow the laptop to output from the front left/right speakers, but the center's (front and rear) remain from the subwoofer and the rear left/right don't output at all.  I imagine, then, that I just need to specify the model, but how do I find that out?  targa-dig and targa-dig-2ch were the only MSI options available (from what I can tell)

---

### Post by lidex on 2010-04-08
Sometimes you need to mix-n-match. Some other options:
```
3stack-dig
3stack-6ch-dig
3stack-digout	
```
After you make changes check alsamixer.

Edit: What I meant was use options for other chipsets, not use them all at the same time -- you should try the above models singly.

---

### Post by alienjon on 2010-04-14
Sorry for waiting a few days before replying, but I've been a bit busy with life and such.  Anyway, I just had a look again at the sound issue and started off where I left.  I began by testing the speakers by running speaker-test (specifically: speaker-test -c 6 -D surround51 -t wav) and, as I had left things, I only got sound out of the front left/right/center and rear center (subwoofer?) channels.  I then decided to check the Ubuntu-side of things again (via the taskbar icon) and happened to notice that it is now recognizing the 5.1 sound (I must have missed this step the last time I restarted with the targa option set in the alsa configuration.  I set it to the 5.1 output, but the speaker-test still does not register with those channels working as they should.  I tested it manually (ie: I played an mp3 and put my ears close to each speaker) and was happy to discover that I was, in fact, getting sound out of each speaker despite what sound-test was reporting.  I'm guessing that, maybe, the Ubuntu configuration (targa option?) is only running a virtual 5.1 sound, but it is really a 2.1/3/3.1 or some such?  Anyway, it seems to be working better, but if anyone has any further info on the issue, I'm definitely interested in hearing more!

---

### Post by lidex on 2010-04-14
Surround sound:
[http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

---

### Post by alienjon on 2010-04-15
Yeah, that's one of the threads I had gone through.  It was a bit helpful.

---

### Post by DarkProphet1313 on 2010-05-31
So anyone figure out what the actual fix was?  I also have the MSI e7235 and cannot get all speakers on laptop to work at same time.  So far following almost all the steps that have been taken in this thread, ive come to becoming stuck.  Any help would be appreciated

---

### Post by alienjon on 2010-05-31
I suppose I still don't know with exact certainty what solved the problem (there are, as I think the thread shows, a lot of variables that I went through) but I believe that installing the unsupported drivers and, more importantly, editing the alsa configuration file are the important aspects of getting it to work for me.  Also make sure that you've enabled the 5.1 sound via the Gnome applet (once I got it to show there it worked for me).  I'm afraid I'm not using that computer right now, but if you're still having problems later let me know and I'll see if I can track down the exact files I edited.

---

### Post by DarkProphet1313 on 2010-06-01
I still havent got it to show the 5.1 in the gnome applet.  I used the realtek linux drivers from the realtek site, compiled and installed the packages, and my guess is somewhere in the addition of targa to the alsa.conf is where my problem is.  Its the only step i havent completed because on the list for the file there is no line for options snd-hda-intel so i have not specified the model.  Should i have added this line in the alsa.conf file or is there something that i have not completed correctly.

---

### Post by alienjon on 2010-06-01
Not alsa.conf, alsa-base.conf, my bad.

The only change I made in this file was to add (at the end of the file):

```
sudo echo "options snd-hda-intel model=3stack-6ch-dig power_save=10 power_save_controller=N" >> /etc/modprobe.d/alsa-base.conf
```

The pain in the butt part with all of this is that I needed to restart the computer completely to test any of this, so after you make the change you'll need a reboot.

---

