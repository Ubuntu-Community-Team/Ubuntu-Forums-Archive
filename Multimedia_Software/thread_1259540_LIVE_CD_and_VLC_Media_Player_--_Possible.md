---
title: "LIVE CD and VLC Media Player -- Possible?"
date: 2009-09-06
forum: Multimedia Software
---

### Post by Halonomicron on 2009-09-06
Hi, I've generally always been a Windows user (DOS in the old days)....until today.  My hard drive died last night while I was enjoying a fine German hefeweizen with a friend who'd just gotten back from Germany.  Today, I spent most of what looks to be one of the last days of Summer recovering my files and diagnosing several bad sectors on my OS drive (a WD Raptor 74 GB).  I was successfull and really only lost files critical to running Windows itself.  Now, I have plenty of hard drives, but they all have important files on them and I have no bootable drive with an OS of any sort, nor any drives with which I could install an OS.  I've decided that I want to use this fine Ubuntu live CD that I downloaded and burnt from my girlfriend's laptop for all my computing needs while I wait for a replacement drive/buy a replacement drive.  I promise that I will install a dual-booting Windows XP/Ubuntu scenario if you help me with this question:

The one thing the Ubuntu Live CD lacks that I don't think I can live without while I wait for my replacement drive is a copy of VLC media player.  I can do without my Steam games, Quakelive, and uTorrent, but I don't think I can live without my Stargate Atlantis.  Is there any possible way to get VLC into this Live CD environment?  The media player that comes with the Live CD is complaining about codecs etc.
:popcorn:

---

### Post by gobberpooper on 2009-09-29
Fortunately you can. I just installed ffmpeg and its dependcies, along with vlc and its dependencies. Worked perfectly, I'm watching Ben-Hur as I partition my hardrive for a clean Ubuntu install.

---

### Post by snowpine on 2009-09-29
Easy:

```
sudo apt-get install vlc ubuntu-restricted-extras
```

Unfortunately, however, you will have to do it every time your reboot--that's the thing about a Live CD, right?

May I suggest installing Ubuntu to a USB thumb drive? That way, you'd have the advantages of a Live CD, but you can install new applications and your changes will be saved from session to session.

---

