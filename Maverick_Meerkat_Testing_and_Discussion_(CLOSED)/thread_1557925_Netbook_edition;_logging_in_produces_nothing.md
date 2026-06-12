---
title: "Netbook edition; logging in produces nothing?"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-08-21
After installing the netbook edition in Virtualbox ( [http://cdimage.ubuntu.com/releases/maverick/alpha-3/](http://cdimage.ubuntu.com/releases/maverick/alpha-3/) ) I log in, but get nothing but a white cursor and purple wallpaper. It's the Alpha 3 release.

---

### Post by kaldor on 2010-08-21
Just did an update... no luck

---

### Post by cariboo on 2010-08-21
Unity doesn't work in vbox because there is no 3D acceleration, you should be able to select the gnome desktop from the login screen.

---

### Post by kaldor on 2010-08-21
Ah, that's too bad :(

But won't this mean Unity might be a bit slow/laggy on some graphics drivers? Especially on netbooks?

---

### Post by KegHead on 2010-08-21
Hi!

I have a Dell mini 9 I hope to upgrade next week.

Good to know info.

KegHead

---

### Post by ktp on 2010-08-21
> **cariboo907 said:**
> Unity doesn't work in vbox because there is no 3D acceleration, you should be able to select the gnome desktop from the login screen.

didn't virtualbox added support for 3d acceleration in guest?  Just wondering...i have never played with it, but something on try one day.

---

### Post by ronacc on 2010-08-21
it don't work on my EEE either just boots to a blank pink screen .

---

### Post by VeeDubb on 2010-08-21
On my Asus 1201n (dual core atom and nvidia ION graphics) all I get is the wallpaper.  Not even a cursor unless the screen saver kicks in.  As soon as I clear the screen saver, I get a cursor and wallpaper and nothing else.

This happens with the default open source driver for nvidia, and the nvidia blob.  It has happened consistently since alpha 3 hit.

I have formatted and reinstalled with Alpha 3, and it did not help.

I then tried with yesterday's daily build and manually instaling ubuntu-netbook after I had everything updated and running.

Still no dice.

It appears that Unity is completely broken for the moment.

---

### Post by cariboo on 2010-08-21
I'm running unity on a Compaq mini 110, running Intel i945 graphics chipset, when the kernel got upgraded to 2.6.15, the screen flashed when every I tried to do any thing, 2.6.16.fixed that problem, but I was getting constant crash reports, 2.6.17 solved that problem.

---

