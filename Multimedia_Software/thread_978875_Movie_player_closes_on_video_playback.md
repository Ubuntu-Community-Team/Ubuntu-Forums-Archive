---
title: "Movie player closes on video playback"
date: 2008-11-11
forum: Multimedia Software
---

### Post by mexicola on 2008-11-11
Fresh install of Ubuntu 8.10, Radeon x1600

At first playback it asked to install the restricted codecs (xvid), now it just closes when I press play.

This happened to me before on my last install. Fixed it by activating the proprietary FGLRX fx driver, which messed up my dual monitor set-up. I deactivated the driver, dual screen settings still a bit messy but video playback worked.

Is it possible to fix this issue without activating/deactivating the driver? I like to keep things clean.

Thanks.

---

### Post by indi911 on 2008-12-16
I am also having this same issue.  I did the codec install when prompted.  Then when I try to play the movie the player will pop up then close instantly.  In that split second I am able to hear a little of the movie.  I am fairly green to this ubuntu.  Thanks for the help.

---

### Post by Ferstefani on 2009-01-14
I have the same issue. Any help? Cheers

---

### Post by areamike on 2009-02-14
I have the same exact problem..I have yet to find a solution.

---

### Post by ferrell.charles on 2009-05-13
I have the exact same problem.  Upgraded to 9.04, and still have the problem.  If I switch from a wmv to an avi or a dvd (switch media type) the movie player opens, then immediately closes.  I have to click it about 4 times, then the player will open and play just fine.  Annoying.  This started not too long ago, so I think it's something in an upgrade package that did it.  I too have the dual monitor set up.

:popcorn:  Happy movie watching! ):P

---

### Post by Another Monkey on 2009-05-15
I am seeing the same thing with 9.04.  I thought it was a codec issue, so I installed some stuff from Medibuntu following the instructions [here]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html"). But no luck.

Glad to know it isn't just be being stupid (again).

Anyone any idea what could be wrong?  What log files to look in?
Could it be related to Intel graphics issues?

Edit:
Seems like it could well be Intel graphics
[http://ubuntuforums.org/showthread.php?t=1134473&highlight=play+wmv&page=3](http://ubuntuforums.org/showthread.php?t=1134473&highlight=play+wmv&page=3)

---

### Post by stephdl on 2009-05-24
if lspci answer that
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

you can try this, it works for me

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by jasti on 2009-06-10
I think I've the same problem.  The player would come on very briefly with a black background and then closed quickly without showing anything.  My WMV files were running fine on my CRT monitor until I had to replace it with a 15" ViewSonic LCD monitor.  I'm using ubuntu 8.04 on my Dell Dim 4100.  Any suggestions would be appreciated.  -  Jasti

---

### Post by jasti on 2009-06-11
Credit where credits are due!  My problem is solved due to  the suggestion of Tomatz's thread dated 11/29/2008. - Jasti
P.S.The title is "Video opens and immediately Closes"

---

### Post by ibrabeicker on 2010-05-10
I fixed mine by uninstalling the movie player from ubuntu (which is called totem) on the add/remove programs and reinstalled.

Very weird

---

