---
title: "Problems burning DVDs"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by 01steven on 2008-01-20
Am running Gutsy Gibbon.
I recently bought an external DVD writer.
Had no problems writing to it and watching videos I'd burnt on a standalone DVD player.
This was done through Gnome's CD/DVD Creator application.

Now I'm encountering diffculties. It looks like the burning process is working, but just after it reaches 100% as the dialog box says it's burning the image, I get another dialog box pop up which says:

[I]Insert a rewritable or blank disc

Please put a disc, with at least 461.8 MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW[/I]

(the numbers obviously change depending on what I am burning, and most of the time the disc types aren't there. I am using DVD + RW and like I said I've not had a problem up till now.

Can anyone help?

---

### Post by pytheas22 on 2008-01-20
I can't offer any specific help but I would recommend trying to burn your image to DVD by using k3b (available through Synaptic) instead of Gnome CD/DVD Creator.  I've had some issues in the past with the latter not recognizing that I had media in the drive, but k3b never gives me a problem.

---

### Post by disturbed1 on 2008-01-21
> **pytheas22 said:**
> I can't offer any specific help but I would recommend trying to burn your image to DVD by using k3b (available through Synaptic) instead of Gnome CD/DVD Creator.  I've had some issues in the past with the latter not recognizing that I had media in the drive, but k3b never gives me a problem.

K3B is only another gui for the same underlying tools that Gnome's CD/DVD burner uses.

Is the image/files your attempting to burn over 4gig in size? If so this is a bug in the current CD/DVD writing tools wodim, growisofs, and genisoimage. To get around it, create the image with mkisofs and burn the image with cdrecord from the command line.

---

### Post by puneit on 2008-01-22
I am facing a similar problem. I have a Philips External DVD Burner. It used to work fine in the days of Dapper, Edgy Eft and Feisty Fawn. I did not burn DVDs for quite some time, but now when I am trying to do it, the burner in Gusty is not identifying a blank CD/DVD. Though I can still burn CDs and DVDs using the same burner in Windows. I have tried Brasero K3B. There seems to be some problem somewhere. If anyone has a solution to it, please help out!
Edit: Nautilus detects a blank DVD and puts its icon on the desktop upon inserting a blank DVD. CD/DVD read operations are working fine

---

