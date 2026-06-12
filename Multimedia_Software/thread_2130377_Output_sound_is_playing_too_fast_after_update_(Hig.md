---
title: "Output sound is playing too fast after update (High-pitched)"
date: 2013-03-29
forum: Multimedia Software
---

### Post by orahende on 2013-03-29
So the strangest thing happened after installing the recent update (on 2.2MB) the other day. Now all the output audio is playing too fast and distorting the original sound. I tried to re-install **Lubuntu **and also got the pavucontrol to be able to stream sound through the coaxial-output (SPDIF) to my audio system, but again, the output audio is faster than the original!

What can the error be?

---

### Post by orahende on 2013-03-29
So I timed a youtube-clip with my wrist watch, 30 sec on my watch timed in at 34 sec on the youtube-clip

---

### Post by prbassplayer on 2013-05-04
Happening on my end as well. Core 2 duo 6Gb ram Nvidia GTX260M. Any help?

---

### Post by RedFox102 on 2013-05-22
Same problem here. Just started happening yesterday, seems to happen only when streaming html5 and flash video, I don't have any problems outside the web browser. I'm on ubuntu 13.04, and have been for almost a month, I have no idea what suddenly triggered this. If anyone has any ideas, let us know, meanwhile i'll see if I can figured out what's changed on my end in the last 24 hours, but off the top of my head the only thing I think I did was update chrome to the latest beta.

Edit: Rolled back to the previous version of chrome beta, and also tried stable, but the problem persists. Any ideas?

---

### Post by Koala Kid on 2013-05-26
Same here. my guess would be PulseAudio

---

### Post by Koala Kid on 2013-05-26
This worked for me
[http://askubuntu.com/questions/141692/youtube-movies-are-playing-too-fast-with-chrome](http://askubuntu.com/questions/141692/youtube-movies-are-playing-too-fast-with-chrome)

---

### Post by odxa20 on 2013-05-29
Thanx so much you saved me !!!

---

### Post by theirishfrog.sh on 2013-06-02
Unfortunately, this did nothing for me. :-(

Any other tips? This wasn't a problem on any incarnation of Ubuntu before 13.04 or on Linux Mint 14.

---

### Post by nemodot on 2013-06-09
Didn't work for me but I solved it by killing and restarting PulseAudio. It just got an update and it's not well polished yet.

killall pulseaudio
pulseaudio

If the problem persist you could replace pulseaudio for the alsa module.

---

### Post by Baldrick_NZ on 2013-06-10
I had the same prob with watching video clips in Chrome too. Then I changed (using Ubuntu Tweak) to Chrome-beta, no problems since. Mint!

---

