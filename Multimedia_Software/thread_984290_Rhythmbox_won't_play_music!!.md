---
title: "Rhythmbox won't play music!!"
date: 2008-11-16
forum: Multimedia Software
---

### Post by bunny_basher on 2008-11-16
Hi,
   When I open Rhythmbox and try to play a song it just says theres an error and goes to the next song. It won't play any songs in my library so it just keeps doing this continuously.

Any Ideas?

Cheers,
Marcus

---

### Post by Keyper7 on 2008-11-16
Ok, first thing to check is if you have the proper codecs installed. Are your songs in mp3 format? Do you have gstreamer0.10-plugins-ugly package installed?

PS: It might take an entire day for me to check your reply to this, but I will.

---

### Post by Therion on 2008-11-16
Open Synaptic.  Search for and install the **ubuntu-restricted-extras** package.

---

### Post by kdardio2415 on 2008-11-17
I'm having the same problem.  I don't think it's codecs, as neither ogg nor mp3 will play.  Music files are also not working in vlc or movie player.

addendum:  checking the properties of the music files shows an error claiming that "could not open audio device for playback.  Device is being used by another application"

---

### Post by ItalOz on 2008-11-17
I can play mp3s with audacious but if I try to play the same ones with Rhythmbox I get a stop signal in front of the file in the play list and does not play.

Funny enough I can even see the cover of the album embedded in the file, so in some way the mp3 file is loaded but not played

---

### Post by Yownanymous on 2008-11-17
Just out of interest, why are the codecs restricted anyway?

I bet it's to do with Micro$oft.

---

### Post by kdardio2415 on 2008-11-17
You seem to have inadvertently placed a dollar sign in the Microsoft.  That's not how you spell Microsoft.

And to an extent, yes, it's partially due to MS and Mac having a stranglehold on the software industry.  There are a lot of legal issues around the restricted software we use in day to day life, and there are no doubt countless sources that can explain it better than me.

---

### Post by rakris on 2008-11-17
Gstreamer and Gstreamer-plugin not installled!!!

---

### Post by Keyper7 on 2008-11-17
So, can the people having problems in this thread say if the previous suggestions helped?

> **Yownanymous said:**
> Just out of interest, why are the codecs restricted anyway?

I bet it's to do with Micro$oft.

Patent issues. But Microsoft is *not* the patent holder in this case.

It also has to do with the fact that Ubuntu tries to ship as much free software as possible. In this case, it prefers the completely free OGG format by default.

> **rakris said:**
> Gstreamer and Gstreamer-plugin not installled!!!

Is this an error message you are seeing or a guess on what the OP's problem is? Please be more clear.

---

### Post by Keyper7 on 2008-11-18
Any progress on this? If one of the previous suggestions worked, it'd be nice if the OP pointed it out and marked this thread as solved.

---

### Post by psyke83 on 2008-11-18
> **bunny_basher said:**
> Hi,
   When I open Rhythmbox and try to play a song it just says theres an error and goes to the next song. It won't play any songs in my library so it just keeps doing this continuously.

Any Ideas?

Cheers,
Marcus

Note: I'm assuming you're using Hardy or Intrepid.

PulseAudio is probably not configured correctly on your system.

First, ensure your PCM mixer is not set to 0% or muted:
```
$ alsamixer -Dhw
```

Secondly, follow the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

If you still have issues, perform the troubleshooting procedure in Appendix A of the guide.

---

