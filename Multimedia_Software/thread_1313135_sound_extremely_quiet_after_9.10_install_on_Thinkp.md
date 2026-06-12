---
title: "sound extremely quiet after 9.10 install on Thinkpad T42"
date: 2009-11-03
forum: Multimedia Software
---

### Post by migo2011 on 2009-11-03
Hello,

I just did a fresh install of a 9.10 on a Thinkapd T42.
Everything works find unless the sound.
It is extremely quiet even if everything (main mixer and application) is turned up to maximum. Then in addition the sound is very bad!
 cat /proc/asound/cards shows

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 11

What can I do? Help is very appreciated.

thanks a lot,
migo

---

### Post by rockdj on 2009-11-05
Unsure if it'll be the same trouble I had on my Dell Optiplex 755 with 9.10, but it worked for me.

I had to open the redesigned Sound Preferences, go to the Hardware tab, and select the right 'Profile' for my hardware device.  In my case I've got a Plantronics headset (shows up as USB DSPv4 Audio Interface) and it was set to be "Digital Stereo Duplex".  With that setting, the audio would be very quiet at maximum.  Changing this around to "Analog Stereo Duplex" makes the max volume very, very loud now.  So much so that I can only use the headset on 25% before it gets painful.

I suppose it'll depend on many things, but switching that profile solved the problem.

Cheers

---

