---
title: "Changing drivers to get wireless card working"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by pr0fess0r on 2005-12-08
Hi
My XH8196 802.11g PCI wireless card shows up as Intersil ISL3890 [Prism GT/Prism] and as eth1 in the Network Config. I used ndiswrapper and installed the Windows driver no problem, but how do I now get Ubuntu to ealise my eth1 card is really a wlan0 so I can get wpa_supplicant working?
thanks in advance for any help

Lucas

---

### Post by Lambert on 2005-12-08
eth1 is just the naming scheme/alias so the os knows what device to direct commands to. It doesn't mean it's not recognized as a wireless device so the problem is not in it's name.

Go to the wirelesstroubleshootingguide in my signature to see if you can troubleshoot your problem

---

### Post by pr0fess0r on 2005-12-08
Hi Lambert

This is the info about my card:

sudo lshw -C network
  *-network:0 
       description: Wireless interface
       product: Intersil ISL3890 [Prism GT/Prism Duette]
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT RE ADY!
       resources: iomemory:b6000000-b6001fff irq:19

I guess it's not ready because we have WPA PSK security on our wlan, so I'm leaving the driver as is and working through the wiki WPA guide:

wpa_supplicant.conf looks like this:

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="MYNETWORK"
scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
         psk=90a1305c45f9d44056f82b05a54894bd6998fd5b250b12f8702bbb6de1766eeb
}

Running wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dprism54 gives me:

ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'eth1' UP
socket(PF_PACKET): Operation not permitted
ioctl[PRISM54_HOSTAPD]: Operation not permitted
ioctl[PRISM54_HOSTAPD]: Operation not permitted
wpa_driver_prism54_set_countermeasures - not yet implemented
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied

which is where I'm stuck. I did install ndiswrapper and the XP driver for the card but I'm not sure whether to stick with the default prism driver or use ndiswrapper:
ndiswrapper -l
Installed ndis drivers:
o4i01a  driver present, hardware present

So... any tips on where to proceed from here would be greatly appreciated :)
cheers

---

