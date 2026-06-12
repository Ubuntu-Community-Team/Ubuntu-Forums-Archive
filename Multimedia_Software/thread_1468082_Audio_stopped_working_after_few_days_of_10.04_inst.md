---
title: "Audio stopped working after few days of 10.04 installed"
date: 2010-05-01
forum: Multimedia Software
---

### Post by phun-ky on 2010-05-01
ok, everything worked fine after a fresh 10.04 install, and after some days now i suddenly got several disconnects from the wifi somehow (all other devices in house does not get disconnected, so its a local issue), tried to restart networking, and when i reboot, it works for some hours, then cuts of again. but, after the latest reboot, the sound card is "gone"
i suddenly have no sound and a wifi that disconnects at will 13:24
everything worked 110% in all previous ubuntu versions

anyone know how i can fix this? or that can try to help me?
lspci says this about my audio device: Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2

wifi device: 09:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI

NOTE! THIS IS AN AUDIO ISSUE ( just ellaborated a bit more to explain what I've done to provoke this )


btw, dmesg says nothing about audio :S

---

### Post by lidex on 2010-05-02
Try this - in a terminal='Applications>Accessories>Terminal':
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic linux-backports-modules-alsa-lucid-generic
```

Now reboot!

---

### Post by JGPRace on 2010-05-19
I had a similar problem, tried the install backports command but this did not solve the problem. Installed the gnome-alsamixer and used it to adjust some levels (nothing was muted). This has brought my sound back, don't know why.

---

