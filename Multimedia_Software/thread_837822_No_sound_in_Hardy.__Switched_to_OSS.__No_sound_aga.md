---
title: "No sound in Hardy.  Switched to OSS.  No sound again."
date: 2008-06-22
forum: Multimedia Software
---

### Post by ratdog on 2008-06-22
Hello. I´m pretty noobish and hope someone can help me through this.

I recently installed UbuntuStudio 8.04 64-bit edition.

Initially I had no sound at all.

I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=780961&highlight=ossxmix+mixers](http://ubuntuforums.org/showthread.php?t=780961&highlight=ossxmix+mixers)
and installed OSS.

That enabled most audio functions such as system sounds and rythmbox.
VLC still wouldn´t play audio, but totem would, so that was OK.

Then one day my soundcard (M-audio 2496) stopped loading on startup and when I followed instructions on the forum to load in manually, I heard a pop on the speakers, but still could get no noises in the sound preferences and tests.  

When I try and load the mixer with the ossxmix command in terminal, it says 'no mixers are available'.  

I'm wondering if anyone has any suggestions, other than a full reinstall.
Should I just go back to alsa and try to get it to work?  The OSS tutorial required blacklisting alsa modules.  How do I undo that?

Any help greatly appreciated!   Thanks

---

### Post by ratdog on 2008-06-25
Anyone know how I can get my soundcard to load at every boot again?

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Did you try alsa? I had problems with sound on my Ubuntu until i run all my sounds through alsa sound driver. For me alsa worked magic ;)

---

