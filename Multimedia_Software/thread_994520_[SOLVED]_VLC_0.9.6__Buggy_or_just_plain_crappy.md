---
title: "[SOLVED] VLC 0.9.6:  Buggy or just plain crappy?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by theluddite on 2008-11-26
I never used to take VLC media player for granted. It was great. As its literature suggested, it was truly the "swiss army knife" of media players. I loved that it could play absolutely anything. You could play a DVD-style directory, an .iso image and absolutely every type of file extension, regardless of the codec. In short, there was nothing that VLC 0.8.6 couldn't do.

Enter VLC 0.9.4. I just updated to Intrepid which, despite what I'd read here, was painless -- with one glaring exception:  VLC 0.9.4.  Let me highlight the host of problems I've experienced that have made VLC unusable:

    * It's a memory hog. I used to be able to play two different movies at once, but with the new VLC my RAM and CPU usage shoots of the charts and everything locks up.
    * Poor command-line interface. I used to be able to open an impromptu playlist of items with VLC from the command line using the glob star, but now it just hangs.
    * Incompatibility with Compiz. I'm pretty sure this is the main problem. Even while playing normal, everyday files VLC will hang insufferably, making it impossible to close the GUI or do anything else on my system. The only way out is to kill the process -- after considerable waiting.

Maybe this is as a result of the switch from GTK to Qt?  The only solution I've seen here is the standard uninstalling and reinstalling, which I've tried with no results. Please, if anyone has actually experienced the same problem and solved it, let me know.  I'd also welcome suggestions for a different media player that can play directories and iso images.  Otherwise, I lament the death of a great media player and sincerely hope that the VLC 1.0.6 release won't be nearly as much as a disappointment.

---

### Post by theluddite on 2008-11-28
So I was finally able to downgrade back to VLC 0.8.6 which completely solved my problem.  Since the newest version is the ones in the software channels, it has to be done manually -- I'm fairly certain none of the repositories have it.  Here's how to do it for an Intrepid install on an amd64.  [COLOR="Red"]Disclaimer:  I am a relative n00b, so if you try this and it wrecks your VLC install don't blame me.  [/COLOR]On the other hand, if your intrepid VLC install was like mine, you have nothing to lose.  

Download the following three packages:

> [libvlc0_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988560/libvlc0_0.8.6.release.h-1ubuntu1_amd64.deb")
[vlc-nox_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988559/vlc-nox_0.8.6.release.h-1ubuntu1_amd64.deb")
[vlc_0.8.6.release.h-1ubuntu1_amd64.deb]("http://launchpadlibrarian.net/15988558/vlc_0.8.6.release.h-1ubuntu1_amd64.deb")

Then remove conflicting newer packages:
> sudo apt-get remove vlc vlc-nox vlc-data

Then install the older versions using GDebi Package installer (right click the files you just downloaded and select the first option) is this order:
> [LIST=1]
[*]libvlc0
[*]vlc-nox
[*]vlc_0.8.6
[/LIST]

And voila!  Back to normal.  No Qt, no hanging, no problem.

---

### Post by manishk on 2008-12-24
It worked for me!! Thanks a lot bro :)

The one feature that I missed was Post Processing, which I depend heavily on. And yes, the UI (of 0.8.x) was much (much) simpler.

One question though, will this 'trick' work for future versions of Ubuntu as well, or will we be forced to use the newer version??

---

### Post by mc4man on 2008-12-24
> One question though, will this 'trick' work for future versions of Ubuntu as well, or will we be forced to use the newer version??

It will be very difficult, possibly one could build a 0.8.6 version, more likely there'll be dependency issues.

In the case of 8.10 while it was in the dev stage 0.8.6 was initially used. That's why .debs were available and in the case of amd64 still easily obtained.

---

### Post by manishk on 2008-12-25
Thanks for the info.

---

