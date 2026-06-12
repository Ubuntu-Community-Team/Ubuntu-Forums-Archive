---
title: "bluetooth"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by gisler_csn on 2008-12-03
hello,

i have ubuntu 8.04 installed on my laptop that has bluetooth. i can send files to my laptop from my phone and the other way around. when i try to view the files on my phone with my laptop i just get an error. the error just simply says "The folder contents could not be displayed. Couldn't parse incoming data". 

also my phone is a lg u990. not sure if this helps

many thanks 
gisler_csn

---

### Post by torstenaf on 2009-04-21
I have the same exact error: "Couldn't parse incoming data."

This error only appears when viewing the "Music" directory on my phone. I successfully viewed the "Graphics" directory which had about twenty files in it. It seems I can also view other directories.

So why just the music directory? Perhaps number of files is greatest (110), or there is some filename that can no longer be parsed?

Last year, I successfully transferred files from my laptop to my phone, a Samsung A717. Some upgrade since then has killed my ability to transfer the files.

This is the only reference to the error I can find:
[https://bugs.launchpad.net/gnome-vfs-obexftp/+bug/121514]("https://bugs.launchpad.net/gnome-vfs-obexftp/+bug/121514")
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/310231?comments=all]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/310231?comments=all")
The solution is supposed to be here:
[https://bugs.launchpad.net/gnome-vfs-obexftp/+bug/140478]("https://bugs.launchpad.net/gnome-vfs-obexftp/+bug/140478")
The solution says to compile the gnome-vfs-obexftp package with
```
--enable-nautilus-workaround
```

Not sure where to go...

Will add to the ubuntu bug report.

---

