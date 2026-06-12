---
title: "No sound in a downloaded game"
date: 2010-11-29
forum: Multimedia Software
---

### Post by DCU Coey on 2010-11-29
Hi, i have downloaded a game called YSFlight but there is no sound on it. I previously played this game on Windows so i know it does have sound. 

i **HAVE** installed "YSFlight for Linux" so i know that isn't the problem, and i have also checked all of the sound settings. Every other 'sound' that is with Ubuntu Linux works fine (music, video, error/notifications).

I am using Ubuntu Linux 10.10 with a Dell Inspiron 1525 which previously had Windows Vista Basic 32 bit. I have never had a sound problem with this laptop.

Does anyone have any ideas of what is wrong? please help


** * I am currently running Ubuntu Linux via a disk (the "Try It" option), to test programs that i like, and this is where i found the problem ***

---

### Post by DCU Coey on 2010-12-01
Please Help!!!! The longer i have no solution, the longer i can't be a Linux user!!!!

---

### Post by lykeion on 2010-12-01
> **DCU Coey said:**
> Please Help!!!! The longer i have no solution, the longer i can't be a Linux user!!!!
Do you only use Linux to play a flight simulator game?

First a tip:
There are some flight simulators available for which all look better than ysflight in my eyes: FlightGear, gl117, SABRE
Just launch Ubuntu Software Center to find them and install.

Back to your problem:
I tested to download and run ysflight and I had no problem with no sound. You might try to run it through PulseAudio OSS wrapper:
1) install pulseaudio-utils
2) run the game through the wrapper:
```
padsp ./ysflight
```

EDIT
Just saw that you are "running Ubuntu Linux via a disk (the "Try It" option)".
If you mean you are running Ubuntu from LiveCD and haven't installed it yet, your sound problem will probably vanish when you do install it properly.

---

### Post by DCU Coey on 2010-12-01
No... not just for the flight simulator!

i'll be installing Ubuntu Linux sometime in the near future as i have a large file that i need to put onto another disk first!! and then i'll see if the problem has gone. If it hasn't i'll install PulseAudio!!

thanks for the help!

---

### Post by DCU Coey on 2010-12-12
I fully installed Ubuntu Linux, but the problem was still there! Anyway, i installed YSFlight for windows and ran it through Wine, and the sound works great! 

How crazy!

---

### Post by stlu on 2012-01-02
> **lykeion said:**
> 
...

I tested to download and run ysflight and I had no problem with no sound. You might try to run it through PulseAudio OSS wrapper:
1) install pulseaudio-utils
2) run the game through the wrapper:
```
padsp ./ysflight
```
...


I'd like to mention that the above solution works.  I am running ubuntu 11.10, and had no sound when I ran the game.  I have no problems with Firefox+youtube, Banshee music player etc.

P.S. (to above poster) IMHO it is not the quality of the gameplay, but the uniqueness of the online community which led me to stick with YSFlight.

---

