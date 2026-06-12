---
title: "Same sound output in two pcs with LAN?"
date: 2010-11-14
forum: Multimedia Software
---

### Post by kenpuu on 2010-11-14
Hello. I have two pcs in home. 

I have one with ubuntu (gnome) and the other with ubuntu server(xbmc + jdownloader web ui + transmission web ui + ajaxplorer). Is posible to have the same output sound in both? I mean, I want to play a song, and I'd like it sounds on all speakers. If its useful, I play music in first pc with mpd + gmpc.
Two pcs are connected in a LAN.

Thank you! And sorry for my english :P

---

### Post by P4man on 2010-11-14
Yep with pulseadio. Install pulse audio device chooser on both. Run it. From the panel applet, configure one (or both) pc as a sound server. On the other machine, Set the output to the server you want to play it on.

---

### Post by kenpuu on 2010-11-14
> **P4man said:**
> Yep with pulseadio. Install pulse audio device chooser on both. Run it. From the panel applet, configure one (or both) pc as a sound server. On the other machine, Set the output to the server you want to play it on.

Thanks. I've found this:
[http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers](http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers)

> How do I use PulseAudio over the network?

Just set the environment variable $PULSE_SERVER to the host name of the PulseAudio server. Alternatively you can modify ~/.pulse/client.conf or /etc/pulse/client.conf and set default-server= (See ServerStrings for an explanation of the format, see FAQ# 18 for all locations you can specify the server to use) For authentication you need the same auth cookies on all sides. For that copy ~/.pulse-cookie to all clients that shall be allowed to connect. Alternatively the authorization cookies can be stored in the X11 server. The server must have module-native-protocol-tcp loaded, with the argument loopback=0 set. Note that this can use pretty much network bandwidth (around 1.3Mbps for 44100Hz sound). If you get choppy sound, try downsampling it.

But I don't know how to set the source or sink. I mean, how do I configure the server? And, what have I do in client? default-server=192.168.1.x?? Only that? Help, please. And thanks again.

---

### Post by P4man on 2010-11-14
Its easier than that. Just install PulseAudio device chooser from the software center. Run it. It adds an icon to the tray. Click it. Click Configure Local Sound server > network server > enable network access.  Check the appropriate options (certainly first two, probably third one too).

On the client (the one sending the sound). click the padevchooser icon, the server should show up in the list of servers and then select the default sink. Click it. Done.

---

### Post by kenpuu on 2010-11-14
> **P4man said:**
> Its easier than that. Just install PulseAudio device chooser from the software center. Run it. It adds an icon to the tray. Click it. Click Configure Local Sound server > network server > enable network access.  Check the appropriate options (certainly first two, probably third one too).

On the client (the one sending the sound). click the padevchooser icon, the server should show up in the list of servers and then select the default sink. Click it. Done.

Thank you very much. With that the second pc plays sound form first, but both output aren't active.

---

