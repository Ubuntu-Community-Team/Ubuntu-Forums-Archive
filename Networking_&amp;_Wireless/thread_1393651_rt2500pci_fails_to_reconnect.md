---
title: "rt2500pci fails to reconnect"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by unitedoceanic on 2010-01-29
hi there,

my problem:

wireless disconnects after a few hours, there is a 50/50 chance that the reconnect fails. if it fails i am asked for the wpa2 key, if i hit cancel and try to connect manually after 2 minutes it connects most times. if i enter the wpa2 key and hit connect i won't get any connection.
reading the loglife of my router shows that my laptop connects and disconnects in a 7s rhythm. a restart solves this problem (is there a command to manually restart the network without the need to restart?

laptop: packard bell easynote w1000
ubuntu 9.10
lspci -v readout:

```
        Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Device 2560
        Flags: bus master, slow devsel, latency 128, IRQ 21
        Memory at c0000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: rt2500pci
        Kernel modules: rt2500pci
```

kern.log shows "phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)." twice every minute

probably related, after suspend or hibernation networking is disabled, enabling it via right-click does not work again after a restart everything works how it should.

thanks

---

### Post by chili555 on 2010-01-29
Please let us see:```
lspci -nn | grep Network
lsmod | grep rt2
```Thanks.

---

### Post by unitedoceanic on 2010-01-29
here you go

```
lspci -nn | grep Network

01:05.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)

lsmod | grep rt2

rt2500pci              15356  0 
rt2x00pci               7900  1 rt2500pci
rt2x00lib              29756  2 rt2500pci,rt2x00pci
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00pci,rt2x00lib
led_class               4096  2 rt2x00lib,sdhci
cfg80211               93052  2 rt2x00lib,mac80211
eeprom_93cx6            1916  1 rt2500pci
oceanic@red-queen:~$ 

```

---

### Post by chili555 on 2010-01-29
It all looks perfectly normal. Please do:```
iwconfig
```You should see something like this:> IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:2A:D7:99   
          Bit Rate=[COLOR="Red"]54 Mb/s [/COLOR]  Tx-Power=13 dBmIf you see something less, please do:```
sudo iwconfig ra0 rate 54M
```Substitute your interface, if it's not *ra0*. Last, please install *linux-backports-modules-karmic-generic*. There is evidently a better rt2500pci module in there.

Post back and let us know the result.

---

### Post by unitedoceanic on 2010-01-29
iwconfig showed me different values 

6Mb/s; 12MB/s; 24MB/s and 36MB/s all caught in the same minute

i set the bit rate to 54Mb/s and i already watched the wireless reconnect on it's own.

fantastic :D

i will test the linux-backports-modules-karmic-generic and report back.

thank you very much for your time and effort!

---

