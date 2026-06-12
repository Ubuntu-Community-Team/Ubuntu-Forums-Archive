---
title: "Can't rip or play DVDs -- at the end of my rope"
date: 2008-12-14
forum: Multimedia Software
---

### Post by BobSutan on 2008-12-14
I'm seriously in need of some expert help. I've spent 40 hours trying to figure out how to rip DVDs with 8.10 and I'm fed up. Someone, anyone, spoon feed me so I can do this already. 

Here's all the apps I've tried already, with complete and total failure:

DVD::rip

Acidrip

DeVeDe

Lemonrip

I don't know if my DVDs all happen to be uberencrypted or what, but EVERY app fails to even display the frakking preview. Oh, that's another thing, I can't even watch DVDs from the disk, let alone rip them. I suspect this is a related issue.

---

### Post by needhelpplease on 2008-12-14
Have you added Medibuntu as a repos and followed their instructions for playing encrypted (standard) DVDs?

---

### Post by BobSutan on 2008-12-14
Nope. If you haven't guessed by now, I'm pretty new to ubuntu and *nix in general. 

I'll head over there and see what's up.

**EDIT**

Okay, I followed their instructions for Intrepid.

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2

So now I'm FINALLY able to get the DVDs to play. I'll see if I can get it to rip here in just a sec.

---

### Post by BobSutan on 2008-12-14
Sweet! I think it's going to work. So for all this time it turns out it's because ubuntu doesn't ship with the required...whatever...to decode DVDs. Why is that?

---

### Post by 2hot6ft2 on 2008-12-15
Proprietary codecs and linux is free so you have to agree if you want to use things are not open source

---

### Post by needhelpplease on 2008-12-15
> **BobSutan said:**
> Sweet! I think it's going to work. So for all this time it turns out it's because ubuntu doesn't ship with the required...whatever...to decode DVDs. Why is that?

Indeed, it doesn't ship with the DVD decoder.  It's due to legal restrictions.  Some countries allow it, others do not, so they put all that stuff in the Medibuntu repos, put that in a country where it's legal, and then they rely on users to make sure that they only download stuff that's legal in their country.  But they can't ship it or else Ubuntu itself would be restricted.

It's annoying and stupid.  Unauthorized DVDs are sold all over the world and the DVD encryption obviously does not hinder them in any way.

---

### Post by Poyntz on 2008-12-15
I've never had problems burning with Brasero (it comes installed with Intrepid Ibex). Type **brasero** in a terminal. 
Also, DVDs/CDs won't burn if you don't have a burner. I know chances are you would, otherwise you wouldn't be trying to burn anything, but you'd be surprised at how many people try to do things when they don't have the hardware

---

