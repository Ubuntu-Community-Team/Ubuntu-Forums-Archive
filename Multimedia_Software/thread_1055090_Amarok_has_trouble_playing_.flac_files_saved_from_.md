---
title: "Amarok has trouble playing .flac files saved from Audacity"
date: 2009-01-30
forum: Multimedia Software
---

### Post by sydbat on 2009-01-30
The title says it all.

It seems that when I save a file from Audacity to .flac, it stutters when playing in Amarok. This does not seem to happen in any other player.

If I burn the tracks to audio CD (.wav) then burn them back to my music folder, Amarok has no problem.

Is this a flaw of/in Audacity (v 1.3.4 from the repos on Hardy)? A flaw in the Amarok codecs?

I am currently recording my vinyl (some other annoyances that I will discuss in another thread) and saving as .flac. I even tried saving as .wav, but get the same result.

Thanks for your help.

---

### Post by sydbat on 2009-05-26
I am bumping this very old thread of mine because I still have not found a reason why Amarok (and only Amarok) stutters/skips/basically does not play .flac files saved from Audacity (1.3.5).

Strangely, if I burn a CD from the saved .flac and then remove the original from my HDD and then replace it with a copy from the CD, it works fine. Same for any other format I save in.

Also, as stated in my OP, it does not matter what format I save from Audacity (.wav, .mp3, .ogg, etc), these files will not play in Amarok, but WILL play in every other media player without a problem.

I have uninstalled Amarok completely and reinstalled it...uninstalled Audacity completely and reinstalled it...uninstalled all codecs completely and reinstalled them...changed from ALSA to OSS to Pulse...all to no avail.

I have Googled using as many phrases as I can think of and have not been able to find an answer (only my question here comes up in relation to this problem).

Does anyone have any ideas? Has this happened to anyone else??

---

### Post by Bloemetjesgordijn on 2009-05-26
well not exactly the same, but maybe ...

Amarok (1.4 on Jaunty) plays one flac file sloooowww. With an other player (for instance VLC)  it plays the same file perfectly.

The details of this file (0202.summertime.flac) are:
samplefreq 44100 Hz
Bitrate N/A

Maybe this helps

---

### Post by sydbat on 2009-05-27
Did Audacity have any interaction with that file?

> Sample rate 44100 Hz
Bitrate N/Ais the exact same as every other flac file. This is why I am confused.

If I take a CD (any CD) and burn it onto the HDD, it plays without a problem in Amarok and all other players. It does not matter what format (flac, mp3, wav, ogg, etc). It is only those files I have recorded or edited in Audacity that have a problem in Amarok.

Because I can play files created or edited in Audacity with every other player, I have to assume there is a problem with Amarok. I wonder if upgrading to Amarok 2 might solve the problem...or if I can upgrade as I am running Hardy. 

Or maybe it is because I am running it in Gnome instead of KDE? I'll install KDE and test it there.

---

### Post by Bloemetjesgordijn on 2009-05-30
> **sydbat said:**
> Did Audacity have any interaction with that file?



Nope no interaction with Audacity

> **sydbat said:**
> I wonder if upgrading to Amarok 2 might solve the problem...or if I can upgrade as I am running Hardy. 


Amarok2 gives me other issues :-(

> **sydbat said:**
> Or maybe it is because I am running it in Gnome instead of KDE? I'll install KDE and test it there.

I am running Gnome

Cheerz

---

