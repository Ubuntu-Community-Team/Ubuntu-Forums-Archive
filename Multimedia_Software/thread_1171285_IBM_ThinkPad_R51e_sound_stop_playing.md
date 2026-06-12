---
title: "IBM ThinkPad R51e sound stop playing"
date: 2009-05-27
forum: Multimedia Software
---

### Post by freakon on 2009-05-27
Hi!

I am having problems with playing sound on my IBM ThinkPad R51e, on my Ubuntu 9.04. After a few seconds, usualy less then 10 sec, my sound hangs, it start repeating a fragment of second of sound for a while. When I restart Ubuntu, the sound start working, and then hangs again after few seconds of playing. When the sound hangs, I can't let the song play, media player just wont start moving the scroller of the song.

I have tried the change and to ALSA IXP, and to PULSE SERVER, but, the problem continues.

How can I solve this? Anyone having the same problem and have solved it?

Thanks!

---

### Post by R.M. on 2009-06-24
Hello!

I have the same issue on my thinkpad R51e, with a fresh Jaunty Jacalope install. But my sound seem to be more stable than yours, it hang if I open a lot of videos/mp3 on a sequence, and, sometimes, it random freezes after ~30 minutes to 1 hour.

When I installed Jaunty I have no sound at all, so i followed the instructions on this post: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) and then I get this "almost functional" sound.

When the sound hangs, restarting pulseaudio ("killall pulseaudio; pulseaudio") didn't work for me, so maybe pulseaudio is not the problem.

There is another solution on this site: [http://sandeep.wordpress.com/2009/05/14/ati-ixp-ad1981b-thinkpad-r51e-sound-on-jaunty/](http://sandeep.wordpress.com/2009/05/14/ati-ixp-ad1981b-thinkpad-r51e-sound-on-jaunty/)

The instructions there is to get rid off pulseaudio and stay only with alsa, but they didn't worked for me.

(Sorry for my bad english, I'm not a native speaker)

---

### Post by pondo on 2009-08-28
I have the same hardware and same issue. This is really annoying. Sound worked fine in 8.10. I may go back to 8.10 until this gets fixed. :-(

---

### Post by emeraldgirl08 on 2009-10-04
This stinks!

Everything works very nice *but* the sound!

All this after I spent all afternoon downloading on a slow server!

Ugh!

Someone said Ibex works better??? Karmic is coming out in a couple of weeks so I'd like to see how that fares.

---

### Post by emeraldgirl08 on 2009-11-02
Have Karmic running on my R51e and there is no hanging-soundbite :D

I don't have all the codecs needed to play much audio and video yet. I hear there are problems and do not know the first step on getting the audio and video working. I'm actually a little afraid that installing more audio/video codecs will cause that horrid sound to return.

Once ppl get the codecs needed sorted out I'll give it a whirl.

---

### Post by R.M. on 2010-01-16
Hi guys, I found two solutions to the problem:

If you are running ubuntu 9.04 try installing the maintainer version of pulseaudio and alsa, according to the instructions on this site:

[http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/](http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/)

That solved the problem for me.

You can also build the kernel from the upstream (instructions on the site above), that solved the audio problem too, but my wireless conection became quite unstable using the custom build kernel.

---

