---
title: "Audigy2zs PulseAudio static"
date: 2011-10-01
forum: Multimedia Software
---

### Post by rye n on 2011-10-01
I just installed an Audigy2 ZS sound card.
ubuntu natty.

I get static from the speakers, weather I'm playing any sound or not.
in
```
$ alsamixer
```
I can turn PCM to 0 and the static goes away. My sound still works and everything is fine. I can still use the volume control in Banshee, but not the Sound Control in my Cairo Dock. This is fine with me, as my speakers have a volume control as well.
After restarting, it is back to static.
I am wondering how I might fix this.

---

### Post by rye n on 2011-10-02
I tried using
```
sudo alsactl store 0
```
so that the alsamixer settings would stay on when I restart tthe computer.
After restarting, I had no sound.
In order to have sound, I had to turn the PulseAudio Sound Control in Cairo Dock back up, which made the PCM bar in alsamixer return to the top (adjusting the PCM bar alone didn't work). Then, turn down the PCM bar.
So, every time I restart the computer, I have to readjust like this. This is annoying and I'd like a way to fix it, but I don't know a whole lot about how to do it.

---

### Post by rye n on 2011-10-06
just put on a youtube video and noticed more staticy sound, quieter than the original problem.
In dconf-editor > desktop > gstreamer > 0.10 > default_elements > 
I changed music-audiosink to alsasink.
This solved the youtube problem.
Still need PCM muted.
Haven't tried restarting since then.

---

### Post by rye n on 2011-10-10
Now, I started up regular ubuntu 11.04, rather than the no effects startup I was using (to run cairo dock instead of unity). Now the sound mutes if I turn PCM to 0. I can turn PCM to 22 without the volume being affected. This leaves me with very faint, almost inaudible crackly sound that isn't too noticeable during music.
I didn't do anything to set up a driver or whatever when I installed this sound card. Is there something I am supposed to do to get it to work? I don't understand what is going on.. I wish someone would give me some kind of advice...

---

