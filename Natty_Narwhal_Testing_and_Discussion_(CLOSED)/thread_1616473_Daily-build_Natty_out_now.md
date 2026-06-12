---
title: "Daily-build Natty out now"
date: 2010-11-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jppr on 2010-11-08
[http://cdimage.ubuntu.com/daily/20101108/](http://cdimage.ubuntu.com/daily/20101108/) :popcorn:

---

### Post by anders_c_ on 2010-11-08
only alternate, will there be any liveCDs before alpha1??

---

### Post by jppr on 2010-11-08
> **anders_c_ said:**
> only alternate, will there be any liveCDs before alpha1??

Is it some problem that it is alternate? Just did that usb-stick installation and system works without proplems :popcorn:

---

### Post by cariboo on 2010-11-08
> **anders_c_ said:**
> only alternate, will there be any liveCDs before alpha1??

It's pretty early in the cycle to be worrying about a Live CD, there are no new features available yet. The Live CD will be available when it's ready.

---

### Post by VMC on 2010-11-09
The Natty [daily-live]("http://cdimage.ubuntu.com/daily-live/current/") is upon us!

If you have Maverick ISO still available you can zsync using it and save over 50% download update files.

Like so:

```
zsync -i maverick-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync
```(substitute 'i386' for 'amd64' on 32-bit systems)

---

### Post by scradock on 2010-11-09
Trying to start in Virtualbox using the daily build -i386.iso as a pseudo-CD, but it fails with a Busybox message and

(initramfs) aufs mount failed

Any ideas? As it's not a LiveCD I don't get a menu of options, just a Plymouth logo screen, then failure......

---

### Post by VMC on 2010-11-09
> **scradock said:**
> Trying to start in Virtualbox using the daily build -i386.iso as a pseudo-CD, but it fails with a Busybox message and

(initramfs) aufs mount failed

Any ideas? As it's not a LiveCD I don't get a menu of options, just a Plymouth logo screen, then failure......

Its the Livecd alright, its just failing. I tried both amd64 and i386 on two difference machines, and they both fail to busybox.

At first , I thought its was my nvidia, but the i386 is an ATI video.

It appears to fail right after selecting the video drivers. I used the usb method.

---

### Post by alz3abi on 2010-11-11
same problem here,cant run it nvidia is installed, any fixes ?

---

### Post by keypox on 2010-11-12
I tried startup disk creator, but it didnt work.

---

### Post by ssam on 2010-11-12
if you are not using it already, testdrive is great.

it shows you all the cds available. gets them with zsync. can then can either boot them in qemu (it takes care of making disk images and stuff) or write them to USB.

---

### Post by floydsp on 2010-11-12
Why are there new files for the last 3 day 10,11,12 and still won't boot?

seems like its a waste of time

floydsp

---

### Post by MadCow108 on 2010-11-12
> **floydsp said:**
> Why are there new files for the last 3 day 10,11,12 and still won't boot?

seems like its a waste of time

floydsp

because they are created automatically from the repositories. There is no extra work involved in creating them.

if you want to install from an iso, the alternate installer works for me.

The daily may boot when the kernel group fixes aufs (as noted in the kernel group minutes).

---

### Post by Quackers on 2010-11-12
OMG! What have you been milking that cow with - a vacuum cleaner? :-)

---

### Post by ranch hand on 2010-11-12
> **Quackers said:**
> OMG! What have you been milking that cow with - a vacuum cleaner? :-)
I think it is just a bad case of sunburn.

This would also explain the cranky look on her face.

---

### Post by coffeecat on 2010-11-12
> **ranch hand said:**
> This would also explain the cranky look on her face.

Seeing as she's only got two legs, she must be taking some of the weight on that swollen - um - gland, which must hurt.

Sorry... what were we talking about? :?

---

### Post by cpatrick08 on 2010-11-15
the live iso from nov 14 works great i am typing this message from the iso so you may want to zsync the iso or redownload the current live iso and so far no changes apparent from maverick

---

