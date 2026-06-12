---
title: "how to install b43-fwcutter?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by spicetrader on 2011-08-18
Can you help me with this most perplexing problem?

I have a compaq Presario C500 windows vista and I installed Ubuntu natty Ubuntu 11.04 by using Wubi.

What I really need right now is an executable b43-fwcutter, and I don't know how to get it.

When I boot up in Ubuntu, I've got no wireless. There's an access point I can connect to (if not using Ubuntu), but Ubuntu isn't activating the interface card. I've got no wired interface nor hope of one.

I slogged through countless webpages and came to the instruction (at [http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#device_firmware_installation)) that I should install b43-fwcutter and use it on wl_apsta_mimo.o. It tells me to install using command

`sudo apt-get install b43-fwcutter'

(sorry if that's not the proper etiquette for posting a command)

but I can't install with that command because apt-get wants to use the Internet. (err msg: "E: Unable to locate package b43-cutter")

So, I have wl_apsta_mimo.o and the other files that come with it in directory broadcom-wl-4.150.10.5.

But I don't have b43-fwcutter and I can't figure out how to get it.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access) tells me "b43-fwcutter is located on the Ubuntu install media under ../pool/main/b/b43-fwcutter/ " but I can't find that directory. Where is it?

All I need (I think) is the b43-fwcutter binary. Just one file.

---

### Post by bcbc on 2011-08-18
You can mount the desktop CD ISO that wubi uses to install. It keeps it, but for some reason it's hidden.

```
sudo mount -o loop /host/ubuntu/install/.fuse_hidden0000000400000001 /mnt
```

Then you'll find the package at /mnt/pool/main/b/b43-fwcutter/

Afterwards, unmount the ISO
```
sudo umount /mnt
```

---

