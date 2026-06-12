---
title: "Capturing Audio Streams"
date: 2009-02-12
forum: Multimedia Software
---

### Post by TBOL3 on 2009-02-12
So, I'm trying to record skype conversations, or at least capture the audio from other programs.  But I can't for the life of me get it to work.

Every source that I've seen tells me to go to alsamixer, and start the capture, and mix sources.  Unfortunently, in alsa mixer, there is no mix option, and no form of mix.   Can any of you tell me how to capture streams?

I am on an HP Pavilion dv6626us, with some Intel audio card (or at least thats what it says).

Thank You

---

### Post by TBOL3 on 2009-02-12
I'm still using 8.04, if that helps at all.

Once again, thanks for any help.

---

### Post by TBOL3 on 2009-02-12
Well, I think I'm a bit closer.

So far, I've been trying to do it with ALSA, to no success.  So I tried doing it with pulseaudio.  It seems to work better, as I can the audio that that apps are putting out.  But I have two problems.

A.  Skype doesn't work.  I don't know why, but skype just won't make ANY audio.  (Flash didn't as well, but at least there was a patch for that).

B.  Audacity still wouldn't record it (but I think the default gnome-recorder might).

Do you know how to either solve these problems, or do it with alsa, thanks.

---

### Post by neu2buntu on 2009-02-13
you should be able to do it using pulse audio and qjackctl (jack) . have a good look at this post [http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

i can use audacity to record anything that goes to my speakers using this tutorial, so i would say it will work for skype also.

---

### Post by TBOL3 on 2009-02-14
Well, I followed the part about setting up a sound server.  But I couldn't get it to either take sound from my co3u, and record sound from anything but my laptop's built in mic (rather then from apps).

---

### Post by neu2buntu on 2009-02-14
is this from my post or another 1. you have to be kind of specific on the forum to get the right help .


give us a bit more info on what exactly you have done. you need to specify your ubuntu version ie 804 or 810 or whatever and what post you have followed etc... info is very important and im just a noob with a bit of experience...lol... but if u stick around the ubuntu forum you will def get your sound issues sorted as i did... and then you will be able to help a noob Too ... good luck

---

