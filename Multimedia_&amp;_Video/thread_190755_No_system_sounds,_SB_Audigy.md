---
title: "No system sounds, SB Audigy"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by XomboX on 2006-06-06
Hi!
I can listen to mp3, movies trough my MPlayer, but I can hear no system sounds and I can not listen to music trough any audio mplayer (Rhythmbox, amarok, banshee), except MPlayer :-(

I use ALSA mixer, everything on max. I have got a SB Audigy, but when I type in terminal "cat /proc/asound/cards" it says I have a SB Audigy2.
There are no linux drivers for SB audigy at creative`s servers.

Have you got an idea where is the dog digged?

---

### Post by lime4x4 on 2006-06-06
I did a fresh install of ubuntu and my sound card was detected correctly (audigy 2 ZS)

john@ubuntu:~$ cat /proc/asound/cards
0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                     Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xa000, irq 209

Not sure why yours wasn't detected properly.. But ubuntu does support it

---

### Post by gullf1sk on 2006-06-06
I got problems with my Audigy aswell. Funny thing is, i had sound on previous boot, but now its gone again :P

---

### Post by XomboX on 2006-06-07
But it was playing nicely since I have installed XMMS and tried to implent different system sounds. I unistalled XMMS, reinstalled ALSA-base and the problem still keep me angry.

When I play a song in rhythmbox, banshee, sound juicer, amarok. It behaves like it is really playing it but I can hear nothing. It is the same as I am trying to play system sounds (the original one).

I wonder you know where I should start to look for the problem. :confused: 
I attached a screenshot.

Thank you for help!

[IMG]http://xombox.mysteria.cz/Obrazovka.png[/IMG]

---

### Post by matc on 2006-06-07
Same/similar problem here with AC97 Sound on Nforce2-Board. Kernel modules seem to be loaded, but nothing can attach to the device (kmix fails - arts seems to send sounds to null device)

cat /proc/asound/cards results in:
--- no soundcards ---

This worked before upgrading to dapper ..... really starting to look forward to upgrade five other systems each with different hardware....

Update: Works here after multiple issues AND installing a new Kernel 2.6.15-23-k7. MAybe it helps with Audigy cards too ?

---

### Post by j0eb0b on 2006-06-07
Similar problems for me.  Everything worked for a while after I upgraded to Dapper and ran Automatix and then just quit last night.  XMMS and other programs appear to be playing the stream but there is no sound output, either system sounds or music.  I too am using the onboard sound chip on an Nvidia N-force 2 MB.  Everything worked well for months using Breezy. Not sure where to begin to troubleshoot either.

---

