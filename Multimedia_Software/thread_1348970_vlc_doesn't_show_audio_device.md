---
title: "vlc doesn't show audio device"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Hesediel on 2009-12-07
My vlc doesn't show the Audio Device on settings, so i can't select for example the 5.1 setting.
In some videos the channel settings aren't displayed too

---

### Post by mc4man on 2009-12-07
If you are using pulseaudio as an output then there will be no choice for audio device like you'd see for alsa or others

---

### Post by Hesediel on 2009-12-07
if i select alsa as outpout the problem still remains

---

### Post by mc4man on 2009-12-07
> if i select alsa as outpout the problem still remains 

Did you click save in vlc's preferences, close and re-open vlc?

As far as proper 5.1 sound I only know in regards to my hardware (audigy 2 ZS) and hardy, karmic
Hardy - got rid of pulse entirely and used alsa no issues

Karmic - for the most part pulse works fine, vlc has the 'weakest' pulseaudio support, but sounds crappy or not at all on alsa.
Plus using alsa w/vlc required switching the device in vlc's setting to get actual 5.1 output vs. 6 ch. mixing. ( to hw:0,3) Then with other non 5.1 audio had to switch back to the default device to get any output.
Hardly worth it

If you have any other card post what it is, maybe someone knows it.

screen shows vlc playing a dts track, sounds excellent with pulse

---

### Post by Hesediel on 2009-12-08
I have a mobo P5KC with ALC883. I make save yes.. My low frequency doesn't work...it works only:

you can see my other post if you understand what i wrote.

[http://ubuntuforums.org/showthread.php?p=8457784#post8457784](http://ubuntuforums.org/showthread.php?p=8457784#post8457784)

But there are some videos where you can select channels and devices audio  (stereo, mono, surround 5.1) my menu in vlc for choosing this doesn't works. It worked once but at system restart, it was gone.

---

