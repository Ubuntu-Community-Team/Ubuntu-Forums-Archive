---
title: "No DHCPOFFERS received"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by mwshear on 2009-11-20
I have a Belkin f5d8055v1 usb 802.11n device that I'm try to use with Ubuntu 9.1

I'm using the rt2870 linux driver from ralink, compiled under kernel 2.6.30

I've removed the default network manager and configured the device via /etc/network/interfaces and /etc/wpa_supplicant.conf.

An old internal broadcom card on the same machine connects first time using the same wpa settings and dhcp but the rt2870 device, using ra0, cannot negotiate a ip address from my wireless router. The router logs show an IP is allocated, and the device shows as associated using ifconfig, but no IP connection is possible, even if I force a static IP vice dynamic.

I've tried disabling the other wireless device but it makes no difference.

The device functions perfectly under Windows XP.

After a week of googling I'm truly stuck....

Thanks in advance,

Michael.

---

### Post by madverb on 2009-11-20
Have you tested with different wireless security settings on the AP?

---

### Post by Iowan on 2009-11-20
> **mwshear said:**
> The router logs show an IP is allocated, and the device shows as associated using ifconfig,...You're saying the device shows the proper IP? Can you **ping** the router?

---

### Post by mwshear on 2009-11-21
Thanks.

Sorry I should have said that i've tried with no security enabled and the old Broadcom card connects, is allocated an IP and can ping. 

The rt2870 can see the network, associate with the access point but no IP is allocated.

---

### Post by mwshear on 2009-11-21
Thanks.

I can force the device to have a static IP but it doesn't still ping through to the router.

With dhcp, no IP is allocated and therefore no ping either.

---

### Post by mwshear on 2009-11-29
Still stuck I'm afraid.

Can anyone who has managed to get the rt2870 driver to work please post their config, esp. 

RT2870STA.dat
/etc/wpa_supplicant.conf
/etc/network/interfaces

Thanks,

Michael.

---

### Post by mwshear on 2009-12-01
I've finally resolved my configuration problems. I've tried to reconstruct how from the beginning:

1. Download the rt2870 driver from [www.ralinktech.com](www.ralinktech.com)
2. Unpack creating directory: 2009_0820_RT2870_Linux_STA_V2.2.0.0
3. Download patch for kernel 2.6.31: rt2870-2.6.31.patch from
[INDENT][http://launchpadlibrarian.net/35348336/rt2870-2.6.31.patch](http://launchpadlibrarian.net/35348336/rt2870-2.6.31.patch)[/INDENT]4. Use apt-get to install kernel headers and build essentials
5. Use apt-get to remove network-manager
6. Carefully follow build instructions in README_STA, modifying config.mk as:
[INDENT]```
'HAS_WPA_SUPPLICANT=y' and 
'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'
```[/INDENT]7. Edit /etc/Wireless/RT2870STA/RT2870STA.dat to include:
[INDENT]```
SSID=yourSSID
NetworkType=Infra
 AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=yourkeyasastring
```

[/INDENT]8. Generate your key as 64 hex chars using:
[INDENT]```
wpa_passphrase yourSSID yourkeyasastring
```[/INDENT]9. Create /etc/wpa_supplicant.conf to include:

[INDENT]```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="yourSSID"
       key_mgmt=WPA-PSK
       psk=yourkeyas64hexcharacters
}
```[/INDENT]10. Create /etc/network/interfaces as:

[INDENT]```
auto lo
iface lo inet loopback

iface ra0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
auto ra0
```[/INDENT]11. Create /etc/modules.conf as:
[INDENT]```
alias ra0 rt2870sta
```[/INDENT]12. Create /etc/sysconfig/network-scripts/ifcfg-ra0 as:
[INDENT]```
DEVICE='ra0'
ONBOOT='yes'     
BOOTPROTO='dhcp' 
```[/INDENT]13. Create /etc/sysconfig/network as:
[INDENT]```
GATEWAY=yourgatewayipasx.x.x.x 
```[/INDENT]14. Add the following line to /etc/modprobe.d/blacklist.conf
[INDENT]```
blacklist rt2800usb
```[/INDENT]Thats it, hope i haven't missed a step and you find it helpful.

Michael. :D

---

