---
title: "Rhythmbox Doesn't Recognize RCA Opal"
date: 2010-01-05
forum: Multimedia Software
---

### Post by disco.sleeze on 2010-01-05
Hi guys,

I have an RCA Opal, 4GB player.  I am having some problems transferring music to it.

I first try the player in MSC mode and just drag and drop the files I want to listen to into the Opal's Music directory.  That works fine, but over half of the songs I transfer over end up in the "Unknown Album" file.  I have checked the ID3 Tags for these songs and they are intact.

Next I have put the player into MTP mode to try to transfer things with Rhythmbox, but Rhythmbox doesn't show the player in the sidepanel.

Any suggestions on how to fix this, or a different program besides Rhythmbox I should try?

Thanks for your help!

EDIT 1: It may be worth noting that mtp-detect in Terminal returns the message "No Raw Devices Found"

I am on Pidgin right now if anyone just wants to IM a response.

---

### Post by Nelsinius on 2010-02-20
I also have an RCA Opal (4Gb) player, and am having some difficulty in converting files to .smv, which will play in my player, using Karmic. I tried the smv_encode program ([http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/](http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/)), but the files were not recognized by the player after transfer. I would be most grateful for your input concerning the use of this player in Ubuntu.

---

### Post by bkann on 2010-02-20
I'm not familiar with your device, nor do I have a specific fix for it, but I just posted a similar work-around that I stumbled upon for my MTP Creative Sleek, here: [MTP MP3 Player Work-Around]("http://ubuntuforums.org/showthread.php?t=1412169")

Your mileage may vary, but basically:

1. If not already installed, install Gnomad2

2.  When you plug the device in (in MTP mode), it should show an icon on your desktop.  Right-click on this and unmount it.

3.  Open Gnomad2 and let it collect the library information, then

4.  Close Gnomad2.

5.  Open Rhythmbox and the device should appear.  You can then browse and maintain the contents.

This worked for me, but again, it's a flimsy work-around using a different device, so I have no idea if it will work for you.

Good luck!

---

