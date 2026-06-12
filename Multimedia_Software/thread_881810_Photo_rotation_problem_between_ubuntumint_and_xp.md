---
title: "Photo rotation problem between ubuntu/mint and xp"
date: 2008-08-06
forum: Multimedia Software
---

### Post by magicpl on 2008-08-06
I experienced the strangest problem.

I downloaded pictures from my camera CF card, resized them, 
put a copy on company's network with xp computers on it and:

Viewing the pictures from the network share: (on 2003 server)
- On linux all pictures show up PROPERLY ROTATED, just like they always were (I didn't rotate them)
- From XP they show up NOT ROTATED (all with the same orientation), no matter what program I try

Like there's some meta information that xp doesn't recognize..

or maybe linux stipped some information that windows is looking for..

First time noticed such issue.. couldn't find help anywhere..

Anyone experienced similar issue? Any ideas what to do (I don't want to rotate already properly rotated pictures again on xp - now and in the future)

I resized pictures using little linux resizer script before I brought them to work.. maybe that could be the problem.. 

Anyone?

PS. Found location of that resizer script I use at home:
[http://aaron.instantspot.com/blog/2007/04/30/Batch-image-resizing-in-Ubuntu](http://aaron.instantspot.com/blog/2007/04/30/Batch-image-resizing-in-Ubuntu)
It uses imagemagick and zenity packages

-------------------
I'm running:

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

$ cat /etc/issue
Linux Mint 5 Elyssa \n \l

---

### Post by perce on 2008-08-06
Somehow (some) Linux programs understand when a picture has the wrong orientation and automatically rotate them. It's possible to disable this feature on Nautilus, rotate the picture manually and save it again with the right orientation. Or you can try to rotate them in XP, I think Linux should be able to understand the change (maybe make a backup copy of the first picture you try to be 100% sure).

---

### Post by magicpl on 2008-08-07
It really seems that the pictures are saved the way xp sees them - not rotated.. and that there is some meta data that ubuntu recognizes to rotate them..

I really would like to find out how to make windows understand the orientation.

I will make few more tests.. I'm suspecting the resizing script I mentioned.

I would really appreciate if anyone let me know if they experienced similar problem.. and if they solved it..

Thanks..

---

