---
title: "Network adaptor problem"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by Macfan1 on 2013-01-26
So I have an ASUS n13 usb network adapter and just installed ubuntu 12.  It worked on windows but when I switched it stopped, is it because I don't have the drivers?  It pops up with the networks around me but when I try to connect it infrequently connects then says I am not connected then keeps retrying.

---

### Post by ahallubuntu on 2013-01-26
Yeah, it uses the Realtek 8192CU chipset that is unfortunately SORT OF supported in Ubuntu 12.04 and 12.10 but doesn't quite work.  The  usual remedy is to blacklist the existing driver and download/install the latest from Realtek instead.

The driver from Realtek you want is RTL8192CU .  See this thread for specific instructions:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

---

### Post by Macfan1 on 2013-01-26
> **ahallubuntu said:**
> Yeah, it uses the Realtek 8192CU chipset that is unfortunately SORT OF supported in Ubuntu 12.04 and 12.10 but doesn't quite work.  The  usual remedy is to blacklist the existing driver and download/install the latest from Realtek instead.

The driver from Realtek you want is RTL8192CU .  See this thread for specific instructions:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

When I try to add files to the blacklist, the blacklist file doesn't exist and it won't let me make one, when I try to install them it says that I have errors. I have compile make driver error 2.

---

### Post by ahallubuntu on 2013-01-26
Are you sure you have the right driver?  RTL8192CU ?  There are a couple with similar names.  If you get the wrong one, it's not goig to build.  I have built this driver successfully several times in Ubuntu 12.04 and 12.10 - pretty sure it still builds easily.

I've never seen a new install of Ubuntu 12.04 that didn't have an existing /etc/modprobe.d/blacklist.conf file.  The installer seems to blacklist at least a few drivers.  Otherwise, you can just create your own.  In a terminal type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

If that's truly an empty file, copy the lines from my post of instructions into that file and save it.  But I truly doubt it's empty.

---

### Post by Macfan1 on 2013-01-26
Hmmm, I'm still getting the compile make driver error 2, and now ubuntu is saying system program problem detected.

---

### Post by Macfan1 on 2013-01-26
> **ahallubuntu said:**
> Are you sure you have the right driver?  RTL8192CU ?  There are a couple with similar names.  If you get the wrong one, it's not goig to build.  I have built this driver successfully several times in Ubuntu 12.04 and 12.10 - pretty sure it still builds easily.

I've never seen a new install of Ubuntu 12.04 that didn't have an existing /etc/modprobe.d/blacklist.conf file.  The installer seems to blacklist at least a few drivers.  Otherwise, you can just create your own.  In a terminal type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

If that's truly an empty file, copy the lines from my post of instructions into that file and save it.  But I truly doubt it's empty.

Hmmm, I'm still getting the compile make driver error 2, and now ubuntu is saying system program problem detected.

---

### Post by kurt18947 on 2013-01-26
Hmmm, this is sorta curious.  Like ahallubuntu I've installed RealTek's driver in the past.  It has worked perfectly. This morning I tried to install on the updated daily of 13.04 and got the error2 message.  I assumed it was because of the unfinished nature of the developmental version or the change to the 3.8 kernel.  Now I wonder.

---

### Post by ahallubuntu on 2013-01-26
> **kurt18947 said:**
> Hmmm, this is sorta curious.  Like ahallubuntu I've installed RealTek's driver in the past.  It has worked perfectly. This morning I tried to install on the updated daily of 13.04 and got the error2 message.  I assumed it was because of the unfinished nature of the developmental version or the change to the 3.8 kernel.  Now I wonder.

I'm not surprised it breaks on the new kernel, actually.  Realtek does seem to update this driver pretty regularly, though, so I'd expect a fix out fairly soon.

---

