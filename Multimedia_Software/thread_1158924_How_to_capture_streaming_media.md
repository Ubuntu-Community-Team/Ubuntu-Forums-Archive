---
title: "How to capture streaming media"
date: 2009-05-14
forum: Multimedia Software
---

### Post by salviablue on 2009-05-14
How can one capture streaming and other types of media
i.e. when I was a M$ whore, I used to just be able press record on the build in sound recorder, and it would record whatever sound(s) was(where) playing. 
How ever I can't seem to get an equivalent thing working in hardy.

I have found loads of posts on using vlc and mplayer w/scripts, but what if you can't get the exact location of the sounds etc?

Besides these routes have not worked for me as yet.

Any ideas, I am probably missing something really simple.

---

### Post by salviablue on 2009-05-14
I have tried screen cast but it recorded no sound, just the "action"

---

### Post by mechdave on 2009-05-14
You can save streamed media by using mplayer with the -dumpstream option.. See [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#streaming-save]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#streaming-save")

---

### Post by salviablue on 2009-05-14
stream not seekable

is what I get from that.
thanks for the suggestion though.
is there no way to do it like i did on M$?

---

### Post by markbuntu on 2009-05-14
streamripper will record a stream. Just drop the url into it.

---

### Post by logos34 on 2009-05-14
It's been ages since I tried to record from system sound (use mplayer or strearipper exclusively)...I just tried it with gnome sound recorder...it used to be so easy--just set source to mix, output to mp3, done...Now I just get a silent track.  Capture sound level is ok...Have to use Audacity to record a signal...Must be PulseAudio screwing everything up...hmm...jeez I wish they'd stop 'improving' things

Edit: managed to record radio stream as wav and mp3, but slightly distorted.  Settings: System>Prefs>Sound>Recording input: Pulseaudio, rest left as 'Autodetect'.  Then back in Gnome Sound Recorder 'record from input' shows only 'Master' (no choice).

Would be nice, though, to be able to get a clear signal.  Nor does mouse-over playback work on resuting file in nautilus.

---

