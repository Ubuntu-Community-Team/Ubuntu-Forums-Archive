---
title: "Audio visualizations for Banshee (or some way in Ubuntu Jaunty)"
date: 2009-06-22
forum: Multimedia Software
---

### Post by SoundGuy.Jon on 2009-06-22
I Jaunty (9.04) and use Banshee media player for music and organizing my iPod. Banshee has a 'Now Playing' tab, which shows the current song, album, and artist, including cover art. That's nice and all, but I was wondering if there was a way to have visualizations like in WMP or iTunes and what not. I know RhythymBox and Amarok can, but I just prefer Banshee. I was looking into .boo scripts to see if it could be done there, but I don't know a whole lot about coding. I know some of the basics in terminal and can usually understand a command that is given to me, plus I know how to untar and all that. So is there anyway this can be done?

Also, I was thinking, this doesn't have to necessarily be in Banshee itself. It could be just another program completely that responds to the current audio that the computer is playing and creates said visualization. And yes, I've googled this, and searched the forums, and have found nothing.

Any help will be greatly appreciated

---

### Post by monraaf on 2009-06-22
Don't now C#, and I have no intention in 'hacking' Banshee, but if you have pulseaudio running, you can feed the monitor source to a gstreamer pipeline.

From a terminal:

```

$ pactl list|grep monitor
Monitor Source: alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor

```

Now use that name in a gstreamer pipeline:

```

$ gst-launch-0.10 pulsesrc device=alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=true

```

You have to substitute the *device=alsaxxxx* with whatever pulseaudio monitor device you have.

Edit: Seams that it also works if you don't explicitly specify the device name. So the shorter version would be:

```

$ gst-launch-0.10 pulsesrc ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=true

```

---

### Post by rolandixor on 2009-08-04
This is actually being worked on in a branch of banshee already. I don't know when it will hit the release, but it should get here soon it seems. Keep your eyes out :D

---

### Post by nmyrick on 2010-02-23
This works better if you use the following command. This way it doesn't force the aspect ratio and you will get a full screen, no matter what kind of computer you have.

gst-launch-0.10 pulsesrc ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false

nmyrick

---

### Post by nmyrick on 2010-02-23
You can also create your own custom launcher for Goom! by just right-clicking one of your panels, or the desktop. Then click "create launcher" then just enter the following command in to the GUI window.

gst-launch-0.10 pulsesrc ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false


nmyrick

---

