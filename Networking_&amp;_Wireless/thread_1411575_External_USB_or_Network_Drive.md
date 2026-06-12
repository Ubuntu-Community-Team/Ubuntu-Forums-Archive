---
title: "External USB or Network Drive?"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2010-02-20
Hi all, looking for a bit of advice and/or opinions here.

Thanks to a growing mp3 collection my PC is getting full quite quickly.  I'm not one for delving into the innards of the machine to install new hard-drives so would be happier with an external solution.

At the moment, my Music folder is shared across the network so my son can access it on his laptop.

If I buy a regular external USB hard-drive, will I be able to have that permanantly mounted and be able to share the Music folder that I would create on it?

Or would I be better off spending a little extra on a networked hard-drive plugged straight into my Netgear router?  If so, any recommendations on a make & model that is happy with Ubuntu as well as Windows?

Look forward to your thoughts.
Dave

---

### Post by .nedberg on 2010-02-20
> **motorcity909 said:**
> 

If I buy a regular external USB hard-drive, will I be able to have that permanantly mounted and be able to share the Music folder that I would create on it?

Yes
> **motorcity909 said:**
> 
Or would I be better off spending a little extra on a networked hard-drive plugged straight into my Netgear router?  If so, any recommendations on a make & model that is happy with Ubuntu as well as Windows?


This is how I would do it. This way you would not need your desktop turned on to access the drive/music. I have no recommendations though.

---

### Post by SecretCode on 2010-02-20
You can certainly leave an external USB drive plugged in all the time, and shared. Just make sure that you've got power-surge protection, ideally a UPS, just as you would for a PC.

Do you leave your PC on 24 hours? If you don't, or you want to save some electricity, that would be the main argument for having network-attached storage.

---

### Post by motorcity909 on 2010-02-20
Thanks for your replies.

I don't leave my PC on 24 hours and the whole issue of son & heir accessing the Music folder will probably be resolved by him having a new laptop soon and simply having all the music he wants actually on his laptop, thus accessible to him even when my PC isn't on.

There is another side to this which is that I run WinXP on Virtualbox so I can still use iTunes.  I access the Ubuntu Music folder via Virtualbox shares (not Samba network shares).

As a trial, I've just set up a new Virtualbox share to a folder on a small external hard-drive I've got and it worked and I could access the folders content within XP Network Places. :)

As a final (promise!) question, what's the best format to have on the external hard-drive, NTFS or FAT32?

Thanks as always
Dave

---

### Post by .nedberg on 2010-02-20
> **motorcity909 said:**
> 
As a final (promise!) question, what's the best format to have on the external hard-drive, NTFS or FAT32?


I would probably use NTFS out of those...

ext4 is my choice though, but it can be "problematic" if you want to bring the disk with you and connect to someone else's computer running Windows.

---

### Post by SecretCode on 2010-02-20
I'd avoid FAT32: the filesize limit of 4GB could be a problem with movies ... virtualbox disk images ... backups ... and more.

---

### Post by motorcity909 on 2010-02-20
Great stuff.  Thanks so much for all your help, have a great Saturday night.

Cheers
Dave
:P

---

