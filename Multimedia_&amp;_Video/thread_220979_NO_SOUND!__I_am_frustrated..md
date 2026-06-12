---
title: "NO SOUND!  I am frustrated."
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by Tyche on 2006-07-22
This has only happened since upgrading (and subsequently clean-installing) Dapper Drake.

My sound card is listed as EMU10K1 - SB Live [Unknown].  This is mounted  in a PCI slot on a Tyan motherboard (using a PIII/750MHz chip), and has worked before.  Checking in all the usual places, including lsmod shows that the card exists and is installed, and the driver is installed.  Checking alsamixer and the Gnome volume control (double-click) also shows the same information.  Still, I have no sound on startup, or any system event sounds, nor do mp3's or oog files produce sound, though the programs (and I've tested a bunch) indicate that the file is playing.

I have tried various solutions listed in various threads with no success.  I have had the help of one more gifted and knowledgable than I, with no success (I do not fault him.  An examination of the threads under Video & Sound show that a number of people have had the same problem, and with a variety of sound cards.  Some have met with success.  Others, apparently, have not.)  I finally went so far as to use the suggestion in  Comprehensive Sound Problem Solutions Guide and uninstall and reinstall alsa and associated sound files/programs (which also meant that I had to reinstall the gdm and ubuntu-desktop).

I still have no sound.

Ladies and Gentlemen - this is getting serious.  Especially when I can put a live cd of PCLinuxOS (using an earlier kernel) into my system and the sound works.  Something is broken in the Ubuntu Dapper Drake distribution.  Something just as effective as cutting the cord to your electric fan then wondering why the fan won't work (and in 118 degree fahrenheit, that can be fatal).  Something has been left "open", or unconnected in the programming.  Whether it's in Alsa or the kernel, I don't know (I'm not a programmer).  Something is not interfacing properly, and the tools are not available to a layperson such as myself to fix it.

PLEASE - is there someone out there who knows what has happened and how to fix it?

Craig
(User Name - Tyche)

---

### Post by jrjr on 2006-07-22
Check your permissions... I had the same trouble.

System/Administration/Users and Groups
Enter your user password
under user tab click your username and then properties
Under user privileges check all the boxes and say ok
You might have to reboot, I cant remember 

Also in the condition of missing permissions, half of the items in my system/administration menu was gone. I had to log in as a user that had working sound and change permissions for the one that was not working.

If you dont have a user like that, you can create one and log into it. Either that or figure out how to turn on permissions from the command line.

Good luck!!

---

### Post by vinayasurya on 2006-07-22
change group to audio with 29 as gid. I think this will work. I had the same problem.

---

### Post by Tyche on 2006-07-22
Already done.

Craig
Tyche

---

