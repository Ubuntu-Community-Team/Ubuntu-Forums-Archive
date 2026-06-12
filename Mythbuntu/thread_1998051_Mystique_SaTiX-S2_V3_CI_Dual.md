---
title: "Mystique SaTiX-S2 V3 CI Dual"
date: 2012-06-06
forum: Mythbuntu
---

### Post by salain on 2012-06-06
Hi, 
I am trying to install the drivers for the PCIe **Mystique SaTiX-S2 V3 CI Dual. **

I have kernel 3.2.0-23 generic (x86_64).

Following the instruction on linuxtv.org, I have loaded the nGene module but it does not work and I think it is the wrong module for the card. 

I have attached the dmesg and lspci output. 

Any help would be much appreciate. 

Thank you 
Alain

---

### Post by salain on 2012-06-08
Got it working!

I use the instructions in the first post [here]("http://www.vdr-portal.de/index.php?page=Thread&threadID=105803&31fc03d2&l=2&534a1273")

It is in German, here is the steps I did to get my card working:

Get ther firmware
```
wget http://l4m-daten.de/downloads/firmware/dvb-s2/linux/all/ngene_18.fw
```Clone the experimental branch of  media_build
```
hg clone http://linuxtv.org/hg/~endriss/media_build_experimental
cd media_build_experimental make download make untar

```Deactivate unwanted module 
```
make menuconfig
```Compile
```
make
```install
```
sudo make install
```Reboot
This worked for me.  For more info follow the link above

Thank you

---

