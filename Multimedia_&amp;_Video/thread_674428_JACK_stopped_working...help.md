---
title: "JACK stopped working...help?"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by avismavis on 2008-01-21
when i run 'jackd -d alsa'
jack reports:

```
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

```

it used to work perfectly with my onboard soundcard.
then i tried to get it to work with my USB interface 
(that was a nightmare and it never worked)
i don't know how to get back to my original settings.... 

furthermore i don't remember what terrible new things 
i taught my computer when trying to get it to acquire my USB interface.

does anyone have any advice? i wish i could just reinstall alsa or something...?

thanks, anthony

---

### Post by ÜbR on 2008-01-22
I've same problem. Something is using hw:0.0. 

I don't know how to fix it, but if I run Jack from terminal by giving command "jackd -d alsa -d hw:0" Jack works fine.

Try if this works for you. Some one should give us help to find process causing this fault.

---

### Post by avismavis on 2008-01-22
> **ÜbR said:**
> run Jack from terminal by giving command "jackd -d alsa -d hw:0"

JACK has the same error:
```
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

```

---

### Post by NW2190 on 2008-01-22
Ya, I have this problem too.  Running JACK from the terminal still results in the same message for me.

---

### Post by ÜbR on 2008-01-23
In my case that command worked.. Problem is that  hw:0.0 is in use. As I say before, you need to know which application or service is using hw:0.0. I my case I've no idea..

Try connect USB -interface after computer is totally booted up. Maybe then that service won't use hw:0.0.

> **avismavis said:**
> JACK has the same error:
```
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

```

---

### Post by NW2190 on 2008-01-23
Ok, I shutdown my computer last night and this morning JACK started working again.  I don't understand it at all considering I had already tried rebooting a dozen times with no success.  Now I'm having trouble using the playback feature of TuxGuitar though.  I just got it working by installing Java and I think that might have something to do with it (not sure though).  My Ardour Recording doesn't work either, although it moves the cursor as if it were recording, it just records silence.

---

