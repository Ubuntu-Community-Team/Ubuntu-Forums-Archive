---
title: "Curious about maverick"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfreak_ on 2010-08-21
Was just wondering if it would be feasible to install maverick on a usb and keep using it and UPDATING it (just to get a feel on the progress) and when finally the release gets out, THEN install it?
So this way no harm to the my system and yet I can get a early taste of maverick, and hopefully find a bug.

---

### Post by philinux on 2010-08-21
Moved to Maverick testing forum.

Pleas read the forum stickys.

---

### Post by jfreak_ on 2010-08-21
Sorry. Thanks for reminding me.

---

### Post by VMC on 2010-08-21
> **jfreak_ said:**
> Was just wondering if it would be feasible to install maverick on a usb and keep using it and UPDATING it (just to get a feel on the progress) and when finally the release gets out, THEN install it?
So this way no harm to the my system and yet I can get a early taste of maverick, and hopefully find a bug.

A couple of questions. Who's going to control boot, Grub for the usb?

Also, why not just create a single partition inside your hard drive and install it that why?

Also what's running on your system now, Windows, Lucid, etc?

---

### Post by tjktyler on 2010-08-21
Feasible? Yes. But it would also be very complicated to setup and use. Ideally, you would have a 16GB flash drive on which to install Maverick. But VMC brings up good points, and the answers to those questions either complicate or simplify things (i.e. not having GRUB on the flash drive complicates things, installing to a separate hard drive partition simplifies things).

---

### Post by ronacc on 2010-08-21
if your computer will boot from a usb stick it should work , I do it on my EEE with both SD cards and usb sticks .

---

### Post by ktp on 2010-08-21
> **ronacc said:**
> if your computer will boot from a usb stick it should work , I do it on my EEE with both SD cards and usb sticks .

yep and bigger the usb, bigger room for you saved data.  I use to run this way when wanted to quickly check something was "weird" on harddrive install.

---

### Post by jfreak_ on 2010-08-22
> **VMC said:**
> A couple of questions. Who's going to control boot, Grub for the usb?

Also, why not just create a single partition inside your hard drive and install it that why?

Also what's running on your system now, Windows, Lucid, etc?

Only lucid right now. But I am a bit apprehensive of installing a alpha release on my one and only work computer, don't want to take any chances with grub. Are my apprehensions misplaced? 
Grub ? what grub for the usb? i was thinking of booting in a live environment everytime except that persistance would be enabled.

---

### Post by ranch hand on 2010-08-22
You should have less problems with grub under 10.10 than with 10.04.  It is a much better version.

You may have other problems as with any testing OS.  This should not effect grub even if you can't boot to 10.10 as long as the grub files on it are readable.  That would be a very remote chance in my opinion.

10.04 has some very real problems on some hardware and mine is one of the boxes that it just will not run right on.  10.10 runs much better than 10.04 on the same drive as 10.10.

I do run all testing on an external drive and will not put a testing OS on my main internal drives.  I use 10.10 all day.  I will not put 10.04 on my internals either.

If I had to put one or the other on an internal it would be 10.10.  There is no way 10.04 is going anywhere near my stable, secure installs.  10.10 would, I think, be a minimal risk.

---

### Post by cariboo on 2010-08-22
Truthfully, if you only have one computer, and it is for real work, I wouldn't even think about installing maverick on it, you'b be better off using a usb drive, created with the usb disk creator, and set the persistence size to whatever you want. 

If you have a big enough drive, you could do a normal install with a / and /home partition, just install it the way you would to a hard drive. I've installed ubuntu on 10Gb hard drives, and it was quite comfortable. You just have to make sure you keep an eye on /var/cache/apt/archives, and make sure you don't keep a lot of archived packages hanging around.

---

### Post by jfreak_ on 2010-08-22
> **cariboo907 said:**
> Truthfully, if you only have one computer, and it is for real work, I wouldn't even think about installing maverick on it, you'b be better off using a usb drive, created with the usb disk creator, and set the persistence size to whatever you want. 

If you have a big enough drive, you could do a normal install with a / and /home partition, just install it the way you would to a hard drive. I've installed ubuntu on 10Gb hard drives, and it was quite comfortable. You just have to make sure you keep an eye on /var/cache/apt/archives, and make sure you don't keep a lot of archived packages hanging around.

So basically, I set the first boot option to usb and keep the usb plugged in permanently? That should work right?

---

### Post by jfreak_ on 2010-08-22
So more problems, downloaded the image, installed on a usb, now it says 'unable to find keyword in boot configuration file'
then  a boot: prompt appears.
Tried installing several times , downloaded image twice , same result.

---

### Post by 23meg on 2010-08-22
> **jfreak_ said:**
> So more problems, downloaded the image, installed on a usb, now it says 'unable to find keyword in boot configuration file'
then  a boot: prompt appears.
Tried installing several times , downloaded image twice , same result.

That problem is covered in at least one recent thread. Please do a forum search, and keep this thread to your original question.

---

### Post by ktp on 2010-08-22
> **jfreak_ said:**
> So more problems, downloaded the image, installed on a usb, now it says 'unable to find keyword in boot configuration file'
then  a boot: prompt appears.
Tried installing several times , downloaded image twice , same result.

hopefully this helps:

[http://ubuntuforums.org/showthread.php?t=1533282](http://ubuntuforums.org/showthread.php?t=1533282)

---

