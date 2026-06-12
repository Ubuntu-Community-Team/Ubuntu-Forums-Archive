---
title: "DVD problems"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by scooter1556 on 2008-02-28
I am having trouble playing dvds which are created on my home dvd recorder. If i open up the dvd in Nautilus all that is displayed is the VIDEO_TS.IFO file, not the AUDIO_TS and VIDEO_TS folders which should be displayed. The folders are shown in windows. DVDs which are created on the computer itself work fine. I am also having an intermittent problem where sometimes dvds are said to be empty in nautilus and i have to eject and load the dvd several times before it recognises that there are files on the dvd. Any help to resolve the issue will be appreciated.

---

### Post by aprilie on 2008-02-28
I don't know if that will be helpful tray to install the following packages 
gxine
libdvdnav4
libdvdplay0
libdvdread3
:)

---

### Post by scooter1556 on 2008-02-28
I currently have all of the libraries suggested installed. Any program i try to play the dvd in says that the disc inserted is not a dvd because the only files detected on the disc are a VIDEO_TS file which nautilus does not recognise as a folder. I can't think why the fact that the dvd was recorded on my home dvd recorder should make a difference, it is detected as a normal dvd with a normal dvd structure in windows and on any standalone dvd player. Thanks for the suggestion aprilie. :)

---

### Post by cozmicharlie on 2008-02-28
I assume then you have all the restricted extras installed.  Can you play a commercial DVD?

---

### Post by scooter1556 on 2008-02-29
Yes, i can play commercial DVDs fine and DVD's which were recorded using a computer, im just having trouble with dvds recorded on my standalone dvd recorder, the file explorer only picks up a VIDEO_TS file, no folders which is what is actually on the dvd, strange! Maybe its something to do with the file format used by the dvd recorder which Ubuntu doesnt support, i can't think what else could be different.

---

### Post by cozmicharlie on 2008-02-29
I assume you are in the USA - what region are the DVD's set too? PAL or NTSC?
Also, what happens if you try to open as root in Nautilus or do a "show hidden files"?  
Do the vob files appear in a Windows computer?  
If so can you attach the files and send them to me.  I can check them on my system and this will tell us if it is something in the dvd files or with your system set up.  If they are too large then let me know and I can gie you instructions for sending large files.

---

### Post by scooter1556 on 2008-02-29
hi cozmicharlie,

Im in the UK and the dvd recorder the dvds were recorded on is PAL. I have tried selecting 'show hidden files' in Nautilus but i still only get the one file "VIDEO_TS" shown. In windows VIDEO_TS is recognised as a folder and i can therefore access the VOB's inside it. Nautilus just doesnt recognise VIDEO_TS as a folder it thinks it is a file. If i rip the dvd using DVD decrypter under Wine the dvd folder that is created contains the correct VIDEO_TS folder and all VOB's are in tact, it is only whilst browsing using Nautilus i am having a problem.

EDIT - I have just had a thought, i no it shouldn't make any difference but could the fact that dvd's created on my dvd recorder only contain a VIDEO_TS folder and not an AUDIO_TS folder aswell make a difference?

---

### Post by yabbies on 2008-02-29
if I remember right, a lot of dvd recorders have a CSS on them

---

### Post by cozmicharlie on 2008-02-29
> **scooter1556 said:**
> hi cozmicharlie,

EDIT - I have just had a thought, i no it shouldn't make any difference but could the fact that dvd's created on my dvd recorder only contain a VIDEO_TS folder and not an AUDIO_TS folder aswell make a difference?

Could be - On a DVD disc, DVD movie files are stored in the VIDEO_TS folder. There is also an AUDIO_TS folder, this is where DVD-Audio would be stored, but usually the folder is empty.  Not sure it would make a difference.  for some reason nautilus is not detecting the directory structure properly.  Maybe it has to do with yabbies comment.

---

### Post by scooter1556 on 2008-03-01
yea, its strange, its weird that the structure of the dvd is detected fine under wine using dvd decrypter etc, but not in nautilus. I guess it must be either a protection on the disc or my dvd recorder uses a different file system\format which nautilus does not support. I'll keep trying :) Thanks for the help

---

### Post by sanddgroper on 2008-03-01
Hi scooter1556
I would go with your DVD recorder not playing well with Ubuntu(linux).
You could try copying your DVD to an iso on Ubuntu and then try burning the
iso to a disk and see if that is read by Ubuntu.

Cheers
Sandy

---

### Post by scooter1556 on 2008-03-01
Hi sanddgroper,

This is the only solution at the minute, I have found that if i copy the dvd to my hard drive using dvd decrypter under wine either as an iso or files i can burn them to dvd in Ubuntu fine and nautilus will read the dvd fine. I will simply use a DVD-RW to transfer it from my dvd recorder to my computer and then put it onto a DVD-R from my computer. Thanks for the help :)

---

### Post by mhedges48 on 2008-03-22
I had the same problem-> fixed it by ripping from the DVD using Thoggen...

---

