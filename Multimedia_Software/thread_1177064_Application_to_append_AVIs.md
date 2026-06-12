---
title: "Application to append AVIs?"
date: 2009-06-03
forum: Multimedia Software
---

### Post by dodle on 2009-06-03
I want to join some AVIs.  Normally I use Avidemux, which is working fine on Windows, but when I use it in Ubuntu the audio of my AVIs gets messed up. 

Is there another good program?  I tried using VirtualDub, but it doesn't work too well with WINE on my machine.

---

### Post by dodle on 2009-06-04
I realized that the problem with Avidemux isn't only on Ubuntu.  Even on the windows version the sound gets messed up.

---

### Post by MartyBuntu on 2009-06-04
You're using the **COPY** feature for audio, right?

Maybe you are re-encoding, that could be the problem.

---

### Post by dodle on 2009-06-05
I am using "copy".  It only seems to be more of a problem with AVIs than Mpegs.  If I take each AVI and convert it to an Mpeg, then append the Mpegs together, the audio turns out fine.

---

### Post by andrew.46 on 2009-06-06
Hi dodle,

> **dodle said:**
> If I take each AVI and convert it to an Mpeg, then append the Mpegs together, the audio turns out fine.

You have perhaps come across the heart of the guide I was just about to mention :-). There is a section of the FFmpeg FAQs that considers exactly your situation and recommends an initial conversion to mpg:

3.18 How can I join video files?
[http://ffmpeg.mplayerhq.hu/faq.html#SEC30](http://ffmpeg.mplayerhq.hu/faq.html#SEC30)

Perhaps this might be worth a look? Yes it is commandline but on this page the commands have been laid out for you :-). If you were interested in trying this approach you could use the repository FFmpeg but I would suggest at the very least setting FFmpeg to [use all available formats]("http://ubuntuforums.org/showthread.php?t=1117283").

All the best,

Andrew

---

