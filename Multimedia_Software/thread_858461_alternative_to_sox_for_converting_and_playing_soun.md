---
title: "alternative to sox for converting and playing sound files?"
date: 2008-07-13
forum: Multimedia Software
---

### Post by bcrowell on 2008-07-13
I used to use sox (and the "play" script packaged with it) to play sounds from the command line, to convert sounds from one format to another, and to do effects on sounds. However, sox has always had a problem with crashes, and it also seems to be getting neglected these days by its maintainers and packagers, so I basically can't get any of the functionality to work these days on my hardy heron x64 box. I've tried recompiling lame, installing libsox-fmt-all, etc.

Here are the alternatives I've come up with so far:

madplay -- decode mp3
lame -- encode mp3
soundstretch -- change tempo or pitch of a sound (works much better than sox, even when sox doesn't crash)

This still leaves me with no way to play a sound from the command line, or to do ogg encoding or decoding from the command line. Any suggestions?

TIA!

Okay, a little googling turned up the answer to my own question.

aplay -- play sound files
oggenc -- encode ogg (part of the vorbis-tools package)
ogg123 -- decode ogg

---

### Post by andrew.46 on 2008-11-22
Hi bcrowell:

> **bcrowell said:**
>  However, sox has always had a problem with crashes, and it also seems to be getting neglected these days by its maintainers and packagers, so I basically can't get any of the functionality to work these days on my hardy heron x64 box.

In defence of SoX a new version was released on November 10th 2008. You might be better compiling this from source if you have trouble with the repository versions of SoX.

  Andrew

---

