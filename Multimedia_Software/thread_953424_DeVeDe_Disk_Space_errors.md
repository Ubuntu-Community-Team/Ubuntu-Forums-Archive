---
title: "DeVeDe Disk Space errors"
date: 2008-10-20
forum: Multimedia Software
---

### Post by saunders on 2008-10-20
Hi,

I'm having problems creating .ISO files in DeVeDe. I keep on getting the "Maybe you ran out of disk space?" error, [as described here.]("http://ubuntuforums.org/showthread.php?t=529405&highlight=devede+disk+space")

I'm using the current version in the repositories, and this error occurs on two different boxes running Hardy and Gutsy respectively.

As background, I'm trying to create an .iso from a ~700Mb avi file. I've tried saving the output file to an ext3 directory with ~3.5Gb free, and an external HD with ~350Gb free, so I'm pretty sure there's plenty of space available.

Any help would be much appreciated!

---

### Post by webaake on 2008-11-11
I had the same problem, it even crashed without notice until I found the problem;

devede uses /var/tmp as temporary dir for converting and if this is on a too small partition problems will occur.

To change this one must edit the file .devede in the /home directory

Only God knows how much diskspace devede uses for temp!

---

### Post by kogos on 2008-12-08
i had the same problem, but disk size is not the true cause of the problem here... Devede is bugged:oops:

I tested it with 3 systems running intrepid... A good example is the last one, having installed intrepid on a new 500GB hard disk (9GB swap, the rest EXT3), so the disk already had 450+GB available for var/tmp temporary data or anything else... I also tried to export my files on this same disk. And again, boom: 

Failed to create the DVD tree
Maybe you ran out of disk space

What i was trying to do is make a DVD disc with mpeg2 files i created on Nero Visio (winxp, i know:-o... feel free to insult me for that). Nothing worked... i even tried to use my 1TB external disk as output folder, but the error message kept showing all the time. 

What i did in my case was re-encoding the files with devede... That means i did not click that little option on the "misc" tab, that the files are already mpeg2 DVD standard files, so Devede started the encode process and it finished the job (i tried creating ISO and DVD structure as well). I have absolutely NO idea if all the people that get this error are using pre-encoded mpeg2 files, but in my case, all that was needed was to let Devede do the encoding all over again... 

Give it a shot, and let us know of updates on this... 

P.S.: english is not my native language, so i hope all the above make sense:)

---

### Post by cbilljones on 2010-09-27
Im getting this error, and i have tons of space, i tried to change the temp dir to /home/cbill/temp   will see if that helps, but i notice i only get the error when doing multiple titles. ILl update tomorrow if it worked or not.

---

### Post by sendblink23 on 2010-09-27
Have you guys tried ManDVD

---

### Post by cbilljones on 2010-09-27
My idea didnt work, ill try mandvd

---

### Post by cbilljones on 2010-09-27
Well i didnt really like mandvd, seemed to lack alot of the options i use in devede. However i may be on to something:
I realized my titles were screwed up, this time i set it to jump to next title when over, and it worked :popcorn:
The problem is i also ran with devede with "sudo devede" that time; so i am now trying same thing, but not as root; ill update in a bit.

---

### Post by cbilljones on 2010-09-27
Ok, it worked, i could have been 1 of 3 things; 

1) the title issue i referred to before
2) menu pic was jpg and needed to be png
3) devede was complaining about the mp3 i used for menu(tried converting a flac to ogg and mp3, same result with both) was damaged so i downloaded a new mp3.

Id be willing to test a little more if need be

---

### Post by StonePiano on 2010-09-29
I had this same error.  
**failed to create the dvd tree maybe you ran out of disk space**

I was trying to make a dvd with a mixture of .flv and .mov files.  Some of the .mov files were causing the problem.  Devede allows you to preview files individually within the program.  When I previewed some of the .mov files, they failed to preview.  (They just stopped immediately and prompted me to replay the preview.)  So I removed those problematic .mov files.  After that I was able to create the devede successfully (although some of the files needed to be excluded).

Those offending .mov files do play ok in MediaPlayer, so I don't know why devede couldn't handle them.  But in my case, it was no great loss to live without them.  

Hope this helps someone.

---

