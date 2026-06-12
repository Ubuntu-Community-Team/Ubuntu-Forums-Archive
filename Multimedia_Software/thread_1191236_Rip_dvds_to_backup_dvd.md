---
title: "Rip dvds to backup dvd"
date: 2009-06-18
forum: Multimedia Software
---

### Post by inphektion on 2009-06-18
I used to use windows and rip my dvds to .avi to store on my xbmc server.  This way my kids couldn't thrash the originals.  However now that we have a minivan that plays dvds i want to make a backup dvd to use and keep the original away.  What programs in ubunut can I use for this?

---

### Post by Revolutionary101 on 2009-06-18
You should be able to use Brasero. 

It comes with Ubuntu so you shouldn't have to download anything.

I have used it to back up my Windows XP install disc. Although I have not tried it to backup DVDs. Tell me if it doesn't work.

---

### Post by SerenityKill3r on 2009-06-18
> **inphektion said:**
> I used to use windows and rip my dvds to .avi to store on my xbmc server.  This way my kids couldn't thrash the originals.  However now that we have a minivan that plays dvds i want to make a backup dvd to use and keep the original away.  What programs in ubunut can I use for this?

Brasero, you can use it to create a 1:1 copy of a DVD.

---

### Post by Revolutionary101 on 2009-06-18
Yes but if you are making a 1:1 copy of a DVD to a DVD wouldn't you have an exact copy?

---

### Post by inphektion on 2009-06-19
What about backing up a disney dvd.  in windows you can use anydvd/clonedvd.  anything in ubuntu or no?

---

### Post by Revolutionary101 on 2009-06-19
Use either Brasero or this program called AcidRip which you can find in Add/Remove programs.

Although AcidRip encodes the DVD to play on your computer's hard drive.

If you use Brasero just make an ISO file then burn it to another DVD.

Hope it works.

---

### Post by yavez on 2009-06-19
Shrinkta to backup the DVD (strip the CSS protection and put it on your HD as an .ISO file, also to strip out unwanted video/audio and shrink the result down to a DVD5 size)

Any CD/DVD burning software like Brasero or Nautilus's built in .ISO burning capabilities to burn to DVD.

Shrinkta for Jaunty is available here: [https://launchpad.net/~c4pp4/+archive/ppa/+sourcepub/632508/+listing-archive-extra](https://launchpad.net/~c4pp4/+archive/ppa/+sourcepub/632508/+listing-archive-extra)

You will also need libdvdcss2 to decode any DVD with CSS protection.  You can get it from the Medibuntu repositories, guide here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So the process is:

DVD > Shrinkta > .ISO > BURN :)

---

### Post by smarcellus on 2009-06-22
Hi, I am new to Linux and installed Ubuntu Jaunty. I am only lacking a couple things to get rid of my windows OS. One is I have been trying to install Shrinkta, but I get an error.

dpkg: error processing /var/cache/apt/archives/shrinkta_0.1.12-0~getdeb1ubuntu1~ppa1~jaunty2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdvd.a', which is also in package shrinkta-devel
Errors were encountered while processing:
 /var/cache/apt/archives/shrinkta_0.1.12-0~getdeb1ubuntu1~ppa1~jaunty2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone know how to correct this. I changed my libdvd.a to libdvd.a.backkup but still get this error. I believe it is because of the directory security.

---

### Post by smarcellus on 2009-06-22
I uninstalled shrinkta-devel, Shrinkta seemed to install but I can not find it in my menus or anywhere.

---

### Post by yavez on 2009-07-08
Sorry for this ridiculously late reply, but it's called DVD Movie backup or something similar in the Ubuntu menu.  Don't know why.  Hope that it helps and it wasn't too late :)  You can also call it from the commandline by typing: shrinkta

---

### Post by yavez on 2009-07-08
> **smarcellus said:**
> Hi, I am new to Linux and installed Ubuntu Jaunty. I am only lacking a couple things to get rid of my windows OS. One is I have been trying to install Shrinkta, but I get an error.

dpkg: error processing /var/cache/apt/archives/shrinkta_0.1.12-0~getdeb1ubuntu1~ppa1~jaunty2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdvd.a', which is also in package shrinkta-devel
Errors were encountered while processing:
 /var/cache/apt/archives/shrinkta_0.1.12-0~getdeb1ubuntu1~ppa1~jaunty2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone know how to correct this. I changed my libdvd.a to libdvd.a.backkup but still get this error. I believe it is because of the directory security.

Also, just download the Shrinkta i386 package from the link I gave above and double click when downloaded.  GDEBI will open and ask to install some more files to get it installed.

---

### Post by smuggly on 2009-07-09
You Can Use DVD 9 to 5 Or Rip To Avi With Acid Ripper Or A Bunch I Use Dvdrip.You Need libdvdcss And libreaddvd Or Something Like That.The Last One The Name Escapes Me Right Now.

---

