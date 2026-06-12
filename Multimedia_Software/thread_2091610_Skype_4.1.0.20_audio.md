---
title: "Skype 4.1.0.20 audio"
date: 2012-12-05
forum: Multimedia Software
---

### Post by msknight on 2012-12-05
Hi Folks,

I recently rebuilt my machine and the new version of Skype not only doesn't play nice, but I can't revert to a previous version easily either.

Machine is a FitPc3, 64 bit, running Ubuntu 12.04 which has been swapped to the lubuntu desktop and the gnome-panel.

Hardware device are...
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The only one active is the ALC888 analogue.

Everything else works. I get the sound when Ubuntu starts, VLC and all other sound devices work fine.

I've tried various fixes that I've found on the internet, but no joy. I've selected all sorts of devices in the set up, and the errors remain more or less constant.

Running Skype from a terminal and then going in to the sound options, generates errors like the following...

```
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib dlmisc.c:254:(snd1_dlobj_cache_get) Cannot open shared library /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:551:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
```

TIA for any help.

---

### Post by eotakos on 2012-12-11
Hello,

I've recently switched to 12.04 64bit and I had issues with skype, so I figured I should pop in. My problems in particular concerned the microphone. That was the main problem, even though in the 'trial and error' method I followed, at times the output was messed up as well.

So, to describe how it went, when I tried to make a call it would immediatelly drop saying 'problems with audio capture', and when I had an incoming call... well, it would just crash. Assuming that you confirm that your mic. is working from the 'sound settings' (which then illiminates the posibility that is a system's error), you can try this:

[http://askubuntu.com/questions/163729/microphone-is-not-working-in-skype](http://askubuntu.com/questions/163729/microphone-is-not-working-in-skype)

which is what I did and worked. In particular, i ran 'gstreamer-properties' and I opted for 'pulse' for audio input, instead of the 'alsa' driver that the link above suggests.

Afterwards, you go to the skype options-> sound devices, and you set there pulse as well. If it doesn't work with the first go, try restarting the computer to make sure it doesn't work :)

good luck, I hope you find this usefull


EDIT : (CORRECTION)
It seems that what I suggest right above is not stable, not a permanent solution at all. It worked for me for two sessions and then, I don't know for what reason it stopped again. Probably some update. Skype continuous to work, but it crashes on incoming calls, and it automatically hangs-up the outgoing calls. I think I'm going to try updating to 12.10... betting that another kernel might cooperate better with the program.

---

### Post by msknight on 2012-12-24
I tried 12.10 - no joy. Same as before, even when I tried the 2.x version first before loading the 4.x skype.

---

### Post by Swistak84 on 2013-01-29
I had very simmilar problem and similar error messages, I've located missing files in libasound2-plugins, trick was to intall 32bit version:

aptitude install libasound2-plugins:i386

---

### Post by gordintoronto on 2013-01-29
Perhaps installing multiarch-support would help. Skype 4.1.0.20 works beautifully for me on 64-bit Mint 13, which is built on Ubuntu 12.04.

---

### Post by Fishnuts on 2013-03-20
> **Swistak84 said:**
> I had very simmilar problem and similar error messages, I've located missing files in libasound2-plugins, trick was to intall 32bit version:

aptitude install libasound2-plugins:i386

This solved my issues! I'm running LMDE

Thanks!

---

### Post by Amigozz on 2013-05-11
> **gordintoronto said:**
> Perhaps installing multiarch-support would help. Skype 4.1.0.20 works beautifully for me on 64-bit Mint 13, which is built on Ubuntu 12.04.


thank so much! It helped me on ubuntu 12.04 x64!

---

### Post by apteryx-deb on 2013-08-30
Thank's> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Swistak84**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12480839#post12480839")                 
                 I had very simmilar problem and similar error  messages, I've located  missing files in libasound2-plugins, trick was to  intall 32bit version:

aptitude install libasound2-plugins:i386

---

