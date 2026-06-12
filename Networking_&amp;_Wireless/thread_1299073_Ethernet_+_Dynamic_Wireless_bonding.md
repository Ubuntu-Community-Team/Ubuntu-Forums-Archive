---
title: "Ethernet + Dynamic Wireless bonding"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by DToNAToR on 2009-10-23
Dry info:
1 PC with Ubintu 9.10 and:
* ethernet NIC - connects to a router that gives internet access. This router has the IP of 192.168.5.1
* wireless card that can connect to any other wireless router giving internet access. This interface's router I'm connecting to doesn't have a static subnet (which means it can be 192.168.0.1 or 192.168.80.1)

What I want to do is to setup a bond which will enslave these two connections and use them equally to connect to the internet, while each one of them may be down at any point.
Also, I would still like to use the ubuntu network manager to connect to wireless access points.

Please assist me with that .. I've read a lot of tutorials but left hanged in the air with the configurations needed to be done ..

Thanks in advance

---

### Post by DToNAToR on 2009-10-23
Please? :)

---

### Post by DToNAToR on 2009-10-24
Trying again ...

---

### Post by ericatkin on 2009-12-08
I've used this in my /etc/network/interfaces and it worked great up to 9.10. There seems to be an issue with the bonding driver or the iwlagn driver that breaks it in Ubuntu 9.10. I haven't figured it out yet, but thought I'd post my solution as it was very nice before. I could seamlessly migrate between wireless and wired based on link status of eth0. /etc/wpa_supplicant/wpa_supplicant.conf needs to be set up for the wireless networks your interested in.


/etc/network/interfaces
---
auto lo wlan0 eth0 bond0                            

iface lo inet loopback                              

iface wlan0 inet manual
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface eth0 inet manual

iface bond0 inet dhcp
        pre-up iptables-restore /root/firewall
        post-down iptables -P INPUT ACCEPT    
        post-down iptables -P OUTPUT ACCEPT   
        post-down iptables -P FORWARD ACCEPT  
        post-down iptables -F                 
        post-down iptables -X                 
        bond_mode active-backup               
        bond_miimon 100                       
        bond_downdelay 200                    
        bond_updelay 200                      
        bond_primary eth0                     
        slaves wlan0 eth0

---

### Post by size_XXM on 2009-12-11
ericatkin,  did this work with networkmanager, or did you have to disable it? How would I go about using this setup - is it manageable through nm, or do I have to cook up a script?

About this not working - what exactly is breaking down? I read somewhere you should inform wpa_supplicant to use the bond interface for this to work (the -b commandline option, used for bridging, or something along the lines of ```
iface wlan0 inet manual
        bond-master bond0
        bond-give-a-chance 10
        wpa-bridge bond0

```Note: I haven't even really tried to get this working (stopped trying for now), and have little/no idea what I'm doing. Use at your own risk :P 
Also, would you mind posting the contents of the wpa...conf file - is there any special config for bridging/bonding, or is this randomly googled example(provided I use the same security scheme) enough?:```
network={
	ssid="my_wpa_ap"
	proto=WPA
	key_mgmt=WPA-PSK
	psk="xxxxxxxxxx"
	priority=99
}
```Lastly, I'm particularly disturbed that wpa_cli doesn't work at all, giving me *Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory* even when the supplicant is running and managing a secured network.

---

