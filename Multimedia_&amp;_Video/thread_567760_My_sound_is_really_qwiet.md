---
title: "My sound is really qwiet"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by osiris2258 on 2007-10-05
I just installed ubuntu, and I have noticed that even with my speakers and the internal settings pumped up to the max, i barely get any audio out of my computer. My motherboard has Realtek - HD ALC88X onboard. I am wondering if maybe I need a driver to get sound? If so , where can I find it?

---

### Post by borris.morris on 2007-10-05
run alsamixer in a terminal (applications -> accessories -> terminal) and max out the pcm channel.

---

### Post by osiris2258 on 2007-10-05
It is maxed out.

---

### Post by borris.morris on 2007-10-05
hmm...... well, then try the drivers. thats your next best bet.

---

### Post by osiris2258 on 2007-10-05
Any idea where I can find linux drivers for my hardware? I only see windows drivers on the manufacturer's website.

---

### Post by RomeReactor on 2007-10-05
Hi. I don't know if this will help you, it's just a suggestion: start playing a media file (audio or video, just as long as it has audio), run alsamixer again and play with the volume levels of other channels; it might be that your Realtek card is using another channel to control the master volume.

Or right-click on the volume applet in the top panel and select "Open Volume Control", go into "Edit->Preferences", check all the channels and use that to play around with the volume levels.

If you find that it *really* is another channel that's controlling the master audio levels, go to "System->Preferences->Sound" in your top panel, and highlight the correct channel. Then right-click on the volume applet, select "Preferences", and again highlight the correct channel.

The good thing is that you **do** get audio output, albeit a low one; I think it has to do with the channel that's actually controlling the master audio being low. Also, just to be thorough, make sure the line is connected to the correct port on your video card. May sound like a joke, but I've seen cases where that was why sound was almost inaudible.

---

### Post by osiris2258 on 2007-10-05
Thanks! Turns out that my "Side" channel is controlling the sound output  for some reason. It's still a bit quiet, so I have turn my speakers up really high, but at least you can hear it now. The only problem is that my keyboard controls have no effect on the sound, only the on screen slider. Any way to redirect this so I can use my volume controls and mute switch?

---

### Post by RomeReactor on 2007-10-05
I'm not really sure, but you might want to install **Lineakd**:
```
sudo apt-get install lineakd
```
 I have a Hewlett-Packard keyboard with internet and multimedia controls, and the only way to enable the sound knob and other media buttons was by installing that--though that was in Edgy; since Feisty, I haven't had to install anything. This is the description Synaptic gives on Lineakd:
> **Linux support for Easy Access and Internet Keyboards**

LinEAK, Linux support for Easy Access and Internet Keyboards, features X11
support, windowmanager independence, ability to configure all keys through
GUI or .conf file, volume control and sound controls.

lineakd is the daemon that runs in the background of an X session and listens
to incoming events from multimedia buttons.

 Homepage: [http://lineak.sourceforge.net](http://lineak.sourceforge.net)

Or maybe installing **Hotkeys** will help:
```
sudo apt-get install hotkeys
```
> **A hotkeys daemon for your Internet/multimedia keyboard in X**

This program sits at the back and listens for the "special" hotkeys
that you won't normally use on your Internet/Multimedia keyboards.
The buttons perform their intended behaviors, such as volume up and
down, mute the speaker, launch applications, etc. It has On-screen
display (OSD) to show the volume, program that's being started, etc.

It features an XML-based keycode configuration file format, which
makes it possible to define the hotkeys to launch any programs you
want.

Otherwise, I'm afraid I can't be of much help to you in that regard.

---

### Post by CheesyPuffs144 on 2007-10-05
I had a similar problem, where everything was maxed out, and it was really quiet. Then when I went into System > Preferences > Sound and randomly clicked "Test" on a randon one, everything started working again. :confused:

At least its good now. :lolflag:

---

### Post by Scorpuk on 2007-10-05
Just a suggestion, but can you check which socket you have your speakers connected to as it does matter:

Orange?  -> Center / Sub Woofer Speakers
Black? -> Rear Speakers
Gray? -> Side Speakers
Green? -> Line out (Front Speakers)

---

### Post by osiris2258 on 2007-10-06
Alright, I spoke too soon. I have better sound now but the max is still low; I have to turn up the speakers and the sound settings much higher than in the windows xp boot on the same machine, and consequently the max is much lower. I am hard of hearing so this is a problem for me, I need to be higher than normal to start with.

---

### Post by RomeReactor on 2007-10-06
Hi again. As Scorpuk and I said in the previous page, make sure the line is connected to the correct port in your card (it should be the green one, I think).

---

