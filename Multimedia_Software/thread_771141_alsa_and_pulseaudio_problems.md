---
title: "alsa and pulseaudio problems"
date: 2008-04-27
forum: Multimedia Software
---

### Post by abds on 2008-04-27
I am having problems with the pulseaudio. When I play audio files, there are disturbances in the sound. These are propotional to the cpu usage... so if i am using more cpu, it goes to hell. This is vlc and totem. In realplayer the sound seems to work fine. 

I am using the 64-bit Hardy Heron.

---

### Post by abds on 2008-04-27
Anyone??

---

### Post by psyke83 on 2008-04-27
Try this solution and please report if it helps: [http://ubuntuforums.org/showpost.php?p=4816308&postcount=6](http://ubuntuforums.org/showpost.php?p=4816308&postcount=6)

---

### Post by abds on 2008-04-27
After I do "pkill pulseaudio" everything is fine.

Editing the daemon.conf file doesnt seem to help. When I restart its back to where it was.

---

### Post by abds on 2008-04-27
Here is the output of lspci | grep audio

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)

---

### Post by &#12465;&#12452;&#12488; on 2008-04-27
You might want to run pulseaudio in its high priority mode.

---

