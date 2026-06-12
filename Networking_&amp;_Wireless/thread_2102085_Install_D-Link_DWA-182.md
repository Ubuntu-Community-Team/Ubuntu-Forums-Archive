---
title: "Install D-Link DWA-182"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by IoSonoIo on 2013-01-06
Hi, i have received a usb pen to connect my pc to internet via wireless. 
It's a D-Link DWA-182. The problem is that i don't know how install it on my ubuntu 12.10. 
I have looked about drivers but nothing. Have anyone ideas about how to proceed? 
On window the installation works. 

Txs a lot for you're help

---

### Post by kurt18947 on 2013-01-06
Could you plug your D-Link DWA-182 in, open a terminal and paste the output of this command?

```
lsusb
```The output should look something like this:

```
$ lsusb
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 003 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]**
Bus 005 Device 002: ID 047d:2048 Kensington 
Bus 009 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f9:01f3 Brother Industries, Ltd 

```The bolded line is what we're interested in.  It should tell what chip set the device uses.

You might have a better response if this were moved to the networking and wireless forum.  You can click the 'report abuse' button and ask a mod to move it.  Just because you click the 'report abuse' button doesn't necessarily mean it's an abusive post.  It's simply a way to get a mod's attention.

---

### Post by IoSonoIo on 2013-01-27
Hi Kurt. Tank's for you're response. I'm so sorry that i Answer only now. But I stayed away of Pc why I had private trouble on last time. 

Ok I did what you asked: 

 > Bus 002 Device 003: ID 2001:3101 D-Link Corp.

This was the answer. 

And now?

---

### Post by wildmanne39 on 2013-01-27
*Thread moved to **Networking & Wireless**.*

---

### Post by kurt18947 on 2013-01-27
> **IoSonoIo said:**
> Hi Kurt. Tank's for you're response. I'm so sorry that i Answer only now. But I stayed away of Pc why I had private trouble on last time. 

Ok I did what you asked: 

 

This was the answer. 

And now?

Not very good news I'm afraid.  Here is some information on your device:

[http://www.wikidevi.com/wiki/D-Link_DWA-182_rev_A1](http://www.wikidevi.com/wiki/D-Link_DWA-182_rev_A1)

It looks to be *really* new which is not necessarily good in the linux world.  There seems to be no linux support as yet and the Windows drivers are in .exe form which makes it more difficult to even try NDISwrapper.  A faint bit of good news is that Windows XP is supported.  If you can install this device on Windows XP, you might be able to copy the device's .inf and .sys and use them with NDISwrapper and see what happens.  I know nothing about NDISwrapper so am of little use there.  I believe the NDISwrapper found in the 12.04 repos is broken, it's recommended to download the source and build your own.  Another issue with NDISwrapper is that if you're using 64 bit Ubuntu, you need the drivers for 64 bit WindowsXP unless the Dlink windows driver works on both.

---

### Post by IoSonoIo on 2013-01-30
Ok I understand :( Then I have to wait....

Tanks a lot :)

---

