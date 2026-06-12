---
title: "No wireless on Toshiba Portege"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by putnam120 on 2011-05-02
I recently bought a Toshiba Portege R835 and wanted to install Ubuntu on it. I wasn't too surprised that the wireless wasn't working, but what does bother me is that Ubuntu doesn't even recognize that I have a wireless card. I haven't installed Ubuntu you (10.04) because of this, however I am able to get online through a wired connection. Can anyone help me, or tell me what other information I would need to provide in order to get some help?

Thanks in advance.

---

### Post by birchhook on 2011-05-04
I just got my R830 and I'm trying to get the wireless working as well.  Please update this thread if you find anything, and I will if I find something.

---

### Post by birchhook on 2011-05-04
Ok I got my R830 working should be pretty much the same for the R835

The upshot is go to synaptic and install:
linux-backports-modules-compat-wireless-2.6.37-maverick-generic-pae
Then reboot

Here's what I did to get there:
went to terminal
$lspci -nn
one of the items was:
4:00.0 Network controller [0280]:Intel Corporation Device [8086:0091] (rev 34)

I searched google for "Intel Corporation Device" 8086:0091 
That brought up this german site which referenced the compat-wireless packages - it gives the instructions on how to install the latest source.  I tried that but it gave build errors.  I was about to try a stable version when I decided that I should just check to see if the packages were already in synaptic.  There are a ton of compat-wireless packages in synaptic, but most of them say not to install them directly, but to install the generic one. So that's what I did, but even then there were 4 to choose from.  I'm not sure which was the right one, but maverick pae seemed right.

Let me know how it goes.

---

### Post by putnam120 on 2011-05-14
Thanks, that and installing all the updates I needed solve my problem.
Sorry it took so long for me to get back to you, but I just got around to doing this yesterday.

---

