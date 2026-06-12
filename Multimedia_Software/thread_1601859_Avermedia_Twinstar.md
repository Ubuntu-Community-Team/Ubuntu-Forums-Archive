---
title: "Avermedia Twinstar"
date: 2010-10-20
forum: Multimedia Software
---

### Post by avermedia on 2010-10-20
Hello,
 
Im trying to install my usb dtt Avermedia Twinstar on a Dreambox 800 receiver.
There is only one drivers and one image working at this moment but i would like to install other image on my box and install also my usb.
 
this is the reply when i try install
 
root@dm800:~# delitedtt.sh 
Usb device 0951:1603 non supported. 
Found compatible usb tuner af9035 
insmod: can't insert '/lib/modules/dvbt/mxl5007t.ko': invalid module format 
insmod: can't insert '/lib/modules/dvbt/tua9001.ko': invalid module format 
insmod: can't insert '/lib/modules/dvbt/af9033.ko': invalid module format 
insmod: can't insert '/lib/modules/dvbt/dvb-usb.ko': invalid module format 
insmod: can't insert '/lib/modules/dvbt/dvb-usb-af9035.ko': invalid module form
t 
rmmod: can't unload 'dvb_usb_af9035': unknown symbol in module, or unknown para
eter 
insmod: can't insert '/lib/modules/dvbt/dvb-usb-af9035.ko': invalid module form
t 
killall: usbtuner: no process killed

---

### Post by avermedia on 2010-10-22
any idea to create drivers for kernel 2.6.18.
 
this drivers are ok for compile method b works
 
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick)

---

