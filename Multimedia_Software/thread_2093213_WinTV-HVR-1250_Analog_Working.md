---
title: "WinTV-HVR-1250 Analog Working"
date: 2012-12-10
forum: Multimedia Software
---

### Post by krystena on 2012-12-10
I dunno where to put this, I just know there is literally a mountain of people looking for help on this. I managed to get the analog channels working and I figured I'd just drop my software stats and what I did to do that in case someone hits some Google and finds this. If its in the wrong spot, feel free to move it.

Let me know if I forgot anything. This is literally off the top of my head. <3

uname -a
```

Linux Luna 3.6.9-030609-generic #201212031610 SMP Mon Dec 3 21:11:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Acquire new kernel from Ubuntu mainline: 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

Install the debs.

I have an NVidia card, I had to rework my drivers, I got the most recent ones from the official site. You gotta do this in recovery, so reboot and go there.
```

mount -o remount,rw /
mount /home
mount /whatever
cd /location/of/NVidia/sh/run/file
sh ./NVIDIA-arch-version-stuff-xxx.xx.run
umount /home
umount /whatever

```

Reboot. 

Let that roll so this process is just not annoying. Now we're updated and we need to now update v4l-dvb (for digital use).

```

sudo apt-get install git
git clone git://linuxtv.org/media_build.git
cd media_build 
./build
sudo make install

```

Reboot.

```

apt-get install tvtime

```

tvtime settings (adjust where needed), sometimes video0 is the tuner, especially for people without a webcam, I do have one, and that makes my tuner /dev/video1

Contents of ~/.tvtime/tvtime.xml (I have it on channel 3 in case you're tuning a device that requires channel 3 to use it, for defaults sake.):

```

<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Matte" value="16:9"/>
  <option name="Channel" value="3"/>
  <option name="NTSCCableMode" value="Nominal"/>
  <option name="Frequencies" value="us-cable"/>
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="PrevChannel" value="2"/>
  <option name="FramerateMode" value="1"/>
  <option name="OverScan" value="8.5"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="100"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="0"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
  <option name="WideScreen" value="1"/>
  <option name="DeinterlaceMethod" value="AdaptiveAdvanced"/>
  <option name="ColourInvert" value="0"/>
  <option name="MirrorInput" value="0"/>
  <option name="InputWidth" value="768"/>
  <option name="ShowCC" value="1"/>
</tvtime>

```

Get a lil script going for tvtime and audio:
```

#!/bin/bash
sudo modprobe snd_mixer_oss
sox -t alsa hw:3,0 -t alsa default --no-show-progress &
/usr/bin/tvtime
killall -9 sox

```

Obviously hw:3,0 isn't gonna be everybody's capture mapping for audio so run this command:

```

arecord -l

```

Find and replace within the script. Example:

card **3**: CX23885 [Conexant CX23885], device **0**: CX23885 Digital [CX23885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Replace the hw: part to match this area.

Run your script, and good luck, again, if I left anything out, lemme know. <3 ):P

mplayer solution instead of tvtime/sox (Covered here -> [http://www.linuxtv.org/wiki/index.php/Saa7134-alsa]("http://www.linuxtv.org/wiki/index.php/Saa7134-alsa")):
```

mplayer tv://"3" -tv driver=v4l2:device=/dev/video1:chanlist=us-cable:alsa:adevice=hw.3,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC

```

VLC Analog (upgraded to VLC 2.1.0-git using PPA from [https://launchpad.net/~n-muench/+archive/vlc]("https://launchpad.net/~n-muench/+archive/vlc"))
```

vlc --input-slave alsa://hw:3,0 v4l2:// :v4l2-dev=/dev/video1 :v4l2-samplerate=48000 :v4l2-standard=NTSC :v4l2-width=720 :v4l2-height=576 :v4l2-input=0 :v4l2-audio-input=0

```

Again, you have to change the audio mapping and your video output and device. These are merely MY settings and you WILL have to change them (of course on the off chance we have the same mapping, hey, good for you). 

PS, I know we updated the dvb and we're not using it, I figured it was just important to have it done. I think most people are trying to scan and view analog channels (/dev/dvb/adapter0/frontend0) when they don't really notice that /dev/video1 is where they need to be checking. Anyways, you can scan digital channels normally now, and if you have any, they should work, digital scans were never a problem with this card to begin with out of the box Ubuntu 12.10. Also, I did not test any of this data with the system not updated, feel free to try. I just gave all the data I could to get a possible result for what I *think* people want to use this card for. 

Also I cannot get the s-video RCA composite adapter to not show black and white video. If anyone knows how to get that out of black and white mode, that would be super. That's the last part of this card that at least I'm aware of that doesn't work 100% correctly, but it does work.

PSS, this is setup for American (USA) TV, norms, channel frequencies will vary outside of the country. I can't cover that all here. :) I'll try to add what I can if anyone finds this useful though.

---

