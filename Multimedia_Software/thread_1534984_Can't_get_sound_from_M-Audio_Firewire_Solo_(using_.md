---
title: "Can't get sound from M-Audio Firewire Solo (using FFADO and JACK)"
date: 2010-07-20
forum: Multimedia Software
---

### Post by BioBiro on 2010-07-20
Hey all,

I'm a complete Linux newbie - only installed it yesterday, and have spent hours trying to get my M-Audio Firewire Solo sound card to work. I can hear nothing at all. I know nothing of Linux, but am willing to learn. While I learn though, it would be nice to listen to a little Hall & Oates. 

I've got to the stage where the error messages I'm receiving don't bring up any results on Google. Here's what things look like (watch out, big pic):

[http://hirsty.net/temp/maudiodesktop.png](http://hirsty.net/temp/maudiodesktop.png)

Those sample rate errors appear in the terminal when I start ffado-mixer. I'm running JACK with everything set as I think it's supposed to be, except that 'Realtime' is unchecked.

If I start JACK running *with *'Realtime' checked, it tries to launch and fails, saying "JACK is running in realtime mode, but you are not allowed to use realtime scheduling. After applying these changes, please re-login in order for them to take effect". I don't know what more it wants me to do - i've already added 

@audio – rtprio 100
@audio - nice -10
@audio – memlock unlimited

to */etc/security/[I]limits*.*conf*, [/I]and selected the 2.6.31-11-rt kernel on GRUB bootup. I'm a member of 'audio' and 'disk' groups like I'm supposed to be. Have I not got the connections right in JACK? Have I got some sample rate settings wrong somewhere?

I'm not even bothered about low latency with the realtime kernel right now, I just want to hear some sound! Anybody got any suggestions? Again, I apologise for any mistakes caused by my inexperience.

---

### Post by BioBiro on 2010-07-20
Sorry everyone, i've had put Windows 7 back on this computer for work. I didn't know i'd have to do this straight away, otherwise I wouldn't have wasted your time since I only posted my original problem 7 hours ago.

Ubuntu feels nice and has some great features I could easily get used to. Unfortunately it seems the Firewire-sound department needs a bit of work (many others on the forum going back to 2008 have reported similar problems and some have given up). I considered purchasing a reported-to-work soundcard just for Ubuntu, but that kind of takes away from the 'free OS' thing I guess. I can't wait to try Ubuntu in another year or two to see if it works with all my hardware and I can make it my main OS :).

---

