---
title: "inspiron 8200, 9.10 --- no dvd playing?!"
date: 2009-11-04
forum: Multimedia Software
---

### Post by iaw4 on 2009-11-04
I just installed 9.10 on a dell inspiron 8200 system.

I throw in a movie DVD ("John Rabe"; purchased it in Germany.)

Movie player tells me that "An Error occured.  no URI handler implemented for "dvd"."  It would be nice if this error would tell me what I need to do, instead.  as it stands, it is pretty uninformative.

then I did an apt-get install gxine, and tried gxine dvd:// .  the good news is that I don't get the same error.  the bad news is that I do get a different error.  I now get "Encryped media stream detected".  again, not much information on what to do.  I started reading the comprehensive guide at the beginning of this forum, but it seems totally overwhelming.

is this the standard end user experience with DVD watching under ubuntu?  could it be made more userfriendly by adding instructions how to fix it where the error(s) occurred?

/iaw

---

### Post by gordintoronto on 2009-11-04
Install the restricted extras.

DVD playback is covered by a patent in the USA, so it can not be included in the distribution.

---

### Post by andrew.46 on 2009-11-04
Hi iaw4,

> **iaw4 said:**
> is this the standard end user experience with DVD watching under ubuntu? 

I suspect so as an 'out of the box' experience. One easy way to get reasonable DVD playback, if you don't want to build your own packages, is to first enable the Medibuntu repository:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```

and then add vlc and libdvdcss2:

```
sudo apt-get install vlc libdvdcss2
```

and this should get you off to a flying start. I attach a screenshot of Jake and Elroy using exactly this setup :).

Andrew

---

### Post by iaw4 on 2009-11-05
thanks.  if anyone from the development team reads this, it would be nice if the attempt to play a DVD would put up a message that says that "DVD playing is disabled in the USA because of patent considerations.  to learn more, please read blah blah"

/iaw

---

