---
title: "Wireless set up on headless system. (10.10 Mav)"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by K_Light2003 on 2011-03-29
Okay I give up so it's time to ask. I have read and read, and am now going in circles.

I have a headless system running fine with eth0, but I need to move the system for a while and need to use wireless. I'm probably doing something wrong somewhere.

So what I need is to leave eth0 set up and running when the lan cable is plugged in, but when the system is rebooted with lan cable unplugged the wireless card kicks in and takes over.

I have put system back to just eth0 so I can start from scratch. I have two wireless cards installed at the moment, in the hope I can get one of them working and intend to remove one card later.

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.50
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1
        dns-search localdomain
```lspci

```
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0c.0 Ethernet controller: Belkin Device 700f (rev 20)
00:0d.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
 *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0d:87:33:ae:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.50 latency=64 link=yes maxl$
       resources: irq:19 ioport:dc00(size=256) memory:cfffc000-cfffcfff memory:cffc0000-cffdffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:33:21:83
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=2.6.35-28-generic firmware=N/A latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes wi$
       resources: irq:16 ioport:d800(size=256) memory:cfffbe00-cfffbfff
  *-network:2 UNCLAIMED
       description: Network controller
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:cfff8000-cfff9fff
```Router setup is as follows:

```
Network Name (SSID):Belkin   
Wireless Security:Configured   
Network Authentication: WPA-PSK + WPA2-PSK 
Data Encryption: TKIP+AES 
Network Key (PSK): <hidden>
```I know the Belkin PCI wireless card works with Ubuntu 10.10 desktop edition, if that's any help. 

Thanks in advance.

---

### Post by K_Light2003 on 2011-03-31
After yet more reading. I can now get wireless to work, well kind of.

Installed wireless-tools and wpasupplicant

```
sudo apt-get install wireless-tools wpasupplicant
```Edited /etc/network/interfaces and removed eth0 (commented out) and added the code below

```
auto lo
iface lo inet loopback


####################################
# works but system won't shut down #
####################################

auto wlan0
iface wlan0 inet dhcp

       wpa-ap-scan 1
       pre-up sudo /sbin/wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -B
       pre-up sleep 5
       post-down killall -q wpa_supplicant

```

Created the HEX psk key with

```
wpa_passphrase Belkin 12345
```

Where 12345 is the routers WPA key in ASCII

Created /etc/wpa_supplicant.conf and added the following lines.

```


sudo nano /etc/wpa_supplicant.conf
``````
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="Belkin"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk=123eaea982395b2fa8e2115e5e8c5c116918c957db4cb6b6111232176afd03bf
        pairwise=TKIP
        group=TKIP
}

```Rebooted the server and wireless comes up at boot and works. (not static IP however)

Now the server will not shut down correctly :confused:  It just crashes when about halfway through the shutdown, and I have to hit the power button to turn it off or reboot resulting in a "dirty" shutdown which is not great.

---

### Post by K_Light2003 on 2011-04-01
Well at least I have sorted getting wpa_supplicant and the wireless card on a static IP now. 

/etc/network/interfaces needs to be changed again just like you would do normaly for a static IP, the wpa_supplicant line has to be changed as well. Remove the pre up and change to just up (in red below)

```


#   Static IP works but system still won't shut down   #


auto wlan0
iface wlan0 inet static

       address 192.168.2.50
       netmask 255.255.255.0
       network 192.168.2.0
       broadcast 192.168.2.255
       gateway 192.168.2.1
       dns-nameservers 192.168.2.1
       dns-search localdomain

       wpa-ap-scan 1
       [COLOR=Red]up /sbin/wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -B[/COLOR]
       pre-up sleep 5
       post-down killall -q wpa_supplicant

```The system still crashes on shut down, all I know is it's something to do with wpa_supplicant and/or the wireless card.

---

