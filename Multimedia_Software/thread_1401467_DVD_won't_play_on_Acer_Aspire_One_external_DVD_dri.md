---
title: "DVD won't play on Acer Aspire One external DVD drive"
date: 2010-02-08
forum: Multimedia Software
---

### Post by qprfact on 2010-02-08
My son has an Acer Aspire One running Ubuntu, and has VLC installed.

As this machine doesn't have a DVD drive, he has an external LiteOn DVD multiformat drive.

He decided last night he wanted to watch Paul Blart Mall Cop (he's only 8!). The DVD went in the drive, the DVD showed on the desktop, and the message came up about "Open with VLC". Which we tried - and VLC closed.

I tried various other ways to get the disk to play - opening VLC and then choosing disk, double clicking on mounted icon on desktop, none would work.

I then installed Totem Movie Player to see if that would cope any better. It didn't.

The one thing I am wondering is about region - we have used the DVD drive in the past to play region free DVDs that I had burned myself, but this may be the first time we have tried one with region encoding.

Could that be it? If so, how do I determine in Ubuntu what region I have and how can I amend it if necessary?

Thanks in advance

---

### Post by wilee-nilee on 2010-02-08
You probably need the medibuntu codecs, just run the command to install the repositories and keys then go to synaptic and tick w32codes and nonfree and libdvdcss2 for installation.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Also install the ubuntu restricted extras in synaptic.

---

### Post by golusweet on 2010-02-08
I think, DVD is encrypted.

You need to add medibuntu's repository, and install libdvdcss2 package.

Add repository first using 

 sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Then

sudo apt-get install libdvdcss2

---

### Post by qprfact on 2010-02-08
Thanks! I will try your suggestions tonight!

---

### Post by qprfact on 2010-02-08
Worked like a dream! These forums are so great - thanks!

---

