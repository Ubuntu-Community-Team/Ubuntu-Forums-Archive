---
title: "Unable to get alsa firmware from ftp site"
date: 2012-12-24
forum: Multimedia Software
---

### Post by eboats on 2012-12-24
I'm trying to download alsa firmware drivers specified in Step 2 of the below page to get my Tascam US-122 usb interface working on my Ubuntu 12.10 :

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

When I try    
wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.19.tar.bz2)

I get the below Connection refused error :

Connecting to ftp.alsa-project.org (ftp.alsa-project.org)|77.48.224.243|:21... failed: Connection refused.

Is this ftp site down?

---

### Post by andrew.46 on 2012-12-25
> **eboats said:**
> Is this ftp site down?

Connection fails from here as well. Searching for that particular file shows it is held in various places including here:

[http://mirrors.wayround.org/www.alsa-project.org/rsync/firmware/](http://mirrors.wayround.org/www.alsa-project.org/rsync/firmware/)

as well as updated versions. Unfortunately I don't know enough about this area to comment on whether the newer versions are better / safer etc.

---

