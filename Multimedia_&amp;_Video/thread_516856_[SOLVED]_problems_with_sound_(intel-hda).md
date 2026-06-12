---
title: "[SOLVED] problems with sound (intel-hda)"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by leo_rockway on 2007-08-03
Hello fellow (x)(k)ubuntuers. I have a problem that I've been trying to solve for weeks now and I really can't find a solution anywhere. Let's see if somebody here can figure out how to get things working.

This is my soundcard according to lspci:

> Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

According to Gnome ALSA Mixer it is a SigmaTel STAC9200. (BTW, I'm not using Gnome, I'm a KDE guy, I only installed the Gnome ALSA Mixer to see if I could solve my problem through that).

I DO get sound and it works without a problem in KDE, but there are certain applications that hint me that not everything is right.

When I run the game Glest or the game Regnum Online, the sound comes out all choppy. The same happens for Tremulous and Open Arena, but not for World of Padman.

I also tried using Audacity and when I try playing a file I can see the green bars moving like I'm getting sound but no sound comes out. The funny thing is that if I run Audacity for windoze with WINE, it works perfectly.

If anybody can give me a hint on how to work around the problem I will be very greatful.

EDIT:
i dont have any more choppy sound... i added
> (define devices '(alsa sdl))


to my ~/.openalrc

I still can't use audacity, and I still can't record sound w/ istambul (i didnt mention that before, but i get an error when i try to record sound... haven't tried recording in audacity yet, i have to get me a mic...)

---

### Post by leo_rockway on 2007-08-09
since my initial problem (choppy sound) is solved, i'll just mark this as solved and post a new thread for my audacity problem.

---

### Post by chriswyatt on 2007-08-15
I don't have a .openalrc but it sounds like you probably have the same problem as me.

---

### Post by dabl on 2007-08-15
I have the same Intel HDA system and STAC chip.

For playback, Audacity is very "picky" -- it requires "original and exclusive" access to the sound system to play at all.  So, you need to shut down Firefox and Amarok and anything else that is remotely likely to access the sound system, and wait a few seconds before starting Audacity.  THEN Audacity will play.

I haven't noticed that the recording side of Audacity has this issue -- I seem to be able to record at will. :)

---

### Post by leo_rockway on 2007-08-16
> **chriswyatt said:**
> I don't have a .openalrc but it sounds like you probably have the same problem as me.

i didn't have it either, i created it myself.

i added the following line:

> (define devices '(alsa sdl esd))

i hope that works for you.

---

### Post by leo_rockway on 2007-08-21
hey chrisswyatt, did you solve your problem? i realized there was something more making the sound all choppy...

this is my /etc/asound.conf file:

> pcm.card0 { type hw card 0
}
pcm.!default { type plug slave.pcm "dmixer"
}
pcm.dmixer { type dmix ipc_key 1025 slave { pcm "hw:0,0" period_time 0 period_size 1024 buffer_size 4096 rate 44100
}
bindings { 0 0 1 1
}
}

i realize that playing around w/ some numbers made majors changes. lowering the rate from 48000 to 44100 stopped the sound from being choppy. changing the buffer size allowed me to play and record at the same time when using audacity. (YES, I CAN RECORD NOW, I'M EVEN USING SKYPE! idk if it was because i upgraded to gutsy or because i changed the files... i think it was both but can't be sure)

---

### Post by SanskritFritz on 2008-01-15
I have 
Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

and your solution was a great help, thank you, now I can enjoy Glest with smooth sound!

---

### Post by leo_rockway on 2008-01-15
I'm glad you found my solution helpful. Glest rocks!

---

### Post by SanskritFritz on 2008-01-16
Yeah, we play Glest a lot with my son :-)
Can you please explain why this solution works? What does it do? I'm a newbie as far sound in linux goes. Thanks.

---

### Post by leo_rockway on 2008-01-31
I believe increasing the buffer is a way to tell Ubuntu that more audio information can be cached. I don't understand why a lower number works better, tho...
I'm not really sure myself why this worked :-P

---

### Post by Brerlapn on 2008-02-03
Leo,

Could you give more detail about the changes you made to your sound file?  I would like to try that, but I wasn't clear what your values were for your buffer.  What was the number before you changed it, and what did you change it to?  I'll check in my file to see if it's obvious what you did, but I would prefer to follow your lead since your solution makes sense.

Thanks!

---

