---
title: "Precise: How to set default soundcard in pulseaudio?"
date: 2012-06-07
forum: Multimedia Software
---

### Post by barisurum on 2012-06-07
I'm struggling to make pulseaudio understand that my preferred soundcard is usb audio. For which I edited the /etc/modprobe.d/asound.conf and changed indexes that usb audio always gets the index 0 but pulse doesn't take that into account. padevchooser is not installable because of dependency problems. I can change individual application settings and configure them to play with usb audio but how can i tell pulseaudio that I want ALL audio to be routed to usb audio sink? Is this ought to be that hard? In 2012? :confused:

---

### Post by Enigmapond on 2012-06-07
Install pavucontrol which is a volume control for pulse but also allows you to choose the fallback or default...

---

### Post by barisurum on 2012-06-07
i set the usb audio as fallback in pavucontrol but every newly run application is routed to my PCI card. I've to manually set them in playback tab.

---

### Post by DaimyoKirby on 2012-12-15
Not trying to commit necromancy hear, but it isn't that old (in my opinion), still needs an answer, and I found this page while experiencing the same problem, so it's likely others will too.

Anyhoo - I was having a problem where every new application I used had to either be manually switched from my integrated audio to my pci card in pavucontrol the first time I used it, or couldn't be switched at all.
I solved this by opening the configuration tab in pavucontrol, and choosing "off" in the dropdown menu for every option that I didn't want (in my case, I set hdmi and integrated sound to "off"). This forces programs to use my preferred choice, my sound card.
Also, I don't know if it is necessary or not, but I made sure that my preferred choice was set as fallback as well.

---

