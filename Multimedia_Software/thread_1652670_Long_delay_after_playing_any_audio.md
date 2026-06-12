---
title: "Long delay after playing any audio"
date: 2010-12-25
forum: Multimedia Software
---

### Post by plaa on 2010-12-25
Hi,

I'm having a problem where almost every audio player creates a 2-3 second delay after playing any audio.

I'm working on some text-to-speech using espeak and festival.  Festival would provide much better speech quality, but it created a 2-3 second delay after any speech before the application exited, which prevents using it.  When I started investigating the issue, it turned out that many other programs display the same behavior.

For example, if I play a 1-second WAV of silence using "play", it displays "Done" very soon and then waits for 2-3 seconds before exiting.  mplayer does the same.  mpg123 does the same.  mpg321 does the same.  ogg123 does the same.

When playing multiple files mpg123 and ogg123 do not generate the pause between the files, but mplayer does.  I'm wondering can there be a bug that causes programs to hang when closing the audio device?

That's so many programs it must be some kind of problem in the system, not the individual programs.  However not every program displays this behavior; espeak exits immediately after the speech has ended.  (Might it for instance exit without closing the audio device properly?)

I haven't noticed anything similar before I upgraded to 10.10.  I'm running XUbuntu on a Thinkpad T60.  The laptop has an Intel HD Audio with AD1981HD codec ([http://www.thinkwiki.org/wiki/AD1981HD](http://www.thinkwiki.org/wiki/AD1981HD)).

Any ideas on how to fix/debug the issue?

Regards,
    Sampo N.

---

### Post by plaa on 2011-01-03
Hi,

Any ideas on how to go about figuring out what's wrong?

Regards,
    Sampo N.

---

### Post by Yellow Pasque on 2011-01-03
Does the same thing happen with aplay?

---

### Post by plaa on 2011-01-04
> **Temüjin said:**
> Does the same thing happen with aplay?

Yes.  The following is from playing a one-second sample.  It first plays for one second and then waits for about two seconds:

> 
$ time aplay sample-1s.wav 
Playing WAVE 'sample-1s.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono

real	0m3.303s
user	0m0.008s
sys	0m0.012s


Espeak is actually the only program thus far that I've found that isn't affected by the problem.

Regards,
   Sampo N.

---

### Post by ajgallego on 2011-11-30
Hello,
 Have you solved this problem?
 I also had this problem using "aplay" and the only solution that I found is running the command in background, and then make a  time delay before playing the next sound. 
Let me explain: My program is written in C++, and I do something like this:

 system ("aplay out1.wav &");
delay( seconds );
system ("aplay out2.wav &");

The delay has the exact duration of the first sound.

---

