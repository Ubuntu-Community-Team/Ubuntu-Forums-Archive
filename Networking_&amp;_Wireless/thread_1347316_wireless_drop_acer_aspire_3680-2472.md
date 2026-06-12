---
title: "wireless drop acer aspire 3680-2472"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by joekeno on 2009-12-06
Hi all, I seem to have lost all the kernel drivers for my wifi set up and even virtual box with the latest update of ubuntu. how would I fix this? Do I need to do a complete reinstal?

I have a acer aspire 3680 with already installed broadcom sta wireless driver (which has been working)
when I run this command on a fresh install in the past it worked for me

sudo apt-get install linux-backports-modules-karmic-generic

sudo apt-get install b43-fwcutter

echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf

echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf

but not nothing
tells me I have all the info already

can anyone help me with this?

---

