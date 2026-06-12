---
title: "Pulseaudio - set as fallback"
date: 2010-05-01
forum: Multimedia Software
---

### Post by NJC on 2010-05-01
And why do the Pulseaudio Sound gods continue their wrath against me (and countless others). :P

Logitech Quickcam 9000 mic works in Audacity and Skype via Pulseaudio in Ubuntu 10.04. Pulseaudio Applet is installed but WHY are the default settings lost on reboot? IE I have to open the applet and "Set as Fallback" again after each reboot.

---

### Post by AndrewGarib on 2010-06-25
I think - don't quote me on this - you need to add a line to etc/pulse/default.pa setting a permanent fallback sink or source.

But I think that solves the problem if you have a permanent sink or a permanent source.

I have a SoundBlaster X-Fi Go! (a USB sound card; works just fine, btw) but I have to set it as the PulseAudio fallback every time I plug it in. I made a little script in the kicker menu that does this:

pacmd set-default-sink alsa_output.usb-Creative_Technology_SB_X-Fi_Go__38389C46031350E50361C0B200000000-00-Go.analog-stereo

(the alsa_output.usb-Creative.... stuff I got from the terminal: pacmd list-sinks)

That's a nice one-button solution to making the X-Fi my fallback audio sink, but I want a nice no-button solution. I can't figure out how to get the KDE Device Actions thingy in System Settings to realize when the USB sound card is plugged in. I also can't figure out how to get qdbus to set the KMix master channel, which would also be helpful.

Anyways, I thought this might help if you're looking for something that fixes your problems on startup. At least, the scripting part works. Check out pacmd and the default.pa file and see what you can do with it.

Anyone with any thoughts on this? Does anyone know how to get KDE Device Actions to recognize my USB sound card? Anyone know how to set the KMix master channel with a command line?

---

### Post by Cotopaxi on 2011-01-06
I am Kubuntu User. What I did with PulseAudio, I also went into:

>System Settings>Multimedia.

Here in “Device Preferences” I choose “Playback/recording through the PulseAudio sound server” as top preference in the different Audio output and input categories.

You should have something very similar in Ubuntu.

Hope this helps.

---

