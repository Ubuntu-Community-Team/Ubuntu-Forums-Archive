---
title: "Can't open music, video (VLC and flash) after update on ubuntu 10.04"
date: 2014-06-12
forum: Multimedia Software
---

### Post by Tet_Juniper on 2014-06-12
Hullu, I just had a major update after 8 months of not using this machine (asus k50c with ubuntu 10.04), and after the update I can't open application such as VLC, Audacious, flash on the net,  games, and other. The applications in question starts loading, but after a few seconds they disappear and wont run. VLC and rythmbox runs, but the programs freezes instantly upon opening a file.    What I've done so far is to reinstall the graphics driver, but no luck there. I've also tried use the synaptic history to try to find out what happened during the update, but since the update involved a more than 100 mb of updates and new packages I can't really tell where to start looking.  My guess is that something that is required run these application has been deleted during the update, but I can't tell at the moment and I don't know how to find out.    Questions for the community: Is there any way to go back to a previous point before the update?  How do I find out what is wrong here? Shall I copy a list of the updated and fresh packages that came with the update (it's long!)?

---

### Post by Yellow Pasque on 2014-06-12
It's an issue with the last kernel update: [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1327300](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1327300)

Boot into previous kernel (2.6.32-60) until it's sorted.

---

### Post by Bucky Ball on 2014-06-12
Will it be sorted? I thought 10.04 LTS had been unsupported for over a year. Either way, perhaps a supported release might be something to think about. Things will probably only get worse, not better, and there hasn't been any security updates for quite some time (unless you're using the server version).

Temüjin's suggestion of booting into an earlier kernel is a good one. My guess is that some of the apps that were updated are too recent for that release, especially if you have third-party repositories you have manually added to your sources. :-k

---

### Post by Yellow Pasque on 2014-06-12
Lucid Server (and included packages, such as kernel) is supported with security updates until 2015.

---

### Post by Bucky Ball on 2014-06-12
> **Temüjin said:**
> Lucid Server (and included packages, such as kernel) is supported with security updates until 2015.

I'm aware of that, but OP makes no mention of using the server version. ;)

You mean the server updates are also going to the regular 10.04 LTS desktop version?

---

### Post by Yellow Pasque on 2014-06-12
> **Bucky Ball said:**
> You mean the server updates are also going to the regular 10.04 LTS desktop version?

Yes ;)

---

### Post by Bucky Ball on 2014-06-12
Useful, and interesting, information.

---

### Post by mörgæs on 2014-06-12
- but all GUI packages lost support more than a year ago. Original poster should consider a fresh install of one of the 14.04's.

---

### Post by Bucky Ball on 2014-06-12
> **mörgæs said:**
> - but all GUI packages lost support more than a year ago. Original poster should consider a fresh install of one of the 14.04's.

These are my thoughts. Somethings gotta give eventually ... perhaps now ...

Seen a lot of 10.04 issues today, though, so perhaps current kernel, as suggested earlier. :-k

---

### Post by Tet_Juniper on 2014-06-13
Shazzam, dudes. I booted into kernel 2.6.32-52 ('cus it was the latest I had apart from the new ****** one), and it works like a blast.   When summing up the responses I think I hear that 10.04 is outdated soon or already - What suggestions for the future do you have? Another system? Please have in mind that I'm using an old and tired machine here... :)  Wow, I'm absolutely grateful to find help. 10+ internet karma to you all!

---

### Post by Bucky Ball on 2014-06-13
All depending how low the computer specs, Lubuntu 12.04 or perhaps Xubuntu 12.04 would be the lightest. You could try the 14.04 releases of both also, see what works. Download the ISOs, burn to disk/USB, boot from the disk/USB, choose the option 'Try Lubuntu/Xubuntu', whichever you're running, and give it a try. See if things work ok. 

Best to post a new thread with a descriptive title for advice on this, though, as this thread has nothing to do with it. ;)

PS: Staff are currently discussing whether we should be providing support for EOL (end-of-life) releases at all on these forums. I'd backup your valuable data and have a think about what you might do. The longer you leave it the more of a security vulnerability your machine becomes if it is online. Not to mention any other issues which might crop up. 

Personally, I have no idea why they would port server kernels to the 10.04 LTS desktop version, but there ya go ... just confuses the issue.

---

### Post by mörgæs on 2014-06-13
Lubuntu 12.04 is not an option as it's also unsupported.

There is advice regarding old hardware in the link in my signature.

---

### Post by Bucky Ball on 2014-06-13
> **mörgæs said:**
> Lubuntu 12.04 is not an option as it's also unsupported.

Of course. Lubuntu 14.04 LTS it is, then! Thanks for the correction. ;)

---

### Post by bapoumba on 2014-06-15
Thread closed as per : [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

