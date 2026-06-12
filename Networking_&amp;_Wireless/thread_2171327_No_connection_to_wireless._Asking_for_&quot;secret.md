---
title: "No connection to wireless. Asking for &quot;secret password&quot;. Dell Precision 4700"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by roberto6 on 2013-08-30
Hi, I cannot get access to my wireless router. Everytime a window with the icon of a key pops up asking for the "secret password of #wireless name#". I introduce my password but it does not work. It seems it is in a sort of infinite loop.

Information:

root@fajnmp2:/home/imatge/fajnmp2/rbaena# uname -a
Linux fajnmp2 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

root@fajnmp2:/home/imatge/fajnmp2/rbaena# lspci | grep -i ethernet
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

root@fajnmp2:/home/imatge/fajnmp2/rbaena# lspci | grep -i network
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

root@fajnmp2:/home/imatge/fajnmp2/rbaena# lsusb | grep -i ethernet
root@fajnmp2:/home/imatge/fajnmp2/rbaena# lsusb | grep -i network

root@fajnmp2:/home/imatge/fajnmp2/rbaena# ifconfig -a
eth0      Link encap:Ethernet  direcciónHW d4:be:d9:82:0a:99
          Direc. inet:192.168.0.192  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::d6be:d9ff:fe82:a99/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:188688 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:112778 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:269583814 (269.5 MB)  TX bytes:13559743 (13.5 MB)
          Interrupción:20 Memoria:f7e00000-f7e20000 

 eth1      Link encap:Ethernet  direcciónHW a4:17:31:4b:52:6e
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:9 perdidos:0 overruns:0 frame:5959
          Paquetes TX:0 errores:25 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 
 lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:3327 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3327 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:328385 (328.3 KB)  TX bytes:328385 (328.3 KB)


 root@fajnmp2:/home/imatge/fajnmp2/rbaena# iwconfig
lo        no wireless extensions.

 eth1      IEEE 802.11abg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
 eth0      no wireless extensions.

Thanks!

---

### Post by bkline on 2013-08-30
Make sure you haven't inadvertently nudged the wireless switch to the "off" position.  That's bitten me more than once.

---

