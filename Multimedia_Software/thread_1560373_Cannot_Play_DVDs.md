---
title: "Cannot Play DVDs"
date: 2010-08-24
forum: Multimedia Software
---

### Post by Nostigex on 2010-08-24
When I put a DVD in either of my two drives, the movie will not play using either VLC or Movie Player.

When I go to 'Open Disc' in VLC, next to 'Disc Device' it lists a string of two very odd characters,  &#65533;&#65533;, as the only option. The drop-down arrow doesn't work. When I click on 'Browse' and navigate to the name of the movie (which I assume is the drive) in the 'Places' menu, nothing happens.

In Movie Player, when I go to Movie > Play Disc "(Insert Movie Name Here)", I get the following error message: "Could not read from resource"

The same thing happens with either drive, with either of two DVDs.

DVDs seem to play fine in Windows XP using VLC.

What's going on here?

---

### Post by dtoronto on 2010-08-24
i believe you need the restricted-extras codecs, to play dvds.  This link should be helpful [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Nostigex on 2010-08-24
I got this message: "Package 'ubuntu-restricted-extras' is already installed."

An update: I tried a third DVD which works for some reason. But the other two still do not play. Nor does the restricted-extras package explain why VLC won't even recognize the devices.

---

### Post by madinc on 2010-08-24
you need to install libdvdcss2

---

### Post by Nostigex on 2010-08-24
Ok, I can now play the DVDs after following the instructions on this page:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Looks like libdvdcss2 is not a package unto itself; rather it's part of the libdvdread4 package and needs an extra line of configuration to get it going.

Now does anyone know why the strange characters (&#65533;&#65533;) would be showing up in the 'Disc Device' field?

Could it have something to do with the fact that Ubuntu doesn't distinguish between the two disc drives?

[IMG]http://www.mediafire.com/imgbnc.php/0656e00faa97ce2389a2d93e63e743f36g.jpg[/IMG]

---

### Post by tommcd on 2010-08-24
> **Nostigex said:**
> 
Now does anyone know why the strange characters (&#65533;&#65533;) would be showing up in the 'Disc Device' field?

Try changing the characters to /dev/dvd, or /dev/sr0 and see if VLC will play a DVD then.

---

### Post by Nostigex on 2010-08-24
Both of those work... what does sr stand for?

---

### Post by tommcd on 2010-08-24
> **Nostigex said:**
> Both of those work... what does sr stand for?
Glad it works ok now.
I don't know what "sr" stands for to be honest. Optical drives in linux used to be listed in the /etc/fstab file as /dev/hdX, where X was the next letter (usually c) after accounting for all of your hard drives.. With newer kernels this has changed to /dev/sr0. 
(Ubuntu does not even list optical drives in the fstab file now. Presumably they are detected dynamically with udev or something.) If you look in the /dev/directory you will likely have a dvd and an sr0 there.
 Similarly, hard drives used to /dev/hda, dev/hdb, etc. They are now /dev/sda, /dev/sdb, etc.

---

### Post by Lois723 on 2010-09-25
Yes!! dtoronto hit the nail on the head with that link; [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs). Solved my problem with that thread (same issue)and a few others. Seems it is dependent on the version of Ubuntu you have what the filenames are I installed libdvd2 and still didnt work so with that link I installed libdvd4 and I now am able to play dvds with totem. They play flawlessly too:).

Thanks so much to the community....

---

### Post by lucacerone on 2010-11-15
Hi guys, I'm experiencing the same issue, but in my case
it just started a few days ago.
Before in the Disc Device I could see the title of the disc in the player.
I'd like just to know if there is any way to change the default
disc and set it to /dev/dvd so that I don't have to write it manually each time. Cheers, 'Luca

---

