---
title: "Flash Player 9 + XDMCP = no sound"
date: 2008-05-16
forum: Multimedia Software
---

### Post by secret_squirrel on 2008-05-16
I have a thin client setup with clients connecting to the Ubuntu server using XDMCP.  The thin clients have an esound server and system sounds come through the thin client fine.

The problem is with Flash Player 9 (e.g. You Tube vids): the audio comes through the server's speakers, not the thin client's.

Now, I know that Flash Player 9 doesn't support ESD (only alsa) so I knew it wouldn't work right out of the box.  However, none of the fixes I've tried have worked.  

Here's what I've tried so far:
1. Under System > Prefs > Sound make sure that ESD is the sound server for everything.
2. Install pulseaudio, pulseaudio-esound-compat, paprefs and paman
3. Tried installing both flashplugin-nonfree-extrasound and libflashsupport (both say that they provide a wrapper that outputs sound via pulseaudio, you can only have one at a time installed).
4. Added user to groups pulse, pulse-rt and pulse-access
5. In /etc/pulse/default.pa append to the load-module module-esound-protocol-unix line "socket=/tmp/.esd/socket"
6. Make sure /tmp/.esd/socket exists.
7. Before running firefox from the command line, set FLASH_FORCE_ESD=1 or FLASH_FORCE_PULSEAUDIO=1
8. Run paprefs and tick first three boxes on network tab.

There aren't any error messages in the logs, the pulseaudio server is definitely running but still the sound comes out of the server.

I've also tested by running a straight XDMCP connection from an Ubuntu PC to the server but the result is the same.

I can think of a couple of possibilities (both could be wrong):
i) Flash Player isn't picking up the wrapper and is still using alsa for the sound.
ii) Flash Player is correctly routing sound into pulseaudio, but pulseaudio isn't acting as an ESD replacement server so the sound still isn't coming out via ESD.

I don't know how to get further though.  Any help appreciated.

Refs:
packages.debian.org/sid/flashplugin-nonfree-extrasound
[www.pulseaudio.org/wiki/FlashPlayer9Solution](www.pulseaudio.org/wiki/FlashPlayer9Solution)

---

