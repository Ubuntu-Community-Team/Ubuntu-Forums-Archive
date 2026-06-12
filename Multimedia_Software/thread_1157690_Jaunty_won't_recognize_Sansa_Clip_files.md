---
title: "Jaunty won't recognize Sansa Clip files"
date: 2009-05-13
forum: Multimedia Software
---

### Post by joshua neff on 2009-05-13
Since upgrading to Jaunty, I can't get my machine to see the MP3s already loaded on my Sansa Clip. Before the upgrade, I had no problem. Now, I can load MP3s onto the clip, but it won't see the files already loaded. Which means I have no way of deleting the MP3s already there, from before the upgrade. Has anyone else had this problem?

---

### Post by robertj20112 on 2009-05-17
> **joshua neff said:**
> Since upgrading to Jaunty, I can't get my machine to see the MP3s already loaded on my Sansa Clip. Before the upgrade, I had no problem. Now, I can load MP3s onto the clip, but it won't see the files already loaded. Which means I have no way of deleting the MP3s already there, from before the upgrade. Has anyone else had this problem?

Absolutely!  Have 2 Sansa clips and the Jaunty file browser will not recognize the installed music on either.  Finally resorted to a workaround: re-installed a copy of Hardy Heron on one of my computers just for the purpose of managing my music on the clips!  Still works fine in Hardy -- copy and paste, delete music files in the file browser with no problem.  Can't imagine what caused this problem but hope it gets corrected in the next LTS version of Ubuntu.

---

### Post by joshua neff on 2009-05-17
*sigh* I wish I had another computer I could install Hardy or Intrepid on. I really hope some solution comes out before the next upgrade!

Thanks!

---

### Post by robertj20112 on 2009-05-17
> **joshua neff said:**
> *sigh* I wish I had another computer I could install Hardy or Intrepid on. I really hope some solution comes out before the next upgrade!

Thanks!

If you have enough space on your hard drive, you can install Hardy on a separate partition on the same computer.  GPartEd Live will allow you to create the partition without messing up your existing installation.  Then you will have a dual-boot configuration on the one computer.  Let me know if you want to pursue this and maybe I can help.

---

### Post by robertj20112 on 2009-06-15
> **joshua neff said:**
> *sigh* I wish I had another computer I could install Hardy or Intrepid on. I really hope some solution comes out before the next upgrade!

Thanks!

I think I have the answer to your problem now: change the USB mode on the Clip.  Select the main menu, down-click to Settings, right-click the wheel, down-click to USB Mode, right-click to show the modes (it is probably on Auto Detect), down-click to MSC.  Now when you connect the Clip to your computer it will show up as another drive and the music will appear in the file browser.  This worked for both my Clips.  Hope this helps you.:D

---

### Post by icheyne on 2009-06-20
I put some Sansa Clip instructions up [here]("https://help.ubuntu.com/community/SansaClip")

---

### Post by Cuba71 on 2009-09-30
As long as you keep using Nautilus to access your Sansa Clip, you should be ok.

You may be able to use Windows from My Computer screen and treating it as a mass storage device.  This is what the instructions that come with the device say.  (I have NOT tested this)

But if you decide to use Windows Media player you may run into problems because of MTP, a proprietary protocol.

---

### Post by joshua neff on 2009-10-06
robertj20112 and icheyne,

It worked! Thanks!

---

### Post by HankB on 2009-10-06
> **icheyne said:**
> I put some Sansa Clip instructions up [here]("https://help.ubuntu.com/community/SansaClip")Hi icheyne,
One thing you might add that may not be clear is the behavior of the Sansa device in MTP vs. MSC mode. If you attach the player in MTP mode and load music, those music files will not be visible if you later change to MSC mode. That is Sansa behavior and has little to do with the host OS(*). If the user wants to deal with files loaded in MTP mode, they need to switch back to MTP mode.

My Sansa Fuze (running v01.02.26 firmware) has three settings for USB configufration - MTP/MSC/Auto. I suspect that Auto could be troublesome going from one version of Ubuntu to another as the behavior of the USB stack could cause Auto to switch between MTP and MSC. I would suggest that users select either MTP or MSC as they prefer and avoid that difficulty in the future.

I would also suggest identifying which version of Sansa firmware your description pertains to as a Sansa upgrade could potentially invalidate the directions.

(*)The Sansa Auto USB setting will cause the Sansa to switch to MTP or MSC mode depending on what it thinks the host OS is. This may not be reliable for all hosts and could affect results.

---

### Post by HDave on 2009-10-24
Thanks for the tip on MSC mode...worked like a charm for me.  What I'd like to understand is how come this worked great in Intrepid, but regressed in Jaunty?!?! :confused:

---

### Post by bardictiger on 2009-11-03
> **robertj20112 said:**
> I think I have the answer to your problem now: change the USB mode on the Clip.  Select the main menu, down-click to Settings, right-click the wheel, down-click to USB Mode, right-click to show the modes (it is probably on Auto Detect), down-click to MSC.  Now when you connect the Clip to your computer it will show up as another drive and the music will appear in the file browser.  This worked for both my Clips.  Hope this helps you.:D

Thanks for this!  It worked in Karmic Koala too.

---

