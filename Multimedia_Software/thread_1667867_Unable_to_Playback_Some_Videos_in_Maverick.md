---
title: "Unable to Playback Some Videos in Maverick"
date: 2011-01-15
forum: Multimedia Software
---

### Post by _roddy_ on 2011-01-15
Hello, 

I'm having a bit of trouble with playback of a few types of videos and I *think* I should be able to do this with the hardware I've got so I'm hoping someone here can help me troubleshoot a bit? 

I'm not what I would call a power user in Ubuntu so you may have to bear with me. =)

Here's what I'm working with:

[list][*]CPU: Intel P4 3.40 Ghz
[*]Memory: 3023 MB generally running about 90% free
[*]Video Card: nVidia GeForce 7300GT, 512 MB 350 MHz, driver version 260.19.06
[*]Display: Outputting to an old CRT TV via S-Video cable at 1024x768
[/list]

I've just moved to Maverick today, I had these same problems with Lucid plus some others that seem to have been resolved in that upgrade.

I've tried these files on VLC 1.1.5 and Totem Movie Player 2.32.0 (using GStreamer 0.10.30) and I get the same results in each player. 

Here are the details on two files I get this with, and what I see when I try to play them:

[LIST=1][*]SYMPTOM: Video seems okay, audio is basically missing - maybe the odd blip but by and large, nothing.
FILE:
Video
Dimension: 640 x 480
Codec: ITU H26.n
Framerate: 30 frames per second
Bitrate: N/A
Audio
Codec: MPEG-4 AAC audio
Channels: Stereo
Sample rate: 48000Hz
Bitrate: N/A
[*]SYMPTOM: Video is extremely choppy, audio is completely missing.
FILE:
Video
Dimensions: 1280 x 720
Codec: H264
Framerate: 25 frames per second
Bitrate: N/A
Audio
Codec: Dolby Digital (AC-3)
Channels: Stereo
Sample Rage: 48000 Hz
Bitrate: 384 kbps
[/LIST]

So.. any ideas? Are my expectations for performance from my hardware unreasonable for that second file? 

Any idea why I can't seem to get audio on the first one?

Thanks for reading, and let me know if I can grab any other information.

Cheers! :D

---

### Post by BicyclerBoy on 2011-01-15
The nvidia 7300 video card is a dog & has no vdpau capability so the CPU has to do all the work.
H264 video is very processor intensive.
My atom netbook matches your machine performance with H264 video.

The P4 CPU is what exactly ? Do you mean the old pentium heater/toaster ? 
Is your PC got any PCIe (express) slots ?
If not then the PC is only good for file server backend box..

If the box has PCIe then..
A good video card is what you need; feature set C purevideo, best video performance & HDMI HD audio capable.
GT220/240/430   all PCIe.

GT220 is minimum that works properly.
GT430 is best in group but highest price.
GT240 may be a bit faster playing games (openGL etc)

---

### Post by andrew.46 on 2011-01-15
Perhaps some of your sound difficulties might be resolved by adding this uncensored version of libavcodec from Medibuntu? Medibuntu can be added as follows:

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

and the unstripped libraries can be added as follows:

```

sudo apt-get install libavcodec-extra-52

```

I was a little curious though about your copy of vlc, I believe maverick has vlc 1.1.4 not 1.1.5?

Andrew

---

