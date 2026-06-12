---
title: "No sound on new Lubuntu installation"
date: 2014-03-15
forum: Multimedia Software
---

### Post by philip18 on 2014-03-15
I've installed Lubuntu on my netbook as Windows was just too slow. But I'm not getting any sound when playing videos or browsing Youtube. I've tried the Netbooks volume and mute hotkeys but to no avail. I've looked for any relevant sound settings but I can't find any.

---

### Post by bookrt on 2014-03-15
Make sure you have run a full system update after install.

You could try installing pulseaudio or xfce4-mixer. Either one of these should give you a GUI to access your sound settings and select the correct soundcard and profile.

---

### Post by SeijiSensei on 2014-03-15
I find it useful to install **pavucontrol**, the Pulseaudio utility to manage streams and control volumes.  See if that helps solve your problem.

Pulseaudio is the default sound server on any recent Ubuntu release; you shouldn't need to install it separately.

---

### Post by bookrt on 2014-03-15
Sorry, I meant pavucontrol, the GUI for pulseaudio.

---

### Post by philip18 on 2014-03-23
Guys, I'm not fully following. I've installed Pulse Audio but it error's when I try to start it "Connection to PulseAudio failed. Automatic retry in 5s. In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured. This situation can also arrise when PulseAudo crashed and left stale details in the X11 Root Window."...

What should I try next?

---

### Post by Yellow Pasque on 2014-03-24
Give info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by philip18 on 2014-03-24
> **Temüjin said:**
> Give info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
 Good system. Here's the info: [http://www.alsa-project.org/db/?f=e41445a1b9cc8db7bd0a23654820044b778bc9a4](http://www.alsa-project.org/db/?f=e41445a1b9cc8db7bd0a23654820044b778bc9a4)

---

