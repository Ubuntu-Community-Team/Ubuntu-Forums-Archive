---
title: "Totem gstreamer refuses to play commercial dvds"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by cor2y on 2007-12-25
[COLOR=Black]I am pretty sure this wasn't the case a few months ago with my dvds.
But totem-gstreamer now refuses to play any and all commercial dvds.
What it does is instead treat the dvd as a cdrom and plays only the audio and not the video.
I have tried uninstalling and reinstalling all the gstreamer plugins as well as the medibuntu version of libdvdcss2, libdvdnav,libdvdread.
If i am missing something i don't know what it is.
I even went as far as to install mplayer and vlc to see if it was a new version of copy protection that was the cause, however both media players played the dvd/dvds just fine.
Anyone have an idea of why this is happening?
Debug mode in the terminal shows no issues. The only issue i have found is that totem will refuse to play the dvd if i go Movie->Playdisc [/COLOR][COLOR=Black]"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc." even though all the plugins for gstreamer are installed and the restricted codecs etc are as well.
However insert the disc totem recognizes its a dvd at first then goes on to label it as cdrom0 and play it as if it was a music cd with visualizations while you can hear the audio.
I know the most logical answer is install totem-xine however xine has problems playing back certain media files (asf) correctly while gstreamer has  no such problem. vlc and mplayer are not viable as i'd like to have just one media player and since totem-gstreamer is the default i'd liek to have that one be working.

Totem-2.20
gstreamer 0.10.* and all the relevant addons/plugins for restricted media playback
libdvdnav, libdvdread,libdvdcss2 (from medibuntu) installed.

I only discovered this when i attempted to play a box set dvd i received as a gift, i thought it was limited to that set of dvds (copy protection) but it turns out all commercial dvds even those i own were not playing back like they did (i am sure i had gstreamer  dvd playback working) before.

[/COLOR]

---

### Post by matt1 on 2007-12-26
exactly the same for me!

---

### Post by joshtheitguy on 2007-12-26
When I re-installed Libdvdcss2 from a .deb package I found from Videolan.org it started working. Do a google search for libdvdcss2 and look for a link pointing to videolan.org.

---

### Post by cor2y on 2007-12-26
you don't happen to remember which version of libdvdcss2 you installed do you?

---

### Post by spydon on 2007-12-26
This happens to me too, should dvd support be included in ubuntu restricted extras?

---

### Post by spydon on 2007-12-26
Okay now mine is working, I installed automatix and vlc, works like a charm.

---

### Post by kelvin spratt on 2007-12-26
This is the link for medibuntu this is the place to get the codecs you need [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) hope this helps

---

### Post by thefirstM on 2007-12-26
I never could get DVDs to work with the Totem/gstreamer system, so I just installed xine instead.  It also allows you to configure more advanced settings like xvmc.

---

### Post by cor2y on 2007-12-26
the problem is somewhere in gstreamer i think, not so much libdvdcss2.
I went to the medibuntu and videolan sites and tried debs even compiled from source and  still the same result from my first post.
My dvd when inserted is treated like music cd by totem-gstreamer with audio only playing no video playback instead i get the goom visualizations.
Trying to play from the menu gives the error
```
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media.
```
No clue how in the world this happened i haven't compiled or updated anything i can recall that relates to dvd playback and i have been using totem-gstremer since i updated to Gutsy, since at last all of the plugins for it were working correctly from dvd playback to other restricted media like real media and m4a audio.
Now all of a sudden this happens.

---

### Post by neilbmclaughlin on 2008-01-04
I had the problems described in this post and followed the instructions posted by binary_bob (November 17th, 2007, 11:29 AM) in this post:

[http://ubuntuforums.org/archive/index.php/t-611841.html](http://ubuntuforums.org/archive/index.php/t-611841.html)

This sorted it for me.

Just as a note - even after I had followed the instructions the DVD I was testing with still threw the error. I then tried another DVD which worked and when I went back to the original DVD that then worked too :confused:

HTH

Neil

---

### Post by itsjustarumour on 2008-01-04
I've just discovered this thread - I had a very similar problem a week ago when playing commercial DVDs.  Totem plays the DVD fine until its about half way through, then suddenly stops and throws up an error message saying that libdvdcss2 is not available!

I'm not near my Ubuntu box at the moment, but I'll revisit the problem and post up any further observations when I can  Just wanted to add my voice to the thread...

:-)


EDIT: I'm using xine-lib version 1.1.8 on Totem Movie Player 2.20.0 by the way, all from the official Gutsy repos.

---

### Post by itsjustarumour on 2008-01-04
OK, I've had chance to try this again.  I get around 60% of the way through the commercial DVD I'm watching, then it stops and I get the following message:

> 
An error occurred

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss? 

Of course, the answer to the question is "no"! ...

---

### Post by cor2y on 2008-02-05
What i have discovered so far.
The Gstreamer library for Gutsy seems picky on dvd playback, and for some reason now refuses to play dvds on my system even with fresh installs of Gutsy.
The Xine Library for Gutsy will MOSTLY work in dvd playback, in places where the error about the dvd being encrypted occurs has no rhyme or reason that i can see, the solution i have found for this is to put the disc in the OTHER dvd drive (if you have more than one) or play the dvd using mplayer/vlc which never reports the decryption error.

---

### Post by buntunub on 2008-02-14
> **cor2y said:**
> What i have discovered so far.
The Gstreamer library for Gutsy seems picky on dvd playback, and for some reason now refuses to play dvds on my system even with fresh installs of Gutsy.
The Xine Library for Gutsy will MOSTLY work in dvd playback, in places where the error about the dvd being encrypted occurs has no rhyme or reason that i can see, the solution i have found for this is to put the disc in the OTHER dvd drive (if you have more than one) or play the dvd using mplayer/vlc which never reports the decryption error.

Using VLC does not help with this issue - it just does not report an error message but still chokes at about the half-way point in playing the DVD. This issue just started for me after the latest kernel update.

---

### Post by buntunub on 2008-02-15
Update to this. Recompiling all the codecs seems to have fixed this issue. Very strange. The last kernel update seems to have broken something about libdvdcss it seems. Anyway, just rerun the usual commands to reinstall/recompile things and all should be well.

---

### Post by HappyFeet on 2008-02-15
just as a sidenote for anyone who cares, is i find that removing totem and totem plugins and install mplayer and mozilla mplayer and also vlc. then get the libdvdcss2. ive never had a problem playing any format or with streaming media. i believe totem has conflict issues. i seen the same issues (totem) on different installs on several pc's. but this is just *my* experience.

---

