---
title: "MP3 Compressing Strangely"
date: 2011-02-20
forum: Multimedia Software
---

### Post by Gannin on 2011-02-20
I have an audio clip that's acting very strangely when it's compressed as an mp3.  When I compress it as an ogg, it sounds just fine.  Even when I compress it as ogg using the lowest quality setting, it still sounds fine.  However, when I compress it as 128Kbps mp3, it has strange warbling, cracking, and popping sounds.

Here's the clip as an ogg, which sounds the way it should:

[http://www.filedropper.com/soundtest](http://www.filedropper.com/soundtest)

And here's the clip as an mp3, which has the strange audio artifacts:

[http://www.filedropper.com/soundtest_1](http://www.filedropper.com/soundtest_1)

I'm using the lame library to create the mp3.  Any ideas?

---

### Post by PaulReaver on 2011-02-20
is this constant bit rate?

could try variable bit rate.... maybe?

---

### Post by Gannin on 2011-02-20
It is constant bit rate, but unfortunately I need to use constant bit rate.

I should add I've also tried EQing it too, hacking off the low end, hacking off the high end, and it's still the same result.

---

### Post by PaulReaver on 2011-02-20
i know your using the lame library but what app are you using to encode this?....

could try scale your cpu to performance when encoding.... I had crackling when my cpu was on ondemand and my cpu usage was quite high (was doing other things in the background)


other than this I've not a clue...

---

### Post by Gannin on 2011-02-20
I'm using Audacity without anything else going on in the background.

I also dropped the original .wav file into an OpenShot project and made a video clip using lame for the library to test it that way, and I had the same results.  The video also had the warbly, cracky, popppy sounds.

---

### Post by PaulReaver on 2011-02-20
I don't know what to suggest if its system wide... happens on openshot too... :(

maybe a slow hard disk??? on IDE

---

### Post by Gannin on 2011-02-20
It's not that either.  My system is modern and up-to-date, and it doesn't happen on every mp3 I create.  Just for the heck of it, I tried setting the CPU to performance and it didn't make a difference.

If you or anyone else wants to have a crack at it, here's the original .wav file:

[http://www.filedropper.com/soundtestuncompressed](http://www.filedropper.com/soundtestuncompressed)

I also just tried turning the file into an mp3 on a Windows machine using both Audacity 1.2 and 1.3 and received the same results each time.

Okay I just found some bizare behavior that maybe is a lame bug?  I took the .wav file and ran lame on it from the command line, still got the audio artifacts.  I tried the -h for high quality, still got the artifacts.  I tried the -f option for fast, and the artifacts went away.

---

