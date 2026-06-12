---
title: "Soundconverter Ubuntu 10.04 doesn't seem to do anything but stress cpu"
date: 2010-07-08
forum: Multimedia Software
---

### Post by lozt.again on 2010-07-08
Since upgrading to 10.04 (amd64), I can't convert audio files with Soundconverter: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

I can drag and drop files or add them all as usual. When I click convert, cpu usage sky rockets, but it doesn't seem to be doing anything. I can leave it for 10 to 20 minutes without anything happening; by this time I end up forcing it to quit.

A bit of a problem for me as I need this to convert my music into suitable formats and bit-rates, to upload to various places.

Any help will be much appreciated. The same thing appears to be happening to Rythmbox too by the way... which I left open with full cpu utilisation for about 3 hours, thinking it might resolve itself. I'm a bit miffed.

Both programs have been purged and reinstalled multiple times.

---

### Post by kassoulet on 2010-07-12
Can you try to run "soundconverter --debug" in a terminal, retry to convert, and paste here the output please?

---

### Post by F525 on 2010-11-18
I have the same problem as 'lozt.again' described. I am trying to convert wav to mp3.

When I click Convert, the SoundConverter window turns Gray, and in System Monitor, the CPU usage goes up to 95 - 100 %. Nothing else happens after that. I have to do an "End Process". Here is the listing from the --debug in terminal:

SoundConverter 1.0.1
  using Gstreamer version: 0.10.28, Python binding version: 0.10.18
  using gnomevfssrc
/usr/bin/soundconverter:1413: DeprecationWarning: Use the new widget gtk.Tooltip
  tips = gtk.Tooltips()
/usr/bin/soundconverter:1417: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.set_tip(self.custom_filename, tip)
Queue done in 0s
launching: 'gnomevfssrc location="file:///home/dad/Public/20101114AM.wav" ! typefind name=typefinder ! fakesink'
Queue done in 0s
launching: 'gnomevfssrc location="file:///home/dad/Public/20101114AM.wav" name=src ! decodebin name=decoder ! fakesink'
got file duration: 3246
20101114AM.wav: type is audio/x-wav, tag reading blacklisted
Queue done in 0s

Then after I do "End Process" in System Terminal, it says: "Terminated"

I am running Mint ver 9 Isadora (i.e. Ubuntu 10.04) 32 bit.

Thank you for your advice, in advance.

---

### Post by kassoulet on 2010-11-19
This is quite an old version, try to install a newer one.

---

### Post by F525 on 2010-11-27
Thank you kassoulet. 
I installed version 1.5.3 and it is working fine now.

---

### Post by Taras.M.K on 2010-12-07
Had the same issue with v1.4.4 (also it worked for me just a month earlier). And it was solved by installing newer version too.
I'm using Mint 9 Isadora 64bit.
Just thought it would be worth to mention...

---

