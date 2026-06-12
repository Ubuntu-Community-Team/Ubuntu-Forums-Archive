---
title: "USB wireless - works on &quot;trial&quot; version of Ubuntu, not on the full version."
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by jp235 on 2009-06-23
Hi all

I have a really old laptop that I used to run Ubuntu 8 on, wanted to switch to Ubuntu 9. This is an ancient laptop with no in-built wireless, so I use a USB adaptor.

I ran the CD in the "Try without installing" mode from the CD, everything worked fine. It recognised the USB wireless adaptor immediately and worked a treat, but now I have installed Ubuntu 9 properly, it won't see the adaptor at all.

Anyone had this before? Any solutions?

Cheers :)

(PS, if anyone saw my post last week, this is not the EeePC I asked about before, it's a different machine)

---

### Post by coffeecat on 2009-06-23
Have you tried other USB devices with the hard drive install? Are they detected?

Post the terminal output of:

```
lsusb
```

---

### Post by jp235 on 2009-06-23
USB memory sticks work fine. lsusb results are as follows:

Bus 002 Device 001: ID ld6b 0001 Linux Foundation 1.1 rout hub
Bus 001 Device 001: ID ld6b 0001 Linux Foundation 1.1 rout hub

Thanks :)

---

### Post by coffeecat on 2009-06-23
I forgot to ask you to make sure the USB wireless device was plugged in when you did lsusb, but I'm sure you did! :p If so, it's not being detected by the USB driver which is why network manager can't find it.

You mention you have an EeePC. Does it have some sort of Linux on it? Or have you another machine running any Linux distro? If so, plug the wireless USB device into the Eee or whatever other machine you've got, open a terminal and try lsusb again. Post the output. What I'm wondering is if the wireless NIC developed a fault just as you installed Ubuntu to the old laptop. If we do lsusb on another machine, at least we can see if it's being detected there.

Another thought: it look as though you have two USB sockets on the laptop. Have you tried the wireless device in both?

---

### Post by jp235 on 2009-06-23
Good point - the laptop has 3 sockets, but it seems to only detect 2. I tried the wireless adaptor in all of them but it still doesn't work.

OK, plugged the adaptor into the eeepc, did the same thing, here's the result. I guess it is the 1st line that you are interested in, but here the whole thing just in case :)

jp235@jp235-laptop:~$ sudo lsusb
Bus 001 Device 008: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thanks again for your time!

---

### Post by coffeecat on 2009-06-24
Well, at least this line...

> **jp235 said:**
> Bus 001 Device 008: ID 0ace:1215 ZyDAS WLA-54L WiFi

...tells us that the wireless dongle is being detected on your Eee and is not completely dead. But why it was detected (and used) on the old laptop in live CD mode and not when you installed to hard disc I'm at a loss to understand.

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1110139&highlight=0ace%3A1215+ZyDAS+WLA-54L+WiFi&page=2](http://ubuntuforums.org/showthread.php?t=1110139&highlight=0ace%3A1215+ZyDAS+WLA-54L+WiFi&page=2)

...where the OP is using a wireless device with the same chipset as yours, and the appropriate wireless driver is zd1211, apparently. There might be some clues there for you, particularly the last post from the OP. I've looked in my /lib/firmware and zd1211 is there, so it does come with a default install. But this still doesn't explain why lsusb is not detecting it, and why it worked with the live CD.

---

### Post by jp235 on 2009-06-24
I'll give that a go, thank you so much for your help, much appreciated :)

---

### Post by iponeverything on 2009-06-24
Try this do get some debug output:

unplug the usb dongle

Open a terminal and run:

```

cd /var/log
tail -vf debug messages

```

Then plug the usb dongle back in.

then run 

```

sudo modprobe zd1211

```

post the output the of tail command.

---

