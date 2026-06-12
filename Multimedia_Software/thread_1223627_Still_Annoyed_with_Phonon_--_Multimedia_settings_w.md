---
title: "Still Annoyed with Phonon -- Multimedia settings won't stick"
date: 2009-07-26
forum: Multimedia Software
---

### Post by wd5gnr on 2009-07-26
I've posted about this before, but not really found any good resolution. I've been living with it, but lately I tried again to attack it.

I have multiple sound cards (two PCI and a few USB devices -- ham radio stuff). Using AMD64 Jaunty (2.6.28-13-generic).

I do not have a problem with ALSA -- I can use all my sound devices.

I have installed pulse audio and also used it without pulseaudio. So I know how to set up pulse and I know how to set up most applications (even the flash player).

So here's the problem: Phonon. No amount of coaxing will make it remember the soundcard I want to use. So if I am using pulse audio and set that to the default, it forgets. If I don't use pulse audio and set a particular sound card to the default it forgets. It wants to use a particular card and no amount of setting and applying will fix it. The "Test" button works but it never actually applies. That means things that are totally dependent on it for audio settings (e.g., amarok2) are totally broken. The KDE sound system also is broken (I tell it to use playsound to play system sounds and that works ok).

Remember, Alsa and Pulseaudio are working. That's not the problem.

The configuration seems to be in phonondevicesrc although deleting or manipulating that file seems to have no effect so maybe that's not where it storing it. The problem does not seem to be related to the Xine or Gstreamer backends sine both have the same problem.

So frustrating. It seems "Windowish" that there is a broken GUI which seems to be the only way to configure this! ;-)

Oh yeah, one other minor issue: 64 bit Sun Java doesn't seem to play audio. I had read that setting dmix to pulse might fix that, but no go. I suspect it is merrily streaming audio to my other sound card but I'm too lazy to disconnect it from the radio and hook up a speaker.

---

### Post by wayward4now on 2009-08-12
> **wd5gnr said:**
> I've posted about this before, but not really found any good resolution. I've been living with it, but lately I tried again to attack it.

The configuration seems to be in phonondevicesrc although deleting or manipulating that file seems to have no effect so maybe that's not where it storing it. The problem does not seem to be related to the Xine or Gstreamer backends sine both have the same problem.

So frustrating. It seems "Windowish" that there is a broken GUI which seems to be the only way to configure this! ;-).


I'm surprised that you haven't received a reply yet. I'm having the very same problems. For some reason my games are being directed to my USB headet. Everything else works with my usual system sounds, except games. When I use device choser the launcher just winks for a bit and fails. Why not just stick with alsa and let it be?? This whole problem is just too crazy. Maybe it needs to be started over from scratch??? BAH! Ric

---

### Post by markbuntu on 2009-08-13
The problem may be with udev which assigns sound devices randomly so what was hw:0 can be hw:1 the next time you boot up. Phonon, (and pulseaudio) is not supposed to care about that and use the names of the devices instead of their hw designation. 

But then again if the xine or gstreamer backend is set to the hw device phonon will try to use that.....if pulseaudio starts before phonon and phonon is set to use hw then phonon will not be able to open the device and will fallback to the next device on the list.

There are ways to fix this. You can set xine and gstreamer to use pulseaudio and then set phonon to use pulseaudio and start pulseaudio  That has worked for me. 

If you don't save your desktop then changes will all be forgotten next time you reboot. That happens.

I have written about using phonon and pulseaudio in KDE4 here

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by wd5gnr on 2009-08-19
I think I found it!

Some how ~/.config/kde.org/libphonon.conf was owned by root! Fixing that seems to have corrected the problem. At least so far.

---

### Post by wayward4now on 2009-09-20
> **wd5gnr said:**
> I think I found it!

Some how ~/.config/kde.org/libphonon.conf was owned by root! Fixing that seems to have corrected the problem. At least so far.

I was as happy as a chicken on cracked corn with alsa and the little gui that allowed one to switch to whatever sound device you wanted on the fly. It just plain worked.   

Sorry, I've tried pulseaudio with and without phonon and fail to see the point of living with my sound stuttering like crazy in a space game. I tried, I really really tried to get with the program. I followed the how-to's until I went blind and darn near crazy.  I have a pretty much plane jane AMD64 with sound on the motherboard. It just works, using nothing but alsa. I used to think that 2 gigs was plenty memory. I ran an 8 line Linux BBS on a 486 with 64 megs of memory. I went to 64bit and back to 32bit. Both times I had to pull out pulse. 

I'm trying like heck to pare my system of all extra "stuff" that I don't need. When I removed pulseaudio it pulled out most of my gnome desktop with it. So long!! So solly! See you!! I hit the red button and gibbered with glee. I'll show THEM! -push- and gnome is fricking gone. I can live without that which aggresses on me, insisting that I have a package installed that wrecks my personal enjoyment of MY OWN @#$%^& computer. It's a mindset I do not like. Not one bit. I even highly resent it, as well. Mark, you listening?? If Ubuntu wishes to take the Fedora ride, I can tell you it's a tobaggon ride to Hell on greased grooves.  Please leave us to our own intelligent choices. I'm hitting 60 and just don't want to get a minute closer to my grave chasing down STUFF that does nothing but disorder my machine. :-({|=

---

