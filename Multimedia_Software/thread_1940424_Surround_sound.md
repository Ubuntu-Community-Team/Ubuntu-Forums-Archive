---
title: "Surround sound"
date: 2012-03-13
forum: Multimedia Software
---

### Post by FatD on 2012-03-13
I am a total noob to  ubuntu and am trying to get my xfi titanium card with 5.1 z5500's  working like it does on windows 7. I started following the guide at:

[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

but have hit a snag, the problem I have though is when I  reach the step to type in:

sudo apt-get build-dep libasound2-plugins

I get the following:

jease@ubuntu:~/Downloads$ apt-get source libasound2-plugins
 Reading package lists… Done
 Building dependency tree
 Reading state information… Done
 Picking ‘alsa-plugins’ as source package instead of ‘libasound2-plugins’
 E: Unable to find a source package for alsa-plugins

I tried searching the forums and google but cannot find a solution or working command thus far, I hope someone can help me get over this step. Thanks

---

### Post by BicyclerBoy on 2012-03-13
Just yesterday I recompiled the alsa-plugins to get a52 plugin working again..it has been broken against certain ffmpeg/libav for a long time.

Forget the libasound2-plugin package, just get the latest alsa-plugins-1.0.25-tar.gz from alsa website..
-unpack archive in home folder
- ./configure  (check for enabled plugs)
- make
- copy over the libs if successful..
missing dependencies will reveal themselves pretty quickly.

The alsa-plugins-1.0.25 seems to work okay with alsa user-space 1.0.24 & alsa-1.0.23 kernel modules in stock kernel of *buntu 10.04.

Note:
- I'm using JSeverensons ffmpeg/libav 4.09 ppa
- a52 plug uses ac3_fixed encoder in libav
- a52 can use bitrate 640K if your amp supports.

Question:
Do you really need to use the a52 (AC3) encoder with a fancy soundcard?
This can be done just as well with mobo S/PDIF.
Do you just want discrete analogue 5.1 outputs (surround51)?

I think the windows XFi soundcard driver includes a AC3 encoder licence but the encoding is done in software (CPU) & not on the soundcard card.

---

### Post by FatD on 2012-03-13
> **BicyclerBoy said:**
> Just yesterday I recompiled the alsa-plugins to get a52 plugin working again..it has been broken against certain ffmpeg/libav for a long time.

Forget the libasound2-plugin package, just get the latest alsa-plugins-1.0.25-tar.gz from alsa website..
-unpack archive in home folder
- ./configure  (check for enabled plugs)
- make
- copy over the libs if successful..
missing dependencies will reveal themselves pretty quickly.

The alsa-plugins-1.0.25 seems to work okay with alsa user-space 1.0.24 & alsa-1.0.23 kernel modules in stock kernel of *buntu 10.04.

Note:
- I'm using JSeverensons ffmpeg/libav 4.09 ppa
- a52 plug uses ac3_fixed encoder in libav
- a52 can use bitrate 640K if your amp supports.

Question:
Do you really need to use the a52 (AC3) encoder with a fancy soundcard?
This can be done just as well with mobo S/PDIF.
Do you just want discrete analogue 5.1 outputs (surround51)?

I think the windows XFi soundcard driver includes a AC3 encoder licence but the encoding is done in software (CPU) & not on the soundcard card.

Thanks for the reply,

I actually thought that was the best tutorial ([http://www.piotrkrzyzek.com/solved-creative-x-fi-titanium-ctxfi-on-ubuntu-11-10/](http://www.piotrkrzyzek.com/solved-creative-x-fi-titanium-ctxfi-on-ubuntu-11-10/)) for me to get my 5.1 working. Currently in sound settings when i choose 5.1 analog ouput (which are only settings) only 3 speakers work, but back left, center and subwoofer are not producing any sound at all. I tried multiple settings in the sound settings area but haven't had luck setting it up to its proper working order.

If you know how I can set this up, or could point me to the right step by step tutorial, I'd greatly appreciate it.

---

### Post by BicyclerBoy on 2012-03-13
There are lots of variants of the X-Fi card..
AFAIK the Ti uses driver snd-ctxfi (EMU20K1, EMU20K2 chipsets).

Have a look thru the output of:
dmesg
for messages about EMU X-Fi snd-ctx etc..

There was a load of bug fixes for the X-Fi Titanium in alsa 1.0.25.
[http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#Creative_Sound_Blaster_X-Fi_.2820K1.2F20K2.29](http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#Creative_Sound_Blaster_X-Fi_.2820K1.2F20K2.29)

aplay -l
look for your card device then
speaker-test -c 6 -r 48000 -D hw:1,0 or similar

You should check the mixer volumes, possible that rear channels are not muted..
alsamixergui
pavucontrol

---

