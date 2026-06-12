---
title: "Linux Multimedia Fail - Lucid Lynx"
date: 2012-05-05
forum: Multimedia Software
---

### Post by Coche Hawk on 2012-05-05
Hi guys,

i try to see a movie but for some reason i can't. I try different ways, but here is the problem:

Trying with VLC:          NO video - sound plays - subtitles allowed
Trying with Movie Player: video plays - NO sound - Subtitles don't load
Trying with Banshee:      video plays - sound plays - Can't find how to allow Subtitles.

Somebody help me please](*,)

---

### Post by StewartM on 2012-05-07
Is it a DVD? 

If so, look here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

sudo apt-get install libdvdread4

Then open a terminal window and execute: 

sudo /usr/share/doc/libdvdread4/install-css.sh

Rebooting may be necessary. 

(There's more troubleshooting on that site).

StewartM

---

### Post by Coche Hawk on 2012-05-10
Hi Steward,
thanks for your reply.I ran the commands, but is already installed. 
Thanks again.
José

By the way, did somebody knows a command to verbose during i play the VCL, by instance?
The movie is 'the wave" is an AVI file, the subtitle is on a separate file.srt

Cheers
José

---

