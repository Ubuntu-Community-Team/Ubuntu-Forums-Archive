---
title: "Simple Graphical Equalizer?"
date: 2010-01-18
forum: Multimedia Software
---

### Post by phaedral on 2010-01-18
As a reference point, I am thinking about winamp's equalizer presets. I would sure love to find something like that in Ubuntu, but instead it seems I have to dig into details of pulseaudio and even then it's not a "simple" answer. My sound is working, it's just crappy because I'm on an eeePC 1005hab.

All pointers appreciated.

---

### Post by sports.car.guy on 2010-01-18
Chuck pulseaudio and just use Alsa. You can easily setup EQ parameters in a configuration file and change the file with only having to restart the application when you change the EQ settings, not a service or the whole system.

As far as I know there is no on the fly graphic EQ that can change frequency levels on the fly for Gnome or KDE with pulseaudio or Alsa.

This solution is probably the best for you even if a text file based one. You can have the raw audio run through the Alsa EQ you create then through Alsa default or whatever channels you choose. If you choose default it should be piped right into pulseaudio for you without an issue.

---

### Post by ratcheer on 2010-01-18
vlc media player has a graphical equalizer built in. vlc is easy to install and easy to use and it will play almost anything.

Tim

---

### Post by Enigmapond on 2010-01-18
Banshee and Audacious also have EQ's, the latter being close to winamp in how it looks. The system-wide EQ is just not happening with Ubuntu. There have been may thread on this and it seems the devs don't think it important enough.

---

### Post by urosg3 on 2010-01-18
Try this one, works great...
[http://ubuntuforums.org/showthread.php?t=1308838]("http://ubuntuforums.org/showthread.php?t=1308838")

---

### Post by phaedral on 2010-01-18
Thanks all for the input. I reckon I'll go back to vlc.

---

### Post by nikolatesla411 on 2012-03-01
This is just SAD! I've been a Linux Admin for over 5 years, and been waiting for a alsa EQ for 3 of those years. They have very good EQ for pulse audio, but pulse does not support all devices. I can not use Skype, or Google talk with pulse.

You know, Microsoft got SOOOOO much bigger than Linux for 1 single reason.

THEY GIVE THE PEOPLE WHAT THEY WANT!!!

Granted they throw in a bunch of unwanted crap along with it, but if ANY Linux distro is EVER going to present a market challenge, they need to get a grip and follow the lead of Microsoft, and GIVE THE PEOPLE WHAT THEY WANT!!!

And the people want A FULL FUNCTION MULTI-BAND GRAPHIC EQ FOR ALSA!!!

I understand people here are not used to such bold statements, but I do NOT do sugar coatings. I'm like the GDM, clean, direct, and to the point.

I'm a born audiophile, and I refuse to keep switching back and forth between Pulse and Alsa just to make a phone call! Rather go pay $60 a month for a cell phone.

This lapse of reason on the part of Linux developers is undeniable and inexcusable. Especially when they spent hundreds of hours getting gaming to work, but seem to be refusing something as simple as a plug-in in MUCH higher demand.

---

### Post by nikolatesla411 on 2012-03-07
Great news! I got sick of waiting for a system wide graphic EQ for Alsa, and stumbled onto a way to make Alsa and Pulse work together, ALMOST flawlessly.

From clean install, install all Pulse options you wish, but do NOT alter Alsa in any way. Go into sound selector and set everything to use Pulse Audio Server. This will make Pulse the default, but also leaves Alsa enabled on anything that Pulse doesn't take over. I am now able to control every aspect of my audio, AND use Google Talk and/or Skype! Alsa adapts to Pulse if left alone, and will even give you a way to switch back and forth with 3 clicks within the volume control that comes with the install.

My specs are as follows: Acer Aspire 4315-2535, Celeron 540 CPU, 2gigs DDR2 at 800mhz, Intel X3 100 graphics with 252mb video memory, crystalbrite 14.1" screen, atheros "signal up" wifi. Have CPU and HD upgrade on the way, and will update this post with how well this audio set up works on the different hardware.

This was surprisingly simple! I thought for sure I'd have to give myself a refresher crash course in coding and have to write my own application compilable for specific systems. Developers need not worry, I don't want your job. I quit trying to work with computers when Radio Shack wouldn't hire me after building them for 2 years. Now, I just play with them.

Enjoy your new sound system!

---

### Post by dummy910 on 2012-07-02
just ran into a 12.04 that was in need of the pulse-audio-eq and here's the link to a .deb file I downloaded, then installed using Gdebi.... the  eq is now alive and well on this ubuntu-studio-12.04 of all things. (running pulse audio for streaming audio, jack for studio functions of course.)
[B]
[http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7.0.2-2~webupd8~oneiric3_all.deb]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Eoneiric3_all.deb")
[/B]

---

