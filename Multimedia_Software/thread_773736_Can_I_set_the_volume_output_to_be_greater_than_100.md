---
title: "Can I set the volume output to be greater than 100%?"
date: 2008-04-29
forum: Multimedia Software
---

### Post by bryan.taylor on 2008-04-29
Some of my media files have the sound encoded at a low volume.  I have to turn up my tuner volume all the way, and it's still too quiet for some of the files.

Is there a way to set the output volume to something greater than 100% using totem, mplayer, or vlc?  I'm using hardy with pulseaudio.

Thanks for your help guys.

---

### Post by Bubba64 on 2008-04-29
Have you right clicked on volume icon and clicked on volume control to see if maybe you have PCM and master or another controlling the volume.

---

### Post by ad_267 on 2008-04-29
If there's only a few of these files then you could open them with audacity and increase their volume.

---

### Post by bryan.taylor on 2008-04-30
Bubba, I'm using PulseAudio, so I don't think I can independently set the Master and PCM levels.  Those are alsa sliders, right?

ad_267, thanks for the tip.  I may do that in the future.

For now I've found that vlc will allow me to set the volume to something greater than 100% (it sounds significantly louder).  It has a volume slider that goes up to 1024 in the configuration section.  My brother tells me that the mac version of vlc allows you to set the volume to 400%.  I assume that 100% in the linux version would be 256 and that the 1024 is 400%, although it doesn't sound like it's really 4 times louder.

---

### Post by jocko on 2008-04-30
> **bryan.taylor said:**
> Bubba, I'm using PulseAudio, so I don't think I can independently set the Master and PCM levels.  Those are alsa sliders, right?

Well, if the volume is turned down in alsa, pulseaudio will never give full output. Check alsamixer.
There may be a way to increase the output level from an individual stream in pulseaudio:
1. Install padevchooser (it will bring some tools for pulseaudio).
2. Start PulseAudio manager (e.g. Program --> Audio & Video --> PulseAudio manager).
3. Go to the"Devices" tab, double click the output stream you want to change.
4. See the volume slider? At least for me it goes up to 480%.

If you like this, you can set padevchooser to start up when you log in (Program --> Audio & Video --> PulseAudio Device Chooser). It will start up in the notification area with shortcuts to other pulseaudio tools. click the icon, select Preferences and set it to start up at session login.

---

### Post by bryan.taylor on 2008-05-12
jocko, thank you very much.  That's exactly what I was looking for. :)

---

