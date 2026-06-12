---
title: "audigy soundcard help please"
date: 2008-05-28
forum: Multimedia Software
---

### Post by longcatspace on 2008-05-28
hi, i have an old audigy 1 soundcard, recently on ubuntu 8.04 (heron) and although i hear the start-up sound i can't get any other sound from my soundcard...

any help would be appreciated x

---

### Post by damansandhu on 2008-05-28
hi , try this thread it will help you

[http://ubuntuforums.org/showthread.php?t=808405](http://ubuntuforums.org/showthread.php?t=808405)

---

### Post by damansandhu on 2008-05-28
So open the file for writing:
Code:

sudo gedit /etc/modprobe.d/alsa-base

add these lines to the bottom:
Code:

options snd-ca0106  index=0
options snd_hda_intel index=1




then diasble your onboard audio in bios.

---

### Post by longcatspace on 2008-05-28
thanks, just trying that, i'll report back when i've messed with my bios x

---

### Post by longcatspace on 2008-05-28
my bios doesn't have an option to disable onboard sound, stragely, at least that's what i think

x

---

### Post by Norst on 2008-05-28
If you have the volume control (Volume Applet 2.22.1) on your gnome panel, you can open it and go to File>Change Device, and select what sound device your using. Also double check that when the Audigy is your device, that the 'Audigy Analog/Digital Output Jack' (on the 'Switches' tab) box is **unchecked** (unless your actually using the digital jack to output to a Receiver/Amp). Thats what I have set here and all is well.

Hope this helps,
Norst

---

### Post by longcatspace on 2008-05-28
thanks, didn't do the trick but it was worth a try x

---

### Post by damansandhu on 2008-05-28
so sound works now?

---

### Post by longcatspace on 2008-05-28
no, no sound yet... except for the start-up sound, and in fact all system sounds, when i go to system/pref/sound/sounds i can click on play beside any of those and hear them, but no mp3, video sound

---

### Post by damansandhu on 2008-05-28
search each and every option of your bios , i think every bios has this option.
and have you installed proper audio and video codecs , if not then goto 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and install restricted formats meta package , goto
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by longcatspace on 2008-05-28
ok, that 1st link is looking good, no sound but less errors than other stuff i've tried, i must go to bed, but i'll try to further this later, thanks for all your help x

---

### Post by Yellow Pasque on 2008-05-28
When you get tired of playing with ALSA, switch to OSS4 (link in sig).

---

### Post by longcatspace on 2008-05-29
ok, so i now have sound fro mp3's videos in the box, but not from firefox, i installed flash 10 which is up, but still no sound...

most of the useful bits came from [here]("http://ubuntuforums.org/showthread.php?t=766683"),

maybe i'll try oss4, it just seems i'm so close now where i am x

---

### Post by longcatspace on 2008-05-29
and indeed i did in the end find where to turn of my onboard sound in the BIOS...

hasn't got me sound in firefox yet, but it's good to know it's there x

---

### Post by longcatspace on 2008-05-29
why bless you temujin, your [response]("http://ubuntuforums.org/showpost.php?p=5006877&postcount=2") to a different thread fixed my firefox woes... thanks also damansandhu for your efforts...

wonderful... i can hear my own music from my [myspace page]("http://www.myspace.com/longcatspace")...

x

---

### Post by Yellow Pasque on 2008-05-29
Awesome! :)

---

