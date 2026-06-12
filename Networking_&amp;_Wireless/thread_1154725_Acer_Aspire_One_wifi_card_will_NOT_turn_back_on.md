---
title: "Acer Aspire One wifi card will NOT turn back on"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by BeerPatrol on 2009-05-10
OK here it goes.

I had the ath5k driver for my atheros card running so that I could run kismet. Once I finished with kismet, my card would not recover from monitor mode. In the process of me figuring out how to put it back in manage mode, i seemed to have disabled my wifi card and i can't get it back up and running. network manager isnt acknowledging it 
lspci -C network  gave me this on the wireless card:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
Any help would be appreciated.

---

### Post by chili555 on 2009-05-10
Here is what I suggest, from a terminal:```
sudo modprobe ath5k
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Does that fix it?

---

### Post by BeerPatrol on 2009-05-10
> **chili555 said:**
> Here is what I suggest, from a terminal:```
sudo modprobe ath5k
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Does that fix it?


That did not fix it, iwconfig does not see my wireless card at all nor does ifconfig. I believe the card's power is literally off, and I cant turn it back on. The power switch on the card never worked in ubuntu so I have no idea how i managed to do this.

edit: ok so i got the card back on, but network manager still shows no available connections under wireless networks

---

### Post by BeerPatrol on 2009-05-10
bump

---

### Post by chili555 on 2009-05-10
> edit: ok so i got the card back on, but network manager still shows no available connections under wireless networksSo does iwconfig now show your wireless interface? What does this tell us?```
sudo iwlist wlan0 scan
```

---

### Post by BeerPatrol on 2009-05-10
> **chili555 said:**
> So does iwconfig now show your wireless interface? What does this tell us?```
sudo iwlist wlan0 scan
```

tk421@Death-Star:~$ sudo iwlist wlan0 scan
wlan0     No scan results


thats all i get

---

### Post by chili555 on 2009-05-10
May we please see:```
sudo cat /var/log/messages | grep -i kill
```

---

### Post by BeerPatrol on 2009-05-10
> **chili555 said:**
> May we please see:```
sudo cat /var/log/messages | grep -i kill
```


I didn't get anything back after typing it in

tk421@Death-Star:~$ sudo cat /var/log/messages | grep -i kill
tk421@Death-Star:~$

---

### Post by BeerPatrol on 2009-05-10
bump

---

### Post by chili555 on 2009-05-10
> I didn't get anything back after typing it inGood! That means the card is *not* being disabled by the switch. May we see:```
iwconfig
```Thanks.

---

### Post by BeerPatrol on 2009-05-10
> **chili555 said:**
> Good! That means the card is *not* being disabled by the switch. May we see:```
iwconfig
```Thanks.

I updated ubuntu, and nm now does not show wireless in grey again. but i ran 
tk421@Death-Star:~$ sudo cat /var/log/messages | grep -i kill
again with no feedback
iwconfig:
tk421@Death-Star:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

before i updated and rebooted it showed my wireless interface (wlan0) and now it obviously doesnt.

---

### Post by BeerPatrol on 2009-05-10
ah, pretty sure i found out why iwconfig isnt showing wlan0. when i updated i think it got rid of my ath5k driver

---

### Post by BeerPatrol on 2009-05-10
i reinstalled linux-backports-modules-intrepid and got my ath5k driver back. still not able to connect to wireless networks BUT this is the output from iwconfig now:
tk421@Death-Star:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by BeerPatrol on 2009-05-10
bump

---

### Post by BeerPatrol on 2009-05-10
bump

---

### Post by chili555 on 2009-05-11
When you click on the Network Manager icon, do you see your wireless interface? Do you see networks? When you click on one and try to connect, what happens?

---

### Post by BeerPatrol on 2009-05-14
> **chili555 said:**
> When you click on the Network Manager icon, do you see your wireless interface? Do you see networks? When you click on one and try to connect, what happens?

i see the interface but i don't see networks

---

### Post by mjoolnir on 2009-05-14
Install aircrack-ng, then do sudo airmon-ng stop **x** (x being your wifi card). Kismet tries to bring the card out of monitor mode and unsleep network-manager when it quits but isn't successful alot of the time.

---

### Post by BeerPatrol on 2009-05-14
> **mjoolnir said:**
> Install aircrack-ng, then do sudo airmon-ng stop **x** (x being your wifi card). Kismet tries to bring the card out of monitor mode and unsleep network-manager when it quits but isn't successful alot of the time.

network manager still isnt showing networks. ive been able to get my card back into managed mode, my only problem is network manager isnt showing any networks.

---

### Post by mjoolnir on 2009-05-14
> **BeerPatrol said:**
> network manager still isnt showing networks. ive been able to get my card back into managed mode, my only problem is network manager isnt showing any networks.

Try ```
sudo gedit /usr/local/etc/kismet.conf
``` and change
```
networkmanagersleep=true
```
to
```
networkmanagersleep=false
```
then reboot

---

### Post by BeerPatrol on 2009-05-14
> **mjoolnir said:**
> Try ```
sudo gedit /usr/local/etc/kismet.conf
``` and change
```
networkmanagersleep=true
```to
```
networkmanagersleep=false
```then reboot

it didnt do anything

---

### Post by BeerPatrol on 2009-05-15
bump

---

### Post by BeerPatrol on 2009-05-15
is all hope lost?:(

---

### Post by BeerPatrol on 2009-05-15
F*$k it. I upgraded to Jaunty and all my problems were solved.

---

