---
title: "HDMI audio via ION mobo ? (so close!!)"
date: 2010-04-24
forum: Multimedia Software
---

### Post by unkle1 on 2010-04-24
Hi all,

Just bought an Asus AT3N7A-I with an Ion chipset. Everything seems to work as supposed to in mythbuntu 10.04 however, I can only pass sound through the analog jacks and not HDMI. It feels as if Im really close with HW and all looking good.

This is what aplay tells me:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and

aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, VT1708S Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```In alsamixer I dont see any IEC958, only 3 * SPDIF and there are all unmuted.
Ive tried various combinations of hw:0,0 / hw:0,1 / hw:0,3 and also speaker-test and aplay playing samples through hdmi:CARD=NVidia,DEV=0
Not a whisper...

The alsa is pretty new, alsactl says version 1.0.22 but I think alsa itself is 1.0.21 (?)

To me, hardware seems to be ok according to the above. The software is also new and I think alsa supported hdmi-audio since 1.0.18'ish

What can I do to test my setup and confirm the various settings ?
(and how do I configure MythTV to use the working setup ? (there are various choices including "ALSA: plughw:0,3" and "ALSA:hdmi" and so on in Setup - General - Audio System))

Would it help me to play with PulseAudio instead ? and if so, how might MythTV react to this change ?

Alsas wiki on digital out mentions "enable PCM Out" but as the wiki also states, it has yet to be described how to do that. Link: [http://alsa.opensrc.org/index.php/DigitalOut#Check_your_mixer](http://alsa.opensrc.org/index.php/DigitalOut#Check_your_mixer)

I'll of course be happy to supply any logs or other diagnostic output from alsa etc. if you need it (and explain how I access the necessary info) ;)

---

### Post by lidex on 2010-04-24
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by unkle1 on 2010-04-25
> **lidex said:**
> Can you post the output of these terminal commands for me please.
Also helpful is the make/model of your PC/Laptop.

Here you go:
```

dte@Myth23:~$ uname -a
Linux Myth23 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686                                                        GNU/Linux

dte@Myth23:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dte@Myth23:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

dte@Myth23:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP7A HDMI

```The make/model of my PC/Laptop would be an Asus AT3N7A-I motherboard (Intel Atom 330), 2GB RAM and a TechnoTrend Budget C-1501 for dvb-c.
I've downloaded and run your comprehensive script. I hope it helps. Im  also following the similar thread where you help Kasuko. Thankyou so  much for your attention and rapid response :smile:

Script output here:
[http://www.alsa-project.org/db/?f=663f6b1355596d86774f2adceea1c0ea9c6a4cc9](http://www.alsa-project.org/db/?f=663f6b1355596d86774f2adceea1c0ea9c6a4cc9)

---

### Post by unkle1 on 2010-04-25
I found this how-to for upgrading a 9.10 to latest alsa and it should solve some hdmi-audio issues.
I will try it and post the result.
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)
[ ]("http://www.alsa-project.org/db/?f=663f6b1355596d86774f2adceea1c0ea9c6a4cc9")

---

### Post by lidex on 2010-04-25
Have you seen this:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")

---

### Post by unkle1 on 2010-04-25
> **lidex said:**
> Have you seen this:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

Thanks, yes, I've seen it and also commented it in the initial post of this thread.

Building and installing alsa driver/lib/utils 1.0.23 was succesfull:
```
dte@Myth23:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Apr 26 2010 for kernel 2.6.32-21-generic (SMP).
```But still no sound through HDMI. With aplay I see this:
```
dte@Myth23:~$ aplay -D hdmi:CARD=NVidia,DEV=0 /var/lib/mythtv/music/testing.wav
Playing WAVE '/var/lib/mythtv/music/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:1059: Channels count non available

dte@Myth23:~$ aplay -D hw:0,1 /var/lib/mythtv/music/testing.wav
Playing WAVE '/var/lib/mythtv/music/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:1059: Channels count non available

dte@Myth23:~$ aplay -D hw:0,3 /var/lib/mythtv/music/testing.wav
Playing WAVE '/var/lib/mythtv/music/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:1059: Channels count non available

dte@Myth23:~$ aplay -D iec958:CARD=NVidia,DEV=0 /var/lib/mythtv/music/testing.wav
Playing WAVE '/var/lib/mythtv/music/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:1059: Channels count non available
```

Devices and PCMs look the same to me as in 1.0.21
```
dte@Myth23:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dte@Myth23:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, VT1708S Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```

---

### Post by JohnnyC35 on 2010-04-25
hey
I have an ION ITX A-U board and had issues with the HDMI.
How I fixed it was upgrade to the newest NVIDIA drivers, reboot, goto alsamixer at the command line and make sure that S/PDIF, S/PDIF1, and S/PDIF2 are unmuted and all the way up. Then goto System, Preferences, Soun, click on the Hardware tab and under profile choose 'Internal Audio Digital Stereo (HDMI) Output + Analog Stereo Input. after that you should be able to hear again :)


oh oops. looks like you tried most of that :S hmm

---

### Post by unkle1 on 2010-04-25
> **JohnnyC35 said:**
> hey
I have an ION ITX A-U board and had issues with the HDMI.
How I fixed it was upgrade to the newest NVIDIA drivers, reboot, goto alsamixer at the command line and make sure that S/PDIF, S/PDIF1, and S/PDIF2 are unmuted and all the way up. Then goto System, Preferences, Soun, click on the Hardware tab and under profile choose 'Internal Audio Digital Stereo (HDMI) Output + Analog Stereo Input. after that you should be able to hear again :)


oh oops. looks like you tried most of that :S hmm

No worries, I appreciate the input :)
Im running Xfce4 though so I dont think I have the System -> Pref -> Sound options.
I cant find anywhere to change the output specifically, - are you running pulseaudio ? (this 'Internal Audio Digi.....' sounds as if it is taken from some pulseaudio-configuration ?).
I'll try installing PulseAudio again and see if that makes a change although I think I've read somewhere that my MythTV-sw wont be too happy with Pulse (?)

Oh, btw you mention this "S/PDIF, S/PDIF1, and S/PDIF2 are unmuted and all the way up" ...all the way up ? In my alsamixer I can only mute/unmute the channels, there is no lvl-control ? (maybe this is a lead?)

**Update:**
playing a test sample through "plughw:x,x" instead of "hw:x,x" yields no error now, but still no sound from the TV though.
aplay -D plughw:0,3 /var/lib/mythtv/music/testing.wav

Maybe someone knows how to "enable PCM" which is missing in the alsa-wiki ?
Or is there (should there be) a way to adjust the volume on the S/PDIF in alsamixer ?

---

### Post by lidex on 2010-04-25
Some related threads:
[http://ubuntuforums.org/showthread.php?t=1372111]("http://ubuntuforums.org/showthread.php?t=1372111")
[http://ubuntuforums.org/showthread.php?t=1417325]("http://ubuntuforums.org/showthread.php?t=1417325")
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=903371]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=903371")
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1046137&page=51]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1046137&page=51")
[http://ubuntuforums.org/showthread.php?t=1287810]("http://ubuntuforums.org/showthread.php?t=1287810")
[http://ubuntuforums.org/showthread.php?t=1023913]("http://ubuntuforums.org/showthread.php?t=1023913")

Number 3 is a mythtv user.

---

### Post by unkle1 on 2010-04-26
Thankyou Lidex for the many links to threads, I've looked into them again and still cant find any good advice. Some of the threads your refer to are from the 8.10-age and many of the workarounds have been made into real solutions and patches since. Also, the link to the kernel-bug shows that it has been implemented in 2.6.31 (im running .32).
I've tried the "grand alsa-upgrade" script which installed 1.0.22.1 but with no luck.

All in all it just shows theres still a way to go before the Ion is 100% cooperative ;)

Maybe its time I do a clean install, try all the little tricks and then, if it still does not work, file a bug-report in launchpad. Would be awesome if a fix could make it in time for the final 10.04-release.

[U][B]Update:
[/B][/U]Did a complete reinstall of MythBuntu 10.04(RC) and with this fresh install, no sound.
Updated the fresh install (did -not- enable any alternative package-sources yet) 299 packages and tested again, no hdmi-sound (analogue stereo works). Its the same behaviour as with the latest ALSA it appears to be playing when aplay gets "plughw:0,3" but there is no sound coming from the speakers of my LG LCD-TV (TVs own info says sound is enabled on the hdmi-input).

Tried also with the latest XBMC Live version as suggested in this thread [http://ubuntuforums.org/showthread.php?t=1372111](http://ubuntuforums.org/showthread.php?t=1372111) still no sound through hdmi.

---

### Post by lidex on 2010-04-26
unkle1:
Follow this post to get the very latest alsa, 1.0.23
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by unkle1 on 2010-04-26
Tried it just now and unfortunately no new results.

What might I look for to verify that all is setup nicely ? I know about the iec958 switches and the pcm-channel turned up and of course the devices and pcms in aplays lists. Is there an even more comprehensive checklist ? I've searched dmesg and xorg.log for "error" and "warning" but nothing disturbing can be found.

Is there some sort of debug mode where I might be able to see the chip rec/transmitting the stream or something like that ? 

Grasping at straws here ;)

---

### Post by unkle1 on 2010-04-27
Breakthrough ! \\:D/

I was advised by Emilio from the launchpad-group of this motherboard to try with (among others) a 9.10 live version.
[https://launchpad.net/~at3n7a-i]("https://launchpad.net/%7Eat3n7a-i")

I booted into the live-version and did a speaker-test as the first thing. No sound.
Now in 10.04-live I have trouble enabling the proprietary Nvidia-drivers but I tried this in 9.10 and it did download and install the drivers (185).
After a "sudo /etc/init.d/gdm restart" I tested again with speaker-test and FINALLY beautiful pink noise started pouring out my TV-speakers ! Joy !

This works:
```
speaker-test -Dhw:0,3 -c2
speaker-test -Dhdmi -c2
aplay -Dplughw:0,3 Noise.wav
```
This does not work:
```
aplay -Dhdmi Noise.wav
aplay -Dhw:0,3 Noise.wav
```I dont know what the difference is between speaker-test -Dhdmi and aplay -Dhdmi but it seems that speakertest automatically uses the "plug" prefix somehow (but whats the difference between plughw:0,3 and hw:0,3 ?).

Also the ALSA version of MythBuntu 9.10 live seems to be:
1.0.20

So the conclusion might be (please help me out here), according to my observations:
This hdmi-audio bug seems to be independent from ALSA as long as its version 1.0.20 or up (I havent updated the ALSA on the 9.10 yet, but will do so, to rule ALSA out as the problem).
The bug seems to be depending on the Nvidia proprietary drivers. Others have reported hdmi-audio being broke at version 190 (and I cant get it working in 195). So, 185 may be the way to go with my current running 10.04.

Theres just one problem though. Even though I installed nvidia-glx-185 in 10.04 I cant select and activate this driver from the "hardware drivers" configuration gui-thing. How do I enable this driver ? (this question should be in another thread but if I can get this working I'll put a [SOLVED] on this thread even though it is in fact a workaround reverting to 185).
Im also pretty curious about my vdpau performance with the 185-drivers.

So this is to be done: Enable nvidia 185 in 10.04 and then I have to figure out the setup for Mythtv when it comes to the device-name (im guessing "plughw:0,3" will work).
I also want to test the different ALSA version on 9.10 (or at least the 1.0.23) but now Im getting doubts as to whether this is possible because it requires a reboot and I havent got a clue if this'll work on a live-version (it is running from a writable USB-stick though).

All in all, progress thanks to the good community ! :)

---

### Post by defaria on 2010-04-30
This thread is holding some promise for me even though I haven't installed mythbuntu or anything like that. I have an HP laptop (dv7) and am struggling with trying to get my HDMI interface to output sound. From [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) I managed to finally get sound to go down the HDMI and out to my home theater. At least now I know that this is possible. In checking this I've noticed that 1) only can play 16 bit wav files and when I do it often loops on the sound or otherwise messes up. But it's clear that sound was send down the HDMI to my home theater. 

To be clear I managed to do the following:

```
$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 37: [ 1- 1]: hardware dependent
 38: [ 1- 2]: hardware dependent
 39: [ 1- 3]: hardware dependent
 51: [ 1- 3]: digital audio playback
 55: [ 1- 7]: digital audio playback
 56: [ 1- 8]: digital audio playback
 57: [ 1- 9]: digital audio playback
$ aplay -D plughw:1,7 file.wav

```

I use PulseAudio and pavucontrol, under Configuration shows a HDA NVidia with a Profile of Digital Setero (HDMI) Output. If I play say a movie with vlc or movie player I can see under Playback the vlc or movie player and can switch the output to HDMI but nothing comes out of the HDMI cable nor my home theater sound system. 

How can I get this working? What sorts of output can I provide you for debugging purposes. Is it simply a driver issue?!? I'm racking my brain over this because this is about the last thing that's making me run a dual boot with Windows 7 (where HDMI works). The other thing is the TV tuner card but that's not as important right now.

Please help.

---

### Post by lidex on 2010-04-30
defaria:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga")

---

### Post by defaria on 2010-05-01
I'm not sure what to make of this. Sounds hopeful but it also seems to be saying that HDMI output is supported with nvidia-glx-180.22 drivers. Yet I have NVidea drivers version 195.36.15! Please don't tell me I need to downgrade to a previous NVidea driver because IIRC I updated to this driver because the X display would go all fuzzy whenever you suspended the system. 

So this does not appear to be a solution for me.

---

### Post by unkle1 on 2010-05-02
Well, I've been messing around with both 10.04 (also the final release) and 9.10 and I cannot make hdmi-audio work in 10.04 due to both xorg 1.7+ and nvidia 195. I could not figure out how to downgrade xorg so my next bet is to go for 9.10 and be very careful about what I upgrade. If I'm still able to play 1080p smoothly with 185 then this'll be the "static" platform for this board. I see no problem in building myth from trunk if I want upgrades :)

I have to say that I still hope either xorg will be made backwards-compatible with 185 but the chances are probably pretty slim. The chance of persuading Nvidia to port the hdmiaudio-support from 185 to 195 is worse I guess. Oh well, we can't have it all ;)

Good luck to you defaria

---

### Post by defaria on 2010-05-02
Actually I'd say we can have it all but it takes time.

If I'm reading you correctly you're saying that HDMI audio output works with a previous version of the Nvidia drivers but not the current one. Surely this is a situation that they will be fixing. I mean why would you want to have it **not** work?

---

### Post by farbird on 2010-05-11
I have a similar issue..

I have 2 LCD TVs both with HDMI input.

tried my ion with 195 driver on both TVs using the HDMI.
One will playback the hdmi audio without problem, the other TV will not produce audio from the ION Hdmi out.

downgrading to 185 driver, hdmi audio works on both TV.

I used both my ION notebook and the Zotac itx board with embedded nvidia9300 and both produces the same results on the same tvs with the 2 different driver versions.

To make things worse, I'd upgraded to lucid and it has no way of downgrading the driver via the repos..

---

### Post by defaria on 2010-05-12
So then it appears to be a driver issue that needs to be resolve. Ho hum - sit, wait and twiddle my thumbs while I wait for Linux to get up to speed on the hardware...

---

### Post by farbird on 2010-05-12
been waiting since ubuntu 9.10..

ie since october 2009 till now [ ubuntu lucid ]

Not sure if Nvidia themselves have acknowledged this issue?

---

### Post by defaria on 2010-05-12
Is there a way or mechanism to get them to take notice?

---

### Post by farbird on 2010-05-12
already posted in nvnews.net forums..

---

### Post by changlinn on 2010-08-29
How did you end up solving this, I am having a similar issue and everything I have tried has led me to a dead end, I was starting to think it was my tv but I am in the same boat as you speakertest works but nothing else.

---

### Post by defaria on 2010-08-29
Changlinn, who are you asking that question of? I've solved my problem a while back so my memory is a little hazy here. I don't think I downgraded my NVidia drivers. I know I have installed the latest ALSA stuff (1.0.23 I believe). I think I followed some of the advice at [http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/6#vga). Oh and I think the real trick was to create an ~/.asoundrc telling pulse audio to default things for PCM and CTL(?)

```
pcm.!default {
  type pulse
}
ctl.!default {
  type pulse
}
pcm.pulse {
  type pulse
}
ctl.pulse {
  type pulse
}

```

Oh and they may have been a "run alsamixer" and toggle on some thing.

---

### Post by changlinn on 2010-09-04
hmm pavucontrol and alsamixer failed with that .asoundrc file.
I think in my case the plot is a bit thicker, without that .asoundrc file I seem to get the audio meter on pavucontrol displaying sound on the HDMI but nothing through the TV, so either it is a faulty cable or a fault with the TV. I am going to have to loan the cable to someone and see.

Edit: now that I think of it the aplay of pink noise worked through the HDMI cable and this tv, so that isn't it. Odd that I get the sound meter moving in pavucontrol.

---

### Post by defaria on 2010-09-06
All I know is that I'm doing this on a dual boot laptop with Win 7 on the other end. Win 7 works fine. The HDMI works just great. So I know the hardware on the laptop can do it, the cable's good and my home theater produces sound. 

Like I said it was some combination of getting 1.0.23 Alsa Drivers, flipping something in alsamixer and then using the ~/.asoundrc to tell it to go through Pulseaudio.

---

