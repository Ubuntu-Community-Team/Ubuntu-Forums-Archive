---
title: "Problem with BT878 chipset TV card"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by gaspar on 2006-12-19
Hi all,
well, I have a TV Capture Card with a BT878 chipset, under Ubuntu Edgy.
The problem is, even after a clean install, Ubuntu can't deal with it.
At starting up, and with dmesg, I get this error:

[17179571.500000] PCI: Error while updating region 0000:02:09.0/0 (f5000008 != ffffffff)
[17179571.500000] PCI: Error while updating region 0000:02:09.5/0 (f5002008 != ffffffff)

A little help here, please?](*,)

---

### Post by lvanderree on 2007-01-15
I just tried to get my old BT878 working:
I had no signal and I think I also saw this error too.

The trick is to set the correct to enter the correct options. when loading the module.

so make sure you have a line

```

  bttv

```
in sudo vi /etc/modules

and your options in

sudo vi /etc/modprobe.d/options

```

  options bttv radio=1 card=50 tuner=5

```

Unfortunately it is a little struggle to find the correct magic numbers, but this works for me, (although I haven't got any audio yet, but I'm sure to find this out as well).

You can find the codes in this file: [http://dl.bytesex.org/releases/video4linux/bttv-0.9.14.tar.gz](http://dl.bytesex.org/releases/video4linux/bttv-0.9.14.tar.gz), just take a look at the CARDLIST files

---

