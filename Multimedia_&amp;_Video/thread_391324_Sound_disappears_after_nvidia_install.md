---
title: "Sound disappears after nvidia install"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by Dylock on 2007-03-23
Howdy

Well I just got through a rocky nvidia driver install, the first install crashed X so I had to uninstall anything nvidia and reinstall the driver, the xorg.conf file got changed a few times but I used a backup to get it back to the way it was I think.  Anyway long story short sound is no longer working in any way shape or form.  It worked as of 2 hours ago but I can't for the life of me figure this out.  

Here is the results of lspci -l
02:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
        Subsystem: Creative Labs Unknown device 1003
        Flags: bus master, medium devsel, latency 64, IRQ 225
        I/O ports at df20 [size=32]
        Capabilities: <access denied>

I have been using alsa and reinstalled all those packages to make sure nothing got messed with but Im stuck :(

Any suggestions would be great.

Dylock

---

### Post by Dylock on 2007-03-23
bumpage, does anyone know how editing xorg.conf or nvidia could have any effect on alsa?

---

### Post by Dylock on 2007-03-23
Current progress: 
I have been reading through this [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+alsa](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+alsa)
I have made it to step 4 of the 'no idea why sound is playing' section and did the modprobe part. Here is the command I ran: sudo modprobe snd-emu10k1x
There was no apparent error and proceded to try sound but with no success.

Now I'm going to go onto purging all sound packages and reinstalling.
Hopefully this will work :(

~d

---

### Post by frequenicity on 2007-03-23
Had the same problem. Disable your onboard sound in your BIOS. Should take care of it...

---

### Post by Dylock on 2007-03-23
hmm ill look into that but I don't see how my onboard sound was affected by a driver update

---

### Post by Dylock on 2007-03-23
i went  into bio and under integrated devides(legacyselect) the audio was already turned off so I don't think that was the problem.

After alsa was removed and reinstalled there is still no sound

EDIT: something else I also checked was to make sure my user had audio 
dylock@dybox:~$ grep 'audio' /etc/group
audio:x:29:dylock
So I know that isn't the problem

---

### Post by Dylock on 2007-03-23
problem fixed!

well this is rather silly but i thought ill try changing the volume of the sound with mpc+mpd and magically i had sound again.

So apparently mpd can remove sound completely from your system if the volume is different.

So to anyone that is having sound problems and uses mpd try turning up the volume via mpd

Im still puzzled as to how the volume of mpd was effected, and why the volume of mpd effected the sound on movies.

oh well cheers
~d

---

