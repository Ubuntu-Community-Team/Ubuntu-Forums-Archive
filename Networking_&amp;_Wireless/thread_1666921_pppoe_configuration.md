---
title: "pppoe configuration"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by adriat on 2011-01-14
Hello

I installed Ubuntu 10.10, but the internet doesn't work.
I have a pppoe connection, so I open the console and tip "sudo pppoeconf". 
I get this message:

“Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. (…) Another reason for the scan failure may also be another running pppoe process which controls the modem”

Someone knows what should I do?

Thank You

---

### Post by dineshs on 2011-01-14
Please post the output of ```
sudo lshw -C network
``````
ifconfig -a
``````
route -n
```and ```
ping -c3 4.2.2.1
```

---

### Post by adriat on 2011-01-14
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:16:ec: xx: xx: xx
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff


ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:16:ec: xx: xx: xx  
          inet6 addr: fe80::216:ecff:fe9e: xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)


route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


ping -c3 4.2.2.1

connect: Network is unreachable

---

### Post by dineshs on 2011-01-14
Do you have a modem connected via ethernet?
If you have windows,
Does the setup work on windows?Do you use a pppoe dialler there?

---

### Post by adriat on 2011-01-14
Yes, my modem is connected via Ethernet, and my conecction works perfectly in Windows.
On the other hand, i haven't installed a pppoe dialler, but i don't know how to check if I have one in my computer (automatically installed by my internet company, or by some program)

thank you for your help

---

### Post by adriat on 2011-01-14
I don't know if this is useful, but with the modem switched off, i get the same result with the console.

---

### Post by dineshs on 2011-01-14
What is the output of the following command in WINDOWS when internet is working?```
ipconfig /all
```

---

### Post by adriat on 2011-01-14
C:\Documents and Settings\Administrador>ipconfig/all

Configuración IP de Windows

        Nombre del host . . . . . . . . . : COLOSSUxxxxx
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo . . . . . . . . . .  : desconocido
        Enrutamiento habilitado. . . . . .: No
        Proxy WINS habilitado. . . . .    : No
        Lista de búsqueda de sufijo DNS:    home

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS : home
        Descripción. . . . . . . . . . .  : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Dirección física. . . . . . . . . : 00-16-EC-9E-xx-xx
        DHCP habilitado. . . . . . . . .  : No
        Autoconfiguración habilitada. . . : Sí
        Dirección IP. . . . . . . . . . . : 192.168.1.10
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   : 192.168.1.1
        Servidor DHCP . . . . . . . . . . : 192.168.1.1
        Servidores DNS . . . . . . . . . .: 192.168.1.1
        Concesión obtenida . . . . . . .  : Viernes, 14 de Enero de 2011 18:37:0
1
        Concesión expira . . . . . . . . .: Sábado, 15 de Enero de 2011 18:37:01


I'm sorry, It's in Spanish. If you have any troble with the translation, let me know

Thank you for your patience :)

---

### Post by adriat on 2011-01-14
Double Post

---

### Post by adriat on 2011-01-14
Double post

---

### Post by dineshs on 2011-01-14
I think your modem is not DHCP enabled by default.Please try this
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections.
Select the tab, wired
select the ethernet connection you want and click edit
select ipv4
method-manual
address 192.168.1.10
mask 255.255.255.0
gateway 192.168.1.1 then hit enter
DNS 192.168.1.1
then click apply
Restart machine and see if the connection works

---

### Post by dineshs on 2011-01-14
If you dont see NM icon try step-1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")

---

### Post by adriat on 2011-01-14
I do have DHCP enabled.
I already tried what you say, but instead of DNS I put other one. Do you think i should try with this new DNS?
Last time, it appeared "connection established" but it still didn't work.

Thank you again

---

### Post by adriat on 2011-01-14
Double post

---

### Post by adriat on 2011-01-14
Double post

---

### Post by adriat on 2011-01-14
I did again all the steps and still not working :S
I go to Network connections -> DSL -> Add
Username (username of my pppoe) password (password of my pppoe) Service (i don't know what should i write)
I also tried Ipv4 Settings Automatic, Automatic addresses (with the DNS you wrote and with one that appears to me in the configuration of the router)

---

### Post by dineshs on 2011-01-14
From windows ipconfig command I understand that you are using `modem in pppoe mode'.If that is the case you need not run pppoeconf or create DSL connection via network manager.Your modem will have username and password stored in it and the connection will be always ON.So let us assume that the connection is OK upto the modem from ISP side.Since your ethernet interface is not getting an IP I think DHCP is not enabled in modem.
What does this mean?
> DHCP habilitado. . . . . . . . . : NoDHCP enabled=No?
Did you try configuring IP manually,then restart?
What do you get for```
ping 192.168.1.1 -c3
```please post result
 If you are sure that DHCP is enabled in modem,please run ```
sudo dhclient eth0
```and post the result.(> I already tried what you say, but instead of DNS I put other one. Do you think i should try with this new DNS?You may try 192.168.1.1 or 4.2.2.1

---

### Post by adriat on 2011-01-15
Hello!

You're right about 'modem in pppoe mode' and about the DHCP using the command ipconfig/all, but in the modem configuration it appears "DHCP server enabled", so i don't know which is right.

When I introduce my IP manually (in the ivp4) it appears to me "connection established" but it still not working, even if I restart my computer. 
I give you a picture, but i don't think it will be useful :S

This is the result of your commands:

ping 192.168.1.1 -c3

```

ping: unknown host 192.168.1.1-c3
```

sudo dhclient eth0

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:16:ec:9e: xx: xx
Sending on   LPF/eth0/00:16:ec:9e: xx: xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by dineshs on 2011-01-15
The attached screenshot says you have specified an IP 192.168.1.1 to your ethernet interface which is also the gateway(ie the modem).This will cause IP conflict.Please follow post #9 carefully ie 
IP [COLOR="Red"]192.168.1.10 [/COLOR]
mask 255.255.255.0
gateway 192.168.1.1
pl see screenshot
If you have no luck still after restart please post the output of ```
ping 192.168.1.1 -c3
```and```
ping 4.2.2.1 -c3
```

---

### Post by adriat on 2011-01-15
Hello!

I changed the address, but i get the same result.
I write you here the responses of your commands:

ping 192.168.1.1 -c3

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2007ms
pipe 2
```

ping 4.2.2.1 -c3

```
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable
From 192.168.1.10 icmp_seq=3 Destination Host Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2016ms
pipe 2
```

I also tried with the new Address:

ping 192.168.1.10 -c3

```
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_req=1 ttl=64 time=0.040 ms
64 bytes from 192.168.1.10: icmp_req=2 ttl=64 time=0.020 ms
64 bytes from 192.168.1.10: icmp_req=3 ttl=64 time=0.018 ms

--- 192.168.1.10 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.018/0.026/0.040/0.009 ms
```

In addition, I upload the screenshots of my internet configuration.

regards

---

### Post by adriat on 2011-01-16
Hello.

In the screenshot-1.png I have to enter the 'device MAC address'. Is it asking for the computer's MAC address or the modem's MAC address??

Regards. Thank you.

---

### Post by dineshs on 2011-01-16
> **adriat said:**
> Hello.
In the screenshot-1.png I have to enter the 'device MAC address'. Is it asking for the computer's MAC address or the modem's MAC address??

Computers(eth0)
Also can you post the result of```
cat /etc/network/interfaces
```

---

### Post by adriat on 2011-01-16
auto lo
iface lo inet loopback

---

### Post by dineshs on 2011-01-16
Please see
[http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10](http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10)

---

### Post by adriat on 2011-01-16
Hello.

I'm doing it now, I 'll tell you in a minute :)

Regards, thanks.

---

### Post by adriat on 2011-01-16
I tried the commands on the website you recommended, but it still not working.
I don't get any error message, it appears to me 'connection established', but i can't load any website.

I don't know what else should i do :S

What do you think?

Thanks

---

### Post by dineshs on 2011-01-16
When it says connection established see if you can ping 192.168.1.1

---

### Post by adriat on 2011-01-16
No, I get the same result

---

### Post by dineshs on 2011-01-17
How many PCs do you have?Only one dual boot PC?
Can you try post #9 once again but with a different IP(instead of 192.168.1.10 try 192.168.1.200 )then see if ping 192.168.1.1 gets reply
If there is no luck please post the results of```
sudo ethtool eth0
```
```
lsmod | grep 813
```
(Ref post#2 in [http://ubuntuforums.org/showthread.php?p=8826203#post8826203](http://ubuntuforums.org/showthread.php?p=8826203#post8826203))

---

### Post by adriat on 2011-01-17
Hello! :)

I only have one dual boot PC via ethernet, and a few PCs via wifi (if we take into account my freinds' pcs)
I tried changing the Address, but i get the same result:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.200 icmp_seq=1 Destination Host Unreachable
From 192.168.1.200 icmp_seq=2 Destination Host Unreachable
From 192.168.1.200 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
pipe 2
```

I had a problem with the command 'ethtool':
```
The program 'ethtool' is currently not installed.  You can install it by typing:
sudo apt-get install ethtool
```

sudo apt-get install ethtool
```
Reading package list ... Done
Building dependency tree
Reading state information ... Done
Ethtool package is not available, but another package
makes reference. This usually means that the package is missing,
has been obsoleted or is only available from another source.
Package 'ethtool' has no installation candidate
```

(It's a translation)

So, I used command 'sudo mii-tool eth0', I hope you find it useful :S

```
eth0: 10 Mbit, full duplex, link ok
```

Regards, thank you.

---

### Post by dineshs on 2011-01-17
And what about ```
lsmod | grep 813
```

---

### Post by adriat on 2011-01-17
```
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
```

---

### Post by dineshs on 2011-01-17
I think your problem is similar to [this ]("http://ubuntuforums.org/showthread.p...03#post8826203")(As referred earlier)
Please follow instructions there.You may also send a private message to chili555 because I am not an expert especially when there is a driverconflict... moreover that post seems not solved.

---

### Post by chili555 on 2011-01-18
I'm not sure the driver conflict is much of an issue. I have a desktop using the same ethernet card and I had to take two steps to cure it just because I am a bit obsessive-compulsive and I'm never happy unless I'm fixing things. Afterwards, I noticed no improvement whatever! Just to rule out the driver conflict, let's fix it. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line at the bottom:```
blacklist 8139cp
```Proofread, save and close gedit. Next, do:```
sudo gedit /etc/rc.local
```Add a new line right above exit 0:```
rmmod -f 8139cp
```Proofread, save and close gedit. Reboot and post:```
dmesg | grep eth
```

However, I am not at all sure we know whether you have an ordinary ethernet setup or pppoe. Can you please look around in your Windows install and see which it seems to be? Is a username and password required to connect in Windows?

---

### Post by adriat on 2011-01-18
Hello.

This is what I got:
```
[    1.873336] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:16:ec:9e:xx:xx, IRQ 20
[    1.957639] radeon 0000:01:00.0: Error during ACPI methods call
[   30.787870] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   41.392032] eth0: no IPv6 routers present
```

Thank you for answering. Regards

---

### Post by adriat on 2011-01-18
I'm writing from Ubuntu!

Thank you very much, chili555 and Dineshs, i'm changing the threat to SOLVED

---

### Post by chili555 on 2011-01-18
Very good! I'm glad it's working. Have fun.

---

### Post by adriat on 2011-01-18
It doesn't work anymore... :S

I updated Ubuntu, and after I rebooted, it doesn't work. I tried to do the same than before, but still not working. Do you know what should I do?

Thank you.

---

### Post by chili555 on 2011-01-18
Let's have a look at:```
dmesg | grep -e eth -e 813
```Thanks.

---

### Post by adriat on 2011-01-18
Double post

---

### Post by adriat on 2011-01-18
```
[    0.195813] pci 0000:00:11.0: reg 14: [io  0x5000-0x5003]
[    0.229813] pnp: PnP ACPI init
[    0.890908] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.891001] 8139too 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.911968] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:16:ec:9e: xx: xx, IRQ 20
[    1.948813] [drm] radeon: 512M of GTT memory ready.
[    1.976365] radeon 0000:01:00.0: Error during ACPI methods call
[   30.311943] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   36.816063] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   36.816067] Modules linked in: binfmt_misc dm_crypt snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ppdev parport_pc snd_timer snd_seq_device psmouse snd joydev serio_raw i2c_piix4 soundcore snd_page_alloc lp parport hid_logitech ff_memless usbhid hid usb_storage radeon ttm drm_kms_helper floppy drm firewire_ohci firewire_core 8139too ati_agp pata_atiixp crc_itu_t mii sata_sil i2c_algo_bit agpgart
[   39.824084] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   41.072033] eth0: no IPv6 routers present
[   51.824094] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   63.824083] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   75.824087] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   87.824076] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

---

### Post by chili555 on 2011-01-18
It looks like it's dropping and reconnecting. Please try this:```
sudo mii-tool eth0 -F 10baseT-FD
```If it does not cause an error, do:```
sudo rmmod -f 8139too
sudo modprobe 8139too
```If that causes an error, try:```
sudo ethtool eth0 speed 10 duplex full
```Post back and let me know.

---

### Post by adriat on 2011-01-18
Double post

---

### Post by adriat on 2011-01-18
Now, it works.

---

### Post by adriat on 2011-01-18
OK, i rebooted again, i disconnected and connected and still working, so I will mark this thread as SOLVED again, and I will tell you how is it going a few days from now.

Thank you very much. 2/2 :)

---

### Post by adriat on 2011-01-20
Hello.

Your solution worked, but not permanantly, so now i don't have access to Internet.
I'm posting again the result of the command dmesg | grep -e eth -e 813

```
[    0.181398] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.885698] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.885773] 8139too 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.908372] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:16:ec:9e: xx: xx, IRQ 20
[    1.974258] radeon 0000:01:00.0: Error during ACPI methods call
[   26.446081] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   32.832045] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   32.832048] Modules linked in: binfmt_misc dm_crypt snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ppdev parport_pc snd psmouse joydev soundcore serio_raw i2c_piix4 snd_page_alloc lp parport hid_logitech ff_memless usbhid hid usb_storage radeon ttm drm_kms_helper ati_agp drm firewire_ohci floppy pata_atiixp 8139too agpgart i2c_algo_bit sata_sil firewire_core crc_itu_t mii
[   35.840110] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.328055] eth0: no IPv6 routers present
[   47.840088] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   59.840087] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   71.840096] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   83.840098] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   95.840572] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  107.840083] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  119.840088] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  131.840079] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  143.840077] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  155.840079] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

---

### Post by adriat on 2011-01-20
I checked the files I changed because of the drivers, and I repeated your last solution, I reboot and It doesn't work. What should I do?

If you need some extra information or the result of a command, let me know.

Regards.

---

### Post by chili555 on 2011-01-20
> Your solution worked, but not permanantly, so now i don't have access to Internet.Which of the two choices I gave you worked? Whichever one we can make permanent.> It looks like it's dropping and reconnecting. Please try this:
Code:

sudo mii-tool eth0 -F 10baseT-FD

If it does not cause an error, do:
Code:

sudo rmmod -f 8139too
sudo modprobe 8139too

If that causes an error, try:
Code:

sudo ethtool eth0 speed 10 duplex full

Post back and let me know.

---

### Post by adriat on 2011-01-20
the first, there was no error

---

### Post by chili555 on 2011-01-20
Please try this:```
sudo gedit /etc/rc.local
```Right above the line exit 0 and below any other lines that you may have added, add this on its own line:```
mii-tool eth0 -F 10baseT-FD

```Proofread, save and close gedit. Reboot and give me your report. 

The forum is slow today. I hope it means more and more of us are learning and enjoying Ubuntu. Sorry if my replies have been slow in coming.

---

### Post by adriat on 2011-01-20
Hello.

I also hope more people are interested in linux. Don't worry about the replies, I am very glad that you are helping.

After I rebooted my computer, it worked perfectly.

Would you mind to explain me what was wrong? I'd like to undersand it and be able to fix it by myself if it stops working.

At first was it a driverconflict problem?
(when i answered you "eth0: 10 Mbit, full duplex, link ok", it didn't work at the speed it should)

And after that, my connection would connect and disconnect over and over again.
We tried the commands:
```
sudo mii-tool eth0 -F 10baseT-FD
sudo rmmod -f 8139too
sudo modprobe 8139too
``` 
I don't understand what these commands do :S

Thank you for helping me and for the explanation!. Regards

---

### Post by chili555 on 2011-01-20
Basically, I just copied a fix I read elsewhere. Evidently, for some, the driver doesn't work well at 100 Mb/sec. but will work well at 10 Mb/sec. What we did was to force it to use 10 Mb/sec. no matter what. Placing the command in rc.local tells the system to use it on boot.

Let me know if you need more help. Sorry for the slowdowns.

---

### Post by adriat on 2011-01-20
Double post.

---

### Post by adriat on 2011-01-20
Double post.

---

### Post by adriat on 2011-01-20
Double post.

---

### Post by adriat on 2011-01-20
Double post.

---

### Post by adriat on 2011-01-20
Once again, Internet doesn't work. The computers is connecting and disconnecting over and over at 100Mbps. The files you told me to change keep the changes I did.
I also tipped:
```
mii-tool eth0 -F 10baseT-FD
```

I have detected that Internet stops working in Ubuntu every time I connect to Internet with Windows.

Should I try something like adding this to /etc/rc.local:
```
ethtool -s eth0 speed 10 duplex full autoneg on
```

*[http://ubuntuforums.org/showthread.php?t=1106186](http://ubuntuforums.org/showthread.php?t=1106186)*

Or may it be Windows interfering?
 
Thank you. Regards.

---

### Post by chili555 on 2011-01-20
Please remove the mii-tool line and add this:```
ethtool -s eth0 speed 10 duplex full
```Please give us your report.

---

### Post by adriat on 2011-01-20
Hello chili555

Again you're right, and internet works perfectly. I'm going to connect with windows and try connect with ubuntu later. I let you know.

Thank you. Regards.

---

### Post by adriat on 2011-01-20
Hello.

It happened again, it was working, but after connecting with Windows, stops working, and now i don't know how to fix it...

Regards.

---

### Post by adriat on 2011-01-21
May it be because I use an extern hard drive to run Ubuntu?
(and later I use it in WINDOWS)

---

### Post by chili555 on 2011-01-21
It could be. Please see here:  [http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/)> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager. Notice it explicitly mentions 8139, also.

There is some impolite language in that forum; I apologize.

---

### Post by adriat on 2011-01-21
Once I do that, will internet work or should I do something in Ubuntu for turning it on?

---

### Post by chili555 on 2011-01-21
> **adriat said:**
> Once I do that, will internet work or should I do something in Ubuntu for turning it on?It should just work.

---

### Post by adriat on 2011-01-21
I think we finally found the solution. Now internet works fine even if I reboot with windows and later with Ubuntu.

Thank you for your help. Regards

---

### Post by chili555 on 2011-01-21
Very good! You will have helped the searchers, as well. Thanks for being patient and persistent.

---

