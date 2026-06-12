---
title: "Creating USB image for 11.04 Daily Build"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2011-03-24
I have a PC I can install Natty on right now for Unity testing. To save a trip to the store to buy DVDs, I thought making a USB image would work fine. I created the image with the USB creator on Maverick but it doesn't seem to work. It finished successfully, but on the PC I try to boot it on it gives the error "Missing Operating System" immediately.

Is this a known issue?

---

### Post by VMC on 2011-03-24
> **kaldor said:**
> I have a PC I can install Natty on right now for Unity testing. To save a trip to the store to buy DVDs, I thought making a USB image would work fine. I created the image with the USB creator on Maverick but it doesn't seem to work. It finished successfully, but on the PC I try to boot it on it gives the error "Missing Operating System" immediately.

Is this a known issue?

Did you erase the usb device first? I think Maverick had problems with syslinux being the wrong version. I only use usb hard drive to install the livecd to and have never since Maverick had any issues. I'm guessing your using a usb flash drive, which I will try shortly to see if any differences.

There was something with one of the config files in the syslinux folder that needed changing, but that error was in reference to starting

---

### Post by kaldor on 2011-03-24
I did erase it first, yes.

---

### Post by VMC on 2011-03-24
> **kaldor said:**
> I did erase it first, yes.

I just created it using natty. That worked. I don't have Maverick installed and I can't find the cd. I'll try using Lucid to install the livecd.

Edit: I just tried it using Lucid and the created usb flash drive worked perfectly. 
What arch do you have and iso did you use? That shouldn't matter but just curious.

---

### Post by KegHead on 2011-03-24
Hi!

Have you tired Unetbootin?

KegHead

---

