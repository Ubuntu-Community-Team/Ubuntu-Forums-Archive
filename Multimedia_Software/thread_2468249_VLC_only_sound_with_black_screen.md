---
title: "VLC only sound with black screen"
date: 2021-10-22
forum: Multimedia Software
---

### Post by satimis on 2021-10-22
Hi all,

Playing .vob on VLC
only sound with black screen

Please help.

Thanks

Regards

---

### Post by monkeybrain20122 on 2021-10-22
How did you install vlc? .deb, snap or flatpak? It works here, vlc installed with flatpak.

---

### Post by satimis on 2021-10-22
> **monkeybrain20122 said:**
> How did you install vlc? .deb, snap or flatpak? It works here, vlc installed with flatpak.
I installed vlc on repo of Ubuntu 20.04

$ apt policy vlc```

vlc:
  Installed: 3.0.9.2-1
  Candidate: 3.0.9.2-1
  Version table:
 *** 3.0.9.2-1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```

After converting .vob to .mp4 running ffmpeg, then I can play the .mp4 file running videos without problem.  It is strange to me vlc unable to work?

Regards

---

### Post by monkeybrain20122 on 2021-10-22
Not sure why. Maybe your vlc is old. Mine is 3.0.16. It works here out of the box (mpv also works) Or maybe there is something about your file.

---

### Post by satimis on 2021-10-22
> **monkeybrain20122 said:**
> Not sure why. Maybe your vlc is old. Mine is 3.0.16. It works here out of the box (mpv also works) Or maybe there is something about your file.
I suppose the problem coming from the 4K display card on this PC [GeForce GTX 1650 SUPER].  Please refer to my another posting

How to install Dell 4K display 
[https://ubuntuforums.org/showthread.php?t=2468250&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2468250&highlight=satimis)

I ran vlc testing the same .vob file on another Ubuntu 20.04 PC, also connecting to the same Dell 4K display.  There is no such problem.

---

