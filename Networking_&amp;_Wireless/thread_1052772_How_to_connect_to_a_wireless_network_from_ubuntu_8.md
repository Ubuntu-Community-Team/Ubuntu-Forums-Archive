---
title: "How to connect to a wireless network from ubuntu 8.1.0"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by parvathy on 2009-01-28
hi,
i have a dell xps M1530 laptop. i wanted to connect to a wireless network. i tried the iwconfig command. it gave an error saying that 
"no wireless extensions" .Is it because that my ubuntu version (Hardy) doesn't have the needed driver. how can i find the exact driver for my laptop?

 thanking you all for the help you have offerde me till now,

with love
paru

---

### Post by kreggz on 2009-01-28
try to type jockey-gtk at the command line and it may detect the drivers you need.

To find your wireless card try:

lspci | grep Ethernet

you should have two entries

---

