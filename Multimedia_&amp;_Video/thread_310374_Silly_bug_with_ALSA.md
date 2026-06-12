---
title: "Silly bug with ALSA"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by auricle on 2006-12-01
Hi,

I use the M-Audio Revolution 7.1 soundcard. A very good little soundcard with 2 ins and 8 outs (designed for surround sound but can be used for anything) which uses the ICE 1724 chipset.

Unfortunately, there is a bug with ALSA that when you boot into the desktop, only the right channel works - the left one is muted until you open alsamixer and adjust the volume of the left channel - it then plays as normal.

Can someone help me to write a script that adjusts the volume in alsamixer everytime I boot into Kubuntu? I don't know anything about scripting.

Thanks in advance!!

---

### Post by pandu.rs on 2006-12-01
Assuming that u have only one sound card the following command shld do the trick. (if u have more sound cards u need to give correct value for -c)

[CODE]
amixer -c -0 sset Line,0 80%,80% unmute
[CODE]

add the above command to startup programs using

System -> Preferences-> Session

select startup programs tab and add the above command.

u can also refer to man amixer.

---

### Post by auricle on 2006-12-02
Hi Pandu,

Thanks for the advice.

After a lot of research, I found out that this is a documented bug that exists with ICE1724 chipsets:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=321]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=321")

This bug has existed for quite a few years and has never been fixed.

The workaround is to set the volume to a different level to your desired volume first and then back to your desired volume.

As I use KDE not Gnome, I created an executable bash script in the ~/.kde/Autostart folder containing the following:

```
#!/bin/bash
/usr/bin/amixer -q set PCM 10% unmute

/usr/bin/amixer -q set PCM 90% unmute &
```

It should now work

---

