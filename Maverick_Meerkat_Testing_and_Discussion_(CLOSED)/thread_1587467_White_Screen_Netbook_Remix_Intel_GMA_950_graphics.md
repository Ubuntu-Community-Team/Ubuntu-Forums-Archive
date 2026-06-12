---
title: "White Screen Netbook Remix Intel GMA 950 graphics"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by marcog on 2010-10-03
I have noticed several threads about a white screen when upgrading. I have the same problem, but one difference: I'm not running in ATI. I'm running on a Lenovo S10-2 with Intel GMA 950 graphics.

Some entries from dmesg logs:

20:16 < marcog> [drm] MTRR allocation failed. Graphics performance may suffer.
20:16 < marcog> just above that: mtrr: no more MTRRs available

Any suggestions on where to start digging?

---

### Post by kansasnoob on 2010-10-03
Have a look here:

[http://ubuntuforums.org/showpost.php?p=9893106&postcount=16](http://ubuntuforums.org/showpost.php?p=9893106&postcount=16)

---

### Post by marcog on 2010-10-03
> **kansasnoob said:**
> Have a look here:

[http://ubuntuforums.org/showpost.php?p=9893106&postcount=16](http://ubuntuforums.org/showpost.php?p=9893106&postcount=16)

Thanks, but that didn't work :(

---

### Post by drmartens on 2010-10-03
I won't help, just wanted to add that I have the same info in dmesg for Intel GMA4500, but everything seem to work (both laptop screen and external monitor). Of course, login screen has wrong resolution, but that's a different issue...

So maybe those "MTTRs" are not the culprit after all. 

But I didn't  upgrade - it was a fresh install. I only upgraded Ubuntu like 5 years ago and decided back then, that it simply was too unreliable (every attempt was full of bugs). Since then I've been doing a fresh install every 6 months and it's been quite good so far, even with betas. 

Good luck!

---

### Post by kerry_s on 2010-10-03
in "~/.profile" put "export CLUTTER_VBLANK=none".

---

### Post by marcog on 2010-10-03
> **kerry_s said:**
> in "~/.profile" put "export CLUTTER_VBLANK=none".

Thanks, but that doesn't work. :(

Here's some info that might help:

I booted into low graphics mode and it worked, but then gave an error dialog saying something about the graphics driver not supporting Unity. Then I also tried the gdm session "Ubuntu Netbook 2D" and that works, except for the panel which is completely broken.

---

### Post by kerry_s on 2010-10-03
> **marcog said:**
> Thanks, but that doesn't work. :(

Here's some info that might help:

I booted into low graphics mode and it worked, but then gave an error dialog saying something about the graphics driver not supporting Unity. Then I also tried the gdm session "Ubuntu Netbook 2D" and that works, except for the panel which is completely broken.

there is no netbook 2d for ubuntu 10.10, are you running a clean install?

---

### Post by marcog on 2010-10-03
> **kerry_s said:**
> there is no netbook 2d for ubuntu 10.10, are you running a clean install?

This is an upgrade from Lucid.

---

### Post by kerry_s on 2010-10-03
> **marcog said:**
> This is an upgrade from Lucid.

no wonder, there was a huge change in netbook, the new unity uses mutter.

i would suggest you grab a netbook live cd & try running from that.
[http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/maverick-netbook-i386.iso](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/maverick-netbook-i386.iso)

---

### Post by marcog on 2010-10-03
So is a fresh install advised?

I'll try grab a CD from someone.

---

### Post by cariboo on 2010-10-03
I would check to see if your upgrade completesd as it sound like something went wrong during the process. When you are at the white screen, press Ctrl-Alt F1, and login, once logged in type:

```
sudo apt-get -f install
```

Seeing as you are doing an upgrade, you will still have aptitude installed, so once the above command is finished type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Once the above two commands have finished, type:

```
sudo reboot
```

Once you are back at the login screen you should have the following session choices:

[list]
[*] Recovery Console
[*] Ubuntu Desktop Edition
[*] Ubuntu Desktop Edition (Safe Mode)
[*] Ubuntu Netbook Edition
[*] User Defined Session
[/list]

---

### Post by marcog on 2010-10-04
> **cariboo907 said:**
> I would check to see if your upgrade completesd as it sound like something went wrong during the process. When you are at the white screen, press Ctrl-Alt F1, and login, once logged in type:

```
sudo apt-get -f install
```


This command doesn't install/remove/do anything. So I take it the upgrade did complete first time round. Anyway, did an update+safe upgrade as well and it didn't fix anything. Still get the Netbook Remix 2D session as well.

---

### Post by sendblink23 on 2010-10-04
> **marcog said:**
> This command doesn't install/remove/do anything. So I take it the upgrade did complete first time round. Anyway, did an update+safe upgrade as well and it didn't fix anything. Still get the Netbook Remix 2D session as well.

I would suggest you to back up any important data(to an external hd)... then do a Fresh Install and you would be fine afterwards

---

### Post by tekknokrat on 2010-10-07
I have the white screen issue with maverick-beta and gnome session (unity removed by package) on intel graphic. 

Unity has slow performance and steals the left side of the screen therefore I tried to revert back to a gnome-session without unity but had no luck yet. Any idea :confused:

---

