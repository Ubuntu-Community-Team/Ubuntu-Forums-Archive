---
title: "Pulseaudio - 2 Problems"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by gwinston99 on 2008-03-23
I have the latest version (0.9.9) of Pulseaudio installed and working in Gutsy on two pc's on my home LAN.  Works great, except for two limitations:

1.  I cannot stream audio from one pc to the other which is connected to my home theatre audio system.  I have tried copying the .pulse-cookie file from one machine to the other, but when I run pabrowse on either machine it still shows different cookie values on each machine.

2.  Real-audio streams (from Real Player or the Rhapsody plugin) are not picked up as streams by pulseaudio, and so cannot be redirected to another device.

Any troubleshooting input would be greatly appreciated.

Thanks,

Gregg Winston

---

### Post by gatman3 on 2008-04-30
Gregg,

I'm not an authority, but... I have some experience with trying to get the linux Rhapsody plugin to do what I want, and I'm afraid you (and I) are probably outta luck with this one.  I have just started playing with pulseaudio and haven't played around with Rhapsody yet over pulseaudio, but I have in the past been unable to get Rhapsody to work over anything other than the default ALSA hw:0,0 sound device.  My original motivation was to get Rhapsody to play to a USB sound device (Turtle Beach Audio Amigo) because my headphone jack on my laptop is broken.  No go.  The Rhapsody plugin routinely crashed when I attempted this.  Not even sure, perhaps Rhapsody doesn't even use ALSA at all.

My guess is that the Rhapsody developers have Rhapsody hard coded to go to the default sound device in ALSA, thereby preventing direct digital streaming to a recording application.  I tried contacting them to get them to admit this, but their support is total mish mosh.  I got answers from the kind of like "wow, I never tried that", or "workaround this by using the default audio device".  It was oh so helpful.

Anyhow, my guess is that pulseaudio will hit the same brick wall with Rhapsody.  But I'm going to try it soon, and I'll let you know if I can get it to work.

---

### Post by gatman3 on 2008-05-01
Quick update...  I have been successful getting pulseaudio to work with the typical audio applications.  Still no joy with Rhapsody.  If anyone knows of a solution, love to hear it!

---

