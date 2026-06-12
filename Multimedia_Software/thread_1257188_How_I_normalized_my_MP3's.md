---
title: "How I normalized my MP3's"
date: 2009-09-03
forum: Multimedia Software
---

### Post by mike.123850 on 2009-09-03
Ok, I know this comes up every once in awhile. I'm not an audiophile and have been fighting with this for a long time. I have found what works for me so I thought I'd post how I did this. 

I am running Ubuntu 9.04 Jaunty.

1) install mp3gain found in the Synaptic Package Manager
2) install vorbisgain (handles ogg files) found in the Synaptic Package Manager
3) install easymp3gain 0.4.2beta (gui for mp3gain) found at [Source Forge]("http://sourceforge.net/projects/easymp3gain/")

**I found easymp3gain in Applications under Sound and Video after installation.

4) open easymp3gain
5) click on the Magnifying Glass button and set this to Track Analysis
6) click on the Gear button and set this to Apply Track Gain
7) click File then Add Folder Recursively
8.) click the folder where you have the files to be normalized
9) click Open (you should see all the files to be changed)
10) click Modify Gain then Apply Track Gain (this will both analyze and apply the track gain)
11) Burn the now Normalized mp3 files.

**I left the default dB setting at 89dB

-----------------------------------------

**To undue the change:
Click Modify Gain then Undo

-----------------------------------------


**If you see songs that have no values next to them, the file may be locked so you may need to change the permissions of the file. This was my problem, may not be what's going on with you.

1) Find the file and single right click on it 
2) Single left click on Properties
3) Click on the Permissions tab at the top
4) Under Owner this should be Read and Write
5) Under Group File Access use Read Only
6) Under Others File Access use Read Only

Once Unlocked try using easymp3gain again. If that didn't do anything I don't know why it's not able to change it. You can either not use that mp3 file or just use it as is and hopefully it's not too soft or too loud.

Hope this is helpful to someone.

Mike

---

