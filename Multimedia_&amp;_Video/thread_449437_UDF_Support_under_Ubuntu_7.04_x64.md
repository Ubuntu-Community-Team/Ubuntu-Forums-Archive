---
title: "UDF Support under Ubuntu 7.04 x64"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by apollo440 on 2007-05-20
Hello everyone

I have a problem connected with reading DVDs with large file support.
When I put that kind of DVD in my DVD recorder, or DVD rom, whatever, it gives me this message
(actually it opens the drive with only one text file)

[B]This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification.[/B]

Is there any way, or official support, to enable UDF reading under 64bit Linux.
Especially by chance to be done with apt-get.

Greetings

---

### Post by solidunit on 2007-05-23
```
sudo modprobe udf
```

then try mounting manually if needed.

fyi, i'm actually still having problems after mounting the disk. mplayer tells me the 8 gig mkv i burned has no video or audio streams in it.

is udf large file support broken in the kernel?

---

### Post by chunchengch on 2007-05-23
$ sudo gedit /etc/fstab

and replace  **/dev/scd0 /media/cdrom0 [COLOR="Red"]udf,iso9660[/COLOR] user,noauto 0 0**
with  **/dev/scd0 /media/cdrom0 [COLOR="Red"]auto[/COLOR] user,noauto 0 0**, it should work for you.

---

