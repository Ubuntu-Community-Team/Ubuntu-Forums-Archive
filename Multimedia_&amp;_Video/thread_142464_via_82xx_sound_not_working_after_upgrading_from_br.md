---
title: "via 82xx sound not working after upgrading from breezy to dapper"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by blatchstev on 2006-03-10
So yesterday I upgraded from Breezy to Dapper (running KDE, if it matters). Sound stopped working. Applications still show as if they're playing, no error messages anywhere, but no sound. Alsamixer (and kmix) are not muted. Permissions on /dev/dsp are rw-rw----.

I can "solve" the problem by doing this:
modprobe -r snd-via82xx
modprobe snd-via82xx
and then restart KDE's sound system, however, on a reboot it's messed again. I think I know enough to write a script to do that, but I'd really prefer a more elegant solution. Does anyone know what might be the problem?

---

### Post by blatchstev on 2006-03-10
Okay, apparently I spoke too soon. Repeating that, and adding in
chmod a+rw /dev/dsp
(as I might have done that before too) doesn't seem to help. Great, now I don't even know how I made it work. :(

---

### Post by recrem on 2007-07-09
I have an AMD Athlon 3200+ with VIA8235 sound chipset and I have been struggling to find a solution to my no audio problem.  I followed all forum tips I could find even though the correct drivers (via82xx) were loaded.

I ended up making the VIA 8235 Alsa Mixer show every option / control and switch.  I then went through every control while playing a CD until I was blasted with full volume...  The culprit was the Line Jack Sense switch!  It was checked initially but when I unchecked it my speakers burst into life...

I was running Dapper with no luck and decided to try Feisty one more time before working this out.

Hope this is helpful to others pulling their hair out also!

---

### Post by Sef on 2007-07-09
Read [this thread]("http://ubuntuforums.org/showthread.php?t=160576&highlight=sound"); it's how how I got sound with the same video card.

---

