---
title: "Removed Volume control"
date: 2009-08-03
forum: Multimedia Software
---

### Post by firewall_03 on 2009-08-03
I was reading a thread about fixing one of my sound issues and it had me remove the volume control from the panel, I got a different one installed, but I don't know how to access the other one.  I believe the ran I am using now is pulse audio.  The reason I am asking is because I muted my front speakers on my laptop and I don't know how to un mute them.  I can seem to figure out the headphone switch problem that some people seem to encounter.

---

### Post by igorzwx on 2009-08-03
I would propose a kind os systematic experimentation.

commands (on Terminal)

aplay -l

lspci -v

lspci > hardwareinfo.txt


The last command will produce a text file " hardwareinfo.txt"


Install several Ubuntu 9.04 on the same box

try:

1. ALSA + esound (without pulseaudio)

2. OSS4 (without alsa and pulse)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

one of these solutions may work


**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by firewall_03 on 2009-08-03
[http://pastebin.com/m97a2450](http://pastebin.com/m97a2450)

I did all the commands and I should try and install those packages?

---

### Post by xc3RnbFO8P on 2009-08-03
In Synaptic Package Manager try to reinstall
**gnome-applets**
**libpanel-applets2-0**

---

### Post by firewall_03 on 2009-08-03
> **Ringi said:**
> In Synaptic Package Manager try to reinstall
**gnome-applets**
**libpanel-applets2-0**

Thats done should I restart?

---

### Post by xc3RnbFO8P on 2009-08-03
> Thats done should I restart?
yes

---

### Post by firewall_03 on 2009-08-03
the didn't work after I restarted

---

### Post by xc3RnbFO8P on 2009-08-03
In Terminal:
> alsamixer
and unmute it there
arrows,  scroll,  m=mute unmute

---

### Post by Moop on 2009-08-03
Go to System-Preferences-Startup Applications. Scroll down to Volume Control and make sure the box is checked for show desktop volume control.

---

### Post by neu2buntu on 2009-08-04
try command in terminal ```
gnome-volume-control
```

---

