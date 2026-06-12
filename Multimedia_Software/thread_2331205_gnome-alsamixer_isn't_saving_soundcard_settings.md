---
title: "gnome-alsamixer isn't saving soundcard settings"
date: 2016-07-19
forum: Multimedia Software
---

### Post by bofh19612 on 2016-07-19
I'm using 16.04 on a Dell D630 laptop and outputting digital audio via the S/PDIF port on the docking station.  I've disabled pulseaudio by putting "autospawn=no" in the client.conf file.  Since I've done that gnome-alsamixer needs to have the soundcard IEC958 checkbox ticked after every reboot.  It won't remember the setting for that parameter although it does remember the PCM volume setting.  Any ideas?

---

### Post by QDR06VV9 on 2016-07-19
So are you saying that Pulseaudio volume controller will not let you select your <your soundcard> IEC958 Device as Default?
But you will have to re-enable pulseaudio.
Maybe I am just missing something here.

---

### Post by bofh19612 on 2016-07-19
I control the volume in gnome-alsamixer's PCM level.  To get the s/pdif output working I have to tick both IEC958 and IEC958 PCM in gnome-alsamixer.  The tick for PCM is enable by default but the other one gets forgotten every time I reboot.  Oddly, gnome-alsamixer remembers changes I make to the mixer volume.  The alsamixer app that is launched in a terminal doesn't let me enable the card at all although it shows it.  The problem with pulseaudio is that you can't uninstall it without removing other stuff.  Oh, it degrades the sound quality as well...

---

