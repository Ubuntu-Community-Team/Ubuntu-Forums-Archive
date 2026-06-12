---
title: "dvd burning problem with linux not windows unrelated to application or hardware"
date: 2009-10-04
forum: Multimedia Software
---

### Post by jayem on 2009-10-04
The issue I have is related neither to copy protection nor to the application used to make the .iso file nor to the hardware used to burn the dvds.

The problem has something to do with writing the dvds under linux, particularly Mythbuntu 9.10 or Ubuntu 9.10 (tried both). For example, when I burn a dvd using Mythbuntu 9.10 (or Ubuntu 9.10)) it works perfectly in any computer but won't be recognized in the dvd players attached to my TVs but if I take the same dvd created with linux and copy it in the same machine running windows to the same type of dvd media then the copy will play perfectly.

I'm convinced that there's something messed up with the way in which Linux or Ubuntu writes the dvd.  I think this has to do with the operating system as I've even tried the above using the same .exe file of ImgBurn to perform this task either running in windows or with Wine.

Any help would be appreciated.

---

### Post by bumanie on 2009-10-04
Encode the video to a .iso with a tool like devede (available from synaptic) - never had a failure with devede prepared disk not playing in a dvd player at home - very simple to use. May be you weren't after an application, you  seemed to be after an answer - to that, I'm not sure why it is not working.

---

### Post by solitaire on 2009-10-04
I have a problems with burning iso's as well. I keep getting messages that the disk didn't burn, but the disks run fine (i mainly burn iso install disks rather than movie dvd). Try burning at the lowest speed possible and see if there is any difference ;)

---

### Post by jayem on 2009-10-04
Thanks for the advice.  I just tried at the lowest speed.  It didn't work.  The dvd seems fine under linux and windows but won't play on my dvd player.  For that level of quality my only current work around is to burn the .iso file from Windows.

Any other ideas?

---

### Post by solitaire on 2009-10-04
it might be a slight glitch with the way Linux burns DVD ISO's.
Try your Windows burning program under WINE (if it works) and see if those DVD's work.

If not you might want to file a bug; someone might have a helpful hint or 2.

You might want to compile your the burning prog manually with the latest version.

---

### Post by jayem on 2009-10-04
I just tried ImgBurn under Wine at slower speed (4x).  The problem persists.  All looks good from any computer but the disk is not recognized in the dvd player.

I think that the problem must be some bug.  Would you know the best place to file such a bug report?

---

### Post by DasEi on 2009-10-04
Which app do you use ?

I had problems with brasero,  but both k3b  and nero ( if you got a win license can use in ubuntu, too) did very good, also start k3b from command line to have possible error messages readable

---

### Post by jayem on 2009-10-04
I've tried k3b and and older version of nero under Wine but the results are consistent.

Do the videos you create work well in dvd players?

---

### Post by DasEi on 2009-10-04
yes they play fine, after installing vlc handbrake is a very good tool, as it uses the big library of vlc 

[http://www.getdeb.net/app/HandBrake](http://www.getdeb.net/app/HandBrake)

---

### Post by jayem on 2009-10-04
Thanks for the link.  I installed Handbrake but it looks to me to be an application to transcode stuff.  I don't believe this is the problem because as mentioned in my first post, I can create the .iso in linux, burn it to dvd in linux, turn the computer on running windows, copy the dvd using the same type fo dvd and then the copy will work on my dvd player but the original, created entirely in linux, will not.

---

### Post by jayem on 2009-10-18
Anyone else with any experience with this?

---

