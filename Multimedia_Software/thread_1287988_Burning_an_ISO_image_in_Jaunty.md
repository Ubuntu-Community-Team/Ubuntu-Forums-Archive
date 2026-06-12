---
title: "Burning an ISO image in Jaunty"
date: 2009-10-10
forum: Multimedia Software
---

### Post by fidelandche on 2009-10-10
Hi I have already searched the forums for an answer but I am unsure if what I have found will work. I want to give PCLinuxOS a try, so have downloaded the image from a mirror, inserted a CD went to burn with Brasreo, it checked the disk first, then it burnt the image to the disk, it then checked the image and that is where the problem begain. It got to about 5% from the end when the tome remaining increased from 45seconds to 18hours:confused: No idea why, so I had to cancel the burn.
 
I have already had problems with Brasreo trying to burn media CD's, it just would not do it. So how do I go about burning this ISO image??
 
Do I follow this guide?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
Or is there another way??
 
Is the method on this guide to check the MD5SUM ok to use to check PCLinuxOS?
 
Many thanks.

---

### Post by Vibin Lakshman on 2009-10-10
> **fidelandche said:**
> Hi I have already searched the forums for an answer but I am unsure if what I have found will work. I want to give PCLinuxOS a try, so have downloaded the image from a mirror, inserted a CD went to burn with Brasreo, it checked the disk first, then it burnt the image to the disk, it then checked the image and that is where the problem begain. It got to about 5% from the end when the tome remaining increased from 45seconds to 18hours:confused: No idea why, so I had to cancel the burn.
 
I have already had problems with Brasreo trying to burn media CD's, it just would not do it. So how do I go about burning this ISO image??
 
Do I follow this guide?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
Or is there another way??
 
Is the method on this guide to check the MD5SUM ok to use to check PCLinuxOS?
 
Many thanks.

Normally that procedure you did should work , please check its md5 or sha checksum , from terminal command md5sum your_iso_file , or try with k3b application to burn an iso file

---

### Post by fidelandche on 2009-10-10
Is K3b ok with Gnome?? I was under the impression that it works only with KDE?? Also if it does work with Gnome do I just download it from the site or is it in synaptic??

---

### Post by mikewhatever on 2009-10-10
I just right click on the iso and select Burn to Disk.

---

### Post by onespeedbiker on 2009-10-10
> **fidelandche said:**
> Hi I have already searched the forums for an answer but I am unsure if what I have found will work. I want to give PCLinuxOS a try, so have downloaded the image from a mirror, inserted a CD went to burn with Brasreo, it checked the disk first, then it burnt the image to the disk, it then checked the image and that is where the problem begain. It got to about 5% from the end when the tome remaining increased from 45seconds to 18hours:confused: No idea why, so I had to cancel the burn.
 
I have already had problems with Brasreo trying to burn media CD's, it just would not do it. So how do I go about burning this ISO image??
 
Do I follow this guide?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
Or is there another way??
 
Is the method on this guide to check the MD5SUM ok to use to check PCLinuxOS?
 
Many thanks.The  BurningIsoHowto is a good guide. A short cut to using Nautilus (CD/DVD Creator) is to simply double click on an .iso file (after inserting a blank CD and canceling the first CD/DVD Creator window) and you should get a "Write To Disc" window that will burn the contents of an .ISO file to a CD/DVD (just click on the Write button). If you get any errors, try slowing down the burn speed from the drop down menu under "Write Options". I used this method to create a Windows boot disc and it worked great. 

AS far as checking the MD5SUM, I would assume it would work as long as you have the corresponding hash; I found this [http://distro.ibiblio.org/pub/linux/distributions/texstar/pclinuxos/live-cd/english/preview/](http://distro.ibiblio.org/pub/linux/distributions/texstar/pclinuxos/live-cd/english/preview/) in case you need it.

Brad


Edit: Added; If you like command lines you can use $ growisofs -Z /dev/scd0=yourfile.iso ;where "scd0" is your burner and "yourfile.iso" is your iso file (usually ubuntu will find the iso file if it is in your Home Folder; if not or if it is in another directory, make sure you give the path to your iso file).

---

### Post by fidelandche on 2009-10-10
Thanks Brad,
 
   Maybe a silly question, but how do I go about finding the correct hash from this site??
 What is the best speed to write an ISO?? I cannot remeber what speed I used when I burnt Jaunty as I was using windose at the time.

---

### Post by fidelandche on 2009-10-11
Ok many thanks for the information, I will try all that once I get home from work in the morning.

---

### Post by onespeedbiker on 2009-10-11
> **fidelandche said:**
> Thanks Brad,
 
   Maybe a silly question, but how do I go about finding the correct hash from this site??
 What is the best speed to write an ISO?? I cannot remember what speed I used when I burnt Jaunty as I was using windows at the time. 1. I have always had good luck with 4x, which is the default speed for most DVD+RW discs. CD-R can burn very fast, but with only 700 mb, even with 4x the burn is less than 5 minutes. 

2.It would depend on which version of  PCLinuxOS you are going to install; i.e. if you choose pclinuxos -2009.2, you would choose the appropriate ISO file to download. Then all you need to do is double click on same file with a .md5sum extention and it will give you the hash for that iso program. Happy Burning !
[URL="http://distro.ibiblio.org/pub/linux/distributions/texstar/pclinuxos/live-cd/english/preview/pclinuxos-2009.2.iso"]
[/URL]

---

### Post by alms66 on 2009-10-11
> **mikewhatever said:**
> I just right click on the iso and select Burn to Disk.
Ditto...:guitar:

---

### Post by buldozerceto on 2009-10-11
I use k3b it is the best cd recording linux software!

---

### Post by areskz on 2009-10-11
I also had problems with Brasero. It did not burn cd at all. So, it showed the burning process, it was even finished without mistakes, but there was nothing on the cd after that. Simulation box was not tick.

---

