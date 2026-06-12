---
title: "[USB Soundcard] Tascam US-122 not working in dapper."
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by Ivhassel on 2006-06-07
I have a Tascam US-122 external USB soundcard, but I can't get it to work in Kubuntu 6.06 LTS. I only bought it recently, so I don't know if it works on breezy, but [this howto]("http://www.ubuntuforums.org/showthread.php?t=30891") seems to claim it worked.

I installed these alsa packages from ubuntu repositories:
I removed & reinstalled all these packages twice, to ensure that this is not the step where it went wrong.
```

alsa-base
alsa-firmware-loaders
alsa-tools
alsa-tools-gui
alsa-utils
alsamixergui
fxload

```

After bootup, *lsmod | grep snd* only reports only my onboard soundcard, an AC97 chip, with the snd_intel8x0 driver. So the driver for the Tascam Us-122 isn't loaded automatically (which seems to prove that something is wrong).

I then proceed to do the following:
> 
root@ingmar-laptop:~# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface **(without fw)**
Bus 002 Device 001: ID 0000:0000
root@ingmar-laptop:~# modprobe snd-usb-usx2y
root@ingmar-laptop:~# /sbin/fxload -s /home/ingmar/alsa-firmware-1.0.10/usx2yloader/tascam_loader.ihx -I /home/ingmar/alsa-firmware-1.0.10/usx2yloader/us122fw.ihx -D /proc/bus/usb/002/002
root@ingmar-laptop:~# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 002 Device 001: ID 0000:0000
root@ingmar-laptop:~# usx2yloader
usx2yloader: no US-X2Y-compatible cards found


The above is based on [this howto]("http://alsa.opensrc.org/usb-usx2y").
The path to the firmware I'm trying to load with fxload is different than the one in the howto, simply because my kubuntu install doesn't have the firmware in that directory. I took the firmware from [ftp://ftp.alsa-project.org/pub/firmware/](ftp://ftp.alsa-project.org/pub/firmware/) , more precisely File: alsa-firmware-1.0.10.tar.bz2, which is the version that corresponds to the dapper packages. ( that seemed like the smart thing (tm) to do )

Anyone any idea what's wrong?
Do I need to re-configure anything in some alsa config file ?

If more info is required, I'll provide that asap.

Hopefully I can get this to work, with a little push in the right direction
Thanks for all coming answers :wink:

---

### Post by Ivhassel on 2006-06-07
After 2 more hours of googling, I found this bug:
 [https://launchpad.net/distros/ubuntu/+source/alsa-tools/+bug/45880](https://launchpad.net/distros/ubuntu/+source/alsa-tools/+bug/45880)

In short: The firmware for this card is not present in the alsa debs available in the repos, and I'll have to compile alsa from source. No biggie, I'll try to up a howto once it works, and should I find the time.

If anyone still could add anything that might prove helpfull, please do. :)

---

### Post by SFN on 2006-06-09
Iwrote [this one]("http://ubuntuforums.org/showthread.php?t=30891&highlight=tascam") a while back for Hoary. It worked then. I haven't tried it since then.

I haven't read what you've posted here, only because I'm exhausted right now. I just posted this in case it shed any light for you.

---

### Post by Ivhassel on 2006-06-10
[QUOTE=SFN]Iwrote [this one]("http://ubuntuforums.org/showthread.php?t=30891&highlight=tascam") a while back for Hoary. It worked then. I haven't tried it since then.[/QUOTE]
Thanks for your reply !
Yes I saw that, but since it uses hotplug, which has been replaced with udev, it's kinda obsolete I thought. I gotta thank you though, the links definitely pointed me in the right direction, and now it's working!

[QUOTE=SFN]
I haven't read what you've posted here, only because I'm exhausted right now. I just posted this in case it shed any light for you.[/QUOTE]
Oh, don't bother anymore, it works now, that's all I wanted.

Could you do me one favor though? 
If you open Alsamixer from the command line:
```

alsamixer

```

Which gives me this output:
```

ingmar@ingmar-laptop:~$ alsamixer
No mixer elems found

```

Do you have that too ? Or would that be a configuration issue on my part ?
I disabled my onboard soundcard, before I did I could use alsamixer for that, but since that card is broken, that seemed kinda useless. :-)

---

### Post by SFN on 2006-06-11
[QUOTE=Ivhassel]
Could you do me one favor though? 
If you open Alsamixer from the command line:
```

alsamixer

```

Which gives me this output:
```

ingmar@ingmar-laptop:~$ alsamixer
No mixer elems found

```

Do you have that too ? Or would that be a configuration issue on my part ?
I disabled my onboard soundcard, before I did I could use alsamixer for that, but since that card is broken, that seemed kinda useless. :-)[/QUOTE]

No, I don't have that.

I just redid that HOWTO that I referenced earlier and updated it for Dapper. Not much changed but as I mention in the new HOWTO, I had done the Ubuntu Studio install earlier. That HOWTO can be found [here]("http://ubuntuforums.org/showthread.php?t=194490").

---

