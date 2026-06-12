---
title: "Cannot get microphone to wok"
date: 2010-02-21
forum: Multimedia Software
---

### Post by The Toxic Mite on 2010-02-21
Hello!

I am trying to get my microphone to work on my Creative Soundblaster Audigy card. It's not muted AFAIK, but I can't get the sound recorder to record anything; nothing shows up on the sound level thingy.

I have imagebin'd a screenshot of my current sound input settings: [http://imagebin.org/85894](http://imagebin.org/85894)

---

### Post by lyall on 2010-03-07
at the command line enter gnome-alsamixer
check you setting 

it is a place to check

good luck and have fun learning

---

### Post by neouser on 2010-03-08
Hello,

Recently I had a similar problem with the mic after I shifted from windows to ubuntu 9.1 (netbook remix). After reading various contributions on various fora I tried one of the most simple suggestions, and it worked!!!

Under sound preferences I just changed the "connector" to microphone 2 instead of 1.

---

### Post by gruvn on 2010-03-08
Not sure if this will help.  My mic wasn't working (for Skype only) and I discovered this bug [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055).  Look for the message by Steve Jackson.  

Essentially, the fix is to install pulseaudio volume control (pavucontrol), and then unlock the left and right faders (for the mic). Set one to max and the other to min, and it should work. If no love, reverse them (ie set the opposite to max).

Hope that helps if the other solutions haven't.

:)

---

