---
title: "Players do not see DVD drive"
date: 2017-02-12
forum: Multimedia Software
---

### Post by John Jason Jordan on 2017-02-12
Xubuntu 14.04, up to date. The computer has a Blu-ray drive plus an external DVD drive (USB). There is no autoplay feature enabled (and I wouldn't want it anyway). The defalt DVD player is VLC. I can insert a DVD into either drive and then in VLC go to Media / Open Disc, then select the drive (/dev/sr0 or /dev/sr1), and when I click on the Play button VLC plays the DVD perfectly.

But if I try to use Totem, Parole, SMPlayer, Xine, or Kaffeine the player cannot play the DVD because there is no way to select it. These players can select and play a file (.mkv, .avi, etc.), but there is no way to play the disc without first ripping and encoding it to a file.

I have installed every library and package for multimedia that I can find, but apparently there is still something missing. I need some clues.

---

### Post by mc4man on 2017-02-12
Not home atm so can't check smplayer player or xine but iirc totem may need the grilo optical media plugin installed to play DVD from menu/sidebar

---

### Post by mc4man on 2017-02-12
From here on 14.04 - 
Totem needs the grilo plugin, scr.1 (may or may not be available to you, have in a ppa..

smplayer needs to be set up, you'd need to choose from drop down, scr. 2,  then works from the open menu

Xine-ui is hardcoded to use /dev/dvd for dvd media. 14.04 does not have /dev/dvd so you'd need to create (was brought back in 16.04). This means only 1 drive can be used. Ex. for /dev/sr0
```
sudo ln -s /dev/sr0 /dev/dvd
```
Whether that symlink survives a reboot haven't checked.
 scr3 shows playback, scr4. shows dvd button in control to start playback

As far as the other mentioned payer have no interest in installing..

Edit; whether the forum adds the screenshots I guess time will tell...

---

### Post by John Jason Jordan on 2017-02-13
I tried to add the grilo optical media plugin, but I can't find it. Searching on 'grilo' in Synaptic I find that I already have installed grilo-plugins-0.2, libgrilo-0.2-1, totem-plugins, and totem-plugins-extra. Available but not installed are grilo-plugins-0.2-mediascanner, gilo-plugins-0.2-dbg, qtdeclarative5-qt.grilo0.1, libgrilo-0.2-1-dbg, gir1.2-grilo-0.2, libgrilo-0.2-doc, libgrilo-0.2-bin, libgrilo-0.2-dev, and rhythmbox-plugins. Can you be more specific as to which package I need?

As for Xine I added the link you suggested, but it made no difference. I don't understand what 'scr3' and 'scr4' mean.

As for SMPlayer, I finally got it to play the DVD by browsing to the VIDEO folder on the DVD, but all it would play was the first couple of minutes with the FBI warning. I went to Preferences (per your screenshot) and set all three to /dev/sr0. When I go to Open > Disc > DVD from Drive it makes the drive (/dev/sr0) blink for a few moments, but then the drive stops and no video is ever displayed. Ditto if I click on the Play button. However, in Browse > Title the correct length of the movie in the drive is displayed, so at least it sees the media.

I can't believe that the only program on Ubuntu that will play a DVD is VLC.

---

