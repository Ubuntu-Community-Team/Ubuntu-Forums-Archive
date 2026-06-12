---
title: "ATI Radeon HD 3000 series"
date: 2009-02-11
forum: Multimedia Software
---

### Post by rexthor on 2009-02-11
[SIZE="2"]I'm running Intrepid Ibex 8.10. I noticed after installing Intrepix Ibex, my graphics card (an ATI Radeon HD 3650) will start in low graphics mode. I use the fglrx driver provided by Canonical. I can set my max resolution to 1650x1080. However, after this is where I encounter my first problems:

Whenever I begin to play a movie using VLC, I noticed some tearing, which is caused by problems with the vertical refresh and the screen. I've followed several instructions found on the forums, such as changing the video output to OpenGL, which seems to fix the problem albeit at a cost: some scenes have a bit of less than one second stuttering. However, after changing some other video options, such as using X11(no Xv), video tearing is noticeable when playing flash videos.

I've also tried installing the latest ATI driver but that hasn't worked, video tearing is visible and the tearing seems to be more of a problem with X than the card driver. Is there anything else I can do to fix my problem or should I wait for Ubuntu's next release, which will have hopefully fixed this problem by default?

Alternatively, do Nvidia video cards, such as the 8000 and 9000 series suffer from the video tearing problem under Intrepid Ibex (with the Canonical provided drivers for those cards) like the one I described above?[/SIZE]

---

### Post by grizlo42 on 2009-07-13
[http://ubuntuforums.org/showthread.php?t=1203437](http://ubuntuforums.org/showthread.php?t=1203437)

---

### Post by da01 on 2011-05-13
In Ubuntu 11.04, (Natty), the problem also shows up when you choose "Ubuntu Classic (No Effects)" from the login menu. The other options (Ubuntu, Ubuntu Classic) should be free from the tearing problems.

(I'm using onboard graphics, ATI Radeon HD 3000, on the GIGABYTE GA-MA78LMT-S2 motherboard. 60Hz Refresh.)

---

