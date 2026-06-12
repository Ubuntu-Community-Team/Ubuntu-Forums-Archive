---
title: "Find broken/defective MP3 files"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by TheFuzzy0ne on 2007-06-14
Hi everyone.

I am trying to find a program or script of some kind which can scan my music collection and locate any MP3 files that can't be played as they are broken in some way.

These broken MP3 files are all duplicates of other working ones, and I have hundreds of them! I don't need them repair, I just want them removed if it's possible. The main reason is that Amarok ceases playback if it crosses 3 MP3s in a  row that it can't play. If there's a setting in Amarok I am missing that will prevent this, I would appreciate it if someone could share it with me. :)

Many thanks.

---

### Post by bashologist on 2007-06-14
Maybe you could use the exit status of a program to test if it's good?

location="/path/to/sound.mp3"
if mplayer /data/music/cat-sounds/angry1.wav -endpos 1 >/dev/null 2>&1; then echo rm "$location"; fi

---

### Post by TheFuzzy0ne on 2007-06-14
> **bashologist said:**
> Maybe you could use the exit status of a program to test if it's good?

location="/path/to/sound.mp3"
if mplayer /data/music/cat-sounds/angry1.wav -endpos 1 >/dev/null 2>&1; then echo rm "$location"; fi

That's a very neat idea. I'd prefer to use that as a last resort if necessary as I'd need to write a script (which might be fairly simple), but it would most likely be buggy as hell as I am fairly new to Linux.

Also, you're script would require me to listen to the entire song. I have about 5000 MP3s, so I would like to avoid it if I can. :P I could delete my entire music collection and re-rip the CDs (most of which I don't even have anymore), but that would take forever. As you can imagine, my MP3 collection didn't grow overnight. It's taken me about 10 years to accumulate.

I would appreciate an brief explanation on what your code does, though, if you wouldn't mind. 

It's the "/dev/null 2>&1" part I don't really understand.

Thanks for your input. :)

---

### Post by reclusivemonkey on 2007-06-14
I'm pretty sure there is a program which does this for you if you search synaptic.

---

### Post by TheFuzzy0ne on 2007-06-14
> **reclusivemonkey said:**
> I'm pretty sure there is a program which does this for you if you search synaptic.
I found "checkmp3". I'm hoping that it does what I need it to. I saw it previously and forgot about in the hope I could find a GUI version. (No idea why, as I am perfectly happy with the console).

Hey, by the way - that's pretty good typing for someone your age, or are you older than you look? :P (Sorry). Cute kid :D

---

### Post by reclusivemonkey on 2007-06-14
> **TheFuzzy0ne said:**
> 
Hey, by the way - that's pretty good typing for someone your age, or are you older than you look? :P (Sorry). Cute kid :D

LOL Thanks =] I'm sure it won't be long before he can type way faster than me!

---

### Post by TheFuzzy0ne on 2007-06-14
Oh, even better. We have an "mp3check" as opposed to "checkmp3" which does EXACTLY what I need. Thanks.

---

