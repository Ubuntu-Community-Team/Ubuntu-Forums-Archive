---
title: "lenovo b560/ubuntu11.04/no wifi: wifi switch won't react to rfkill"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by silvia_g on 2011-06-21
hey! i'm an absolute beginner in ubuntu; i've recently bought a lenovo  b560 (x64) with windows 7 installed, and i'm currently trying to get  ubuntu 11.04 working so that i can erase windows for good; i have a dual  boot with the two OSs.
the thing is that on ubuntu i can't connect  to my wireless network (on windows works fine); i've got the "sticky"  broadcom 4313 card, but i don't think that's the problem (you'll tell  me, I hope); there's a physical switch with the LED on, but the network  manager acts as if it was off ("wifi disconnected by switch); i've tried  "rfkill unblock all" but it's "hard blocked" and won't unblock.. on top  of that the system crashed a few times already, just freezed and i had  to turn it off because nothing else worked..
please help me, i was using ubuntu on my previous PC, really happy of being away from windows, and I don't want to go back..:P
I've  added some of the things recommended in the newbies how to post, but if  there's anything else you need just please tell me how to get it and  i'll post it, ok?
thank you in advance,
silvia

[B]rfkill list all
[/B]0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


[B]~$ sudo lshw -c network
[/B]  *-network               
       description: Ethernet interface (...)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: ac:81:12:0c:a9:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2500000-f2503fff
[B]
lspci -nn[/B]
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

[B]ifconfig
[/B]eth0      Link encap:Ethernet  direcciónHW f0:de:f1:27:40:d3  
          Direc. inet:192.168.1.35  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::f2de:f1ff:fe27:40d3/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1081787 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9296 errores:0 perdidos:0 overruns:0 carrier:2
          colisiones:0 long.colaTX:1000 
          Bytes RX:9324651 (9.3 MB)  TX bytes:1513335 (1.5 MB)
          Interrupción:44 

eth1      Link encap:Ethernet  direcciónHW ac:81:12:0c:a9:56  
          Dirección inet6: fe80::ae81:12ff:fe0c:a956/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

[B]uname -mr (kernel module)
[/B]2.6.38-8-generic x86_64

---

### Post by stefanmuc2k on 2011-07-02
I have one of these machines as well.

For me it worked once I appended the line 
```
 blacklist acer_wmi 
```
to /etc/modprobe.d/blacklist.conf 

It seems the proprietary broadcom driver doesn't play nicely with the acer_wmi module.

---

### Post by chili555 on 2011-07-02
> rfkill list all
0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
3: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: yes
4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
I don't see acer here; I don't think blacklisting acer-wmi is going to help.

---

### Post by chili555 on 2011-07-02
Let's have a look at:```
lsmod
```Thanks.

---

