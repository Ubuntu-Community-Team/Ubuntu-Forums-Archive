---
title: "help please. installing natty from usb, cli installer can not find cdrom media"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doobidoobida on 2011-04-17
I'v been wrestling with installing ubuntu natty on a powerpc. I'v managed to boot natty installation from usb through openfrimware and the yaboot files found here [http://ports.ubuntu.com/dists/natty/main/installer-powerpc/current/images/powerpc/hd-media/](http://ports.ubuntu.com/dists/natty/main/installer-powerpc/current/images/powerpc/hd-media/) . I'm now at a pink screen with a guided installation wizard. eveything goes well up until it searches the drives for an "installer ISO". it reports an error stating "could not find media in cdrom...".

My understanding is that I am supposed to copy the natty-desktop-powerpc.iso onto the drive. I'v done that. I'v even tried extracting the iso onto the drive. I'v even gone as far as creating a seperate partition and using the "dd if=natty.iso of=/dev/sda3" to clone the iso into that partition. 

on the pink setup screen I'v entered the installers built in bash shell and looked through the "cdrom" directory and the ISO contents are mounted in there, aswell in the "hd-media" dir. the iso file is there...
I don't understand what I'm doing wrong. could anyone be kind enough as to shed some light on my dilema? I'd greatly appreciate it.

just as a note for awareness, I should state that I'v been following instructions from this 8.04 installation guide [https://help.ubuntu.com/8.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/ch05s01.html). I know this is not an installation guide for 11.04 but I'v figured the difference is minimal.

---

### Post by dino99 on 2011-04-17
[http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu](http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu)

---

### Post by wojox on 2011-04-17
Download the [mini.iso]("http://ports.ubuntu.com/dists/natty/main/installer-powerpc/current/images/powerpc/netboot/") from here and dd it onto your usb.

---

### Post by doobidoobida on 2011-04-17
Thank you much for your replies!

wojox, this installation asks for an ubuntu archive mirror address. is this a network install where I need a  second computer configured with a tftp and dhcp service installed on the same network? if not, what am I supposed to use as the url

---

### Post by wojox on 2011-04-17
> **doobidoobida said:**
> Thank you much for your replies!

wojox, this installation asks for an ubuntu archive mirror address. is this a network install where I need a  second computer configured with a tftp and dhcp service installed on the same network? if not, what am I supposed to use as the url

Try:

```
ports.ubuntu.com
```

---

### Post by doobidoobida on 2011-04-17
did that, then it asks for directory with a default value of "/ports-ubuntu/" I leave that on and it starts downloading and installing then freezes.

---

### Post by uRock on 2011-04-17
Moved to Natty Narwhal Testing & Discussion.

---

### Post by Yellow Pasque on 2011-04-17
> eveything goes well up until it searches the drives for an "installer ISO". it reports an error stating "could not find media in cdrom..."
You need to add this to the boot options:
```
cdrom-detect/try-usb=true
```

---

### Post by doobidoobida on 2011-04-18
How would I get to the boot options?

---

### Post by Yellow Pasque on 2011-04-18
> **doobidoobida said:**
> How would I get to the boot options?
Press 'e' (for edit).

---

### Post by nicc777 on 2011-04-26
I also have some issues with PPC. I have an eMac and the CD boots fine and the installer runs ok up to a point where I get the error message "An error has been detected while trying to use the specified Ubuntu archive mirror"

I used the ISO from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and downloaded the PPC ISO with a time stamp of "26-Apr-2011 00:04".

I tried also installing without the network - assuming it would just use the CD/DVD media to complete the install, but no cigar. It keeps getting stuck with the same error and each time you click the "Ok" button the screen just re-appears until you click about 20 odd times by which time the button has no more effect.

Any ideas?

---

