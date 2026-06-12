---
title: "KAudioCreator error when ripping to MP3"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by prophet665 on 2007-10-13
Ok...got the LAME codec using :
sudo apt-get install lame

Everything went fine.  I then tried ripping a CD to MP3 format and I get the following error:

[B]lame --preset standard --ta 'Iron Maiden' - --tt 'Invaders'


Assuming raw pcm input file
LAME: Can't get "TERM" environment string.
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding <stdin> to <stdout>
Encoding as 44.1 kHz VBR(q=2) j-stereo MPEG-1 Layer III (ca. 7.3x) qval=3
ÿûd[/B]

The MP3 encoder settings are the default:
~/%{extension}/%{albumartist}/%{albumtitle}/%{artist} - %{number} - %{title}.%{extension}

New to Linux, so it might be a permissions issue, but I doubt it since i should be ripping to the home directory and I am using /tmp for the temporary WAV file.  

I am willing to use another ripper to get the job done, but it seems I should be able to get this one working. 

Thanks in advance everyone.

---

### Post by prophet665 on 2007-10-14
No one?  Wrong forum, maybe?

---

