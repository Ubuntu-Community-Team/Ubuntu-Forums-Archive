---
title: "trouble installing an external multidrive"
date: 2010-01-22
forum: Multimedia Software
---

### Post by CKMBDavis on 2010-01-22
My apologies in advance as I'm new to this board. I've recently picked up a Toshiba Portable SuperMulti Drive which states that is compatible with Ubuntu. However, when I try to install LinDVD, it gives me the following message:
Error: Wrong architecture 'lpia'
Any ideas on what this means, or how I may go about getting this external drive to work? Thanks to all in advance.

---

### Post by PRC09 on 2010-01-22
Dont know to much about the lpia stuff but some info here....

[http://www.phoronix.com/scan.php?page=news_item&px=NzczOA](http://www.phoronix.com/scan.php?page=news_item&px=NzczOA)

---

### Post by CKMBDavis on 2010-01-22
Thanks for the info, although I'll admit to being quite clueless about what it all meant. Ultimately, I just need to know if that error message means there's no chance I can use that multidrive.
Thanks!

---

### Post by PRC09 on 2010-01-22
What machine are you trying to use this on and which version of Ubuntu?

---

### Post by adam814 on 2010-01-22
My guess is you have a .deb package for LinDVD and it's for the wrong architecture.  Post the output of this:
```
dpkg --print-architecture
```

The "lpia" architecture is optimized for the Intel Atom and related processors.  If it comes down to it you *should* be able to force the architecture and install an i386 package on an lpia system or vice versa (amd64 won't work).

---

### Post by CKMBDavis on 2010-01-22
I have Ubuntu 9.10 . The laptop I have is a fairly old Acer Aspire 3680. When I type "dpkg --print-architecture" it says i386. Nothing else. Not sure what other type of info you may need.

---

### Post by PRC09 on 2010-01-22
Does your machine recognise the drive when you try to use it for anything else.Maybe that version of LinDVD is looking for the lpia architecture only.Just a guess on my part.

---

### Post by adam814 on 2010-01-22
Yeah, your install is 32-bit Karmic.  The package you're trying to install is for lpia.  You *could* use "dpkg --force-architecture -i <LinDVDpackage>" where <LinDVDpackage> is the file you downloaded to install it, but they most likely also provide an i386 version.

If you're just wanting to watch a DVD you could just install VLC or MPlayer.  Both are popular and support almost any media format out there.

---

### Post by CKMBDavis on 2010-01-23
Yes, I have the VLC player and enjoy it. My main purpose for purchasing the Multidrive was for the DVD burner.

---

### Post by adam814 on 2010-01-23
Isn't LinDVD just another player?  If you want burning software why not try Brasero or K3B?

---

### Post by CKMBDavis on 2010-01-23
I suppose it is, and I certainly feel like a fool! I just assumed that LinDVD was necessary for the multidrive to work -I had yet to actually insert any discs in it. I do have Brasero already installed, so I will give it a whirl later on. Thanks so much "adam814", and "PRC09" for your helpful advice - it is much appreciated!

---

