---
title: "Audio crackles and stutters only when played through mythtv"
date: 2008-09-30
forum: Multimedia Software
---

### Post by nerver on 2008-09-30
Hey,

I have a very odd problem when playing video files through mythtv and I can't seem to find anything regarding this issue in my google searches...

What happens is that when I open up mplayer from my desktop and play a file (.avi in this case) everything is fine, sound and video are perfect. When I play the same video through mythtv (which is setup to use mplayer for .avi files) the video works and the sound is in sync but there is a lot of crackling and it stutters a bit as well. This is the same for music files also, if I play an .mp3 with banshee it works perfect but if I play it in mythmusic it has the same crackle/stutter.

I have tried every combination of choices in the sound settings, but it seems nothing I do there makes a difference and I can't understand why it would work when played normally off the desktop but not with mythtv. I am at my wits end lol.

Is there anyway to make mythtv use the same audio settings that are setup in my system for these other programs that work?

I am using:
Mythbuntu 8.04.1 with the Gnome desktop installed and I have an ASUS M3N78-VM SLI motherboard that has onboard sound which uses nvidia hda i believe. It is surround sound capable but right now I've just got stereo speakers plugged into the front headphone jack. (I also tried plugging into the jack on the back but its the same)

If anyone can help I would greatly appreciate it, everything ele about my mythbox is functioning quite well but I can't set it in my living room until I get this resolved :(

Thanks,
-Sean

ps. The audio is fine when watching livetv or livetv recording as the audio goes through my pvr-350 rather than the onboard audio.

---

### Post by nerver on 2008-10-05
anyone? please?

---

### Post by nerver on 2008-10-06
Update:

So I was reading around trying to figure this out and I messed around with some configuration files suggested in these 2 threads:

[http://ubuntuforums.org/showthread.php?t=44753&page=6]("http://ubuntuforums.org/showthread.php?t=44753&page=6")

and

[http://ubuntuforums.org/showthread.php?t=30076]("http://ubuntuforums.org/showthread.php?t=30076")


Strangely enough, now the audio works fine when playing video through mythtv no matter what I change the audio settings too, but music playback through mythtv still has the same issues as before.

I'm even more confused now because I thought that mythtv used the same audio settings for video and music playback?

Anyone have any ideas whats happening here? Its quite likely that I'm just missing something that I should know since I'm still fairly new to linux.

---

### Post by nerver on 2008-10-16
I ended up just putting an old pci sound card in my mythbox and everything works perfectly now. I will wait until I have a better sound setup and see if the suround or spdif output works for the onboard audio. Im still very confused about why i would only have a problem with mythmusic and nothing else though.

If anyone comes accross this post and has any ideas I'm still very curious to know.

Cheers,
-Sean

---

### Post by Windreaver on 2008-11-01
Dont think there is any sound fixes as of yet.  I have been searching all over as well.  The only posts Ive seen is *Install a sound card*  Which I will be doing tomorrow :)

---

### Post by nerver on 2009-04-01
This no longer appears to be an issue, the onboard sound for this mb works perfectly once i upgraded to ubuntu 8.10

---

