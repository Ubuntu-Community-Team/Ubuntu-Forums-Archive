---
title: "playing VOB files from camcorder"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by JGT on 2008-02-25
I first installed Ubuntu on a (now) dual boot XP machine. I'll replace this computer with a Ubuntu-only PC in the future when I have migrated all my work to Linux.

Basically the only real outstanding problem is managing my home JVC camcorder material. I have hours of irreplacible family material stored on mini-DVDs and backed up on a removable hard drive and dada DVDs.

The problem is that the file format used is VOB. The only (Windows) program that I have found useful is Womble Mpeg Video Wizard.

I desparetely need a Linux solution  - I want to reliably play this VOB material in Ubuntu, and then burn DVDs playable on regular DVD players.

Since it's difficult to just play DVDs on Ubuntu, am I stuck with Windows to play the VOB format?

---

### Post by Creative2 on 2008-02-25
try with vlc player  video or xine. vob are mpg (well..there are some differences but........anyway..)

**Read about codecs in my signature, **

*Little note

-If you have a dv video camcoder , you could use kino to import video directly from your cam  but i don't know nothing about your cam..

-cinelerra is a video editing software it can import mpg file..

---

### Post by JGT on 2008-02-25
Thanks. Do I need any plug ins or other updates?


I currently use Womble because other MPEG players could only see part of the file (eg. 10 min in a 30 min clip) when I renamed the files MPEG so other players could see the VOB files. I believe that's caused by small clips being joned together to form larger VOB files. Please excuse my crude terms.

---

### Post by Creative2 on 2008-02-25
mm i have understand few but...yes camcoders use to record new clicp and merge with old clips, 

if you have firewire output on your cam you could try to plug in to your computer (with firewire input ) and use kino , kino for dv cam is a great piece of software

---

### Post by JGT on 2008-02-25
Don't know about Firewire. The camcorder was only supplied with a USB cable, and the manual is in Japanese so it's hard to check!

Thanks for your help.

---

### Post by Creative2 on 2008-02-25
mm anyway now renaming file from Vob to mpeg or mpg you are able to see that files or not on ubunut ^? have you read about codecs and that stuff ?

---

### Post by JGT on 2008-02-25
I'm at work so I'll check VLC later.

Renaming VOB to MP(E)G definately doesn't work properly on Windows. I understand that the VOB files are a kind of wrapper that contain mpeg plus additional information. 

I found that renaming the files leads to very strange effecds, like only seeing portions of the longer file, not being able to move the slider thing to choose where in the clip to watch, and a black screen where video should be.

This is why I need a VOB player.

---

### Post by Creative2 on 2008-02-25
well if you have your files now you could get some informations with this :

ffmpeg -i YOURRFILE | grep Stream 

anyway before get codecs and vlc player :)

---

