---
title: "WiMAX USB is not detected"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by H-Racky on 2011-03-02
Hello.

Recently I bought a USB modem SEOWON SWU-3120. [According to the manufacturer]("http://www.seowonintech.co.kr/en/product/detail.asp?num=111&big_kind=B04&middle_kind="), Linux is supported, but ubuntu doesn't detect it 

Both "usb-modemswitch-data" and "usb-modeswitch" packages are installed (I use GSM and CDMA modems without any problem).

When I try to add a new broadband network I have only two choices: GSM and CDMA networks. WiMAX doesn't appear. Looks like Ubunto 10.10 "doesn't know" about the existence of the WiMAX technology. I sent some e-mails to the manufacturer but they never answered.

I friend of mine informed me to try the following commands:
[B]sudo lshw -C network
lsusb
ifconfig -a
nm-tool[/B]
**dmesg | tail -10**

The result is this:
```

ze@ubuntu-netbook:~$ sudo lshw -C network
PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:6a:78:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:b0:11:14
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

ze@ubuntu-netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 002: ID 1076:7f20 GCT Semiconductor, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ze@ubuntu-netbook:~$ ifconfig -a
eth0      Link encap:Ethernet  Endereço de HW e0:cb:4e:b0:11:14  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:45

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:12 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:12 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  Endereço de HW 1c:4b:d6:6a:78:b3  
          BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

ze@ubuntu-netbook:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        1C:4B:D6:6A:78:B3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        E0:CB:4E:B0:11:14

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
ze@ubuntu-netbook:~$

ze@ubuntu-netbook:~$ dmesg | tail -10
[   36.408139] Skipping EDID probe due to cached edid
[   36.452180] Skipping EDID probe due to cached edid
[   36.492149] Skipping EDID probe due to cached edid
[   36.697310] Skipping EDID probe due to cached edid
[   39.436300] Skipping EDID probe due to cached edid
[   42.981140] Skipping EDID probe due to cached edid
[   54.876159] Skipping EDID probe due to cached edid
[   54.912166] Skipping EDID probe due to cached edid
[   54.952198] Skipping EDID probe due to cached edid
[   54.992121] Skipping EDID probe due to cached edid
ze@ubuntu-netbook:~$
```He also suggested that this device could be detected as ethernet device and should appear somewhat like a CD rom. But Ubuntu doesn't "move" an inch when I plug the modem.

If CGT chipset wasn't detected by lsusb, I could think that the modem was just but an empty plastic box.

What can I do in order to have this device working on Ubuntu 10.10? Under Windows 7 it works fine.

---

### Post by sanderj on 2011-03-02
> 
When I try to add a new broadband network I have only two choices: GSM and CDMA networks. WiMAX doesn't appear. Looks like Ubunto 10.10 "doesn't know" about the existence of the WiMAX technology


Do you mean the USB-Wimax does provide GSM and CDMA? If so, have you tried using that?

Have you tried the modem under Ubuntu 11.04 Alpha 2 daily build?
And under Windows (if you have that)

BTW: Is WiMax available in Portugal? If so: in private networks (like Wifi) or publick networks (like UMTS)?

---

### Post by H-Racky on 2011-03-02
> **sanderj said:**
> Do you mean the USB-Wimax does provide GSM and CDMA? If so, have you tried using that?

No, this usb just works with WiMAX. I just tried to add a new connection to Ubuntu and searched for WiMAX, but only got GSM and CDMA.


> **sanderj said:**
> Have you tried the modem under Ubuntu 11.04 Alpha 2 daily build?
And under Windows (if you have that)

Under Windows 7 works fine. The drivers are available in a CDrom, but no Linux drivers available. Never tried Ubuntu 11.04.

> **sanderj said:**
> BTW: Is WiMax available in Portugal? If so: in private networks (like Wifi) or publick networks (like UMTS)?

As far as I know, there are no WiMAX public carriers in Portugal. I'm in Angola.

---

### Post by sanderj on 2011-03-02
Does [http://ubuntuforums.org/showthread.php?t=1539288](http://ubuntuforums.org/showthread.php?t=1539288) help you?

It seems you have to put the modem into a certain mode, which will change it's lsusb status. See [http://ubuntuforums.org/showpost.php?p=9646938&postcount=10](http://ubuntuforums.org/showpost.php?p=9646938&postcount=10)

Disclaime: I have no Wimax experience myself.

---

### Post by H-Racky on 2011-03-02
Just read the last answer I wanted to read:

> **1R3N1CU5 said:**
> I'm from BD bro...and the new usb wimax modem released by qubee is not supported in linux! 

It comes with its own driver that automatically activates the modem on Windows...& unless the driver is installed the modem does not power on when plugged in.

I did speak to a qubee technical person, & he told me that mac & windows are currently supported...& that he's urging his boss to create another driver for Linux users :-k

Who knows how long it will take to be released, if it ever does! :(


Thanks anyway.

---

