---
title: "Amarok hogs the sound, even when not playing anything"
date: 2009-06-04
forum: Multimedia Software
---

### Post by WindPower on 2009-06-04
Hello,
I've been trying to play music using Amarok 2 on Kubuntu 9.04 64-bit, and Amarok works fine and all. However, whenever it is launched, no other audio comes from any other application (Flash (YouTube), VLC, games, etc.), even if Amarok isn't playing anything. How can I fix this?
Also, Flash embeds seem to stop working after a while. They simply turn into a blank white zone, and sometimes a refresh fixes it, but at one point it turns gray/grey and it's no use refreshing anymore, gotta restart Firefox.

---

### Post by mauripop on 2009-06-12
Hi, I have the same problem here. I have no sound from any web app using flash after I use audio on amarok, even after I quit amarok, even after I log out and back in! I have to completely restart the computer to get sound back on web apps. Now the last time I had to reboot my PC several times a day was in 2002, the last time I used Windoze on a regular basis.

---

### Post by piggoy on 2009-06-16
Same problem here! It's really annoying. Does someone please know a fix?

---

### Post by mauripop on 2009-06-16
[FONT="Arial"]I've found a fix.

The problem seems to be Ubuntu's implementation of knotify4. I guess a bug file is in order. It seems knotify isn't letting go of the sound resources as it should. At the konsole, enter the following:[/FONT]

[FONT="Courier New"]sudo killall knotify4[/FONT]

That fixed it for me on the two computers i've experienced this problem.

---

### Post by mauripop on 2009-06-19
I think I found a permanent fix for the above problem. It has to do with KDE apps, and amarok in particular, taking control of the audio hardware instead of using PulseAudio to share the audio resources with all apps, even non-KDE apps like Firefox. 

Run systemsettings, go to Multimedia, and change the Device Preference for all Audio Output so that Pulse Audio is the first option instead of the hardware audio device. Apply and presto.

---

