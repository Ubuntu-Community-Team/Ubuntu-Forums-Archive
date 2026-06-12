---
title: "How to scan negative/film on Linux?"
date: 2014-08-24
forum: Multimedia Software
---

### Post by satimis on 2014-08-24
Hi all,

AMD 8-core cpu
32G RAM
1024M VRAM
Epson Perfection 3490 photo scanner
xsane
Host	Ubuntu 12.04 desktop 64bit
Virtualizer  Oracle VirtualBox

This is my first time scanning negative/film on Linux.  Neither I have a Windows machine here.  My old Epson scanner still works without problem on scanning photos.

Click Negative: Invert colors for scanning negatives button
Adjust  Autoadjust gamma/brightness/contrast button

all without effect.

The scanned file is attached to this posting.

Please advise how to scan negative/film with xsane?  Thanks

(I have considered installing Windows on a VM but I have no experience making a scanner working on it)

Regards
satimis

---

### Post by kurt18947 on 2014-08-24
We have a Canon 8800F so our situation might be different from your own.  We found sane worked very well for photos.  It didn't work well at all for slides and negatives because sane didn't activate the Canon's backlight in the lid.  We downloaded an evaluation copy of VueScan from hamrick.com.  It worked perfectly once we purchased a license.  The evaluation mode puts a watermark on scanned images but will tell you whether VueScan will work for you or not.

---

### Post by satimis on 2014-08-24
> **kurt18947 said:**
> We have a Canon 8800F so our situation might be different from your own.  We found sane worked very well for photos.  It didn't work well at all for slides and negatives because sane didn't activate the Canon's backlight in the lid.  We downloaded an evaluation copy of VueScan from hamrick.com.  It worked perfectly once we purchased a license.  The evaluation mode puts a watermark on scanned images but will tell you whether VueScan will work for you or not.
Hi,

Thanks for your advice.

Before posting I have searched VueScan a while.
VueScan Scanner Software
[http://www.hamrick.com/](http://www.hamrick.com/)

Supported scanners:
[http://www.hamrick.com/vuescan/vuescan.htm#supported](http://www.hamrick.com/vuescan/vuescan.htm#supported)
Epson Perfection 3490 is on the list.

Download file - vuex3294.tgz

I hesitate to install it on the host for testing because I have no confidence to delete it after testing.  Can I try it on VM?  I'm not experienced to make VM connecting the scanner via the virtual USB.

How long can I try before paying the licence?  Thanks

Regards
satimis

---

### Post by ajgreeny on 2014-08-24
You do not have to install vuescan, you simply run it from the executable that is in your download.

---

### Post by satimis on 2014-08-24
> **ajgreeny said:**
> You do not have to install vuescan, you simply run it from the executable that is in your download.
Hi,

Thanks for your advice.

Whether after untar vuex3294.tgz the executive is there?  Run it on terminal and it will detect the scanner automatically? No setup is necessary?

Regards
satimis

---

### Post by ajgreeny on 2014-08-24
In my unregistered copy of vuescan 9.2.11, which I just extracted to my Downloads folder and put in a folder named Vuescan there are three files, vuescan,  vuescan.8ba and  vuescan.ds.

The first named vuescan is the executable; just double click it and it should start.  I can not remember whether or not I had to run command ```
chmod =x Downloads/Vuescan/vuescan
``` to make the file executable, but I don't think I did; I believe it is executable when extracted.

---

### Post by satimis on 2014-08-25
> **ajgreeny said:**
> In my unregistered copy of vuescan 9.2.11, which I just extracted to my Downloads folder and put in a folder named Vuescan there are three files, vuescan,  vuescan.8ba and  vuescan.ds.

The first named vuescan is the executable; just double click it and it should start.  I can not remember whether or not I had to run command ```
chmod =x Downloads/Vuescan/vuescan
``` to make the file executable, but I don't think I did; I believe it is executable when extracted.
Hi,

Your advice works for me, not necessary running 'chmod'.

Now I have the negative scanned, size 4x6.  My old Epson scanner did the job.  But  I have no way converting the negative to postive on GIMP.  

I found;
How to convert color negatives with GIMP (on YouTube)
[https://www.youtube.com/watch?v=Ifwz7vxm4Mc](https://www.youtube.com/watch?v=Ifwz7vxm4Mc)

But I couldn't read the menu bar, including drop-menu.  The font is too small.  Can you help?

Thanks

Regards
satimis

---

### Post by satimis on 2014-08-25
Hi all,

Further to my late posting I found following 2 interesting video

1)
How to make digital photos from film negatives
[https://www.youtube.com/watch?v=iMO50AlGyrw](https://www.youtube.com/watch?v=iMO50AlGyrw)

2)
How to Scan Film Negatives on iPad 
[https://www.youtube.com/watch?v=QUO4Wida_wY](https://www.youtube.com/watch?v=QUO4Wida_wY)

Should it work I'll use the money for purchasing a new scanner to buy a quality camera.  Because after scanning all old negatives the scanner will retire.  I don't think I'll use it any more.

I'll make a test with my Sony digital camera.  Fix the negative on the window door of a book shelves and put a LED Flexible Light Strip behind to take a picture.  I'll come back if successful.

I must refresh my memory on GIMP.  I haven't doing graphic editing for long time.


Regards
satimis

---

