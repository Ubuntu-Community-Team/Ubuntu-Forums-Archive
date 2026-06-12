---
title: "Strange sound Intel ICH7 HDA, Conexant 20551"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by fearpi on 2008-01-02
Since I upgraded to Gutsy, sound control has worked very strangely, and quality has been plainly bad - I get a distracting hiss out of my speakers (or headphones, if they are plugged in), the volume of which is a direct function of my PCM volume. Fine, you say, turn down the PCM to 80%, and control your volume with the master. Well, master volume changes nothing. I can have the master at 0%, 50%, or 100%, and the sound is the same volume. PCM is the only way I have to control my sound, and besides that, the hiss is evident unless PCM is muted or all the way down. Sound works otherwise; I can watch movies, play games, listen to music, etc. But this hiss is very distracting, and I have no problems under Windows.

I have attempted all kinds of combinations with the line
options snd-hda-intel model=x position_fix=y
in /etc/modprobe.d/alsa-base.

lspci -v tells me:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

The heading at the top of alsamixer:
Card: HDA Intel
Chip: Conexant CX20551 (Waikiki)

If anyone can help out, that would be great. I have been trying to fix this on my own since Gutsy came out, crawling google, ubuntu's forums, archived alsa mailing lists, etc. I've read that Gutsy has been a step backwards for many others as well, notably HP and Compaq laptop owners (I have an HP dv5000) and I am quite frustrated with my sound problem at this point. Any help is welcome.

---

### Post by HeWhoE on 2008-01-15
I've been irked by this problem too.

$ lspci -v
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0


---

### Post by m4dm4n on 2008-04-08
I have exactly the same sound device which I just managed to fix the no-sound problem on when I discovered this hideous hissing behind everything. This may sound dumb but I fixed it by muting the "CD" volume. It seems like the hissing was a result of something to do with the CD drive. I have an Asus F3SR and I'm using ALSA 1.0.15. Hope that helps anyone else with that problem.

---

### Post by fearpi on 2008-04-10
I'd try it. Unforunately, I don't have a CD slider.

---

