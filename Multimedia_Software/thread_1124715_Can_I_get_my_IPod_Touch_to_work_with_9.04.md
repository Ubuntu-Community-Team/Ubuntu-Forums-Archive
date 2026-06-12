---
title: "Can I get my IPod Touch to work with 9.04?"
date: 2009-04-13
forum: Multimedia Software
---

### Post by tysonxg on 2009-04-13
I am running an up-to-date version of 9.04 and whenever I plug my IPod in via the USB cable, Ubuntu reads it as a camera.  I have tried to search google and the Ubuntu forums for the answer but I haven't found an answer.
So...
Is there anyway to use a non jail-broken IPod Touch(2nd Gen) with Ubuntu?

---

### Post by djbushido on 2009-04-13
What is the problem with it being recognized as a camera, as long as it works?
Anyway, with it plugged in, will you post the results of this command:"sudo fdisk -l" where that - is -L only lowercase.

---

### Post by tysonxg on 2009-04-13
Well the problem with it being read as a camera is that i cannot figure out how to access the music files...

Here are my results for that command:

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

---

### Post by djbushido on 2009-04-13
This fdisk indicates that the Ipod is not recognized by the system.
Wait until Ubuntu mounts it (apparently as a camera) and then re-try this.

---

### Post by albinootje on 2009-04-13
> **tysonxg said:**
> Is there anyway to use a non jail-broken IPod Touch(2nd Gen) with Ubuntu?

This might help :
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by tysonxg on 2009-04-13
> **djbushido said:**
> This fdisk indicates that the Ipod is not recognized by the system.
Wait until Ubuntu mounts it (apparently as a camera) and then re-try this.

Dose mounting it mean that it shows up as an icon on my desktop? and if yest it says the same thing...

---

### Post by djbushido on 2009-04-13
well, then that means that Ubuntu, not HAL, is mounting it. At that point, I have absolutely no idea what to do, sorry.
One more thing though: is there an alternate USB mode that you can try? some music devices have an MTP (media transfer protocol) and an MSC (mass storage class) mode.
As you can see, I don't have an Ipod (just a generic mp3 player) so other than that I don't think I can help you any more. Again, sorry.

---

### Post by kyle2595 on 2009-05-24
I was trying to use Banshee to manage my first generation iPod Touch and when i plugged it in nothing happened, Ubuntu thinks that my iPod is a camera too.  If any one knows how to get Ubuntu to recognize my iPod as an iPod, pleas help!

---

### Post by petersonmicaelt on 2009-06-14
I've been working on this for some time, I have a first gen jail broken iPod touch (16 GB). I installed the BSD subsystem, and it looks like the internal memory is split into two parts. A "user" area this is where photos, and contacts go, and a music partition that is blocked form both access through the shell, or through ssh. I have tried creating a mount point on the iPod directly but no luck, I'm going to look into the config files both on the iPod and anything I can find in iTunes for more of an idea on how this works.

---

### Post by PureLoneWolf on 2009-06-15
Umm..spam much - That's a Windows application and there are plenty of free apps on Linux to do this if you can get it recognised.

That said, for the Touch, Virtualbox PUEL (running XP guest) and MediaMonkey for me = Winner, unless you want to jailbreak your touch...even then I seem to remember reading that this only worked for firmware that was 1.4 or earlier.

---

### Post by zenbachry on 2009-06-18
Wow. Well, it seems that my search might have come to a failure. I was searching to see if Ubuntu would have worked with his iPod Touch 2nd Gen. But as it seems, Apple is doin' another...uhm...how to put it nicely...stupid?....(sorry to you Apple lovers, I cannot stand Apple nor can I stand Microsoft!)...move by encrypting their devices (I do have to say, doin' that just gives people more of a reason to hack the device).

Anyway! If there is way to do it without "jailbreaking" the iPod, I'd like to know.

Thanks.

Oh yea, and virtual machine-ing isn't going to be possible. Hes got an older PC. Its only got 900 MHz and 512 MB RAM.


Oops, I noticed I didn't specify it was a friends iPod. My bad xD I'm doin' the search for him, because he's thinking about switching.

---

### Post by Chronon on 2009-06-18
I'm not aware of any way without jailbreaking.  If you're willing to do that then there's [this]("https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing iPhones and iPods Touch w/ Firmware 2.x"). 

Is there a reason you don't want to jailbreak?

---

### Post by zenbachry on 2009-06-18
Lol, I could careless about jailbreaking. But, like I said, it isn't for me. Its a friends iPod, and he probably doesn't want to jailbreak. I can suggest it to him, but I doubt it. And I could careless about jailbreaking 'cause I don't like Apple products (as said before).

---

