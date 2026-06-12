---
title: "True 5.1 over SPDIF with Audigy 2 ZS?"
date: 2008-06-30
forum: Multimedia Software
---

### Post by riromero on 2008-06-30
I have an Audigy 2 ZS [SB0350] sound card. It is connected via SPDIF coax to my Logitech z-5500 surround speakers. When I play stereo encoded music, I get beautiful sound from all six speakers (stereo encoded of course). However, if I play a DVD (totem, mplayer, or vlc) with sound set for AC3 passthrough I still only get stereo sound on all speakers. I've tried fresh installs and permutations of a wide variety of settings found from searching but nothing works. This dashes my hopes for using the machine as my HTPC. I hate to go back to Windows where everything worked fine. Any help? I'm at my wits end.

- Reuben

---

### Post by Trollslayer on 2008-06-30
As far as I know Creative cards only handle stereo through SPDIF - I'm going for a C-Media based card by Asus because of this.
The only way I can get Creative 5.1 is by analogue connections.
This apepars to be because the ALSA developers can't get information from Creative so I'm not waiting

---

### Post by riromero on 2008-07-01
Finally, I managed to get the right combination of configuration files and command line options to get beautiful 5.1 sound over SPDIF. Except now, mundane stereo encoded music or videos no longer are working. Can't I somehow get both? 5.1 sound over SPDIF for DVD movies and 2.0 sound over SPDIF for everything else?

- Reuben

---

### Post by riromero on 2008-07-03
Finally (nearly) everything works. I spent quite a bit of effort to figure out what essential piece it all depends upon and got quite a surprise. The only thing that mattered in the end was invoking mplayer with right options.

   mplayer dvd:\\1 -ao alsa -ac hwac3

I got rid of all the /etc/asound.conf, ~/.asoundrc, /etc/pulse/daemon.conf files that I had accumulated and started from scratch. The only thing that ended up mattering was the mplayer options. However, neither Totem or VLC gives 5.1 digital sound from my Audigy 2 ZS over the SPDIF coax cable.   I've tried a million combinations and no joy. Adding to the frustration, speakertest only gives output on two of the front channels even though mplayer works fine. Not much of a test since it added greatly to the confusion. Oh well, I can live with this result.

- Reuben

---

### Post by rockstar on 2008-07-03
I have the same sound card and the same speakers.  Why did you use SPDIF? I haven't been using the speakers that much because almost everything I listen to is stereo.  Could you give more details on your setup and how you made it work? Thanks

---

### Post by riromero on 2008-07-03
My main goal is to play DVDs with decent 5.1 surround sound. I have speakers that accept a digital SPDIF connection so I just want to pass the digital stream straight through the card with no decoding. This wasn't (and still isn't) working with Totem even though I set 'AC3 passthrough' in the settings. That launched me into a fools errand among the multitude of web pages with recommended configurations. Nothing worked. Oftentimes I would break the sound completely and have to reinstall the OS. On my latest reinstall, I didn't make any changes other than installing mplayer and using the options shown above. That's the only way I've ever been able to get the digital stream over SPDIF. Very frustrating.

- Reuben

---

### Post by rockstar on 2008-07-03
So how do you get SPDIF output with the Audigy 2 ZS notebook? Did you buy a second cable? I have one output cable that splits into Orange, Green & Black.  The three cable system works perfect with windows and Creative gives you a tester to verify all 5.1 channels.  I would use the 3 cable system if i could verify the channels.  How do you know you're getting 5.1.  How did you know all your channels worked?

---

### Post by riromero on 2008-07-03
Sorry, but my Audigy 2 ZS is a PCI card in my desktop computer, not notebook. It has a separate SPDIF jack along with the Black,Green,Orange ones. If you are lucky, maybe one of your jacks doubles as SPDIF?

And I know my card is sending digital audio because the LCD display on my digital receiver that's plugged into the card says so. Plus you can hear the difference in movies that have sounds on the rear speakers. This is quite distinct.

- Reuben

---

### Post by BB2008 on 2009-06-14
Riromero, I have the same set of speakers and sound card (sound card not yet installed on the ubuntu PC). So are you saying that you could get digital out from the creative audigy 2zs sound card, and hook it up to your z5500 speaker system using a toslink to mini toslink cable? Please let me know as I was planning to do the same but so far was under the impression that it can't be done. You will give me much needed hope :D.

---

### Post by devguy on 2010-01-31
I'd like to chime in that today I updated my PulseAudio from the UpdateManager.  After playing back some videos with an AC3 track, I noticed my receiver was actually being submitted the AC3 track in full 5.1!  And when I went back to playing an MP3, it channeled it back down to 2.1 PCM.

This was on an Audigy 2 ZS with Ubuntu 9.10 x86-64 using XBMC.

Edit:  Sorry, I was deceived a little bit.  Upon rebooting the machine, I lost all I had gained with the passthrough and struggled greatly to find out what happened.  Turns out that the process of updating PulseAudio left it suspended until the reboot.  ALSA remained until then, which allowed for the passthrough.  I updated ALSA to the latest stable revision and now run XBMC with pasuspend command and have consistent working spdif passthrough.

Hope that helps someone else.

---

