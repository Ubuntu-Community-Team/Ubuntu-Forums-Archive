---
title: "Please help with zsync"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-02-03
I'm trying to learn to use zsync.

I think I should enter the command : zsync url/file.zsync

This should update my .iso file, is this correct?

Then, to update is there a way to open the .iso without burning it?

Is this, in any way, a better method to update than using update manager or synaptic?

---

### Post by cariboo on 2011-02-03
zsync only keeps the iso up to date, you can open an iso a couple of ways, you can mount is using the following command:

```
sudo mount -o loop <image>.iso /mnt
```

substitute the name of the iso for <image>


Right click on it and select open with archive manager.

This isn't a substitute for using update-manager or synaptic

---

### Post by ratcheer on 2011-02-03
To answer your first question (how to use zsync), I run a script that resides in the same directory with my iso image (the one I want to update). The script contains the following command:

zsync [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync)

for the daily Live image OR

zsync [http://cdimage.ubuntu.com/daily/current/natty-alternate-i386.iso.zsync](http://cdimage.ubuntu.com/daily/current/natty-alternate-i386.iso.zsync)

for the daily alternate image.

Tim

---

### Post by psusi on 2011-02-03
If you already have natty installed, update manager keeps it up to date.  You use zsync to update your iso image so you can test booting the cd and possibly installing without having to download the entire new image each time.

---

### Post by JRV on 2011-02-04
Thank you all, that explains it.
I'll' mark the thread solved now.

---

### Post by alaukikyo on 2011-02-05
You can also use [gui script for zsync]("http://ubuntuforums.org/showthread.php?t=1680882") .

---

