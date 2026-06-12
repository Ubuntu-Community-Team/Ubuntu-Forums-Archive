---
title: "Problems with DVDs and other media"
date: 2010-03-27
forum: Multimedia Software
---

### Post by Trilby on 2010-03-27
I am using Ubuntu 9.10 64Bit and cannot play DVDs.
I put in the disk and select play with Movie Player.
I then get the message:[I]

Could not read from resource.[/I]

If I then go *Movie >> Play Disk 'DVD NAME' *I get the message:
[B]
*Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.*[/B]
[I]
Please install the necessary plugins and restart Totem to be able to play this media.[/I]

This is followed by a link to [http://www.gnome.org/projects/totem/#codecs](http://www.gnome.org/projects/totem/#codecs) where I cannot see any means to download the plugin I need.

Also, I have some .dvr-ms files, which are recordings of TV programs made on my old Xp media centre edition computer (which had a TV tuner and an aerial port). These play with Movie Player but there is no audio.

Hope someone can help.
Thanks,

Trilby

Note: In case it is of any relevance, I am a UK user

---

### Post by wojox on 2010-03-27
To play a dvd:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Trilby on 2010-03-27
> **wojox said:**
> To play a dvd:

```
sudo apt-get install libdvdread4
``````
sudo /usr/share/doc/libdvdread4/install-css.sh
```


When I enter the first command, I get:

[I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/I]I assume this is not supposed to happen.
I've gotten this message with every solution I've tried that involves terminal.

Likewise with the second, I get:
[I]
--2010-03-27 16:48:56--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37252 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-xiWCRg/libdvdcss.deb'

100%[======================================>] 37,252       161K/s   in 0.2s    

2010-03-27 16:48:56 (161 KB/s) - `/tmp/dvdcss-xiWCRg/libdvdcss.deb' saved [37252/37252]

dpkg: status database area is locked by another proces[/I]

---

### Post by wojox on 2010-03-27
You need to shut down Synaptic Package Manager or Ubuntu Software Center. You can only have only package manager open at a time. ;)

---

### Post by Trilby on 2010-03-27
> **wojox said:**
> You need to shut down Synaptic Package Manager or Ubuntu Software Center. You can only have only package manager open at a time. ;)

I didn't have either open when I tried it. However, I restarted my laptop and tried again. The process apparently worked, but when I tried a DVD, I got the message:

[I]The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

[/I]The computer then searched for the plugin and didn't find anything. To my surprise it then proceeded to play the dvd, but only the director's commentary.

I then tried to play the dvd with a program I had downloaded in an earlier (failed) attempt, VLC media player. This worked without any noticeable problems.

Problem solved.
Thank-you very much,

Trilby  :-D

---

