---
title: "96/24 spdif output on Karmic Koala"
date: 2009-11-05
forum: Multimedia Software
---

### Post by jornahow on 2009-11-05
This may seem Like a trivial question but I have searched the forums for a solution without success.

I started with Ubuntu 9.04 (Jaunty) installed on a Zotac Ion 330 used as an HTPC with XBMC and other audio/video playback packages.  The primary purpose of this setup is a music server.  I have high res 96/24 flac music files on my hard drive. I am feeding my PS Audio dac from the spdif toslink output on the motherboard.  I switched to Karmic Koala and ended up purging pulse audio before I got my spdif output working again.  My problem is that the 96/24 audio files are only output at 44/16 Hz resolution. I only need stereo output, not multichannel sound. Is there someone who can tell me (in simple terms) how to configure alsa to output a 96/24 signal to my dac.  If I playback using Aqualung for example, it shows that the source file is 96000 Hz but the output is alsa @ 44100 Hz SRC type Linear Interpolator. Any help configuring for 96/24 output would be greatly appreciated.

---

### Post by jornahow on 2009-11-05
Still hoping someone will respond with advice for this issue...

---

### Post by jornahow on 2009-11-06
I'm still hoping someone see this post and propose a solution

Thanks for reading!

---

### Post by Ubuntaqua on 2009-12-15
I have the exact same issue, with the same motherboard, with the same sound usage (high def audio).
I try to use the Coax output and not the toslink but it should be the same.

Try to edit (using sudo)  /etc/pulse/daemon.conf and change the line 
; default-sample-rate = 48000
by
default-sample-rate = 96000

then do "pulseaudio -k" in the terminal to kill the currently running pulseaudio session.

This is the "normal thing to do" but strangely doesn't work for me.
I'm still lost in this issue.

---

