---
title: "Increase Sampling Rate"
date: 2011-05-13
forum: Multimedia Software
---

### Post by sosovirus on 2011-05-13
Hi All,:D
I'm Very New In Ubuntu,:KS
1st
I Use Ubuntu 10.10 & Sound Card creative sound blaster live 5.1 & Internal Sound Card
The main problem that i'm using GNU Radio 3.2.2 In my master and i use the sound card as acquisition card (ADC & DAC) but the main Problem that in GNU Radio the maximum sampling rate for the audio source is 48KHZ. Why??:confused:
I Used my creative sound blaster live 5.1 many times as acquisition card in windows under 192KHZ (Using Matlab):P
But now i only can use it to 48KHZ only:(
(i tried many methods to change it but i can't get any one working (one of them is JACK Control))

2nd
I Installed Matlab 2010b for UNIX
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
i can't Run it in application menu /programing /matlab 2010B
(Failed to execute child process "matlab" (No such file or directory))

So Please Help Me in This,
But Please With Full Detailed Cause I'm Very New To Ubuntu Usage:confused:
Thanks In Advance
Islam Galal

---

### Post by k0d3g3ar on 2012-04-06
Are you sure you are not confusing Sample Rate with Bit Rate?  48khz sample rate is above CD Audio quality (44.1khz) which is what I use for all of my audio since its compatible with the widest player standards...

---

### Post by mocha on 2012-04-06
Inside /etc/pulse/daemon.conf is where you set the sample rate for pulseaudio.  It defaults to 48 kHz if you don't specify a value.

---

### Post by k0d3g3ar on 2012-04-06
I think that value is overridden by any value in the .pulse folder in the user's home directory though.  It probably needs to be set in both places.

---

