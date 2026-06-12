---
title: "VPN Crashing all Network Connection"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by toord on 2009-05-02
Hey guys,

I did a brief search around the forums about this problem to no avail. I found something relating hot to set up a vpn connection but am fairly certain this is not a setup related issue.

OK. I can establish a vpn connection with my workplace. (i.e. I can access the intranet and even remote desktop to my 'doze machine at work). All fine and dandy. Suddenly 15-20 seconds later all my network connections are dead. Can't access the internet, intranet and then the RDP client crashes with a 'broken pipe' error. I disconnect from the VPN connection and nothing. Still no internet of any sort. I disconnect from the local network, disable then re-enable my networking and then I can get back on the internet w/o any issue whatsoever. As soon as I connect to my work place using VPN ... back to square one. This issue was also present in 8.04 and was never able to get it working. It's one of the reasons I still keep a dual boot at home.

My HW:
Centrino Perynn 8300
Intel AGN 5100 (wireless)
SATA HD
4 Gb DDR2

Running Ubuntu 9.04

Any help is much appreciated.

Peace.

---

### Post by toord on 2009-05-03
Bump. Have tried just about everything. My knuckles and finger tips are begging for mercy. This is driving me nuts.

---

### Post by animusvirtus on 2009-05-11
Same thing happens to me.
I connect but, then i cant get into any website. Soon as i get out of the vpn, internet works again.

Here is the terminal:

dubido@dubido:~$ vpnc
vpnc: couldn't open `/etc/vpnc/default.conf': Permission denied
dubido@dubido:~$ sudo vpnc
[sudo] password for dubido: 
Enter IPSec gateway address: vpn.uchile.cl
Enter IPSec ID for vpn.uchile.cl: uchile
Enter IPSec secret for [email]uchile@vpn.uchile.cl[/email]: 
Enter username for vpn.uchile.cl: csuazo
Enter password for [email]csuazo@vpn.uchile.cl[/email]: 
Connect Banner:
| *** Bienvenido al Servicio VPN de la Universidad de Chile *** :)

VPNC started in background (pid: 5904)...
dubido@dubido:~$ firefox
dubido@dubido:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:19:db:46:34:6e  
          inet dirección:192.168.1.101  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::219:dbff:fe46:346e/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:25502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20984 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:31597319 (31.5 MB)  TX bytes:3055773 (3.0 MB)
          Interrupción:251 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tun0      Link encap:UNSPEC  direcciónHW 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet dirección:172.25.3.14  P-t-P:172.25.3.14  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1412  Métrica:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:500 
          RX bytes:22488 (22.4 KB)  TX bytes:6106 (6.1 KB)

---

