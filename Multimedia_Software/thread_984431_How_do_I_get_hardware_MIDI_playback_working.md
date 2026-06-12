---
title: "How do I get hardware MIDI playback working?"
date: 2008-11-16
forum: Multimedia Software
---

### Post by Harrkev on 2008-11-16
I have a nice fresh 8.10 install on an older system with a Sound Blaster Audigy 2 card.

I have Jack working great.  MIDI in/out works just fine, and I can have my keyboard trigger Timidity just fine too (but the latency on Timidity is terrible).  I can record my keyboard from Rosegarden, and Rosegarden songs play back just fine on my keyboard.  I even got the "real time" kernel working, and, with 8.10, it finally does not crash my nVidia driver (wow).

My Audigy 2 card has hardware dedicated to playing MIDI noises, but I cannot figure out how to make it work.  The only way that I can get ANY MIDI sound out of my computer speakers is with Timidity, which is sub-par.

I see lots of info on how to install Timidity, and some info on getting MIDI I/O working, but almost nothing to getting hardware soundcard MIDI playback going.

Any ideas where I can go to look for more info?

Thanks.

---

### Post by Eck on 2008-12-24
Install awesfx.

Copy (in root file manager) some soundfonts to somewhere like /usr/share/sfbank/creative

On login do:  (just as your normal user, it works fine that way)

asfxload /usr/share/sfbank/creative/CT4MGM.SF2  (as an example).

If you logout and in again, you'll need to do that (every time :( ), but first do:

asfxload -i  

That removes the previous font from memory so you're not loading them on top of each other.

In KDE I would set the midi hardware output in KControl's Audio panel, then kmidi would play my files us.  There's pmidi and playmidi too, but those are command line.  In Gnome, I'm sure I noticed a spot in one of the applets in gnome-control-center that had a drop-down for midi.  Don't recall it at the moment.

I think the gstreamer0.10-plugins-bad package has a Rhythmbox plugin for midi (wildmidi, I think).  Rhythmbox may still show the midi files as errors in importing the database, but if you search for a title and hit the play button it'll play them anyway.

I just switched over to an M-Audio Revolution and notice the difference when using Timidity.  The hardware midi was much better.  Of course, I haven't bothered yet to setup soundfonts for Timidity, just using the freepats.  So it may be more capable than I'm hearing at the moment.

I was actually surprised at how easily it is in Debian Lenny to setup timidity.  I just installed that and freepats, noticed a scroll by while aptitude was running dpkg-reconfigure on timidity to uncomment the connect to alsa line in timidity's /etc/init.d/timidity file, did that and ran dpkg-reconfigure timidity, and from then on midi worked.

Just not as nice sounding as on my Audigy 2 ZS.  But everything else actually sounds nicer on the Revo!  Think it's because Alsa is forced to tinker like crazy with the old SoundBlaster Live! sources to adapt to the Audigy whereas they got the M-Audio chip going a bit more easily.  Too bad the headphone jack won't work, gotta use a 2 way switcher cable.

---

