---
title: "Hercules Deluxe Optical Glass Webcam - Ubuntu Jaunty"
date: 2009-07-31
forum: Multimedia Software
---

### Post by surelock22 on 2009-07-31
Hey guys,
Got a Hercules Deluxe Optical Glass Webcam (pretty sweet little cam for less than $30 delivered) for my Windows Laptop. Looking to get it to work for my desktop (Ubuntu Jaunty) too. Can it happen? 

Thx 4 hlp.

---

### Post by Mdyter on 2009-08-07
i got today one too. 
who can say how to make it work?

---

### Post by dutchlady123 on 2009-08-09
Many thanks to ur post. I love it.




[[color=#FFFFFF]_demande simulation pret personnel en ligne_[/color]](http://simulationpretpersonnel.com)[color=#FFFFFF] - Pret personnel en ligne et de comparer les meilleurs taux afin de... La demande de prêt personnelen ligne[/color][[color=#FFFFFF]_demande simulation pret personnel en ligne_[/color]](http://simulationpretpersonnel.com)

---

### Post by sinozzuke on 2009-09-02
> **surelock22 said:**
> Hey guys,
Got a Hercules Deluxe Optical Glass Webcam (pretty sweet little cam for less than $30 delivered) for my Windows Laptop. Looking to get it to work for my desktop (Ubuntu Jaunty) too. Can it happen? 

Thx 4 hlp.

Think it uses gscpa_sonixj driver, if your lsusb drop you ID 06f8:3008 Guillemot Corp.

I wasn't able to install it couse modprobe says me:

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

And I don't know what to do. I have readen this is a bug, and I know it's solved somehow, but I can't find how! Any clue?:P

---

### Post by sinozzuke on 2009-09-25
> **sinozzuke said:**
> Think it uses gscpa_sonixj driver, if your lsusb drop you ID 06f8:3008 Guillemot Corp.

I wasn't able to install it couse modprobe says me:

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

And I don't know what to do. I have readen this is a bug, and I know it's solved somehow, but I can't find how! Any clue?:P

Well, renaming /etc/modprobe.d/oss-compat to /etc/modprobe.d/oss-compat.conf fixed the problem of the modprobe error.

But now I use 
sudo modprobe gspca_sonixj 
sudo modprobe gspca_main

then I plug the camera and open Cheese and no camera detected
:(

---

### Post by surelock22 on 2009-09-27
This is just going to be one of those: chalk it up to hardware compatability. Shoulda, coulda, woulda. My stepdaughter is using it on her HP 'netbook (which has one built in BTW), but the Hercules is alot nicer, and it has the built in, ultra bright LED's. I won't class this as solved being that people are still trying to get it to work....

---

### Post by sinozzuke on 2009-09-27
> **surelock22 said:**
> This is just going to be one of those: chalk it up to hardware compatability. Shoulda, coulda, woulda. My stepdaughter is using it on her HP 'netbook (which has one built in BTW), but the Hercules is alot nicer, and it has the built in, ultra bright LED's. I won't class this as solved being that people are still trying to get it to work....

Didn't catch you surelock22... Is this solved? Think not, my webcam is the same of your stepdaughter's and doesn't work. How wants to class this as solved?

I'm just saying that my webcam, as yours have and ID and terminal can says you what ID is. You do it by typing at terminal with the webcam plugged

lsmod

You type this and it says the ID of your camera. This is the chip name. If 2 cameras look the same outside, inside can have different chipsets.
I'm not a guru, not a programmer, just an user. But, I read posts and do what they say. 

First you need to know what chipset is for knowing what driver to use. If is there some driver for you (or us)

;)

---

