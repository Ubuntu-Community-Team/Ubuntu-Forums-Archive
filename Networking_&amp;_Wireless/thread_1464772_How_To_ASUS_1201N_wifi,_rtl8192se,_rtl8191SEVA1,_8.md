---
title: "How To: ASUS 1201N wifi, rtl8192se, rtl8191SEVA1, 8171"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2010-04-28
I listed all possibilities for how this device will show up.  Although the driver loads in Lucid, it does not work.  It makes wlan0 appear, but it will not connect to anything, even by trying to use terminal commands.

Mini How To (and this works on 32 or 64 bit Lucid and probably any others):

1.
Go to 
[https://launchpad.net/~matt-price/+archive/mattprice](https://launchpad.net/~matt-price/+archive/mattprice) and add the ppa to your sources

2.
sudo apt-get update && sudo apt-get install rtl8192se-dkms 

3. 
Go to 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)
and get to post 288 and follow any directions there and in subsequent posts.  Apparently it does not wake from suspend properly until you do the tweaks.

---

