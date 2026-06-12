---
title: "Conexant Modem Difficulties"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by Karamthulhu on 2005-12-11
Yes; I'm using dial up. It's unfortunate, but I am.

I have an internal modem, identified by Windows as **Conexant D480 MDC V.92**. However, Ubuntu seems to be unable to see it, hindering me from accessing the Internet.

Network administration was unable to auto detect the modem port, which was what got me suspicious.

I then tried to run "pppconfig" in Terminal, which was also unable to detect the modem port. This forced me to manually try out each one; coincidentally, none of them worked.

Is there anything I can do to combat this problem (preferably without much hassle)?

Many thanks.

---

### Post by GilGalad on 2005-12-11
For conexant modems you need to download the drivers from [www.linuxant.com](www.linuxant.com)
There is a free driver but it only does 14kbps. I suggest to install the free one and see if it works before paying the small fee for the full one.

---

### Post by Karamthulhu on 2005-12-11
Thanks, I'll try that as soon as I'm able to. :)

One more (newbie) question: is there any way to access the driver for installation on my Windows partition from Ubuntu (since I obviously can't download it directly from Ubuntu)?

---

### Post by GilGalad on 2005-12-11
This is what I'll do:
```

sudo -s -H
mkdir /mnt/windows
mount /dev/hda1 /mnt/windows
cd /mnt/windows

```

where /dev/hda1 is the partition in which windows is installed. It can be different on your computer (hda2, hda3, hdb1, ... if IDE disks; sda1,... if SCSI).

---

### Post by Karamthulhu on 2005-12-11
;>_> This is more difficult than I had thought.

I went to Linuxant, identified my modem as HSF, and downloaded the ZIP for my Ubuntu kernel version.

Evidently it won't work, as I was unable to open the .deb file after extracting the ZIP.

I then downloaded the TAR version of the drivers, extracted it, and was left confused as to how to install it; the instructions on the website were inadequate for my limited knowledge on Linux. :p

If anyone could provide information on how to install drivers, it would be greatly appreciated, and I apologize for my ignorance on this matter.

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=Karamthulhu];>_> This is more difficult than I had thought.

I went to Linuxant, identified my modem as HSF, and downloaded the ZIP for my Ubuntu kernel version.

Evidently it won't work, as I was unable to open the .deb file after extracting the ZIP.

I then downloaded the TAR version of the drivers, extracted it, and was left confused as to how to install it; the instructions on the website were inadequate for my limited knowledge on Linux. :p

If anyone could provide information on how to install drivers, it would be greatly appreciated, and I apologize for my ignorance on this matter.[/QUOTE]

You don't open a .deb file-- it is more like a .msi file from Windows.  Try this command:
```

$ sudo dpkg -i packagename.deb

```
You will need to substitute the real name of the .deb  file above.  Installing from source is a somewhat more advanced topic.  If you search the forums, this question actually comes up at least once a week, and several people have put together excellent tutorials on how to do it for the layperson. 

Here is one:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

