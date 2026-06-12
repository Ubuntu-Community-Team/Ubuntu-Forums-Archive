---
title: "ATI Radeon 9200SE and resolution.."
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by bushtor on 2006-02-14
Hi,

I have tried to browse forum articles about this ut haven't found a detailed enough explanation to answer my question.

I have installed ubuntu 5.10 and got it up and running without problems ;-)

However my screen resolution is restricted to a max 1024 x 768.  My screen and card is well capable of 1280x1024 and I wonder how I can tweak the system to use this resolution.  The max selectable is 1024x768.

The video card is actually a ATI Radeon 9200 SE, but in xorg.conf it is referred to as:

Identifier "NVIDIA Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
Driver	"nv"
BusID	"PCI:2:0:0"

Thanks in advance for a tip to a relevant howto or the necessary steps to have my card display 1280x1024.

best regards

Tor

---

### Post by gremlin hunter on 2006-02-14
sudo dpkg-reconfigure xserver-xorg

Then just follow along.

---

