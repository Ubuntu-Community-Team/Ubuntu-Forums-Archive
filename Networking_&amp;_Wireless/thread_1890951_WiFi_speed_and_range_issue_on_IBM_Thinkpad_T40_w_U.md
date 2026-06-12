---
title: "WiFi speed and range issue on IBM Thinkpad T40 w/ Unbunt 11.10"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by zheka8 on 2011-12-04
Hi,

I just installed Ubuntu 11.10 on an old IBM Thinkpad T40. Wireless card is Atheros and as far as I can tell I'm using the ath5k driver. Wireless works when I'm within a few feet of the access point, and it's slow. Farther away, adapter picks up the network and shows it with decent bars, but does not connect. I've tried a few things that I could find in the forums such as disabling IPv6, hwcrypt, blacklisting acer_wmi.

Thanks

Details:

IBM Thinkpad T40
Ubuntu 11.10
3.0.0-13-generic i686
Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)

iwconfig
```

wlan0     IEEE 802.11ab  ESSID:"2121"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:68:5B:97   
          Bit Rate=18 Mb/s   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:54  Invalid misc:668   Missed beacon:0
```lsmod
```

ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
```dmesg
```

[   23.210124] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   23.210196] ath5k 0000:02:02.0: registered as 'phy0'
[   23.645287] ath: EEPROM regdomain: 0x61
[   23.645292] ath: EEPROM indicates we should expect a direct regpair map
[   23.645299] ath: Country alpha2 being used: 00
[   23.645302] ath: Regpair used: 0x61
[   23.750180] Registered led device: ath5k-phy0::rx
[   23.750243] Registered led device: ath5k-phy0::tx
[   23.750258] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
[   23.750261] ath5k phy0: RF5111 5GHz radio found (0x17)
[   23.750264] ath5k phy0: RF2111 2GHz radio found (0x23)
[   91.791202] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[   94.917685] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[   97.769343] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[   97.827820] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[   98.138551] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[   98.314102] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[  160.586756] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[  161.274295] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[  162.860013] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
[  163.657751] ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x80081035
```lshw -C network 
```
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:10:28:0f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0240000-c024ffff
  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:05:4e:40:da:d8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-13-generic firmware=N/A ip=192.168.1.103 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11ab
       resources: irq:11 memory:c0210000-c021ffff

```sudo /etc/init.d/networking restart
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 
```

---

### Post by bluexrider on 2011-12-04
has this been an issue or did you notice it with the new kernel

---

### Post by zheka8 on 2011-12-04
I was running Windows XP prior to this. All my other devices work fine with the access point, and so did the laptop with Windows.

---

### Post by zheka8 on 2011-12-04
Found another post that mentioned slow speeds with Ubuntu 11.10 and recommended removing network-manager and installing wicd. No luck, but it seems that in both cases (network manager and wicd), the issue is during authentication stage. If my laptop is in a different room from the AP, it shows signal strength as fine, but simply will not authenticate. Tried with WEP and WPA2 with no luck.

---

### Post by zheka8 on 2011-12-05
Anyone?

---

### Post by zheka8 on 2011-12-05
ndiswrapper solved the issue

---

