---
title: "[SOLVED] howto change PulseAudio sampling rate"
date: 2008-11-21
forum: Multimedia Software
---

### Post by jodaka on 2008-11-21
Hello there

I've got Emu 0404 USB device and it gives me distorted sound due to sampling rate incompatibilities. 0404 by default works in 48Khz, but PulseAudio default sampling rate is 44.1

I need to change PulseAudio's default sampling rate from 44.1 to 48

or to change sampling rate for my 0404 USB card which doesn't seems possible to me :(

p.s. I'm on ubuntu 8.10

---

### Post by Yellow Pasque on 2008-11-21
If your sound card receives a 44.1KHz stream, it should automatically resample it to 48KHz if it can't play 44.1KHz natively.

Nevertheless, you can try configuring the default sample rate. See this: [http://linux.die.net/man/5/pulse-daemon.conf](http://linux.die.net/man/5/pulse-daemon.conf)

---

### Post by markbuntu on 2008-11-21
You can change that in 

/etc/pulse/daemon.conf

Just look for the line
```

;default-sample-rate = 44100

```
and change it to look like this:
```

default-sample-rate = 48000
[code]

be sure to edit out the ; 
you will need to restart pulseaudio for that to take effect
To stop pulseaudio:
[code]
killall pulseaudio

```
To restart pulseaudio
```

pulseaudio -D

```

Be sure to let us know if that works for you or not. If it does, please mark this thread as solved using the thread tools above.

---

### Post by jodaka on 2008-11-21
> **Temüjin said:**
> If your sound card receives a 44.1KHz stream, it should automatically resample it to 48KHz if it can't play 44.1KHz natively.

Nevertheless, you can try configuring the default sample rate. See this: [http://linux.die.net/man/5/pulse-daemon.conf](http://linux.die.net/man/5/pulse-daemon.conf)

well, as for card - in linux it doesn't automatically resample anything. No native drivers :(

thanks for the link! Will try this right now

---

### Post by Yellow Pasque on 2008-11-21
> You can change that in /etc/pulse/daemon.conf
The man pages states that PA will look in the user's home dir (~/.pulse) for daemon.conf before resorting to using the system-wide file in /etc. So make sure you write the "default-sample-rate = 48000" to ~/.pulse/daemon.conf as well if that file exists

---

### Post by Yellow Pasque on 2008-11-21
> **jodaka said:**
> well, as for card - in linux it doesn't automatically resample anything. No native drivers :(

thanks for the link! Will try this right now
The last time I checked, EMU chips resampled in hardware. Maybe the USB card is different.

---

### Post by crshman on 2009-11-11
Perfect, thanks a bunch guys!

---

### Post by ipuppyp on 2010-02-23
hi!
this solution works fine with e-mu 0404! 
thanks!
:D

---

### Post by flatko on 2010-12-07
> **markbuntu said:**
> 
be sure to edit out the ; 


All right, I've never paid attention to that fact and always wondered why it ignores my 48kHz and defaults to 44.1kHz. Thank you very much, markbuntu!!

---

