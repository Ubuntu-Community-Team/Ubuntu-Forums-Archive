---
title: "Can't download new drivers with non-working wireless drivers..."
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by Smokersroom on 2010-06-27
Hi All,

I've installed Ubuntu Netbook 10.04 on my HP DV2000 laptop and now I want to get my wireless to work by installing the proprietary broadcom drivers (4311, I think). But my internet doesn't work yet obviously, so I need to download the drivers to my thumb drive on my desktop and install them on my non-networked laptop.

My issue is that I don't know:

a) Where to get the drivers
b) How to install them from a local drive

Is there a guide as to how to do this?

Thanks in advance.

S.

---

### Post by bumanie on 2010-06-27
Look at the output of  > sudo lshw -C networkMy wireless card is disabled, I am trying to find a solution. Look[ here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454") for a possible fix if yours comes up as disabled. Mine keeps reverting back to disabled after a reboot, some others seem to have found permanent fixes in the lauchpad thread, linked above.

---

### Post by bkratz on 2010-06-27
> **Smokersroom said:**
> Hi All,

I've installed Ubuntu Netbook 10.04 on my HP DV2000 laptop and now I want to get my wireless to work by installing the proprietary broadcom drivers (4311, I think). But my internet doesn't work yet obviously, so I need to download the drivers to my thumb drive on my desktop and install them on my non-networked laptop.

My issue is that I don't know:

a) Where to get the drivers
b) How to install them from a local drive

Is there a guide as to how to do this?

Thanks in advance.

S.

You might want to look at this thread esp. section 2 regarding b43 without internet access.

[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146)

---

