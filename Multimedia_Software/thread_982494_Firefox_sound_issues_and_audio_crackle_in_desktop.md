---
title: "Firefox sound issues and audio crackle in desktop"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Soturi on 2008-11-14
Hi everyone,

I've been a long-time Ubuntu supporter, but only recently have I had the opportunity to install it for my personal use. I have noticed a few problems with my sound.

The first problem happens in Firefox. If I am playing a song in Rhythmbox, or any other music player, if I try to play any kind of sound in Firefox, I hear nothing. This is most accurately illustrated in playing videos. Unless I exit the music player and restart firefox, I cannot hear anything.

The second problem is also related to audio: sounds occasionally crackle or pop for no particular reason. It happens randomly, but always at the beginning of a sound. For example, I can play 10 songs in a row just fine, but the 11th has a loud pop or crackle as it begins. This also happens with Pidgin notifications, occasionally the beep crackles and pops as it plays.

Thank you in advance for any help!

---

### Post by psyke83 on 2008-11-14
Welcome. I'm going to assume you're using Hardy, correct? If so, then your problem is definitely PulseAudio. Hardy shipped with PulseAudio (a sound server), but it was not configured correctly by default. You need to take some time to configure it properly.

Read the FAQ of the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide for more information, and follow the steps if you're feeling adventurous.

Configure PulseAudio properly before investigating the crackling/popping issue.

---

