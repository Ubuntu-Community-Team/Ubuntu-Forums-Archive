---
title: "New Install Lockup Issue"
date: 2011-01-28
forum: Mythbuntu
---

### Post by jm2299 on 2011-01-28
I'm trying to install Mythbuntu 10.10 to a new computer I just built - Core i3, GT 240, 4 GB RAM, 3 SATA HDDs, ASUS MB.  It looks as though it is going to start up, but before it leaves the screen with Mythbuntu in the center along with the progress dots it locks up and the screen shows black and white squares.  I've downloaded it twice and verified that the iso was not corrupt.  The lockup screen looks like this:
[IMG]http://i54.tinypic.com/2ezodqh.jpg[/IMG]
Any thoughts?  Thanks.

---

### Post by nhtrader on 2011-01-28
If I were in your shoes, I would assume that my hardware works and my next attempt would be to download and install a simple version of ubuntu or [http://www.linuxmint.com/](http://www.linuxmint.com/)

Plus if the ubuntu version installs properly, then you can simply install MythTV.
The same CD that you burned would allow you to install just MythTV.

However if this fail, then I would assume that I have a hardware problem and I would check/jiggle all of the connections/jumpers once again.

---

### Post by BicyclerBoy on 2011-01-28
To help debug..
Try running a Ubuntu install CD as 'live CD'.

You can try changing the BIOS video adapter initialization order..
i.e. try i3 GPU first (very poor performance but will work)
Then try PCIe (your GT240) video first/primary/only

---

### Post by jm2299 on 2011-01-28
I don't get to a point where I have the option to select anything.  My mainboard doesn't have integrated video so I don't have a way to check that out either. 

I also tried (as nhtrader suggested) to just download standard ubuntu desktop and I get the exact same result.  I don't have any extraneous hardware installed here, seems like a video card driver issue to me but I don't have the option to change anything before install.

Anxious to get this up and running, wanted to go the linux route but this may push me towards windows - I've never had this problem installing any version of windows.



> **BicyclerBoy said:**
> To help debug..
Try running a Ubuntu install CD as 'live CD'.

You can try changing the BIOS video adapter initialization order..
i.e. try i3 GPU first (very poor performance but will work)
Then try PCIe (your GT240) video first/primary/only

---

### Post by jm2299 on 2011-01-28
Ok, finally figured it out.  Running the nomodeset option fixed it.  Turns out I'm not the only person who has had this issue, see this thread:

[http://ubuntuforums.org/showthread.php?t=1600807](http://ubuntuforums.org/showthread.php?t=1600807)

Thanks to those who responded!

---

### Post by BicyclerBoy on 2011-01-29
AFAIK Are you trying to use the integrated video adapter in the i3 CPU ?

 In the BIOS you can change the video boot order to PEG first (PciExpressGraphics).
Then you get to use the GT240..

Edit:
I think I see how your soln works.. 
I think this nomodeset fixes a problem that has root cause in the nouveau kernel module.
Nomodeset stops the nouveau kernel module from blocking the nvidia driver. The possibly more correct approach is blacklisting the nouveau driver.

---

### Post by jm2299 on 2011-01-29
Unless I am misunderstanding something your motherboard has to support the integrated video in the i3.  Apparently ASUS decided it wasn't necessary in this particular mainboard, which was unfortunate.

-Jason

> **BicyclerBoy said:**
> AFAIK Are you trying to use the integrated video adapter in the i3 CPU ?

 In the BIOS you can change the video boot order to PEG first (PciExpressGraphics).
Then you get to use the GT240..

Edit:
I think I see how your soln works.. 
I think this nomodeset fixes a problem that has root cause in the nouveau kernel module.
Nomodeset stops the nouveau kernel module from blocking the nvidia driver. The possibly more correct approach is blacklisting the nouveau driver.

---

### Post by BicyclerBoy on 2011-01-29
Is that right...

That mobo must be real cheap or maybe they understand the i3 IGP is not very good.

---

