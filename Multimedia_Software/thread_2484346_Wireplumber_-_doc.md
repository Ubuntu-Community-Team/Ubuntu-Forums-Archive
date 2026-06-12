---
title: "Wireplumber - doc"
date: 2023-02-23
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-02-23
I have found that wireplumber is needed on one PC for audio, but on another it isn't.  OS version is 22.10.  I installed wireplumber-doc, but cannot find it.  Where is it?

Thank you,

John

---

### Post by mIk3_08 on 2023-02-24
I don't know about the wireplumber. Maybe this releases will help. 

[WirePlumber 0.4.6 Released For Managing PipeWire]("https://gitlab.freedesktop.org/pipewire/wireplumber/-/releases/0.4.6")
[PipeWire  0.3.62 Released With Bluetooth Offloading Support ]("https://gitlab.freedesktop.org/pipewire/pipewire/-/releases/0.3.62")
[PipeWire  0.3.60 Released With Many Fixes, Improvements]("https://gitlab.freedesktop.org/pipewire/pipewire/-/releases/0.3.60")
[PipeWire 0.3.57 Adds AAC Decoder, Opus For Bluetooth]("https://gitlab.freedesktop.org/pipewire/pipewire/-/tags/0.3.57")
[PipeWire  0.3.52 Released To Continue Enhancing Linux Audio/Video Streams]("http://https://gitlab.freedesktop.org/pipewire/pipewire/-/tags/0.3.52")
[PipeWire  0.3.46 Released With Critical Bug Fixes, Better Sound Sharing With  Zoom]("https://gitlab.freedesktop.org/pipewire/pipewire/-/tags/0.3.46")
[PipeWire  0.3.44 Released With Latency Improvements, Minimal PW Server Support]("https://gitlab.freedesktop.org/pipewire/pipewire/-/releases/0.3.44")

Regards and cheers.

---

### Post by cigtoxdoc on 2023-02-24
Thank you very much.  Right now, Ubuntu 22.10 only provides 0.3.58-2.  I finally found the wireplumber-doc file.  It is in /use/share/doc/wireplumber.  Unfortunately, it doesn't say much, and does not give the details on when wireplumber is required and when it is not.  John

---

### Post by &amp;KyT$0P# on 2023-02-26
Are both machines definitely using Pipewire for audio?
If so, maybe the other one is using [FONT=Courier New]pipewire-media-session[/FONT] instead of Wireplumber?

---

### Post by cigtoxdoc on 2023-02-26
Good question, halogen2, and thank you for asking it.  Right now, I am working from a remote location with my Dell 7720 laptop.  According to System Monitor, paystray, pavucontrol, pipewire, pipewire-pulse, and wireplumber are active.  If pipewire-media-session is active, it is not showing in System Monitor. I will have to check my desktop PCs the next time I am in my office.

Wireplumber appears (note: appears) to be the software that on laptops controls if audio output goes to built-in speakers, audio jack, or maybe USB headset.  The uses of wireplumber are not specified in wireplumber-doc.

I hope that the moderators of this forum can provide a positive answers to the functions and uses of wireplumber.  I have asked this question on the wireplumber page of GitLab ([https://gitlab.freedesktop.org/pipewire/wireplumber/-/issues/421](https://gitlab.freedesktop.org/pipewire/wireplumber/-/issues/421)), but have not received a reply to date.

John

---

### Post by cigtoxdoc on 2023-03-02
Wireplumber also works on a ThinkCentre M83 desktop.

---

