---
title: "Ipod Nano 6G solution but I need it explaining pls.."
date: 2012-07-21
forum: Multimedia Software
---

### Post by keevill on 2012-07-21
Can some learned person explain to me in simple terms what the below means. I am an experienced Ubuntu guy but not able to quite comprehend what this means.
I've downloaded the libhashab.so md5sum = bb7180cb0c9cee2a605a5a276672913e (555149 octects)
And that's as far as I can get.
I too am trying to somehow get music onto my Nano 6G using Ubuntu Presise Penguin and I came across this post.

Thx,
-keevill-

_______________________


I've successfully synced my iPod Nano 6G with gtkpod on Ubuntu 11.10.
Here's a brief summary of what I've done to get this running:

- replace Ubuntu's libgpod 0.8.0 with 0.8.2. I may put packages into
  my PPA at a later point for easier installation, although precise
  already has the correct recent version available.

- place the infamous libhashab.so/libhashab64.so into /usr/lib/libgpod/
  -rw-r--r-- 1 root root 543K 2012-01-21 19:34 libhashab.so
  md5sum (32 bit): bb7180cb0c9cee2a605a5a276672913e
  (Google is your friend.)

- after Ubuntu automounts the iPod, force it to read-write mode using
  sudo mount -o remount,rw,force <mountpoint>

- take ownership of all files & directories
  sudo chown -R <your_user_name>: <mountpoint>

- run gtkpod

- sync, be happy :-)

---

### Post by fixitdude on 2012-07-21
"place the infamous libhashab.so/libhashab64.so into /usr/lib/libgpod/"

Looks like you copy it to /usr/lib/libgpod/   (as root of course, also re-boot)

I would make a copy of any existing libhashab.so files first so you can put them back.

You may have to find more online posts about doing this, and I hope you understand that this is just to get "gtkpod" working on a older Ubuntu so maybe you want Ubuntu 12.04 anyway since it would have updates and newer drivers.

---

### Post by keevill on 2012-07-21
> **fixitdude said:**
> "place the infamous libhashab.so/libhashab64.so into /usr/lib/libgpod/"

Looks like you copy it to /usr/lib/libgpod/   (as root of course, also re-boot)

I would make a copy of any existing libhashab.so files first so you can put them back.

You may have to find more online posts about doing this, and I hope you understand that this is just to get "gtkpod" working on a older Ubuntu so maybe you want Ubuntu 12.04 anyway since it would have updates and newer drivers.

whoops, just realised I'm running 11.10 .
Does that make any difference to your reply?
Do I use sudo nano or sudo gedit to edit the libgpod file ?
Thx,
-keevill-

---

### Post by monkey21stc on 2012-08-17
Sorry for reviving this thread but I just purchased an ipod nano 6g,
I've followed the guide and downloaded the libhashab.so file but I realized that there is no /usr/lib/libgpod folder. 

So I created a new folder /usr/lib/libgpod adjusted the necessary permissions and managed to transfer successfully my first album into my ipod.

However, upon reconnection, an error popped up indicating a hash error, rendering the ipod unusable until I do a restore from itunes.

So how should I go about solving this?

Edit: I am using precise 12.04 by the way


Many thanks and regards,
Monk

---

### Post by joel.bacal on 2013-02-07
I figured out to use it in Banshee in ubuntu 12.04

1. Install libgpod4_0.8.2 and libgpod-common_0.8.2  from [http://franck78.ath.cx/](http://franck78.ath.cx/)

2. Downloaded libhashab.so and in root mode place it in /usr/lib/libgpod and put all permisions to read and write.

That's it :p

---

### Post by danwood76 on 2013-04-16
Sorry to bump this thread.

If the libhashab.so doesn't work for you I have a solution I have posted here:
[http://ubuntuforums.org/showthread.php?t=1611473&p=12606043#post12606043](http://ubuntuforums.org/showthread.php?t=1611473&p=12606043#post12606043)

It consists of a modified libhashab.so ;-)

---

