---
title: "Jsymphonic wont start"
date: 2010-06-08
forum: Multimedia Software
---

### Post by arayilpdas on 2010-06-08
(fixed it myself - figured out the path for the device and it worked. Thanks)

When I first downloaded jsymphonic, I didn't know that I had to connect the mp3player before running the application. When started it showed something like device > invalid path. Realising my mistake i connected the device and tried to start jsymphonic, but it wont start. When tried from the terminal the following appeared! 

arayilpdas@arayilpdas:~$ jsymphonic
8 Jun, 2010 9:19:05 PM org.danizmax.jsymphonic.gui.SettingsHandler startDocument
INFO: Reading file /home/arayilpdas/.jsymphonic.xml...!
8 Jun, 2010 9:19:05 PM org.danizmax.jsymphonic.gui.SettingsHandler endDocument
INFO: Done reading file
08 Jun 2010 21:19:05 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : Initializing JSymphonic...
08 Jun 2010 21:19:06 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:mountDevice : Mounting the device "Invalid path"
08 Jun 2010 21:19:06 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
08 Jun 2010 21:19:06 [WARNING] org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : The device path /home/arayilpdas/Invalid path/esys does not exist!
08 Jun 2010 21:19:06 [SEVERE]  org.naurd.media.jsymphonic.device.sony.nw.NWEsys:<init> : Invalid OMGAUDIO directory.
Exiting program.
arayilpdas@arayilpdas:~$ 

I am a lay user, but i could see "invalid path" inside the stuff  that  terminal spat at me. I believe what I did initially had something to do with all this. Help in very simple terms would be highly  appreciated. 

Regards
Dr. Das

---

### Post by magtrask on 2010-12-04
Hi, I have a Sony NWZ - E354.
Trying to use it with JSymphonic as suggested here.
When I start the program I get the error: "Cannot find OMGAUDIO folder.  Device path probably wrong."
I think the device path is correct:  /media/WALKMAN  as this is what appears when I hover the mouse over the WALKMAN icon in Home Folder.
Any suggestions?

Well, the device path was correct.  I created a folder called OMGAUDIO in the Walkman directory.  But its still not a happy machine.  It has 2 GB of music it can't play (FLAC) which I tried to delete from the player, but it put this into a .TRASH file on the Walkman directory and I am unable to remove it from this, so its still taking up all that space.  Overall, I'm thinking the Sony isn't worth it and I may return it.  SanDisk seems to meet with the most approval around here, although I recently returned a brand new clip+ that was full of glitches.  Anyone tried Archos products?

---

### Post by mcorr on 2010-12-04
I've spent the whole day trying to work out the same problem, and your post has just given me what I needed, thank you arayilpdas!  I'm totally new to Linux, and not the most computer-literate in any case, so it's really difficult trying to work these things out.  However, I read your post and copied what you did (typing jsymphonic into the terminal) and got exactly the same response.  What a moment of joy to realise all I had to do was create a folder!

Magtrask, if you're having the same problem, I would suggest opening terminal and typing in 'jsymphonic' and see if you get the same response we did.  If so, all it took was creating a folder alongside OMGAUDIO on your walkman and naming it 'esys'.  I was getting exactly the same error message as you, and then couldn't open Jsymphonic at all, but just adding that folder has done the trick and it's all working fine now!

---

### Post by mcorr on 2010-12-04
Argh, well it didn't work, it just looked like it did.  I seem to be able to copy files to my MP3player using Jsymphonic, then when I remove it, the files don't appear to be there.  They must be getting stored somewhere that the MP3 player can't access them from, but Jsymphonic can still see them?  Any further advice would be much appreciated!

---

### Post by magtrask on 2010-12-04
Yes, I'm having that problem too.  It seems that the music has transferred via JSymphonic, and space is taken up, but the player says there is no music or files.

---

### Post by djdg on 2011-02-28
Having the same problem. :(

This is a topic with the same subject (I think)

[http://ubuntuforums.org/showthread.php?t=118759](http://ubuntuforums.org/showthread.php?t=118759)

---

