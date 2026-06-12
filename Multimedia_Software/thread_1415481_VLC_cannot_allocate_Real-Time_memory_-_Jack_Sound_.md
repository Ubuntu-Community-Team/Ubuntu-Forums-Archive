---
title: "VLC cannot allocate Real-Time memory - Jack Sound Server"
date: 2010-02-24
forum: Multimedia Software
---

### Post by zenon222 on 2010-02-24
I am using vlc as a source for jack and it's running very buggy.  Below are the errors spat out to the terminal when running.  The lock down memory error occurs when I press play in vlc.

Any clue what can be causing this? I have the audio group set to reserve 90MB for Real-Time operation

```
zenon@zenon-ubuntu:/usr/src/vlc-1.0.5/vlc-1.0.5$ ./vlc
VLC media player 1.0.5 Goldeneye
[0x1f94888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x2a0bb68] dummy demux: command `nop'
Enhanced3DNow! detected
SSE2 detected
cannot lock down memory for RT thread (Cannot allocate memory)
Enhanced3DNow! detected
SSE2 detected
cannot lock down memory for RT thread (Cannot allocate memory)
Enhanced3DNow! detected
SSE2 detected
cannot lock down memory for RT thread (Cannot allocate memory)
jack_client_thread zombified - exiting from JACK

```

---

