---
title: "WINFF Troubles"
date: 2012-02-29
forum: Multimedia Software
---

### Post by donsmouse on 2012-02-29
i am using kubuntu 11.10 with gtk record my desktop, after recording the screencast the ogv file looks fine but when i try to convert it with winff this is what it looks like:
no matter what i convert it to it looks like this all the time
please anybody can help me?

Thanks in advance

---

### Post by donsmouse on 2012-03-02
I have searched all over the net and can't find a solution to this
does anyone have an answer?????
 
 
Thanks in advance

---

### Post by inobe on 2012-03-02
looks the the quality settings are low.

in winff there are ways to improve output quality, that'l require some googling and reading the docs.

there are also desktop recorders that have youtube uploaders built in.

kazam is nice [https://launchpad.net/kazam](https://launchpad.net/kazam)

nixi explains it [http://www.youtube.com/watch?v=yqedu_lxcv4](http://www.youtube.com/watch?v=yqedu_lxcv4)

---

### Post by donsmouse on 2012-03-04
thank you ill give it a try thanks so much

---

### Post by FakeOutdoorsman on 2012-03-04
You can try using ffmpeg directly. If you tell me what output format you require I can give you an example command. Are you using 11.10?

---

### Post by donsmouse on 2012-03-04
yes i am using kubuntu 11.10 64 bit
 
once i issue the command to record it how do i stop the command from recording?
 
i want to record it as an avi video
i tried kazam and it wouldnt load on the machine for some reason also pleasae not that my video card is an amd 880g ati mobility radeon hd 4250 graphics card
i hope this helps
 
 
thank you

---

### Post by FakeOutdoorsman on 2012-03-04
> **donsmouse said:**
> once i issue the command to record it how do i stop the command from recording?
What I meant is that you can continue to use recordmydesktop and you can then use ffmpeg to re-encode the video from recordmydesktop to whatever format you like.
 
> **donsmouse said:**
> i want to record it as an avi video
First install **libavcodec-extra-53**. It will enable the mp3 encoder in ffmpeg.
```
sudo apt-get install libavcodec-extra-53
```
Now for an example:
```
ffmpeg -i input.ogv -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 output.avi
```
Note that AVI is a container format and can contain various video formats.

---

### Post by donsmouse on 2012-03-04
ok thank you ill give it a try
thanks so much in advance

---

### Post by donsmouse on 2012-03-04
ok i did what you said and here is the output again,maybe i need to lower my video quality in gtk recordmy desktop

---

### Post by donsmouse on 2012-03-04
maybe is my graphics card i know on my desktop it had a nvdia geforce card installed and it worked perfectly on gtk recordmy desktop, so i wonder if its just because of ati driver i downloaded from there website?
 
anyway i don't know what could be causing this problem,but i would love to fix it.

---

### Post by FakeOutdoorsman on 2012-03-04
Does the ogv file from recordmydesktop also look bad? Have you tried another player other than Dragon Player; such as VLC, MPlayer, or ffplay?
```
ffplay out.ogv
ffplay output.avi
```

---

### Post by donsmouse on 2012-03-05
yes no matter what player i use it looks the same
i even tried playing around with different settings in recordmydesktop and nothing works except for when i lower the video quality in it,then it works and then you can make out some things but then its blury.
the original ogv files are perfect

thank you

---

### Post by donsmouse on 2012-03-05
I finallygot kazam to work and it works great when i export it to youtube.

but i need a program that i can record with and then be able to edit the movies afterwards
i tried xvidcap and also tried the downgradable instructions to get the sound work with no luck im on a 64 bit system and it wants to use i386.

Any ideas on what other programs i should use?

Thanks in advance

---

### Post by ron999 on 2012-03-05
> **donsmouse said:**
> 
the original ogv files are perfect

If you upload a sample somewhere, maybe we can work on it.

---

### Post by donsmouse on 2012-03-05
the only place i could upload it would be youtube
i think kazam does a perfect job so far

---

### Post by donsmouse on 2012-03-05
i have installed ubuntu 12.04 beta 1 to see if this fixes the problem which i hope it does

if anyone else has any ideas please let me know

thanks in advance

EDIT: Ubuntu 12.04 worked perfectly,since its only in testing mode right now im going to install ubuntu 11.10 and see if i get the same perfect results which i hope i do
Thanks to all who helped me out with this,kubuntu must have some kind of bug that wont let me convert my videos or something i dont know.

EDIT: how to go back to ubuntu 12.04 because the videos were looking choppy again.

---

### Post by donsmouse on 2012-03-05
ubuntu 11.10 still shows choppy videos here is my xorg file, please have a look and see if i am missing anything please

Thanks in advance

---

