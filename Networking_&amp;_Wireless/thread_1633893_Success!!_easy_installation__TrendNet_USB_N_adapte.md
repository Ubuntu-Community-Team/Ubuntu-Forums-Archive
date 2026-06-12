---
title: "Success!! easy installation  TrendNet USB N adapter"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by walt.smith1960 on 2010-11-29
I thought with the trials and travails of Wireless, Linux and 802.11N adapters, I'd post a success story.  I bought a Trendnet TEW-649UB USB single frequency adapter.  lsusb indicates the following:

ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

 I enabled wireless backports in Maverick and the adapter showed up in Network Manager but showed disconnected and wouldn't connect.  Dmesg indicated that firmware wasn't loading. This seems to be a somewhat common problem with the Realtek 819X chipset.  I was feeling impatient so used NDIS-GTK. I got the Windows XP drivers off the CD and they installed no problem at all.  I suspect I might have better performance with the native software and may pursue that when I have time and need a project. But for now Maverick and ThinkPad T61 are happy with their new toy.

Edit:  Not all is sweetness & light.  The device works great.  It seems to not want to resume after being suspend. Unplugging and re-plugging fixes the problem.

---

### Post by walt.smith1960 on 2010-12-03
I was able to get Lucid to work with native software after reading this bug fix:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)
Everything works as expected.

---

### Post by MajesticHazard on 2011-01-19
I was looking for a usb adapter to connect my box to a 802.11N router at 5GHz. I was hoping you could confirm that that actually worked, not just the b or g bands. I haven't seen many success stories and I've had a few false starts with other adapters.

---

