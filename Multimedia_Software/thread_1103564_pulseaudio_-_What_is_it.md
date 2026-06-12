---
title: "pulseaudio - What is it?"
date: 2009-03-22
forum: Multimedia Software
---

### Post by Dirjel on 2009-03-22
Sometimes, while I'm listening to music on Rhythmbox, or watching a video on Youtube, my sound stops working.  I looked checked my running processes, and I saw pulseaudio on top.  It sounded like something that would be needed for sound, so I killed it and started it up again.  My sound started working again.  Lovely.

Today, though, rhythmbox locked up again, and I had no sound from anything else.  I killed the pulseaudio daemon, but before I could start it up again, rhythmbox started working, and I can hear the audio on Youtube and Totem and such.

So... what exactly does pulseaudio do, besides using up extra CPU and memory, and causing my audio to stop working at random intervals?

---

### Post by PrinceArithon on 2009-03-22
It gives you a headache and makes you want to kill someone.

Ok seriously it seems that pulse audio kinda takes control of the sound driver and helps organize how things use the sound driver...but I will admit, I'm not entirely sure if I'm correct.  All I know is that it causes me problems too.

---

### Post by Dirjel on 2009-03-23
So if I never use it again (automatically killall pulseaudio on logon), it won't break anything?

---

### Post by 3rdalbum on 2009-03-23
Back in the "bad old days" (like, a year ago) programs would be written to output sound through the ALSA system, or through the OSS system, or through ESD sound server. Unfortunately, if a program was outputting sound through OSS, it would block programs that used ALSA or ESD. This was a real problem if you wanted to use old software or badly-written proprietary software (like Flash 7 or earlier Skype).

Pulseaudio unifies the sound situation on Linux. Actually, it even unifies the sound situation on Unix. Programs that are written to use Pulseaudio will not be able to lock other software from outputting sound. Programs that aren't written for Pulseaudio will automatically be redirected through Pulseaudio.

Pulseaudio also gives you extra features, such as being able to control the volume of each program. For instance, when I'm playing Blu-ray movies, the volume is very low - I need to turn the speakers up. If I'm also on an instant messenger at the same time, then the IM sound notifications are incredibly loud by comparison. With Pulseaudio, I can turn the IM program's sound down.

There are other special features planned for Pulse, such as sounds from programs coming out of a particular speaker depending on what virtual desktop they are located on.

At the moment, Pulseaudio is kinda in its infancy. Killing it probably won't outright break anything as it hasn't been properly integrated into the Ubuntu desktop yet (that's why you're having trouble with it). But without Pulseaudio you'll probably return somewhat back to the old days of OSS programs stopping any other programs from outputting sound.

NOTE: Do not remove any Pulseaudio packages from your system as it may break Gnome! Kill it if you want to, but don't delete it.

---

### Post by darthmob on 2009-03-23
> **3rdalbum said:**
> Pulseaudio also gives you extra features, such as being able to control the volume of each program. For instance, when I'm playing Blu-ray movies, the volume is very low - I need to turn the speakers up. If I'm also on an instant messenger at the same time, then the IM sound notifications are incredibly loud by comparison. With Pulseaudio, I can turn the IM program's sound down.now that's a nifty feature! how exactly can you do that?

---

### Post by PrinceArithon on 2009-03-23
> **Dirjel said:**
> So if I never use it again (automatically killall pulseaudio on logon), it won't break anything?

If you kill it during the logon you won't have any sound for anything.

Here has been my solution for fixing pulseaudio...when it dies off and messes up go into the terminal and type:

killall -9 pulseaudio

Make sure after you typed that in that you turn off your media players and shut down your browser.

Then press:

"alt + F2"

Then type in the box:

pulseaudio

After that your system should work fine again...it's a temp fix but it seems to be working for others who have this problem as well.

---

### Post by Dirjel on 2009-03-23
Pulseaudio isn't running right now, and I still have sound for everything.

---

