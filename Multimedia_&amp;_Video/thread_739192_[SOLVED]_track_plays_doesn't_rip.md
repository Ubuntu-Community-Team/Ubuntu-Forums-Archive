---
title: "[SOLVED] track plays doesn't rip"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by kewlfuzz on 2008-03-29
hi guys,

i've got a cd where the first track is > 30 min long and i can play it but when i try to extract using sound juicer it unchecks the first track and just extracts the rest, is there some way i could workaround this?

ANY ideas on how to get this track into HD would be helpful

thanks for the ubuntu love,
kewlfuzz

---

### Post by mcduck on 2008-03-29
First make sure that what you have is a real audio CD, not some copy protected disk. That kind of problem sounds like the disk might not be a real audio CD.

Then, try some better ripping program. I recommend Grip as it's able to fix different errors on scratched (or copy protected) disks. Besides, multi-core CPU's are quite common these days and Grip allows you to run multiple encoding processes at the same time to speed up the ripping..

---

### Post by kewlfuzz on 2008-03-29
it is a real audio cd, like i said everything plays, but only the first track won't rip, i tried getting grip as suggested, but when i try to rip+encode i get

Warning (grip)
Invalid encoder executable.
Check your encoder config, and ensure that it specifies the full path to the encoder executable.

i have dled the restricted extras
sudo apt-get install ubuntu-restricted-extras

i know i am an absolute beginner here but is there something else i need?  what config file should i change?  what should i add to it?

thanks,
kewlfuzz

---

### Post by mcduck on 2008-03-29
You'll probably need to install lame as well, and then check in Grip's settings that it's set to use lame for encoding.

---

### Post by kewlfuzz on 2008-03-29
i tried to dl lame and the settings in grip were set to lame but still got the same error message, still interested in finding a solution for using grip, it might involve the solution i did find:

i was able to extract using sound juicer, after trucating the title (apparently it was too long for any program to add an extension onto it)

thanks,
kewlfuzz

---

### Post by mcduck on 2008-03-30
Great you at least got the job done :)

Anyway, here's how I have configured Grip:

1. Config/Rip/Ripper:
-Make sure ripper is set to "Grip (cdparanoia)
-If your disks are in mint condition, with no scratches, mark the boxes for "Disable paranoia" and "Disable Extra Paranoia". These control the level of scratch/error detection and enabling them will give you better results with bad disks but also makes the ripping slower.
-In the "Rip file format"-field change the path to your liking. I'm using "~/Desktop/%A/%d/%n.wav", which puts ripped files into my desktop based on the Artist and Album.

2. Config/Encode/Encoder:
- Set the encoder to "lame"
- "Encoder executable" should be "/usr/bin/lame"
- For the "Encoder command-line" I'm using this: "-V2 --vbr-new %w %m"
- "Encoder file extension" should be set to "mp3"
- "Encode file format". Set the path and naming for the encoded files, I'm using "¨/Desktop/%A/%d/%t %n.%x". You'l find the explanations for different variables in the help, but %A is artist name, %d disk name, %7 track number, %n track name and %x file extension.

3. Config/Encode/Options:
- Enable "Delete wav after encoding", you probably don't need the uncompressed wav file for anything.
- If you want Grip to also make a playlist of the disk you can enable that here, and also set a path for the playlist file.
-If you have a multi-core CPU, or one that supports Hyperthreading, set the "Number of CPUs to use" to 2  (or higher for more cores).

With these options you should get pretty high quality mp3 files. There's also some random options under Config/Misc but they shouldn't need any explaining so just take a look yourself if there's anything you want to change.

...


Then, put in the disk. Grip should get the track names and other stuff automatically,  but if you want to edit the tags yourself press the pen icon (Marked as "Toggle Disk Editor). When done, just go to Rip tab & hit "Rip+Encode"

---

### Post by kewlfuzz on 2008-04-01
okay that was my problem the /user/bin/lame

i knew it'd be something silly like that

you'd think a gnome app would assume we kept lame and the rest of our encoders in /user/bin, but whatever thats what i get for being a noob :P

thanks man,
kewlfuzz

---

