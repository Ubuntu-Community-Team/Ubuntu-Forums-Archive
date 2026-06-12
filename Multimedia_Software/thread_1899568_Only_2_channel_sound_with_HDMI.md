---
title: "Only 2 channel sound with HDMI"
date: 2011-12-23
forum: Multimedia Software
---

### Post by duncang92 on 2011-12-23
I have an MSI E350IA-E45 - AMD APU running Ubuntu 11.10. [http://www.guru3d.com/article/msi-e350iae45-amd-apu-fusion-review/](http://www.guru3d.com/article/msi-e350iae45-amd-apu-fusion-review/)

I managed to get the video working correctly (eventually) using the AMD driver from their site. Using either of the proprietary drivers from the Additional Drivers panel caused me no end of grief.

What I noticed is that my sound driver only supports 2 channel HDMI although I know that the motherboard is capable of full 5.1 sounds through the HDMI output.

Digital Stereo (HDMI) Output is the only option available in the   Sound panel System Settings pulldown in the Hardware tab.

aplay -l reports that I have 3 devices:

Generic [HD-Audio Generic]

and

SB [HDA ATI SB] ALC887-VD Digital AND Analog


alsamixer for the HD-Audio Generic tells me that the chip is an ATI R6xx HDMI. 

Following the trail of the chip didn't help me find anything about a driver (other than one option that I found and downloaded a driver and blew sound up completely until I found how to reset back to the initial 11.10 installation state.


This is really bugging me as running this as my home theatre with HDMI and a 5.1 surround sound and then listening to everything in 2 channel stereo is getting boring :(

Any help would be very gratefully appreciated.

Cheers and Merry Christmas, Duncan

---

### Post by inobe on 2011-12-23
install pavucontrol, in the config tab, select desired output.

---

### Post by duncang92 on 2011-12-28
Thanks a lot butpPavucontrol only gives me some extra options.

It still reports that my HDMI audio is 2 channel only.

I believe that I need to find a Linux driver (under Ubuntu 11.10) for a Realtek ALC887.

Any pointers?

---

### Post by lidex on 2011-12-31
> **duncang92 said:**
> Thanks a lot butpPavucontrol only gives me some extra options.

It still reports that my HDMI audio is 2 channel only.

I believe that I need to find a Linux driver (under Ubuntu 11.10) for a Realtek ALC887.

Any pointers?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by cbowman57 on 2011-12-31
Good information [here.]("https://wiki.archlinux.org/index.php/PulseAudio")

I was amazed at the difference in sound after tuning my pulseaudio.

---

### Post by lidex on 2011-12-31
> **cbowman57 said:**
> Good information [here.]("https://wiki.archlinux.org/index.php/PulseAudio")

I was amazed at the difference in sound after tuning my pulseaudio.

Informative link. Very nice!

---

### Post by cbowman57 on 2011-12-31
> **lidex said:**
> Informative link. Very nice!

I hope it helps out some.

---

### Post by duncang92 on 2012-01-02
Here's the link to the ALSA output.


[http://www.alsa-project.org/db/?f=5abcf87419879061254f7dc4d0b797406755c659](http://www.alsa-project.org/db/?f=5abcf87419879061254f7dc4d0b797406755c659)

Cheers.

---

### Post by lidex on 2012-01-03
> **duncang92 said:**
> Here's the link to the ALSA output.


[http://www.alsa-project.org/db/?f=5abcf87419879061254f7dc4d0b797406755c659](http://www.alsa-project.org/db/?f=5abcf87419879061254f7dc4d0b797406755c659)

Cheers.
I would suggest renaming/moving your asound.conf file and start over using info from this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by shantiq on 2012-01-03
> **cbowman57 said:**
> I hope it helps out some.


thank you [really cool info]("https://wiki.archlinux.org/index.php/PulseAudio")

you say  >  I was amazed at the difference in sound after tuning my pulseaudio.


what did you /can one/should one look out to   modify exactly    if you do not mind saying...

---

### Post by cbowman57 on 2012-01-03
> **shantiq said:**
> thank you [really cool info]("https://wiki.archlinux.org/index.php/PulseAudio")

you say  


what did you /can one/should one look out to   modify exactly    if you do not mind saying...

Unfortunately it's hardware specific so there isn't a generic recipe, but there are some good threads, FAQs & Wikis that walk you through it.  There is a really good thread hidden here in the archives that I can hardly ever find, but the Archwiki is easy to find & most everything applies.

Basically the out-of-the-box alsa & pulseaudio configuration use low-mid quality settings. On my system the default was low bit-rate playback, the wrong drivers & they capped pulse audio cpu usage, so I gave it the right driver, increased playback bit-rate, changed the 'nice' level.  It's been awhile since I've made changes so I've forgotten most of what I did.

Here are some key entries in the daemon.conf worth looking at:
**nice-level** = (I use -3)
**resample-method** = (I use speex-float-9 or src-sinc-best-quality)
**default-sample-format** = (you'll need to determine this from instructions in wiki, I use float32le)
**default-sample-rate** = (Device & resource dependent, I use 96000)

If you have a surround type system you may want to mess with default-sample-channels & default-channel-map but I only have a simple sub w/2 speakers so didn't bother with that.

---

### Post by duncang92 on 2012-01-03
Cheers although reading through all of this all points to people having trouble getting any sound at all.
 
I do have sound over HDMI :) although my problem is that it is all downmixed to 2 channel since the Audio driver is 2 channel only.
 
I did some more searching after looking through the ALSA output.
 
ALSA tells me that I have a ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310].
 
Some googling gave me [http://www.ubuntu.com/certification/catalog/category/AUDIO](http://www.ubuntu.com/certification/catalog/category/AUDIO) which shows Ubuntu 11.10 and my sound hardware.
 
My guess is that my install of 11.10 didn't include this driver ..... how do I find it?
 
Cheers, Duncan

---

### Post by BicyclerBoy on 2012-01-03
The HDA audio device uses alsa snd_hda_intel

For HDMI audio you need to use the proprietary video driver (nVidia & AMD).

The APU/mobo audio device labels are confusing but it looks to me that card0 is the HDA HDMI codec. (could be wrong).

Look for eld files in:
ls -al /proc/asound/card0/eld*

For example if eld#1.0 exists then post the contents:
cat /proc/asound/card0/eld#1.0


Try:
speaker-test -c 2 -r 48000 -D hw:0,3
speaker-test -c 6 -r 48000 -D hw:0,3

---

### Post by jocko on 2012-01-04
> **duncang92 said:**
> I do have sound over HDMI :) although my problem is that it is all downmixed to 2 channel since the Audio driver is 2 channel only.
HDMI and spdif has always been reported as digital stereo, so that's not your problem...
If all you want to accomplish is passthrough of dolby or dts, see my reply to [this thread]("http://ubuntuforums.org/showthread.php?t=1902638")...

---

### Post by duncang92 on 2012-01-12
Here's the output:


root@xbox:~# ls -al /proc/asound/card0/eld*
-rw-r--r-- 1 root root 0 2012-01-12 16:00 /proc/asound/card0/eld#0.0


root@xbox:~# cat /proc/asound/card0/eld#0.0
monitor_present		1
eld_valid		1
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0


If I check card1 then:

root@xbox:~# ls -al /proc/asound/card1/eld*
ls: cannot access /proc/asound/card1/eld*: No such file or directory
root@xbox:~# cd /proc/asound/card1
root@xbox:/proc/asound/card1# ll
total 0
dr-xr-xr-x 5 root root 0 2012-01-12 16:02 ./
dr-xr-xr-x 5 root root 0 2012-01-12 16:02 ../
-r--r--r-- 1 root root 0 2012-01-12 16:02 codec#0
-r--r--r-- 1 root root 0 2012-01-12 16:02 id
dr-xr-xr-x 3 root root 0 2012-01-12 16:02 pcm0c/
dr-xr-xr-x 3 root root 0 2012-01-12 16:02 pcm0p/
dr-xr-xr-x 3 root root 0 2012-01-12 16:02 pcm1p/

and for card0:

root@xbox:/proc/asound/card1# cd ../card0
root@xbox:/proc/asound/card0# ll
total 0
dr-xr-xr-x 3 root root 0 2012-01-12 16:03 ./
dr-xr-xr-x 5 root root 0 2012-01-12 16:02 ../
-r--r--r-- 1 root root 0 2012-01-12 16:03 codec#0
-rw-r--r-- 1 root root 0 2012-01-12 16:03 eld#0.0
-r--r--r-- 1 root root 0 2012-01-12 16:03 id
dr-xr-xr-x 3 root root 0 2012-01-12 16:03 pcm3p/
root@xbox:/proc/asound/card0#

---

### Post by duncang92 on 2012-01-12
I read through the following and I know what you're saying here ..... I tried the same modified for the fact that I'm using XBMC and could only get the usual "Device not initialized. Check Audiosettings".


> **jocko said:**
> HDMI and spdif has always been reported as digital stereo, so that's not your problem...
If all you want to accomplish is passthrough of dolby or dts, see my reply to [this thread]("http://ubuntuforums.org/showthread.php?t=1902638")...

---

### Post by BicyclerBoy on 2012-01-12
Your card0/eld#0.0 shows
connected monitor & valid eld...but the eld contents are all zero..
so the audio capabilities are not reported correctly & you get default stereo only.

dmesg | grep HDA

You are using AMD catalyst driver ?
You have only 1 HDMI monitor/TV/AVR connected ?
This is connected to the video card directly ?
What alsa (user space) version does speaker-test report ?

---

### Post by duncang92 on 2012-01-13
dmesg shows:


dmesg | grep HDA
[   33.105150] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   33.105240] HDA Intel 0000:00:01.1: irq 41 for MSI/MSI-X
[   33.105277] HDA Intel 0000:00:01.1: setting latency timer to 64
[   33.176537] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.601357] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input7

You are using AMD catalyst driver ?

I couldn't find a specific AMD catalyst driver for the audio, only the video. For the video I am using the "AMD Catalyst™ 11.11 Proprietary Linux x86 Display Driver". I tried the Ubuntu "Additional Drivers" and the two video drivers would kill my system and there are no additional sound drivers listed.


You have only 1 HDMI monitor/TV/AVR connected ?

1 HDMI output from the motherboard (my mobo has integrated sound and video) directly to the TV.

This is connected to the video card directly ?

Yes. Mobo to TV.

What alsa (user space) version does speaker-test report?

speaker-test 1.0.24.2

---

### Post by BicyclerBoy on 2012-01-14
Meant to ask for dmesg | grep HDMI
but this is already in your alsa config dump (from the alsa info script).
And there is no human readable ELD info reported there..

Try multi-ch LPCM pink noise from terminal:
speaker-test -c 6 -r 48000 -D hw:0,3

You do not need any special driver for the audio codec. All the HDMI audio codecs are HDA-intel standard compliant. There could be some AMD APU specific stuff in that driver tho'...

It is very possible that the AMD driver does not yet allow HDA over HDMI for your chipset/APU.
AMD were very concerned about exposing the HDCP & related HDA mechanisms in there drivers.

---

### Post by duncang92 on 2012-01-16
Here's the speaker-test return:


root@xbox:~# speaker-test -c 6 -r 48000 -D hw:0,3

speaker-test 1.0.24.2

Playback device is hw:0,3
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument


Anything other than a speaker count of 2 gives the "Invalid argument" return.

My guess being that the Sound panel in System Settings etc. only shows the card as being "Digital Stereo (HDMI) Output" and checking "Test Speakers" only shows me Front left and Front right.

i.e. my loaded audio driver only allows 2 channel and there is no 5.1 driver available. Hence all of my issues.

I am certainly becoming resigned to the fact that I may have to buy a sound card and use up my only PCI-E slot ... bummer since I wanted to add a TV-in card  and add PVR capabilities to my XBMC.

But how to have a separate sound card and still run audio and video out on one HDMI lead?

---

### Post by BicyclerBoy on 2012-01-16
Sound cards are just a waste of money & a slot..
Only a HDMI output soundcard (or some custom digital interface to expensive DAC) will match the performance of the video card output..

HDMI audio on AMD APU/etc hardware is still 'a work in progress'
[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)

The root cause of your problem is you do not have any ELD over HDMI reported..so alsa does not know the audio capabilities.

You should be okay getting AC3/DTS 5.1 S/PDIF over HDMI.
You can not test using speaker-test..

---

### Post by shantiq on 2012-01-17
> **cbowman57 said:**
> Unfortunately it's hardware specific so there isn't a generic recipe, but there are some good threads, FAQs & Wikis that walk you through it.  There is a really good thread hidden here in the archives that I can hardly ever find, but the Archwiki is easy to find & most everything applies.

Basically the out-of-the-box alsa & pulseaudio configuration use low-mid quality settings. On my system the default was low bit-rate playback, the wrong drivers & they capped pulse audio cpu usage, so I gave it the right driver, increased playback bit-rate, changed the 'nice' level.  It's been awhile since I've made changes so I've forgotten most of what I did.

Here are some key entries in the daemon.conf worth looking at:
**nice-level** = (I use -3)
**resample-method** = (I use speex-float-9 or src-sinc-best-quality)
**default-sample-format** = (you'll need to determine this from instructions in wiki, I use float32le)
**default-sample-rate** = (Device & resource dependent, I use 96000)

If you have a surround type system you may want to mess with default-sample-channels & default-channel-map but I only have a simple sub w/2 speakers so didn't bother with that.



thank u for this will play with it all sometime soon  :KS

---

### Post by cbowman57 on 2012-01-17
> **shantiq said:**
> thank u for this will play with it all sometime soon  :KS

It's worth the time & effort if you enjoy good sound fro your PC.  Go slow & backup. :)

---

### Post by duncang92 on 2012-02-10
Well I fixed it .... kinda.

I upgraded to Catalyst 11.12 and suddenly found that I could now set the custom sound settings in XBMC to use passthrough (plughw:0,3 in my case) which allows my sounds system to do all the decoding ..... basically what I wanted in the first place.

Before I upgraded to Catalyst 11.12 if I tried the custom passthrough setup then as soon as I would try playing a movie/TV show I would get the old favourite "Could not initialize audio device" error from XBMC.

Cheers, Duncan


> **BicyclerBoy said:**
> Sound cards are just a waste of money & a slot..
Only a HDMI output soundcard (or some custom digital interface to expensive DAC) will match the performance of the video card output..

HDMI audio on AMD APU/etc hardware is still 'a work in progress'
[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)

The root cause of your problem is you do not have any ELD over HDMI reported..so alsa does not know the audio capabilities.

You should be okay getting AC3/DTS 5.1 S/PDIF over HDMI.
You can not test using speaker-test..

---

