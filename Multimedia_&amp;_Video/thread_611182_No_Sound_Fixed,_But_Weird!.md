---
title: "No Sound: Fixed, But Weird!"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by A. J. Rimmer on 2007-11-12
I am using an “Ultra” brand laptop with 2.8 GHz P4 and 1 GB of RAM.  The motherboard sound (Silicon Integrated Systems SI7012) has never worked, starting with Breezy and going up through all the upgrades.

Yesterday I did a fresh installation of Gutsy, and again tried to get sound working.  I think by now I know just about all the tricks and tweaks by heart.  Somewhere along the way I tried to open the Sound Recorder and got an error message that ESD was not installed, so I installed pulseaudio-esound-compat as suggested by the error message.  Still no sound.  (I don't think pulseaudio-esound-compat had anything to do with my final result, but I mention it here just in case.)

Well, I have another laptop (HP dv5000) running Feisty.  The motherboard sound on that laptop has output, but I have never been able to get sound into it.  On that machine I run a few applications for which I absolutely need reliable sound in and out (digital-mode radio communications programs: WSJT and FLdigi), so I bought an inexpensive 24-bit external USB sound card to use with it.  As long as I was experimenting with Gutsy, I thought I would plug the USB sound card in to the Ultra laptop just to see if it would work on this machine.

I went to System / Preferences / Sound and tried to generate a test tone, but forgot to set the playback device to USB, and was much surprised to hear sound coming from the laptop's speakers!!!  I unplugged the USB sound card and the sound still worked.  I logged out and back in, and the sound still worked.  I rebooted and the sound still worked.  I shut down, restarted and booted into Windows, restarted and booted into Ubuntu and the sound still worked.

I don't get it, but after over a year of fooling with this thing I now have sound on this laptop.

!!!

---

