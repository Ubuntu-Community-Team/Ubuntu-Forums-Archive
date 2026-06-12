---
title: "Audio Device Not Available without local user logged in"
date: 2012-12-20
forum: Multimedia Software
---

### Post by MidnightJava on 2012-12-20
On my Ubuntu 12.10 system, I have a USB sound card which provides a two-way connection to my Ham radio, enabling me to send and receive digital data over the air. The USB sound card installs a driver automatically when I install it.

I often connect to my system remotely using NoMachine NX Server. If I have not first logged into the Ubuntu system at the local keyboard, then in my NX session the sound card is not available. Once I log onto the machine locally, the sound card is present from an NX session.

This is a problem because sometimes I need to reboot the system remotely. I'm able to re-establish the NX session, but then I have no sound card, until I can obtain physical access to the system.

There must be some sort of initialization of the sound card driver that occurs for a local login, but not for an ssh session. Does anyone know where that is? Or is there a way I can simulate a physical login once I've established an ssh session or an X-Server session?

---

### Post by MidnightJava on 2012-12-22
I set the user accounts setting to login on startup, and that's an adequate solution for remote restarts without losing my audio device. I'd prefer not to do auto-logon on startup, even though my kids have not yet grasped that Ubuntu is something they can play with. So if anyone knows how I can enable the audio device from an ssh or NX session after reboot without auto-logon, I'd like to know how to make that work.

---

### Post by Yellow Pasque on 2012-12-23
By default, pulseaudio is set to run as a user daemon, which means it starts when user logs in.
You can either -
1) run pulseaudio in system-wide mode
2) set nx to output audio directly to the ALSA device

---

