---
title: "Cannot access wireless router 192.168.1.1 on Ubuntu 12.04 but ok on Windows. Internet"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by pedrospeixoto on 2013-05-31
[COLOR=#333333][FONT=Ubuntu Beta]When I try to access/ping my wireless router TP-Link TL-WR541G on Ubuntu 12.04 I get no response.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I am connected to the wireless network and can access internet without issues. The access to the router on Windows works fine.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]It seems to be a problem similar to: [http://ubuntuforums.org/showthread.php?t=2145774](http://ubuntuforums.org/showthread.php?t=2145774) but had no success with the solution there proposed, and also [Can not ping router in Ubuntu 12.04, works fine in Windows]("http://askubuntu.com/questions/232254/can-not-ping-router-in-ubuntu-12-04-works-fine-in-windows") but I do have access to internet.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]For me this seems very strange, as I can use the wireless network finely, but just can't access the router. I really need frequent access to the router, so this is very important for me. I would appreciate a lot any help.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I have configured the driver of my Broadcom controller based on other posts, also tried other drivers, but found that wl works well.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I apologize for some of the outputs in Portuguese, not English, I hope this is not an issue.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]ifconfig:[/FONT][/COLOR]
```

eth0      Link encap:Ethernet  Endereço de HW e8:11:32:98:04:89  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:50 Endereço de E/S:0xe000 


eth1  Link encap:Ethernet  Endereço de HW e0:ca:94:02:f6:bb  
      inet end.: 192.168.1.101  Bcast:192.168.1.255  Masc:255.255.255.0
      endereço inet6: fe80::e2ca:94ff:fe02:f6bb/64 Escopo:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
      pacotes RX:6994 erros:18 descartados:0 excesso:0 quadro:115280
      Pacotes TX:7958 erros:13 descartados:0 excesso:0 portadora:0
      colisões:0 txqueuelen:1000 
      RX bytes:4709740 (4.7 MB) TX bytes:1681376 (1.6 MB)
      IRQ:16 


 lo   Link encap:Loopback Local  
      inet end.: 127.0.0.1  Masc:255.0.0.0
      endereço inet6: ::1/128 Escopo:Máquina
      UP LOOPBACK RUNNING  MTU:16436  Métrica:1
      pacotes RX:1351 erros:0 descartados:0 excesso:0 quadro:0
      Pacotes TX:1351 erros:0 descartados:0 excesso:0 portadora:0
      colisões:0 txqueuelen:0 
      RX bytes:210664 (210.6 KB) TX bytes:210664 (210.6 KB)

```



iwconfig:
```

lo        no wireless extensions.


eth1  IEEE 802.11abg  ESSID:"PeSiWiFi"  
      Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:CD:F6:71:F4   
      Retry  long limit:7   RTS thr:off   Fragment thr:off
      Power Management:off


eth0  no wireless extensions.

```


nm-tool

```

NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
Type:              Wired
Driver:            r8169
State:             unavailable
Default:           no
HW Address:        E8:11:32:98:04:89


Capabilities:
Carrier Detect:  yes


Wired Properties
Carrier:         off




- Device: eth1  [PeSiWiFi] -----------------------------------------------------
Type:              802.11 WiFi
Driver:            wl
State:             connected
Default:           yes
HW Address:        E0:CA:94:02:F6:BB


Capabilities:
 Speed:           54 Mb/s


Wireless Properties
WEP Encryption:  yes
WPA Encryption:  yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
*PeSiWiFi:       Infra, 00:23:CD:F6:71:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 73 WPA WPA2


IPv4 Settings:
Address:         192.168.1.101
Prefix:          24 (255.255.255.0)
Gateway:         192.168.1.1


DNS:             201.6.2.152
DNS:             201.6.2.32

```


lspci:
```

Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7179]
    Kernel driver in use: wl


 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a5]
    Kernel driver in use: r8169

```



/etc/network/interfaces:

```

auto lo
iface lo inet loopback
route:


Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1

```

---

### Post by wildmanne39 on 2013-05-31
To access the router you should use an ehternet connection.

---

### Post by pedrospeixoto on 2013-06-01
I do have access using cable, but I really would like to access using the wireless network. I just can't figure out what is wrong and why it is not connecting as it should be.

Thanks

---

