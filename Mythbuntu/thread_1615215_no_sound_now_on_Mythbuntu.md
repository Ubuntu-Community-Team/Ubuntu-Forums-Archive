---
title: "no sound now on Mythbuntu"
date: 2010-11-06
forum: Mythbuntu
---

### Post by linuxhippy on 2010-11-06
I just did a fresh install of Mythbuntu 10.10 on my old 32 bit Pentium 4 pc.  I have my hard drive partitioned into 4 parts so I was able to keep my last install of Mythbuntu 10.04 on /dev/sda2 while all the recordings are safely on /dev/sda4.  I also made a backup of my settings on a usb and then was able to get all restored...except for my sound.

Now I have no sound on Mythbuntu 10.10 but do in 10.04.  My sound is integrated SB Audigy 2 and I have 2 Conexant tuner cards which alsa puts ahead of my soundcard as the default setting for audio.  Alsamixer shows all 3 cards using F6 but won't move it's last setting of SB Audigy 2 to position 1 in its list of cards.

I also used the XFCE mixer to select SB Audigy 2 as my soundcard.  That kept but I still hear nothing.

I also added my user to the audio group.  I then rebooted.  Still no sound.

Any ideas?  Maybe copy the alsa.conf file in my working Mythbuntu 10.04 to 10.10?

---

### Post by linuxhippy on 2010-11-06
fixed-now I have sound again.  I did an update and it download 61 packages-1 of those gave me sound I guess.  Looks like mythbuntu 10.10 doesn't work out of the box!

---

### Post by linuxhippy on 2010-11-06
sound went out again when I rebooted.  I found the alsaconfig settings in /usr/share/alsa/alsa.conf and saw that alsa was seeing my card 0 as a sound card.  alsamixer shows that card 0 is my tuner card and that card 2 is my SB Audigy 2 sound card.  So I edited alsa.conf and changed the 0s to 2s and then rebooted.  Now I have sound.

---

