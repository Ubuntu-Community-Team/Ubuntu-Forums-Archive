---
title: "No sound at startup"
date: 2010-01-31
forum: Multimedia Software
---

### Post by Zilioum on 2010-01-31
A few days ago, my sound suddenly stopped working. I was able to get it back with ```
alsamixer
```, "front" was muted. 
Sadly, this problem also persist when I restart my pc. Is there a way that I dont have to unmute at every startup?

---

### Post by Zilioum on 2010-02-03
bump

---

### Post by VertexPusher on 2010-02-03
PulseAudio overwrites your saved alsamixer settings on startup.

The easiest way to fix this is to remove PulseAudio:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

---

### Post by Zilioum on 2010-02-03
Sound works from the start again, thanks a lot. Whats the whole deal anyway with pulseaudio and ALSA ? What exactly did I install and what did I uninstall?
New Problem: The volume control in the panel is gone, and my volume control buttons dont work anymore.

---

### Post by Zilioum on 2010-02-08
bump

---

### Post by Zilioum on 2010-02-12
How can I reinstall ALSA? Should I get rid of PulseAudio so I dont have the same problem again (no sound at startup). Do I need both?

---

### Post by Zilioum on 2010-02-15
After some research, I decided to reinstall PulseAudio since I need it. Everything is back to normal, which means no sound at startup again.

---

### Post by Zilioum on 2010-02-16
bump

---

### Post by Alexandre Putt on 2010-02-16
I had the same annoying problem with muted sound after each new start in 9.10. This seems to have been fixed in Lucid. I suggest you wait till the official release and then upgrade.

If this is not a solution, I'd look for a start up script to change the volume. Unfortunately I have limited Linux experience to write such a script myself, but googling might help. This should not be a big thing.

---

### Post by Zilioum on 2010-02-19
Thanks, good to know. Has anyone another suggestions? Or an explanations why this happened in the first place? Because my sound worked without problem for months.

---

### Post by Zilioum on 2010-02-28
I found a solution: Right click on the volume icon --> sound preferences
Under "Hardware" I switched from Analog Stereo Output (Or Duplex,dont remember) to "Analog Surround 5.1". What you can choose will depend on your soundcard. Now I dont have that annoying "no sound at startup" problem anymore. 

Cheers

---

