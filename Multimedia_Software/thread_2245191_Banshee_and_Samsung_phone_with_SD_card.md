---
title: "Banshee and Samsung phone with SD card"
date: 2014-09-21
forum: Multimedia Software
---

### Post by jolindbe on 2014-09-21
Hi!
I am running Ubuntu 14.04, and have just bought a Samsung Galaxy Light with a 32 GB memory card, so that I can put my music on it. However, this MTP transfer is giving me gray hairs.
I have now browsed through very many forum threads, modified system files, tried with PTP instead of MTP, and so on. At some point, Banshee found the phone, but would put the files BOTH on the memory card and on the phone memory, and would only recognize 5 GB of storage (should be 8 GB and 32 GB respectively). What I want is: The SD card in the phone should show up as a music player in Banshee, so that I can sync a playlist with it. Or: I could live with pluggin in the SD-card into the computer's SD reader and finding it in Banshee.

I have put a file named .is_audio_player in the root of the SD card containing "audio_folders=Music/". Still, Banshee does not find it, no matter if I connect through MTP or through the SD reader. Nautilus finds the card, but is very slow on MTP, working fine through SD reader. Any ideas?

---

### Post by jolindbe on 2014-09-21
I now see that the .is_audio_player file cannot be seen in Nautilus (also if hidden files are shown). I can see it in the terminal if I plug the SD card in the SD reader, but I can't figure out how to open the MTP directory in a terminal, so I can't see if it is there when the phone is connected through USB.

I have followed this guide: [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) which did not help.

---

