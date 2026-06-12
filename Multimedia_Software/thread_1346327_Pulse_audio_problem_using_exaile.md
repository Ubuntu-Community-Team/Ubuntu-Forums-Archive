---
title: "Pulse audio problem using exaile"
date: 2009-12-04
forum: Multimedia Software
---

### Post by slaveofone on 2009-12-04
I have a virtually brand-new installation of Ubuntu Studio 9.10. When I load a bunch of songs into Exaile and press play, everything works great for about an hour or so and then suddenly the sound just dies and my system goes into overdrive until I kill Exaile. This is the message that pops up:

pa_stream_writable_size() failed: Connection terminated

I was able to find a little bit of a work-out by changing Exaile's playback engine. Using "Gnome" or "Pulseaudio," after about an hour, the system hiccups again, but instead of stopping all music and going into 99% processor use, it gives me that error, skips to the next track, and continues playing for another hour before repeating the process.

I have installed xmms2 and used that for extended periods of time without experiencing this error.

Anyone know how I can fix this?

---

### Post by slaveofone on 2009-12-08
The error message continues to pop up after about an hour of continuous play. I have also now noticed that xmms2 every once in awhile will stop playing music and begin super-fast-forwarding through all the tracks in a list giving no sound output while doing so.

Anyone think they know what's going on with exaile or xmms2 and how I can deal with it?

Thanx

---

### Post by VertexPusher on 2009-12-09
You can fix the problem by removing PulseAudio.

First, make sure that these packages are installed:

[B]gstreamer0.10-alsa
gnome-alsamixer[/B]

Then remove the following packages:

[B]gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio[/B]

(This will remove some other packages as well, including **ubuntu-desktop**. Don't worry about that, it's just an empty metapackage. You can undo all the changes later by reinstalling ubuntu-desktop.)

Open a terminal window and enter the following command:

**gstreamer-properties**

This will open the GStreamer configuration panel. On the audio tab, select the ALSA plugin for both output and input, then close the window.

Restart the computer. Now you should have glitch-free sound in all applications. Use gnome-alsamixer to control the sound card volume. You can put its launcher next to the notification area like this:

[img]http://img694.imageshack.us/img694/4810/volume.png[/img]

---

### Post by quequotion on 2010-09-17
> **VertexPusher said:**
> You can fix the problem by removing PulseAudio.

First, make sure that these packages are installed:

[B]gstreamer0.10-alsa
gnome-alsamixer[/B]

Then remove the following packages:

[B]gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio[/B]

(This will remove some other packages as well, including **ubuntu-desktop**. Don't worry about that, it's just an empty metapackage. You can undo all the changes later by reinstalling ubuntu-desktop.)

Open a terminal window and enter the following command:

**gstreamer-properties**

This will open the GStreamer configuration panel. On the audio tab, select the ALSA plugin for both output and input, then close the window.

Restart the computer. Now you should have glitch-free sound in all applications. Use gnome-alsamixer to control the sound card volume. You can put its launcher next to the notification area like this:

[img]http://img694.imageshack.us/img694/4810/volume.png[/img]


Why does it always come down to "purge pulseaudio"?

---

### Post by Yellow Pasque on 2010-09-17
You bumped the 9-month old thread for that?

---

### Post by rwalkerIII on 2011-11-03
So, why does it always come down to purging pulseaudio?  Three years later Exaile still suffers the same error with pulseaudio despite the numerous tickets opened on this problem.

---

