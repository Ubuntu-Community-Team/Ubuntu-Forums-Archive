---
title: "Problems with video playback and editing."
date: 2013-05-06
forum: Multimedia Software
---

### Post by The Whambangler on 2013-05-06
Hello all,
I've recently purchased a rather expensive camcorder, and am looking to do some video editing on my computer. I am running the current and fully updated version of ubuntuu. The problem first started when I tried watching the videos I recorded, unedited, with vlc. All the people moving seemed... choppy? I guess that's how I'd describe it. They have lines running through them, even though the background generally looks fine. I'm also not able to skip ahead at all, or the video stops working. When I tried watching the videos in Movie Player, everything was fine, so I figured I wouldn't worry about it. Unfortunately when I try opening video in editing software, OpenShot or Pitivi, I have the same problem: people full of lines and the inability to skip. I was wondering if maybe there's a driver or something I should download? I'll be up front with you, I'm not the most technologically advanced monkey on this rock. But I have a lot of passion for film making and a strong ability to learn. Anyone who helps me gets a credit in my first full length feature film: Baron von Roten Defends the Honor of the Tribe. :popcorn:

---

### Post by The Whambangler on 2013-05-06
Also, I've had trouble playing youtube videos ever since the most recent update. The sound still plays fine, but the video is not smooth. Not sure if this has anything to do with anything, just thought it may help.

---

### Post by The Whambangler on 2013-05-07
OK, so youtube works fine on firefox, that must be an issue with chrome. I still can't fix my problem though. I'm thinking about downloadin other editin softerware and trying that out. It's weird how it only works in Movie Player, and even in that it often freezes up if I try skipping. Maybe I have to convert to a different format? Right now they're .MTS, "MPEG-2 transport stream"

---

### Post by Yellow Pasque on 2013-05-07
What kind of hardware do you have?
```
lspci
```

---

### Post by The Whambangler on 2013-05-08
> **Temüjin said:**
> What kind of hardware do you have?
```
lspci
```
HP Compaq dx2400

---

### Post by Archit88 on 2013-05-08
> **The Whambangler said:**
> OK, so youtube works fine on firefox, that must be an issue with chrome.

if you are recently updated to ubuntu 13.04 , i suggest you to go with Chromium browser or / Firefox since Chrome is not compatible with 13.04 ATM.

---

### Post by Archit88 on 2013-05-08
> **The Whambangler said:**
> HP Compaq dx2400

Can you post the whole output of ```
[COLOR=#000000][FONT=Ubuntu Mono]lspci[/FONT][/COLOR]
```

---

### Post by The Whambangler on 2013-05-08
> **Archit88 said:**
> Can you post the whole output of ```
[COLOR=#000000][FONT=Ubuntu Mono]lspci[/FONT][/COLOR]
```

Yeah, I don't know it off the top of my head. I'll figure it out when I get home... somehow. Once again, I don't really know much about computers, thank you for your patience.

---

### Post by The Whambangler on 2013-05-08
> **Archit88 said:**
> if you are recently updated to ubuntu 13.04 , i suggest you to go with Chromium browser or / Firefox since Chrome is not compatible with 13.04 ATM.
Yeah, I've just been using Firefox. I'm not fami;liar with Chromium, but it's a really cool name.

---

### Post by The Whambangler on 2013-05-08
> **The Whambangler said:**
> Yeah, I don't know it off the top of my head. I'll figure it out when I get home... somehow. Once again, I don't really know much about computers, thank you for your patience.

Oh, I didn't know I was not allowed to say that word. My bad lol

---

### Post by QIII on 2013-05-08
No, you are not allowed to use that word.  I fixed it for you.  I suggest reviewing the Forum Code of Conduct, to which you agreed when you created your account.

---

### Post by The Whambangler on 2013-05-08
> **QIII said:**
> No, you are not allowed to use that word. I fixed it for you. I suggest reviewing the Forum Code of Conduct, to which you agreed when you created your account.

My bad again. I figured that the word being autoreplaced by stars woulda been enough. Had I known that the stars themselves were offensive I woulda changed the word like you did right away. Won't happen again.

---

### Post by The Whambangler on 2013-05-10
I thought I had the most updated version of ubuntu, but that doesn't seem to be true. Ima try updateing tomorrow, I gotta head to work then I'm goin out right afterwards, but here's my system specs:

UBUNTU
Release 12.04 (precise) 32-Bit
Kernel Linux 3.2.0-41-generic
GNOME 3.4.2

HARDWARE
Memory 2.9 GiB
Processor Pentium(R) Dual-Core CPU E5200 @ 2.50 Ghz x 2

SYSTEM STATUS
Available disk space 37.6 Gib

---

### Post by The Whambangler on 2013-05-11
bump

---

### Post by Yellow Pasque on 2013-05-11
...
> **Archit88 said:**
> Can you post the whole output of ```
[COLOR=#000000][FONT=Ubuntu Mono]lspci[/FONT][/COLOR]
```

---

### Post by The Whambangler on 2013-05-12
I really think it has to do with the file type. The camera came with media conversion software, but it's not linux compatible. Does anyone know a good one?

---

### Post by The Whambangler on 2013-05-13
I found this: [http://karuppuswamy.com/wordpress/2010/06/07/how-to-convert-canon-mts-video-files-to-other-formats-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/07/how-to-convert-canon-mts-video-files-to-other-formats-in-ubuntu/)

But it requires doing things I'm not really comfortable doing...

---

