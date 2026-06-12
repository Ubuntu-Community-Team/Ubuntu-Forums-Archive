---
title: "Poor quality MP3 playback"
date: 2013-11-02
forum: Multimedia Software
---

### Post by lah7 on 2013-11-02
Hello. I've noticed something abnormal about my music playback through Banshee lately.

In some music it's obvious, in others not, but certain parts of the track sound poorer quality then usual (some parts of a song may sound a bit 'screecher' then it should)
I've noticed this several times on both headphones and playing through my speakers, so this isn't my hardware or a loose wire. I'm not musical enough to know exactly this odd thing is, but I suspect it's how MP3s are played back on my system.

_To test:_ I imported a soundtrack that's **MP3** into Audacity and exported it to **OGG**. Playing the **MP3** within Audacity and the exported **OGG** via a music player sounds exactly as it should, but playing the original MP3 sounds poor quality.

I'm not too sure if this is something to do with PulseAudio since my upgrade to Ubuntu 13.10 not too long ago as I had trouble with Audacity and Skype making fast/distorted sounds. :mad:

Also, this 'poor quality' MP3 playback seems to happen mainly on **audio players** installed on my system, that's **Banshee** and the default** Videos** player. Could this be a codec/package issue?

I'm not really sure what to do, there's something weird with playing MP3 files...

Any suggestions are greatly appreciated. :)

---

### Post by christophersacchi on 2013-11-02
Hello,

Why don't you try and see if RhythmBox works? It may solve your problem. Use: "sudo apt-get install rhythmbox". Use the command inside the quotes in a terminal, without the quotes actually being there. Try and see if you can reproduce the problem on my suggested media player and other media players.

Regards,
Christopher Sacchi

---

### Post by Yellow Pasque on 2013-11-02
> **christophersacchi said:**
> Why don't you try and see if RhythmBox works?

Use something else instead of Rhythmbox, because it uses gstreamer just like Banshee and Totem. Try audacious.

---

### Post by lah7 on 2013-11-02
Thank you both for your speedy responses!

- **Rhythmbox** produces the same results.
- **VLC** works okay at a ever-so-slightly lower pitch (for some reason, always noticed that, even in Windows)
- **Audacious** plays without any problem. :D

So **gstreamer** is likely to be the culprit of affecting playback of MP3 files. Ideally I'd like to keep on using Banshee/Video as my main software for audio. But if I absolutely must, I may accept I need to use Audacious or suffer poor quality.

I'm thinking gstreamer needs a re-installation or its configuration would want a reset (if it has one?) Or if it's a bug after the upgrade. Alternately, could this be a problem with the package communicating with gstreamer that allows playback of the restricted mp3 format?

---

### Post by kostkon on 2013-11-02
> **lah7 said:**
> its configuration would want a reset (if it has one?)
Yes there is the tool gstreamer-properties you could try, it used to be more easily accessible in the past, but it is now hidden in recent versions of Ubuntu. Either run it from the terminal or press ALT+F2 and give
```
gstreamer-properties
```

Hope that helps.

---

### Post by Yellow Pasque on 2013-11-02
There are two ways for gstreamer to play mp3's: either using the fluendo mp3 plugin (less legal issues) or using the libmad plugin found in gstreamer1.0-plugins-ugly package. So, if you have the gstreamer1.0-fluendo-mp3 package installed, remove it (and make sure gstreamer1.0-plugins-ugly is installed) to try the regular libmad plugin. Conversely, if you don't have the fluendo plugin installed, go ahead and install it to see if it improves things.

Concerning gstreamer-properties, that was a tool to change output sinks back in the gstreamer0.10/gconf days. I'm not even sure if it works for gstreamer1.0 apps now that they use dconf.

---

### Post by kostkon on 2013-11-02
> **Temüjin said:**
> Concerning gstreamer-properties, that was a tool to change output sinks back in the gstreamer0.10/gconf days. I'm not even sure if it works for gstreamer1.0 apps now that they use dconf.
I thought the same thing but checked and it still exists in saucy, so I don't know. Hopefully everything is set to autodetect, but you never know.

But you are right, it must be a codec problem, I just re-read the first post.

---

### Post by lah7 on 2013-11-03
I had the packages[COLOR=#000080] gstreamer0.10-fluendo-mp3 [/COLOR]and [COLOR=#000080]gstreamer1.0-fluendo-mp3 [/COLOR]installed, so I went ahead and uninstalled these. [COLOR=#000080]libmad0 [/COLOR]appeared to be already installed, so I gave it a reinstallation.

**It worked!** There's no more distorted quality anymore. So thank you so much for your responses! :)

---

