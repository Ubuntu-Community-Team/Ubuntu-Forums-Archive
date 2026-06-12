---
title: "HOWTO set digital out as default ALSA device"
date: 2008-05-24
forum: Multimedia Software
---

### Post by realn on 2008-05-24
I have a very simple question for which I couldn't find any answer. It's a shame that such simple things are so complicated sometimes.

Config: Kubuntu 8.04, with following soundcard:

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I would like to be able to:
1) Set the digital output as the default device in ALSA. For the moment I can use it, but only by setting it in EACH application as output device hw=0,1. I had to do it for xmms&mplayer, don't even know how to do it for VLC ( I mean I couldn't make it work).

2) Have a master volume control for this digital output. For the moment I can control it only in each application if I set it to "use software control". I couldn't find any other way to control it.

3) Be able to share this output among several multimedia applications : there is to say play several sound sources at the same time.

It might seem trivial, please help me, I spent a couple of days on these issues. 
Note: I don't have any .asoundrc, /etc/asound.conf config files. Also alsaconf is apparenlty removed from alsa-utils. Anyway, I wouldn't have known how to use it.
Thank you all.

---

### Post by realn on 2008-05-25
Could someone please help me ?

---

### Post by Zorael on 2008-05-26
I'm just guessing now, but I think you can set it by creating/modifying your [FONT="Courier New"]/etc/asound.conf[/FONT] file (system-wide) or your [FONT="Courier New"]~/.asoundrc[/FONT] file (user-specific) to look something like this.
```
pcm.!default { 
type hw 
card 0 
device 1 
}
ctl.!default { 
type hw 
card 0 
device 1 
}
```

---

### Post by realn on 2008-12-12
Uber-cool. It worked !
Now I have a couple of more questions:
1) How to control the volume with this settings - for the moment I can use the volume from the player application: smplayer, xmms. But I have a radio screenlet with no volume control and I cannot control at all the volume for this one.
2) How do I play several audio sources simultaneously? For the moment, I launch the radio player, I have sound. If I launch another player with another audio source - no sound.

 Thank you all for your support.

---

### Post by pseudonym on 2008-12-12
By writing your ~/.asoundrc that way you disable software mixing. There are two things you can do instead -

**Option 1** -

1. Remove your ~/.asoundrc file, log out, then log back in again.

2. sudo aptitude install gnome-alsamixer

3. Open GNOME ALSA Mixer from the Multimedia menu and see if you have an option for 'IEC958' output or similar. On my card (X-Mystique, based on C-Media 8768 ) I can toggle between digital and analogue using a checkbox in GNOME ALSA mixer. This is very handy, as I have up to three different speakers connected to my machine.

**Option 2** -

1. Keep GNOME ALSA Mixer installed, even if option 1 didn't work for you.

2. Write a more sophisticated ~/.asoundrc file following step 4 of these instructions [here]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound"). Ignore the fact that it's for Myth TV.

3. Once you have your ~/.asoundrc, log out, then log back in again. You should now be able to play sound from multiple sources.

NB. I do not know how, or if, the above is affected by pulseaudio, as I do not have that installed on my system.

**Oops! Just noticed you're using Kubuntu. You should be able to set the default sound device in the K Control Centre (I've forgotten how, but it's fairly easy). If that doesn't work, and you want to try option 2 above, you will need to turn off the ArTS sound server by setting it in K Control Centre to not run at startup.**

---

