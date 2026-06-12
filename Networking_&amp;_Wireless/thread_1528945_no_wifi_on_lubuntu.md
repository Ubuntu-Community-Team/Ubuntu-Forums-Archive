---
title: "no wifi on lubuntu"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by supermooshman on 2010-07-11
Hi all, 

I just installed lubuntu on my eee 901, and everything seems to be ok, but my wireless card doesn't seem to be detected?

if I type ifconfig -a, it does not show (in ubuntu it worked like a charm)

does anyone know how to solve this?


ps: in anohter thread I found a reference to the following, but since I have no idea if that is what can help me I am hesitant to try it, if anyone has experience, can they have a look if this would help me?
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

many thanks

---

### Post by ov3rcl0ck on 2010-07-11
This isn't a LUbuntu only problem. You just need to install the drivers, they may be on backport because they haven't been tested or they have a bug.

You'll have to install:
```

sudo apt-get install linux-backports-modules-wireless-lucis-generic

```
for a PAE kernel:
```

sudo apt-get install linux-backports-modules-wireless-lucis-generic-pae

```

I think the first one will cover 64bit, but not sure.

---

### Post by supermooshman on 2010-07-11
> **ov3rcl0ck said:**
> This isn't a LUbuntu only problem. You just need to install the drivers, they may be on backport because they haven't been tested or they have a bug.

with the risk of sounding extremely stupid: eh?

does that mean that for the time being I am stuck to the cable?

---

### Post by cavalier911 on 2010-07-11
Please run these 2 commands in lxterminal and paste results from both in reply so we can identify the wireless interface

```
sudo lshw -C network
```

From this output find bus info: 
Take last 5 numbers on the right. 
(example) bus info: pci@0000:**00:0d.0**

```
lspci -s **00:0d.0** -vv
```

---

### Post by supermooshman on 2010-07-11
ok, now I feel really stupid...

I found the answer here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443)

apparently the "trick" was to press fn+f2, don't know if that is the bulletproof solution, but it seems to work for me

anyway thank you both for your input!
cheers

---

### Post by djaqed on 2012-01-04
So, I have a EEEPC Asus 701 and my wifi isn't working either. I tried the apt-get for the package you said it couldn't find it. Any other suggestions?

---

### Post by wildmanne39 on 2012-01-04
Hi, you should start your own thread to get better support this one is old.
Thanks

---

### Post by coffeecat on 2012-01-05
@djaqed, please start your own thread.

Old thread closed.

---

