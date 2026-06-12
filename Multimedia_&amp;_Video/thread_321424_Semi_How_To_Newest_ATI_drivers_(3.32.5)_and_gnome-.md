---
title: "Semi How To: Newest ATI drivers (3.32.5) and gnome-screensaver"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by djembe330 on 2006-12-18
EDIT: this is for the 8.32.5 driver! (incorrect thread name)

I am not sure if anyone else was having problems similar to mine, but here is a summary of what I experienced:

I have an X1400 ati mobility card in my dell 1505 running edgy.  I had the fglrx driver from the repos installed (8.28.8 ) and most things worked great (glxinfo and fglrxinfo gave correct outputs, etc).  3D apps worked, as well as the GL screensavers.

Unfortunately, it seems that 8.28.8 and xorg 7.1 dont play very nicely together since Xvideo is not supported with this configuration.  I read on ati's site that the newest driver (8.32.5) would fix this.  I use my laptop to watch movies and tv shows with TV-out quite often and the lack of Xv was noticable.

So I followed the directions here: [WIKI ATI howto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to install the latest drivers from the ATI website.  Everything went smoothly.....a little TOO smoothly;) 

Xvideo was now working!  But starting up gnome-screensaver on gl-matrix got horrible frame rates.  fglrxinfo and glxinfo still gave the correct responses though (direct rendering enabled with the fglrx 8.32.5 driver).  Strangely, some other 3d apps (nexuiz) worked just fine.

Since I figured it was a gl issue, I tracked the problem to the library /usr/lib/libGL.so.1.2

So I downloaded the 8.28.8 .deb from the edgy repos, extracted it, and found libGL.so.1.2

Then I copied this (while making a backup of the original!) to /usr/lib and updated the symlinked libGL.so.1 to match that libary.  Move the backup out of /usr/lib to somewhere like your desktop at this point and run "sudo ldconfig"

I restarted the X server and it actually worked!  Xvideo is still present (it still is running 8.32.5 drivers) but the gl stuff is working as it did before also!

I am going to go watch a movie on my now-working-flawlessly setup (crosses fingers 8) ).  If anyone wants more details (I know this is a bit of a messy post) about how I did this step-by-step, let me know.

---

### Post by nmincone on 2006-12-18
Have you rebooted since you changed/updated the driver? Restarting the x server doesn't necessarily reload the graphics driver.

---

### Post by djembe330 on 2006-12-19
Yes, I have rebooted twice now.  GL screensavers still humming along nicely and Xvideo is still enabled.  This is with fglrx 8.32.5 installed with the libGL.so.1.2 replaced with the version from fglrx 8.28.8 from the repos.

Hopefully this will continue working correctly.  If anyone has a more elegant fix, i am all ears; however, after searching through forums and google for a few days now I couldn't find any other solutions.

Tomorrow morning (EST) I will write out exactly what I did so if anyone else has the same problems they can follow.  For now it is sleep time!

---

