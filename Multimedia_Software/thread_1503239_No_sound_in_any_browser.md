---
title: "No sound in any browser"
date: 2010-06-06
forum: Multimedia Software
---

### Post by SPARTAN-118 on 2010-06-06
Okay, I know that there have been a few threads with this problem, but let me just say that no fix has worked insofar. 

This includes turning PCM to max, and uninstalling the Kaffeine Mozilla plugin. The latter did not work, as apparently, according to KPackageKit, said plugin is not installed.

I do not believe that this is an issue with flash, rather, it is the recent upgrade I performed, the one that added all those multiple GRUB options.

I was using [Sabayon Linux]("http://www.sabayon.org/") not too long ago, and one kernel would work, while the other only had sound with non-internet applications.
Kubuntu, however, has this problem with both kernels.

This poses a problem for me, as, while I do enjoy my music, I occasionally go on sites such as YouTube. Which, obviously, needs sound.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```In my sound preferences, I have USB Audio set as Preferred for all categories (Playback and Capture). However, as mentioned, sound only works for non-internet apps.

Another issue I have is that USB Audio is also a 7.1 card, but is only recognized as 2.1. This may be unrelated, but any fix that would solve both these puzzles would be greatly appreciated.

Thanks,
Matt.

---

### Post by SPARTAN-118 on 2010-06-15
As it's been a week, and I would really like to watch flash videos and play online games in my browser, I just thought I'd give some more information.

Google Chrome started displaying "missing plug-in" on some pages, and Youtube said to upgrade to latest flash player. So, I went and downloaded the [development version of Chrome with integrated flash](http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html).

So, now Flash works - but still no sound. :(

---

### Post by SPARTAN-118 on 2010-06-15
As it's been a week, and I would really like to watch flash videos and play online games in my browser, I just thought I'd give some more information.

Google Chrome started displaying "missing plug-in" on some pages, and Youtube said to upgrade to latest flash player. So, I went and downloaded the [development version of Chrome with integrated flash](http://googlechromereleases.blogspot.com/2010/03/dev-channel-update_30.html).

So, now Flash works again - but still no sound. :(

---

### Post by SPARTAN-118 on 2010-06-18
New - and disturbing - update: it seems my system will only play sound through Amarok and system sounds. This means no VLC media player or Dragon video player. I usually use Youtube for my video needs, but since it appears flash is being screwy, I turned to some videos I've had on my computer for a while.

Well, I tried watching a few of my videos, but none had sound (the most recent video is [here]("http://eecomics.net/?strip_id=1163"), it is an animation of a comic I read. Click on the "location" link beneath the video and download the .avi file). 
Yet Amarok *does* have sound.
Odd?
Yes, but not really, if it just has to do with what sound engine these programs have. Question is, How Do I Get These Programs to Output Sound to my Default Sound Module/Engine/Sound Card???

Thanks, 
Matt.

---

### Post by lovinglinux on 2010-06-27
Try [http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

### Post by SPARTAN-118 on 2010-06-30
Finally, a reply! :P

Unfortunately, I have a very unique case. I have an external sound card with my laptop, through which sound must play to my 5.1 (only recognized as 2.1 so far on any Linux) Logitech X-540 speakers.

Playing through Pulse Audio (a sound server that is too complex for my tastes) does not output via this sound card. And no, it's not a result of my using this sound card that I have no audio in browsers.

As you can see [here](http://ubuntuforums.org/showthread.php?t=1490855), I've mentioned my sound card before. I had wanted to stick with Xfce, but I ended up switching to a KDE desktop because it's the only one that will work with the sound card.

Also, for some reason I have no "alsaconfig" command via the Terminal, yet I can adjust the settings via the GUI Mixer in the Panel Notification area, so I've already tried the universal "adjust PCM to max" solution. And how does that help, anyway? I thought PCM was capture? :?

Matt.

---

### Post by Yellow Pasque on 2010-06-30
Ok, so you have your KDE system settings preferring your USB audio, but that only controls Phonon and apps that use it (like amarok and KDE system sounds). Apps that use ALSA directly (Flash, Chrome, maybe VLC) are most likely trying to output to your onboard audio, since it has index 0. Fix this in /etc/modprobe.d/alsa-base.conf (make sure you have kdesudo installed and you can use either kate or kwrite depending on which of them is installed):
```
kdesudo kate /etc/modprobe.d/alsa-base.conf
```
Add to the end:
```
options snd-usb-audio index=0
options snd-hda-intel index=1
```
Save. Quit. Restart.
If it doesn't work, make sure you can play a sound file on the USB using aplay. More info: [http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

---

### Post by SPARTAN-118 on 2010-07-01
When you say "at the bottom," do you mean at the very bottom, or with the rest of the "options"? Because either way, I don't think it really helps much.

Here is my alsa-base.conf file:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
[B]options snd-usb-audio index=0
options snd-hda-intel index=1[/B]
```

That's with the alterations you suggested.

Also, can you tell me the command(s) for aplay-ing sound through the USB? I've been to that link before, and I cannot make heads nor tails of it.

Thanks,
Matt.

---

### Post by Yellow Pasque on 2010-07-01
Yes, just like that. Now boot with that and post your aplay -l

---

### Post by SPARTAN-118 on 2010-07-04
My "aplay -l" has always outputted the following, even BEFORE adding in the options you suggested:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Perhaps "Preferring" the device in System Settings-> Multimedia caused it to be set as default, but obviously that hasn't helped with my Flash problem.

---

### Post by lidex on 2010-07-06
Have you seen this thread:
[http://ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")

More simply:
[http://symbolik.wordpress.com/2009/05/18/kubuntu-9-04-and-flash-audio/]("http://symbolik.wordpress.com/2009/05/18/kubuntu-9-04-and-flash-audio/")

---

### Post by SPARTAN-118 on 2010-07-07
I really need to combine threads or something.

The reason I didn't choose Ubuntu over Kubuntu (Gnome over KDE) is because PulseAudio won't detect my sound card - at ALL. That means, it doesn't even appear in the Output/Hardware tab. So that solution does nothing for me.

Another thing that I found quite odd is that, even when I unplug the USB soundcard, no sound comes out of my laptop's speakers. I figure, since Kubuntu is not detecting my speakers as 5.1, I might as well just plug it in to my laptop directly through the headphone port. I would get crappier sound quality, but perhaps using an internal, onboard sound source would help with my Flash problems.

I will check back later, after I have tried this.

EDIT: HAHA! I have solved my problem by doing what I mentioned earlier in this post. In System Settings -> Multimedia, I preferred "Intel HDA" for everything, and now Flash plays sound! :D
(Smileys cannot express how I feel right now!)

---

### Post by aravind4j on 2012-04-30
i too have the same problem but mine is desktop and i have 5.1 sound card to my system but even after selecting the master channel as my sound card !! it still has the same problem :( 
no sound in anything except amarok & vlc player 

please help 
 :confused:

---

