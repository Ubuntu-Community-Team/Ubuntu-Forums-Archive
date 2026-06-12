---
title: "iPod Touch doesn't show up in Rhythmbox"
date: 2010-05-26
forum: Multimedia Software
---

### Post by puzzler995 on 2010-05-26
I have an iPod Touch 2nd Gen with 3.1.3, Ubuntu 10.04, and the most up to date software, and my iPod doesn't appear in Rhythmbox. It shows up with Nautilus, so I know its being read.
Thanks
Puzzler995

---

### Post by puzzler995 on 2010-05-27
just an update: the iTouch is not read in Banshee, but is read in Amarok, so I will just use that for now :)

---

### Post by joosto on 2010-05-28
My iPod touch used to show up, but it doesn't anymore. I will try Amarok to see if that works.

---

### Post by puzzler995 on 2010-06-08
Well Amarok is now screwed up... UGH I need some help. PLEASE

---

### Post by joanga on 2010-06-08
> **puzzler995 said:**
> I have an iPod Touch 2nd Gen with 3.1.3, Ubuntu 10.04, and the most up to date software, and my iPod doesn't appear in Rhythmbox. It shows up with Nautilus, so I know its being read.

Did you by any chance upgrade to Lucid, and did you previously install 3rd party packages to work with your iPod?

I've got the same setup and had the same problem. Check in the directory /etc/udev/rules.d to see if you have files like 85-usbmuxd.rules or 90-libgpod.rules. If so, delete them. Then run on the command-line:

```
sudo restart udev
```The udev daemon is supposed to start usbmuxd to access the iPod when you plug it in, but those old files in /etc/udev/rules.d messed it up on my system.

---

### Post by puzzler995 on 2010-06-08
> **joanga said:**
> Did you by any chance upgrade to Lucid, and did you previously install 3rd party packages to work with your iPod?

I've got the same setup and had the same problem. Check in the directory /etc/udev/rules.d to see if you have files like 85-usbmuxd.rules or 90-libgpod.rules. If so, delete them. Then run on the command-line:

```
sudo restart udev
```The udev daemon is supposed to start usbmuxd to access the iPod when you plug it in, but those old files in /etc/udev/rules.d messed it up on my system.

I used to use iFuse, before I upgraded to Lucid, but I have none of those files, and sudo restart udev does no help. :/ Thanks anyway...

---

### Post by Paul Vega on 2010-06-17
Can someone please give me the terminal command to delete these files? I do not know how else to do it as trying to delete them by 'Edit - Delete' only tells me that I do not have permission.

> **joanga said:**
> Did you by any chance upgrade to Lucid, and did you previously install 3rd party packages to work with your iPod?

I've got the same setup and had the same problem. Check in the directory /etc/udev/rules.d to see if you have files like 85-usbmuxd.rules or 90-libgpod.rules. If so, delete them. Then run on the command-line:

```
sudo restart udev
```The udev daemon is supposed to start usbmuxd to access the iPod when you plug it in, but those old files in /etc/udev/rules.d messed it up on my system.

---

### Post by puzzler995 on 2010-06-17
> **Paul Vega said:**
> Can someone please give me the terminal command to delete these files? I do not know how else to do it as trying to delete them by 'Edit - Delete' only tells me that I do not have permission.

just use
```
gksu nautilus
```

---

### Post by {Brian} on 2010-10-27
I'm not sure if we have the same problem, so heres a description of mine:

1. At one point my ipod would be read, and synced with rhythymbox.
2. One day this no longer happened (after some library update a couple weeks ago).
3. I would plug in my ipod, it would show up for half a second then immediately disappear, even making the sound that it makes when it syncs.

I haven't found a nice solution to the problem, but when you plug your ipod, go to computer:/// and find your device. Right click on it and select open. find rhythmbox music player and click it. if your ipod doesnt show up, disconnect it and reconnect it (with computer:/// open) and try again.

---

