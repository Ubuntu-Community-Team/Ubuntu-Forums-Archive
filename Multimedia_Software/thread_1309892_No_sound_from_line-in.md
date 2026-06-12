---
title: "No sound from line-in"
date: 2009-11-01
forum: Multimedia Software
---

### Post by jimqode on 2009-11-01
After a clean install of ubuntu 9.10 I can't get sound from line-in jack of my sound card. I can record from line-in fine, but I couldn't find the output volume setting on the new mixer.

Thank you for your help.

---

### Post by ajgreeny on 2009-11-01
Similar problem with a microphone.  I used to be able to hear the mic input through the speakers, but now it's all silent, though like you I can still record with no problem using either sound recorder, or audacity, and the mic works fine with skype, though again I can not hear myself in the speakers.  There must be some way to sort this, surely!

---

### Post by Jamesss on 2009-11-02
I also have just completed a clean install and have no sound from my line in. I can see it displayed in Sound Preferences, and record in audacity but it doesn't come through the speakers. This is my sound card:

```
  *-multimedia            
       description: Multimedia audio controller
       product: ES1371 [AudioPCI-97]
       vendor: Ensoniq
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12
       resources: irq:16 ioport:d800(size=64)

``` 

Any ideas?

---

### Post by Jamesss on 2009-11-02
Ok well I think I've found a solution for now - I started alsamixer from the command line and unmuted everything and raised the faders (you can switch between playback and capture with the tab key. Left/right goes through the faders and up down for the level).
Also tried installing alsamixergui via synaptic but that only offered master and capture controls that did nothing! Would be nice to have a gui for this though.

---

### Post by jimqode on 2009-11-02
Thank you for your reply Jamess. It works with alsamixer. But I also think this should be accessible from gui mixer.

---

### Post by JCK-longhair on 2009-11-12
I've just installed GNOME ALSA Mixer thanks to a reply on another thread - maybe this is the GUI you're looking for?

---

### Post by Jamesss on 2009-11-14
Yes that's the gui I need for setting the levels. It's still kind of weird with the new Sound Preferences gui in karmic - whenever I unmute the line in it automatically ticks the capture box in gnome-alsamixer BUT also unticks the mix box, so I'm ONLY able to record from the line in. So the new Sound Preferences gui is pretty much useless to me - looks like I will have to use gnome-alsmixer to get the settings I need.

Also  gnome-alsamixer starts with lots of faders I don't need - how can I disable these? (eg 3d control, etc.) Edit/Sound Card Properties does not remember the settings.

---

### Post by 666porcondissaum on 2010-03-16
... something happened after the last or one of the last updates here. I used to tune my guitar and also play through creox with some effects but suddenly the line in isn't working anymore. And every time I open the sound preferences and work around with the input sources, at each source only front mic works. Any idea?:guitar::frown:](*,)

---

### Post by brunolabs on 2010-10-09
Same problem here:
[http://ubuntuforums.org/showthread.php?t=1574698]("http://ubuntuforums.org/showthread.php?t=1574698")

No solution yet though. :(

---

