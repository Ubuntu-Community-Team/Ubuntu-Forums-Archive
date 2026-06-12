---
title: "[SOLVED] Youtube kills Firefox"
date: 2008-06-24
forum: Multimedia Software
---

### Post by PinkBullets9 on 2008-06-24
I recently came back to Ubuntu and everything is going great. There is just one weird issue that I can't seem to fix. The first video I watch on youtube works perfectly. But as soon as i click on another video firefox immediately crashes. I would rather have it so I don't have to keep restarting firefox to change videos. Any Suggestions? Thanks in advance!

---

### Post by Pjotr123 on 2008-06-24
Are you using the right Flash Player? It should be the Adobe Flash Player.

Apply this simple how-to for 100 % multimedia support, including Adobe Flash Player:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by PinkBullets9 on 2008-06-24
Well I just figured out something very strange. Firefox will only crash with a second youtube video if there are no other tabs open. If the youtube videos are played in a second tab they will run perfectly fine. I don't know if this changes anything but at least i don't have to close out every time i want to switch videos. :D

---

### Post by |{urse on 2008-06-24
what are your system specs? flash works loathesomely awful on linux due to adobe's not-niceness.

---

### Post by PinkBullets9 on 2008-06-24
AMD Athlon X2 3800+
1 GB Patriot RAM
160 GB harddrive (dualboot with XP)
Nvidia 6200 gfx card

I installed this parition just yesterday so I am pretty new to Hardy Heron, I was on Feisty for 5 months beforehand before it died and I went to Windows :(

---

### Post by PinkBullets9 on 2008-06-24
Turns out it needs like 10 videos to crash in a second tab, still crashes though T_T

---

### Post by JohoTehAzn on 2008-06-24
I have this problem too.

If I have a YouTube video open with multiple tabs open and I close the tab with the YouTube video, all of FireFox crashes.  It gets rather annoying when I'm in the middle of a download.

My specs:
Acer Aspire 5100-5728
AMD Turion 64 dual core
1 GB DDR2 RAM
ATI Radeon Xpress 1100

I installed the Adobe Flash Player by downloading the tar.gz from Adobe's website and installing it from there.

I had the same problem previously, prior to reformatting my computer (which I did just yesterday).

---

### Post by PinkBullets9 on 2008-06-24
i installed flash through firefox actually because it came up with the box and did it for me. I don't think it should make much of a difference how it is installed as long as it installs correctly.

---

### Post by Lorenz on 2008-06-25
Same problem here - very annoying!

---

### Post by xcesarfrancox on 2008-06-27
Check out this two posts:

[http://ubuntuforums.org/showthread.php?t=839938](http://ubuntuforums.org/showthread.php?t=839938)
[http://ubuntuforums.org/showthread.php?t=839816](http://ubuntuforums.org/showthread.php?t=839816)

It is a flash bug, and here's the fix:

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

---

### Post by PinkBullets9 on 2008-06-27
well thanks man it is working now almost perfectly. I get this weird gray box thing but refreshing the page is a lot better than having to restart firefox :D

---

### Post by DarrenCT on 2008-06-30
I was actually able to resolve the problem following the steps, but without installing nspluginwrapper.  Just did the --purge uninstall of the flashplugin-nonfree, and re installed libflashsupport, then installed the flashplugin-nonfree.  

Firefox no longer crashes after the first video!!! hurray!

---

