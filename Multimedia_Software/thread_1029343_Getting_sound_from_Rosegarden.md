---
title: "Getting sound from Rosegarden"
date: 2009-01-03
forum: Multimedia Software
---

### Post by Colin@oxford on 2009-01-03
There have been a number of posts here and elsewhere about the difficulty in getting sound out of Rosegarden.  I too had these problems (and almost gave up several times).  I am very much a beginner in this area, so what I have to say is only what has worked for my system and I hope that others can suggest neater solutions.

I am running Hardy and do not have a sound card, just the chip on the motherboard.  I can get sound out of all programs tried except Rosegarden.  Audacity works well (but distorted using Jack+ALSA).  MIDI files play using Audacious and TiMiDity++.  Rosegarden connects 4 MIDI outputs to timidity's inputs when starting, and since timidity can clearly play these files I was disappointed that I could still not hear anything.

The Rosegarden home page did not help me much, but I did discover this page which gave me encouragement:

[http://www.legg.uklinux.net/rosegarden_sound_howto_fc7.html]("http://www.legg.uklinux.net/rosegarden_sound_howto_fc7.html")

At this point I obtained QSynth and started this up after starting Rosegarden.  The JACK connect screen then shows that in addition to the four connections to timidity, the port labelled 

7: out 5 - MIDI output system device

is connected to QSynth.  Unfortunately, still no sound :(

I then deleted all the connections and made one connection from 

3: out 1 - General MIDI device

to QSynth.  Sound!  Yes, really! :D

Playing further with JACK, I discover that despite Rosegarden's dcoumentation insisting that it is using ALSA, JACK running with OSS as its back end works just the same.  Since I appeared to have problems with ALSA as the backend to JACK, this is useful.

So I have at least a work-around.  I then uninstalled timidity, started Rosegarden again and then QSynth.  This time the sound is produced without any changes to JACK's connections.  It seems that if timidity is around then Rosegarden connects to it, but that this connection does not work.  Without timidity, Rosegarden does not complain, but does not connect anything.  When QSynth is around then Rosegarden connects (correctly) to it.

So the little script recommended in the cited page to start JACK, QSynth and Rosegarden together appears to be the right approach.

---

### Post by kwtm2 on 2009-01-14
Hi!  I, too, managed to get Rosegarden working.  I did it without using JACK; in fact, it turns out that it's easier to get things working by not using JACK.  I've posted a quick HOWTO below at:

[http://ubuntuforums.org/showpost.php?p=6547465&postcount=2](http://ubuntuforums.org/showpost.php?p=6547465&postcount=2)

which is actually from my post at LinuxQuestions at:

[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/#post3408082](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/#post3408082)

Hope this helps.  I see that you managed to use JACK, and I haven't quite learned how to use it yet.  It should be simple, but even after a lot of fiddling there were too many variables to tell me if it was failing due to JACK or due to the other programs connected to it.  Things were much simpler to figure out without JACK in the equation.

---

### Post by markbuntu on 2009-01-14
It is really helpful to use patchage to manage those kinds of connections. It is very intuitive and easy to use. Just point and click to conect and disconnect everything.

---

