---
title: "Headphone not detected since"
date: 2015-04-25
forum: Multimedia Software
---

### Post by jyrki-deneve on 2015-04-25
Hi,

I updated from 14.10 to 15.04 this week, but since the update my headphones aren't working. My laptop is a Dell XPS 13 (9333).

This is my alsa info: [http://www.alsa-project.org/db/?f=526031ff699f10e8f808f0d424a7afd6af40aba9](http://www.alsa-project.org/db/?f=526031ff699f10e8f808f0d424a7afd6af40aba9)

In the sound settings, I only see speakers even when headphones are plugged in.

I already tried many things I found on the internet, but none of them helped.

---

### Post by dino99 on 2015-04-25
install 'pavucontrol' and check/set the 'configuration' first, then 'Output Devices' tabs (from the menu: Sound > Pulseaudio Volume Control)

---

### Post by jyrki-deneve on 2015-04-25
I attached two screenshots of the configuration and output tab.

I did already try to set the HDMI dropdown to off, because of this [http://mangel312.blogspot.be/2015/04/uubuntu-1504-vivid-vervet-on-2014-dell.html](http://mangel312.blogspot.be/2015/04/uubuntu-1504-vivid-vervet-on-2014-dell.html), but it didn't work.

---

### Post by ajgreeny on 2015-04-25
Go back to the window you show in your first screenshot and click in the dropdown box which shows "Speakers" and I think "Headphones" will probably show if your setup is anything like mine.  You may then find they are either set with too low a volume or are muted.

---

### Post by jyrki-deneve on 2015-04-26
I only see the "Speakers" option in that dropdown.

---

### Post by Yellow Pasque on 2015-04-26
```
snd_hda_intel: model=dell-headset-multi
```

Is it possible you added this in the past but now it is no longer necessary?

---

### Post by vicente5 on 2015-04-26
I was having the same problem than you are, and I've noticed the following problem:
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headset-mic-dell-inspiron.conf:23] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headphone-mic-dell-inspiron.conf:24] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-dell-inspiron.conf:23] Name makes no sense in 'General'


And I've managed to make it work doing the following:
Editing each of the three files, and removing the offending line.
After that, I've rebooted, and now I'm able to make it work!

---

### Post by jyrki-deneve on 2015-04-27
This solved the issue for me also. Thx vicente5!

> **vicente5 said:**
> I was having the same problem than you are, and I've noticed the following problem:
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headset-mic-dell-inspiron.conf:23] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headphone-mic-dell-inspiron.conf:24] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-dell-inspiron.conf:23] Name makes no sense in 'General'


And I've managed to make it work doing the following:
Editing each of the three files, and removing the offending line.
After that, I've rebooted, and now I'm able to make it work!

---

### Post by Stuart_Robertson on 2015-05-07
> **vicente5 said:**
> I was having the same problem than you are, and I've noticed the following problem:
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headset-mic-dell-inspiron.conf:23] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headphone-mic-dell-inspiron.conf:24] Name makes no sense in 'General'
pulseaudio[1575]: [pulseaudio] alsa-mixer.c: [/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-dell-inspiron.conf:23] Name makes no sense in 'General'


And I've managed to make it work doing the following:
Editing each of the three files, and removing the offending line.
After that, I've rebooted, and now I'm able to make it work!

Rather than deleting the lines, replace the 'name' variable with 'description-key'. It just seems like they've changed the name of the variable that names the port in your sound settings.

---

