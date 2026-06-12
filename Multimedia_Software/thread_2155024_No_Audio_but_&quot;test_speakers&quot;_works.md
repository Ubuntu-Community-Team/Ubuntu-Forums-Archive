---
title: "No Audio but &quot;test speakers&quot; works"
date: 2013-06-16
forum: Multimedia Software
---

### Post by graingert on 2013-06-16
I have a laptop with speakers. I recently tried to watch a flash video on the computer and wasn't getting any sound. Later on I tried to listen to online radio and still wasn't getting any sound. I restarted the computer and it didn't help but when I went into the sound settings and properties I clicked the "test" for each speaker and I'm getting noise through them (the test in gstreamer-properties also works). But ALL other programs will not play any sound to the speakers.

Same issue as: [http://ubuntuforums.org/showthread.php?t=1697117](http://ubuntuforums.org/showthread.php?t=1697117) but that wasn't resolved either

alsa info dump: [http://www.alsa-project.org/db/?f=4323b6f0aa25aaa4bd59ee446f4a81af1cde7bf6](http://www.alsa-project.org/db/?f=4323b6f0aa25aaa4bd59ee446f4a81af1cde7bf6)

---

### Post by r_avital on 2013-06-16
Forgive a silly suggestion:

First, are you running gnome, or kde?

If gnome, and you have the "indicator applet" on one of your panels, you should see an icon shaped like a conical speaker.  Click it, select "properties" and go to the "output" tab.  Look at the "connection" item - if it's on "analog output" - you're piping the sound to your speaker connectors on the laptop, to be used by external speakers.  If it's on "analog speakers" it should deliver sound to the laptop's on-board speakers.

hth

---

### Post by Yellow Pasque on 2013-06-16
So it sounds like it's pulseaudio that's borked. Try these commands:
```
rm -r ~/.config/pulse
pulseaudio -k
```

---

