---
title: "Jaunty &quot;Null Output (Pulseaudio Mixer)&quot; ... No sound after reboot?"
date: 2009-06-02
forum: Multimedia Software
---

### Post by Zombie Feynman on 2009-06-02
Hi all,

I'm not entirely sure what happened to my computer, my install of Jaunty is only a couple of days old. My sound was working perfectly last night when I shut down my laptop (hp tx1000), but this morning there's none to be found. In the mixer, rather than the ALSA options that I had last night, all I see is "Playback: Null Audio (PulseAudio Mixer)". I'd really like to get my sound working again, and I've tried a couple of fixes like adding myself to the audio group, but none have done the trick. My sound device is an nVidia Corporation MCP51 High Definition Audio (rev a2).

Cheers!

---

### Post by Phkillah on 2009-06-11
same here...

---

### Post by Regenweald on 2009-06-12
[http://ubuntuforums.org/showthread.php?t=1012636&page=2](http://ubuntuforums.org/showthread.php?t=1012636&page=2)

Try this thread.
Little edit:

1. Add user to audio group
     ```

     sudo adduser 'you' audio

``` 
2. Delete contents of ~/.pulse
3. Reboot.

---

### Post by madchine on 2009-07-26
These symptoms can also occur if MPD doesn't play nice with PulseAudio and decides to highjack the audio device. That way Pulse can't see the real audio device and decides that a virtual 'null device' is the main audio output device. If you use MPD, be sure to check your /etc/mpd.conf file (especially the user to run as and the audio output section).

---

### Post by awe on 2009-08-30
How do I join a user to an additional group when my users are on an LDAP tree? Can I just put two group numbers?

---

