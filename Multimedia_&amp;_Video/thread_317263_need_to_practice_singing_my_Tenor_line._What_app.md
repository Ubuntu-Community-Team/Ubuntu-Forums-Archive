---
title: "need to practice singing my Tenor line. What app?"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by hanzj on 2006-12-12
Hello,
I will be part of a trio of Soprano, Alto, and Tenor (me). I would like to practice singing the tenor tune of Silent Night in order to get it in my head. I don't know the correct (musical) terminology. What kind of program am I looking for?  I need a simple program for this simple task. 

If I could get a program that will let me enter more than one tune, (in other words, I want to enter Soprano, Alto, and Tenor), that will be great. But I would like the option of muting the soprano and alto tunes in the beginning, but making these tunes play when I feel more confident.

Thank you.

---

### Post by predaeus on 2006-12-12
You could try Rosegarden a sequencer and musical notation editor.
```
sudo apt-get install rosegarden
```
It depends on KDE libraries and will install them if you do not use Kubuntu already.

Mind that for my Creative Labs Audigy4 soundcard I have to load midi voices e.g.
```
sfxload Ultimate.SF2
```
after every reboot to get midi to work. You might have to look for those voice files on the web.

---

### Post by hanzj on 2006-12-12
thanks. i am currently trying noteedit, which is a kde program, too.  It looks like what i need, but I need to fix the midi playback. I can't hear a thing when I press the play button.

---

### Post by goodmanbrown on 2006-12-12
If you don't have a midi soundcard, use timidity running in server mode as the destination for noteedit's midi data.  From the command line:

```
timidity -iA -B2,8 -Os1l -s 44100 &
```

Then start noteedit and select one of the timidity ports as your midi device.

---

### Post by hanzj on 2006-12-12
Goodmanbrown,
I ran that command you gave (timidity -iA -B2,8 -Os1l -s 44100 &) and I see 4 other timidity choices in the Settings dialog (for a total of 8). I have tried many of the 8. Some are completely silent. While others sound good in some parts of the compositiion, while bad in others.
Is it because my computer is too old/slow for noteedit?

When I play a song in noteedit, my systems resources applet shows 100% usage.

---

