---
title: "Can't play DVDs"
date: 2010-10-20
forum: Multimedia Software
---

### Post by valero80 on 2010-10-20
I'm trying to watch Blade Runner but every time I try to open it with Totem it tells me "could not read from resource". I heard VLC is supposed to play it fine but it doesn't do anything other than making my drive make a noise. I read in another post to install regionset but that didn't do anything. Any help?

---

### Post by andrew.46 on 2010-10-20
Hi valero,

The best documentation for enabling dvd playback can be seen here:

Restricted Formats Playing DVDs
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Hopefully this will get your dvds playing :).

Andrew

---

### Post by mc4man on 2010-10-20
Do you have libdvdcss2 installed?
If not or unsure run this in a terminal
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by tommcd on 2010-10-20
> **valero80 said:**
> I'm trying to watch Blade Runner but every time I try to open it with Totem it tells me "could not read from resource". ...
Make sure that **libdvdcss2** is installed as Mc4man said. You can get it by enabling the Medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Also try installing the **xine** player. Xine is great for playing DVDs.
```
sudo apt-get install xine-ui
```

---

### Post by jimmers on 2010-10-21
Hi Velaro,
I am running Lucid, and use VLC with no problems, you could always try Kaffeine with Gxine installed, I had trouble watching DVDs with Karmic until I installed Kaffeine & Gxine.

Luck

---

### Post by perspectoff on 2010-10-21
From 

[http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability)

or

[http://kubuntuguide.org/All#DVD_Playback_Capability](http://kubuntuguide.org/All#DVD_Playback_Capability)

You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories from the command-line interface (Terminal or Konsole): 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb

VLC is the best video player (although MPlayer is a pretty close 2nd, IMO). 

Oh yes, VLC had a bug in one of its updates. When you open your DVD (Media -> Open Disc) make sure the disc device is

/dev/sr0

(or sometimes /dev/cdrom0, depending on your system).

In one of the updates it got changed and the DVD device wouldn't be accessed.

(I personally don't care for Xine, Kaffeine (for DVDs, anyway), DragonPlayer, Totem, or any other players which are far less powerful than VLC and MPlayer.)

---

### Post by NM5TF on 2010-10-21
> **valero80 said:**
> I'm trying to watch Blade Runner but every time I try to open it with Totem it tells me "could not read from resource". I heard VLC is supposed to play it fine but it doesn't do anything other than making my drive make a noise. I read in another post to install regionset but that didn't do anything. Any help?
did this happen after an upgrade by any chance??? same thing happened to me after last 2 upgrades...look at fstab to see if /media/cdrom0 is present...

---

### Post by linuxwonder on 2010-10-21
hi mc4man: Did the  "libdvdcss2" install as you suggested on my 10.04 system and it worked like a charm! Thanks!

---

### Post by sirius56 on 2010-10-22
After installation of 10.10, I lost all DVD capability.

The terminal command given above in #4 restored video.

Thank you.

sudo /usr/share/doc/libdvdread4/install-css.sh

---

