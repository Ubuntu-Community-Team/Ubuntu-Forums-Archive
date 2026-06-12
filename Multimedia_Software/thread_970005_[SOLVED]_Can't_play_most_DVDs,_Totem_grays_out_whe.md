---
title: "[SOLVED] Can't play most DVDs, Totem grays out when told to play DVDs"
date: 2008-11-03
forum: Multimedia Software
---

### Post by RPG Master on 2008-11-03
Ever since I installed ubuntu on my HP Pavilion dv2000 I haven't been able to play any commercial DVDs. When I put in a DVD Movie player ends up graying out and I have to force-quit it. I have installed all the codecs and still nothing. :confused:

And I used to be able to watch movies on Vista :(

---

### Post by RPG Master on 2008-11-04
Um... help please :-|

---

### Post by mcgarry83 on 2008-11-04
I know you said you installed all the codecs, but one thing a lot of people forget is libdvdcss2, you can download it from the medibuntu website.

---

### Post by RPG Master on 2008-11-04
Thanks, now I can play DVDs in VLC....

But Totem won't get past the "ATTENTION don't copy this movie..."  part. It just stops. Any help with this? I really don't care much for VLC (it doesn't work with my media keys...)

---

### Post by RPG Master on 2008-11-04
Any more help?

I wanna watch my movie :popcorn:

---

### Post by mcgarry83 on 2008-11-05
Im not sure what. Im having some problems with DVD's myself. It seems that whatever player I use (VLC, Totem, Gxine) they all kill my processor. Gxine kicked it up to almost 85% which is ridiculous. I have never had problems with this before, the playback is all jerky and skips a lot. Im very upset about it, and I've been trying to fix it since the 1st. I even tried using a lighter desktop like Xfce with no luck.

---

### Post by cor2y on 2008-11-05
RPG MASTER sounds like there are two things perhaps that are a problem.
1) You are using totem-gstreamer and not totem-xine for dvd playback
2) The dvd you are using may be something from one of the heavily drm'd encrypted regions like Region 2 (europe/germany) instead of Region 1 (U.S.) i ran into this problem with the one dvd i bought at a flee market that was not Region 1 but instead Region 2.

To solve problem 1 add the [medibuntu repos]("https://help.ubuntu.com/community/Medibuntu") install, libdvdcss2, libdvdread3, libdvdnav4 and totem-xine totem-xine via synaptic or apt-get in the terminal.
```
 sudo apt-get install totem-xine libdvdcss2 libdvdnav4 libdvdread3
``` after adding the medibuntu repos.
Then in **Nautilus** go to Edit->Preferences->Media Tab and set totem-xine to be the default dvd media player (if you wish not to use totem-xine you can set any other installed media player for example mplayer or vlc) and thats it when inserting dvds totem-xine will now play dvds instead of gstreamer, why not totem-gstreamer? well the gstreamer decoders do not handle dvds that well.

As to problem number 2 i have heard the latest libdvd libraries (libdvdcss2, libdvdnav4, libdvdread3) solve this problem but they are not officially in the repos yet and require compiling by you which would mean you would have to create deb files etc from the source, i haven't tried so don't know if those claims are true, HOWEVER i can say as of this date with Intrpid Ibex and using the latest medibuntu repos i STILL have not been able to play the region 2 dvd i bought in Linux using totem-xine, mplayer or vlc using the free/opensource dvd decoders, i still think cyberlink's linux dvd software is too expensive to try with that although on my stand alone dvd the discs play fine (my stand alone player is region free).

---

### Post by inportb on 2008-11-05
For problem #2, I have resorted to using the Windows shareware DVDFab on Wine to copy the disc contents onto the harddrive (or a "clean" disc) before playing. It's not the most elegant solution; but hey, DRM is not elegant at all ;p

---

