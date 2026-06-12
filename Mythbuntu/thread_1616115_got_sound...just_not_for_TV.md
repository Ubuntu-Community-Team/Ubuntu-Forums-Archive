---
title: "got sound...just not for TV"
date: 2010-11-07
forum: Mythbuntu
---

### Post by linuxhippy on 2010-11-07
I am trying to get my new install of Mythbuntu 10.10 configured.  I managed to get my sound card working with mplayer radio streams by editing /usr/share/alsa/alsa.conf and making all references to card 0 changed to card 2.  I have 2 Pinnacle cards in my pc and 1 SB Audigy 2 card.  Alsamixer shows that alsa thinks that cards 0 and 1 (my tuner cards) are audio cards and has put my real audio card at position 2.

The problem shows itself when I try to configure my tuner cards in mythbackend.  The audio device is ALSA:default.  When I watch TV on mythfrontend I hear nothing but do see a picture.  The only other audio choice in mythbackend in NONE.

I found that there are /dev/snd "files" that are being made.  

drwxr-xr-x  2 root root      100 2010-11-07 15:08 by-path
crw-rw----+ 1 root audio 116,  7 2010-11-07 15:08 controlC0
crw-rw----+ 1 root audio 116,  5 2010-11-07 15:08 controlC1
crw-rw----+ 1 root audio 116, 19 2010-11-07 15:08 controlC2
crw-rw----+ 1 root audio 116,  8 2010-11-07 15:08 hwC2D0
crw-rw----+ 1 root audio 116, 20 2010-11-07 15:08 hwC2D2
crw-rw----+ 1 root audio 116, 10 2010-11-07 15:08 midiC2D0
crw-rw----+ 1 root audio 116,  9 2010-11-07 15:08 midiC2D1
crw-rw----+ 1 root audio 116, 21 2010-11-07 15:08 midiC2D2
crw-rw----+ 1 root audio 116, 22 2010-11-07 15:08 midiC2D3
crw-rw----+ 1 root audio 116,  6 2010-11-07 15:08 pcmC0D0c
crw-rw----+ 1 root audio 116,  4 2010-11-07 15:08 pcmC1D0c
crw-rw----+ 1 root audio 116, 18 2010-11-07 15:08 pcmC2D0c
crw-rw----+ 1 root audio 116, 17 2010-11-07 15:08 pcmC2D0p
crw-rw----+ 1 root audio 116, 16 2010-11-07 15:08 pcmC2D1c
crw-rw----+ 1 root audio 116, 15 2010-11-07 15:08 pcmC2D2c
crw-rw----+ 1 root audio 116, 14 2010-11-07 15:08 pcmC2D2p
crw-rw----+ 1 root audio 116, 13 2010-11-07 15:08 pcmC2D3p
crw-rw----+ 1 root audio 116, 12 2010-11-07 15:08 pcmC2D4c
crw-rw----+ 1 root audio 116, 11 2010-11-07 15:08 pcmC2D4p
crw-rw----+ 1 root audio 116,  3 2010-11-07 15:08 seq
crw-rw----+ 1 root audio 116,  2 2010-11-07 15:08 timer

Can I put these into mythbackend as a sound device?  It hasn't worked so far, so if so then how is it done?

---

### Post by klc5555 on 2010-11-08
The problem is the likely the frontend, which plays the audio, not the backend.

Since mythfrontend runs as your main login user (not "root" or "mythtv"), usually you'd use aplay -l to see what your main user is getting for visible audio devices, and then use Debian/Ubuntu's usual "asoundconf set-default-card" at the user level to set the default card for alsa for this user to what it ought to be. As per [http://manpages.ubuntu.com/manpages/intrepid/man1/asoundconf.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/asoundconf.1.html)

Once the default card is set in this fashion for your main user, alsamixer and audio ought to work correctly for all of the main users applications, including mythfrontend.

It's one of those few things that's easier in Ubuntu than in distros where you have to compose .asoundrc files or edit asound.conf or whatever.

---

### Post by linuxhippy on 2010-11-08
I tried asoundconf and it's not on my pc (I did a sudo updatedb and locate asoundconf).  It's also not available from the synaptic repos I have.  Which repository can I get it?

---

### Post by klc5555 on 2010-11-08
My bad.

I failed to anticipate that Ubuntu upstream would eliminate asoundconf without actually having something equally useful in place and ready to go. But evidently they did it. Two steps back without the one step forward.

However, there is a thread here from Ubuntuforums.net on how to set your default card on Ubuntu in the brave new post-asoundconf world: [http://kubuntuforums.net/forums/index.php?topic=3106282.new](http://kubuntuforums.net/forums/index.php?topic=3106282.new)

Hopefully doctordruidphd's workaround for Karmic still holds the current version.

Otherwise, I'd recommend trying an .asoundrc file in your main user's home directory of the sort described in the section "Brief Example" here: [http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

### Post by bance on 2010-11-08
Please see [here]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Audio_System") and [here]("http://ubuntuforums.org/showthread.php?t=1615567")....

good luck Steve,

---

