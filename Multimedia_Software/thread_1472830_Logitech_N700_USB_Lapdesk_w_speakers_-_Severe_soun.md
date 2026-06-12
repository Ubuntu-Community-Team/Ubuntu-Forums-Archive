---
title: "Logitech N700 USB Lapdesk w/ speakers - Severe sound crackling"
date: 2010-05-04
forum: Multimedia Software
---

### Post by El Lance-O on 2010-05-04
The product I am using can be seen [here]("http://www.logitech.com/en-us/notebook_products/cooling_pads/devices/6564").

I've been reading a lot about the USB sound crackling issue, and it's nothing new, mostly with USB sound cards. The N700 is laptop cooling pad with built-in speakers. They work FANTASTIC with music and streaming radio, but whenever I watch a video, using Totem, Mplayer, or VLC, it crackles to the point of it being unwatchable. VERY loud pops.

The threads I have found on this matter are:
[here]("http://forum.synology.com/enu/viewtopic.php?f=63&t=22429"), [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755"), and [here]("http://ubuntuforums.org/showthread.php?t=1459251").

It seems to be a severe issue with Pulseaudio, but there doesn't seem to be a way to set ALSA as the default sound driver. Lucid Lynx seems to greatly inhibit options to the user, including login screen options, so overall this just seems like a non-user friendly release IMO.

If anyone could help, I would be greatly appreciated. Let's get rid of these rice crispies in my speakers! :popcorn:

---

### Post by El Lance-O on 2010-05-04
The product I am using can be seen [here]("http://www.logitech.com/en-us/notebook_products/cooling_pads/devices/6564").

I've been reading a lot about the USB sound crackling issue, and it's nothing new, mostly with USB sound cards. The N700 is laptop cooling pad with built-in speakers. They work FANTASTIC with music and streaming radio, but whenever I watch a video, using Totem, Mplayer, or VLC, it crackles to the point of it being unwatchable. VERY loud pops.

The threads I have found on this matter are:
[here]("http://forum.synology.com/enu/viewtopic.php?f=63&t=22429"), [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755"), and [here]("http://ubuntuforums.org/showthread.php?t=1459251").

It seems to be a severe issue with Pulseaudio, but there doesn't seem to be a way to set ALSA as the default sound driver. Lucid Lynx seems to greatly inhibit options to the user, including login screen options, so overall this just seems like a non-user friendly release IMO.

If anyone could help, I would be greatly appreciated. Let's get rid of these rice crispies in my speakers! :popcorn:

---

### Post by El Lance-O on 2010-05-04
Upon further testing, I've noticed a couple more things.

Crackling:
.avi playback
.divx playback
Streaming Shoutcast TV

No Crackling:
Flash video
.mp3 playback
Streaming radio (Pandora, Shoutcast)
.mp4 video playback (one file I tried worked fine)

This seems to be an encoding issue, maybe a sound frequency conflict? Any thoughts on how to set a new system-wide encoding rate?

I really just want to watch some movies without the sound of a miniature war in my speakers.

---

### Post by El Lance-O on 2010-05-04
Upon further testing, I've noticed a couple more things.

Crackling:
.avi playback
.divx playback
Streaming Shoutcast TV

No Crackling:
Flash video
.mp3 playback
Streaming radio (Pandora, Shoutcast)
.mp4 video playback (one file I tried worked fine)

This seems to be an encoding issue, maybe a sound frequency conflict? Any thoughts on how to set a new system-wide encoding rate?

I really just want to watch some movies without the sound of a miniature war in my speakers.

---

### Post by Iowan on 2010-05-04
Threads merged.
From the Code of Conduct:
> Please do not cross post, or post the same thing in multiple locations.

---

### Post by El Lance-O on 2010-05-04
Yeah, thanks for the *help*. :roll:

Anyways, back to the issue:

I've also noticed that SOME flash video crackles, but not others. Definitely seems like an encoding conflict somewhere. I've tried switching to ALSA and OSS, still no change.

I'm not familiar with audio systems, so I really have no idea where to begin to fix this.

C'mon, someone has to have *some* kind of an idea!

---

### Post by El Lance-O on 2010-05-05
bump

---

### Post by El Lance-O on 2010-05-08
And again, bump.
This is a severe pulseaudio issue, there has to be SOMEONE that can help.

108 people have looked at this thread, obviously I am not alone in this problem.

---

### Post by lidex on 2010-05-08
I'm not convinced this belongs to pulse. It seems to me all audio would be affected in that case. Which specific apps are problematic?

---

### Post by El Lance-O on 2010-05-09
It seems to be system-wide. VLC, Mplayer, Totem, Firefox, anything really.

Whenever I go to gstreamer-properties and change the architecture to ALSA and test the pipeline, the crackling is still there so you may be right, but I'm still convinced it is related to Pulseaudio in someway.

I've used ALSA with no problems in the past, but now that Pulseaudio is default, it seems to cause quite a bit of problems.

---

### Post by lidex on 2010-05-11
Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

---

### Post by Nythain on 2010-05-14
I've had similar problems with lucid, except mine go as far as to completely cut one speaker out unless i turn the sound way up, and even at around 50% volume, everything sounds like its being played at 200% volume... here's hoping the above link helps

---

### Post by El Lance-O on 2010-05-20
> **lidex said:**
> Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

Nope, that didn't help. There is still severe popping. It's not stuttering, but it sounds like someone is snapping millions of twigs in my speakers.

It has gotten to the point where when I start Ubuntu, I have to manually start pulseaudio before I can even access my sound options, and the volume jumps erratically when I change it. Sometimes it will not work properly, and only Dummy Audio shows up under output, rendering sound VERY quiet.

---

### Post by [A]madeus on 2010-05-20
> **lidex said:**
> Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html](http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html)

lidex, Thanks for your suggestion but it doesn't work for me as well.

El Lance-O, i'd like to share that the cracking sound happens noticeably every time Firefox or Chromium is running with Flash plug-in contents. Seldom to find the cracking sound when running Totem solely.

i'm using Bose USB Audio as an external speaker.
[PHP]
amadeus@amadeus-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

amadeus@amadeus-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

amadeus@amadeus-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1981
[/PHP]

---

### Post by lidex on 2010-05-20
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

### Post by [A]madeus on 2010-05-20
lidex, many thanks for your help. 

The cracking sound seems to have a lot improvement now.
i installed the ALSA backports, as your suggestion.

It still happened some cracking sound whenever i play a Flash game on Facebook and listen to a music from Rhythmbox at the same time.
It is so MUCH better than before, though :))

lidex, if you don't mind, please help me answer a question.
1. Is the ALSA backport something i should install manually after upgrade to Lucid? Or i just missed it at the first place (i upgraded to Lucid via Update Manager).

Thank you again for your help, i appreciate it. :KS

---

### Post by lidex on 2010-05-20
> **'[A]madeus said:**
> lidex, many thanks for your help. 

The cracking sound seems to have a lot improvement now.
i installed the ALSA backports, as your suggestion.

It still happened some cracking sound whenever i play a Flash game on Facebook and listen to a music from Rhythmbox at the same time.
It is so MUCH better than before, though :))

lidex, if you don't mind, please help me answer a question.
1. Is the ALSA backport something i should install manually after upgrade to Lucid? Or i just missed it at the first place (i upgraded to Lucid via Update Manager).

Thank you again for your help, i appreciate it. :KS

You're welcome. Not sure what is causing the continuing problem and I am sure that will bug me until I figure it out. The backports are a manual install item - not everyone needs them and some are better off will a full alsa upgrade.

---

### Post by El Lance-O on 2010-05-21
Nope, crackling still present after update of kernel and install of backport updates for ALSA.

For example, when I do an audio test under gstreamer-properties, it is nothing but constant and consistent crackling, it almost sounds like the speakers are damaged. However it works flawlessly under Windows and Mac, so this is certainly an Ubuntu issue.

Thanks again lidex for being so helpful, I really appreciate the prompt support! =D>

---

### Post by absolut1983 on 2011-11-14
Hi, folks.

I'm considering buying the N700 lapdesk with speakers and I'd like to know if you guys are still experiencing problems with it even three development cycles later.

Thanks.

---

### Post by lindude on 2011-12-06
> **absolut1983 said:**
> Hi, folks.

I'm considering buying the N700 lapdesk with speakers and I'd like to know if you guys are still experiencing problems with it even three development cycles later.

Thanks.

I wouldn't buy it again. I've read many fixes but nothing seems to help me, I'm a noob though and might have messed things up by trying this and that,

---

