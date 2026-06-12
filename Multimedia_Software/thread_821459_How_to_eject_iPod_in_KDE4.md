---
title: "How to eject iPod in KDE4"
date: 2008-06-07
forum: Multimedia Software
---

### Post by wl2776 on 2008-06-07
I have Kubuntu 8.04 and KDE4 (even 4.1, probably).
When I plug in my ipod nano 3g, the New Device Notifier shows it and offers opening it in the Dolphin.
Amarok also works with it.

Everything is fine until I try to eject it.
Both New Device Notifier and Kicker show "eject" (button or word, respectively), but ipod still writes that it is connected, after I press this.

I always have to run kdeeject, either manually or through Amarok's "post-disconnect"

Is it possible to make KDE4 to properly eject ipod?

---

### Post by RyanVanDiemen on 2008-06-13
Hi, I have the same problem. Have you solved it?

---

### Post by RyanVanDiemen on 2008-06-13
Hi guys, can anybody help with this? I am not able to eject Ipod in KDE via Amarok. Even kdeeject command doesn`t work for me. If I disconnect ipod in Amarok it says post-disconnect command failed. It says the same in Gnome, but at least I`m able to eject it via icon on desktop. I can`t do the same in KDE. If I try to safely remove it in Dolphin it says either device is not mounted or device is busy... It is basically unmounted but on Ipod screen it still shows as Connected. I`ve seen quite a few posts how to use Post-command line in Amarok but none works for me. I`m a bit frustrated now, because I`m trying to switch to KDE after few years in GNOME as I realized I use more KDE apps as they suit me better. But I don`t want to go to gnome every time I need to eject my ipod. Thanks for all your replies.

---

### Post by RyanVanDiemen on 2008-06-14
anybody?

---

### Post by LucaTNT on 2008-09-18
You should set the SUID bit of the eject executable and use it in Amarok:
```
sudo chmod 4755 `which eject`
```
In Amarok set "eject %d" as post-command

---

### Post by skram on 2008-12-04
A bit more comfortable is:

> sudo chmod 4755 /usr/lib/kde4/libexec/kdeeject

and in Amarok

> /usr/lib/kde4/libexec/kdeeject %d

Then the eject button in the device notifier will work, too.

---

### Post by laluz on 2009-04-13
for me it was necessary to do a few more things, otherwise kdeeject would complain that it can not eject the /media/IPOD

```
sudo blkid
```
to get the UUID of the iPod and then add it to the fstab
```
UUID=XXXX-XXXX /media/IPOD    vfat      user,rw,utf8,umask=000 0 0
```
then I have mounted the iPod looked at the /etc/mtab for it's device name and did this 
```
sudo chown YOUR_USER_NAME /dev/IPOD_DEVICE_NAME
```
and also 
```
sudo chmod u+s `which eject`
```

I do not know if this is the right way, but it worked for me. If somebody knows more about the KDE4 internals and could propose a better way to handle that I would be happy to learn.

---

### Post by laluz on 2009-04-13
ah, and for the configure screen in Amarok I am using this:
Pre-connect 
```
mount /media/IPOD
```
Post-disconnect 
```
/usr/lib/kde4/libexec/kdeeject %m
```
anything else did not work.

---

### Post by lebrun on 2009-11-10
This works for me in Karmic:
```
/usr/lib/kde4/libexec/kdeeject -q %m
```

---

