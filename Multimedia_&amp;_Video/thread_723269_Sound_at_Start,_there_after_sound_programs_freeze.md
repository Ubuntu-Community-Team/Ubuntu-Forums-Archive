---
title: "Sound at Start, there after sound programs freeze"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by flickerfly on 2008-03-13
I've recently developed a problem after messing around with recordmydesktop. I don't know if it is related or the heavier than normal use of my USB headset might also be related.

In any case, here are my symptoms:
[LIST]
[*]I hear sound at login. In fact, I hear the same login sound twice, one immediately after the next.
[*]I hear no sound after login.
[*]Any program dealing with sound freezes when I try to play audio or video.
[/LIST]

The programs I've messed with include
[LIST]
[*]Banshee (Stable and SVN)
[*]VLC
[*]Totem
[*]MPlayer
[*]jack.play
[*]aplay
[/LIST]

I noticed some errors about not being able to find JACK, so I figured I might get around this by installing that. This has not been the case, but I'm not sure if it might need further configuration that I haven't given it.

I've restarted the machine several times including once with the USB headset removed to assure that there was only one sound card available. I've checked to make sure my kernel sound modules are still installed. The sound card still shows up with lspci. alsamixer still detects the device. I've tried a reinstall of all the alsa related packages in apt that I could find. 

I haven't seen any error messages aside from the suggestion that Jack was missing coming from Banshee.

Any suggestions on where I can go from here?  :confused:

---

### Post by superprash2003 on 2008-03-13
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by flickerfly on 2008-03-13
Using SuperPrash's link, I found that most of the options in the dropdown boxes in the gnome-sound-properties utility cause the utility to freeze when I press the Test button. This includes ALSO, Intel ICH6 and Intel ICH6-IEC958.

ESD is an exception as it provided an error instead.

OSS works so I setup the default mixer to OSS Mixer.

I'd like to know what the bigger problem is though? Why can't I use ALSA? Why doesn't it auto-detect properly?

---

### Post by superprash2003 on 2008-03-13
probably because it doesnt support your card!!!you could hunt for linux drivers for your card on the internet.. hopefully future ubuntu versions will have better support for sound cards

---

### Post by flickerfly on 2008-03-13
It was working great for the last two years, same card, same hardware and I've been running gutsy since about the time it came out. I seriously doubt it is an unsupported card.

---

