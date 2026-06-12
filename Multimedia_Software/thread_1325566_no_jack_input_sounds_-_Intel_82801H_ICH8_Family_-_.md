---
title: "no jack input sounds - Intel 82801H ICH8 Family - Dell Studio"
date: 2009-11-13
forum: Multimedia Software
---

### Post by marioquark on 2009-11-13
here i am:

i own a **Dell Studio 1535** notebook
a **Intel Corporation 82801H (ICH8 Family)**
i use Ubuntu Karmic 9.10
i have installed **ALSA 1.0.20** and **PulseAudio 0.9.19**

*i can't get any sound from jack line-input* when i plug in a mini jack.
i supposed hardware would *switch from built-in mic to jack input*, but it's not what happens...


i'm goin crazy! :)

with mixer, nothing to do: i used all software i know and all input switches and slides configurations solved my problem.
so i'm trying to get some informations to get driver module work:
here ```
/usr/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz
``` i get how to tell ALSA options for my hardware. in "Module snd-hda-intel" section i can specify my model. i would try this, but in file ```
/usr/share/doc/alsa-base/driver/HD-Audio.txt
``` i can't find my model.

many informations can be found on [http://ubuntuforums.org/showthread.php?t=843012&highlight=Intel+Corporation+82801H+input](http://ubuntuforums.org/showthread.php?t=843012&highlight=Intel+Corporation+82801H+input) to get some help.

what can i do to get line-in working?
thank you very much guys!
quark

---

### Post by sawick61 on 2009-11-13
> **marioquark said:**
> here i am:

i own a **Dell Studio 1535** notebook
a **Intel Corporation 82801H (ICH8 Family)**
i use Ubuntu Karmic 9.10
i have installed **ALSA 1.0.20** and **PulseAudio 0.9.19**

*i can't get any sound from jack line-input* when i plug in a mini jack.
i supposed hardware would *switch from built-in mic to jack input*, but it's not what happens...


i'm goin crazy! :)

with mixer, nothing to do: i used all software i know and all input switches and slides configurations solved my problem.
so i'm trying to get some informations to get driver module work:
here ```
/usr/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz
``` i get how to tell ALSA options for my hardware. in "Module snd-hda-intel" section i can specify my model. i would try this, but in file ```
/usr/share/doc/alsa-base/driver/HD-Audio.txt
``` i can't find my model.

many informations can be found on [http://ubuntuforums.org/showthread.php?t=843012&highlight=Intel+Corporation+82801H+input](http://ubuntuforums.org/showthread.php?t=843012&highlight=Intel+Corporation+82801H+input) to get some help.

what can i do to get line-in working?
thank you very much guys!
quark

sound is an output device not input.  the sound "comes out" of the computer.   the input is for a mic.

---

### Post by marioquark on 2009-11-13
oh, sure! i'm an engineer... i know :|
*input sound* means i can't get sound **captured and sent to monitor** (output) or **graphic monitor** (VU meter)

---

### Post by marioquark on 2009-11-20
in the ```
/usr/share/doc/alsa-base/driver/HD-Audio.txt.gz
``` file, written by Takashi Iwai i can read:

> The **automatic switching of the built-in and external mic** per plugging is implemented on some codec models but not on every model.  Partly because of my laziness but mostly lack of testers.  Feel free to submit the improvement patch to the author.

where can i find infos?

---

### Post by marioquark on 2009-11-20
is there any ```
options snd-hda-intel index=0 model=6stack-digout position_fix=1
```
statement in the /etc/modprobe.d/alsa-base.conf file i can set?

---

### Post by OolongBrothers on 2009-12-06
Hi marioquark,

I am experiencing a similar problem as you (I also have the same audio chipset). The functionality is definitely gone from the new gnome-volume-control applet.
However I got input monitoring to work by using the console tool alsamixer. Please check the bug report below and see if the workaround I state there works for you. In that case mark that the bug affects you too and perhaps add a comment. So we drum up some attention to the issue and perhaps get the fix in the next release.

The bug report can be found here: [https://bugs.launchpad.net/ubuntu/+s...ia/+bug/486164](https://bugs.launchpad.net/ubuntu/+s...ia/+bug/486164)

Regards, Alex

---

### Post by marioquark on 2009-12-07
tanks a lot! now i can record audio, but no monitoring... :(
let's feedback!

---

