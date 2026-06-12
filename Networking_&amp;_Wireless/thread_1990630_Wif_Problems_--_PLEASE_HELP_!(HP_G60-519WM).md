---
title: "Wif Problems -- PLEASE HELP !(HP G60-519WM)"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by darank on 2012-05-29
I have been having wireless connectivity issues with my hp laptop after installing ubuntu 12.04 LTS precise pangolin, and have tried many fixes such as the one suggested here: [http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/) , but none of them have worked with any success. 

I get connection through an ethernet chord, but when using wireless, the network manager says im connected however my internet still doesnt work !! the hardware button works and everything too.

Here's what i got:
```

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


```
and
```

~$ sudo lshw -class network
^[[C  *-network           
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:e6:29:f5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:11:7c:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2600000-d260ffff

```
and
```

~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

let me know if i need to post anything more from the terminal.

I'm super new to linux as well so i dont know my way around very well, sorry.

Any and all help is welcome !!

---

### Post by gnusci on 2012-05-29
Did you try with Wicd?

---

### Post by darank on 2012-05-29
uhhm im not sure bc i dont know what that is...

---

### Post by gnusci on 2012-05-29
> **darank said:**
> uhhm im not sure bc i dont know what that is...

Open Ubuntu Software Centre (USC) and search for Wicd, and install it. Then use it to configure your WiFi.

---

### Post by darank on 2012-05-29
alright im downloading it right now, but is it pretty straight forward as far as using it ??

---

### Post by gnusci on 2012-05-29
It works much better with the Realtek wifi.

---

### Post by darank on 2012-05-29
> **gnusci said:**
> Open Ubuntu Software Centre (USC) and search for Wicd, and install it. Then use it to configure your WiFi.
ok so i tried Wicd, but it said im connected to my home internet and everything, however on the menu bar the wifi networks say unavailable. Im not entirely sure i used it right though.

I tried it a second time to see if i was just using it wrong, and it said that the authentication failed bc of a bad password, however after double checking the password and encryption type it still said the same thing. Basically it didnt work.

should i disable all the connections before trying this ?? im not sure it its just me, or if the it just didnt work.

---

### Post by gnusci on 2012-05-29
Try disabling the NetworkManager first

[https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)

Then run Wicd again.

---

### Post by darank on 2012-05-29
> **gnusci said:**
> Try disabling the NetworkManager first

[https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)

Then run Wicd again.

I have no idea how to disable the NetworkManager, i tried following the direction in the link however when i put the code in i get error messages:

```
~$ sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo: /etc/dbus-1/event.d/26NetworkManagerDispatcher: command not found

and 

~$ sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo: /etc/dbus-1/event.d/25NetworkManager: command not found

```

im have no idea what the file thing is talking about.

---

