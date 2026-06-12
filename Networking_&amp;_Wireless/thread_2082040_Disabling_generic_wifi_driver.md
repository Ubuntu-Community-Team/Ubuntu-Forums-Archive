---
title: "Disabling generic wifi driver"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by ZOMFG on 2012-11-08
Hi,

I am experiencing some issues with Wi-Fi, where it disconnects every minute, and never reconnects..so I installed a ralink driver on my system, however when i run "lspci -knn" the kernel driver in use always shows as rt2860, and not the installed driver..
I am wondering if I can disable the 2860 and enable the one i installed.


I blacklisted the 2860 in modprobe.d/blacklist.conf, but it makes no difference after reboot.


Driver i installed - DPO_RT3562_3592_3062_LinuxSTA_V2.4.1
I disabled ipv6 and power management (some people said that helps.. but it didn't for me)Also created a "blacklist-internal-wifi.conf" file in modprobe.d and listed the rt2860 and rt280 modules as blacklisted, but after reboot the wifi is still going nuts..
 
Could anyone please let me know how to activate the RT3562/3592 driver instead of the 2860?


Thanks

---

### Post by chili555 on 2012-11-08
> Driver i installed - DPO_RT3562_3592_3062_LinuxSTA_V2.4.1This driver was written at Ralink using RT2860 as a template. It is for a PCI device, a close relative chipset, wireless, etc. Why start with a clean sheet of paper when 90% of the work is already done?

Somewhere deep in the C code is an alias for rt2860 that sadly shows up in lspci -knn. That doesn't mean that is the module that's loaded and driving your device. The only authoritative, absolute answer is:```
lsmod
```Which is loaded?

Let's troubleshoot your connection:```
lsmod | grep -e rt2 -e rt3
ls /etc/modprobe.d
lsb_release -d
iwconfig
```Thanks.

---

### Post by ZOMFG on 2012-11-08
Hm.. let's try this:
** lsmod | grep -e rt2 -e rt3**
```
tom@ragequit ~ $ lsmod | grep -e rt2 -e rt3
rt3562sta             990799  0
```
**tom@ragequit ~ $ ls /etc/modprobe.d**
```
alsa-base.conf                blacklist-modem.conf         net.ipv6.conf.all.disable_ipv6 = 1
blacklist-ath_pci.conf        blacklist-oss.conf           net.ipv6.conf.default.disable_ipv6 = 1
blacklist.conf                blacklist-rare-network.conf  net.ipv6.conf.lo.disable_ipv6 = 1
blacklist-firewire.conf       blacklist-watchdog.conf      oss-compat.conf
blacklist-framebuffer.conf    dkms.conf
blacklist-internal-wifi.conf  echo
```

**tom@ragequit ~ $ lsb_release -d**
```
Description:    Linux Mint 13 Maya
```

(for the below - fyi - i'm currently on a wired conn)
**tom@ragequit ~ $ iwconfig**
```
lo        no wireless extensions.


ra0       Ralink STA  
          
eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-11-08
> net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
These three are malformed and will have no real effect. The best way to disable IPv6 is within Network Manager; please see attached. You may as well remove these files:```
sudo rm /etc/modprobe.d/net.ipv6*
```> tom@ragequit ~ $ lsmod | grep -e rt2 -e rt3
rt3562sta             990799  0The driver you want is the driver that's loaded and none more. More importantly:> Description:    Linux Mint 13 MayaMaya uses the 3.2.xx kernel version. The staging Ralink drivers, including rt2860sta, are not included in 3.2.xx. If that is the purpose of blacklist-internal-wifi.conf, to blacklist what doesn't exist, you may as well remove it, too.```
sudo rm /etc/modprobe.d/blacklist-internal-wifi.conf
```Please disconnect the ethernet and run and post:```
sudo iwlist ra0 scan
dmesg | grep rt3
cat /etc/modprobe.d/blacklist.conf | tail -n5
```Thanks.

---

### Post by ZOMFG on 2012-11-08
sudo iwlist ra0 scan
```

ra0       Scan completed :
          Cell 01 - Address: E8:40:40:AC:29:31
                    Protocol:802.11g
                    ESSID:"reply-wpa"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: E8:40:40:AC:29:30
                    Protocol:802.11g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:47/100  Signal level:-71 dBm  Noise level:-74 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:27:22:14:C2:BB
                    Protocol:802.11b/g/n
                    ESSID:"I3P"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:47/100  Signal level:-71 dBm  Noise level:-66 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:26:3E:EB:6E:40
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:89:58:A8:C3
                    Protocol:802.11b/g
                    ESSID:"Vodafone-11425573"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:24:36:B5:EC:4E
                    Protocol:802.11b/g/n
                    ESSID:"Rocco\xE2\x80\x99s Mac Pro"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:89/100  Signal level:-55 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 07 - Address: 00:27:0D:57:82:E0
                    Protocol:802.11g
                    ESSID:"reply-wpa"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:47/100  Signal level:-71 dBm  Noise level:-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: 00:0E:2E:A0:78:59
                    Protocol:802.11b/g
                    ESSID:"A2D"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-83 dBm  Noise level:-78 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 09 - Address: 00:26:3E:EB:69:C4
                    Protocol:802.11b/g/n
                    ESSID:"PxGuest"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s


```

dmesg | grep rt3
```

Returns nothing

```

cat /etc/modprobe.d/blacklist.conf | tail -n5

```

blacklist rt2800pci
blacklist rt2860pci
blacklist rt2860
blacklist rt2x00pci
blacklist rt2800usb


```

---

### Post by chili555 on 2012-11-08
> cat /etc/modprobe.d/blacklist.conf | tail -n5

Code:

blacklist rt2800pci
blacklist rt2860pci
blacklist rt2860
blacklist rt2x00pci
blacklist rt2800usb

There is nothing harmful in here, but to be rigorously correct, you could amend it so that ending section only includes:```
blacklist rt2800pci
```The remaining  parts of the file above remain unchanged.

Which of the access points above are you trying to connect to? All, except one, are pretty weak.

Let's try:```
dmesg | grep -i rt2
```

---

### Post by ZOMFG on 2012-11-08
Hi,

thank you for your help so far.

I am trying to connect to reply-wpa currently. Which is our corporate network, it uses a wpa2, PEAP, + user auth.

Although no other network works well either. I get the same issues connecting to my hotel wifi or at home..

---

### Post by ZOMFG on 2012-11-08
**dmesg | grep -i rt2**```

[ 5201.498097] rt28xx_get_wireless_stats --->
[ 5201.498100] <--- rt28xx_get_wireless_stats
[ 5207.496559] rt28xx_get_wireless_stats --->
[ 5207.496565] <--- rt28xx_get_wireless_stats
[ 5213.494802] rt28xx_get_wireless_stats --->
[ 5213.494804] <--- rt28xx_get_wireless_stats
[ 5219.488292] rt28xx_get_wireless_stats --->
[ 5219.488298] <--- rt28xx_get_wireless_stats
[ 5225.488701] rt28xx_get_wireless_stats --->
[ 5225.488707] <--- rt28xx_get_wireless_stats
[ 5237.478971] rt28xx_get_wireless_stats --->
[ 5237.478977] <--- rt28xx_get_wireless_stats
[ 5243.479371] rt28xx_get_wireless_stats --->
[ 5243.479376] <--- rt28xx_get_wireless_stats
[ 5249.470834] rt28xx_get_wireless_stats --->
[ 5249.470836] <--- rt28xx_get_wireless_stats
[ 5255.468122] rt28xx_get_wireless_stats --->
[ 5255.468128] <--- rt28xx_get_wireless_stats
[ 5261.464732] rt28xx_get_wireless_stats --->
[ 5261.464738] <--- rt28xx_get_wireless_stats
[ 5267.461874] rt28xx_get_wireless_stats --->
[ 5267.461876] <--- rt28xx_get_wireless_stats
[ 5273.458280] rt28xx_get_wireless_stats --->
[ 5273.458282] <--- rt28xx_get_wireless_stats
[ 5291.451695] rt28xx_get_wireless_stats --->
[ 5291.451701] <--- rt28xx_get_wireless_stats
[ 5297.451421] rt28xx_get_wireless_stats --->
[ 5297.451424] <--- rt28xx_get_wireless_stats
[ 5303.446206] rt28xx_get_wireless_stats --->
[ 5303.446211] <--- rt28xx_get_wireless_stats
[ 5309.440771] rt28xx_get_wireless_stats --->
[ 5309.440773] <--- rt28xx_get_wireless_stats
[ 5315.440571] rt28xx_get_wireless_stats --->
[ 5315.440577] <--- rt28xx_get_wireless_stats
[ 5321.433433] rt28xx_get_wireless_stats --->
[ 5321.433438] <--- rt28xx_get_wireless_stats
[ 5327.430313] rt28xx_get_wireless_stats --->
[ 5327.430318] <--- rt28xx_get_wireless_stats
[ 5333.427976] rt28xx_get_wireless_stats --->
[ 5333.427982] <--- rt28xx_get_wireless_stats
[ 5339.425277] rt28xx_get_wireless_stats --->
[ 5339.425282] <--- rt28xx_get_wireless_stats
[ 5351.418758] rt28xx_get_wireless_stats --->
[ 5351.418761] <--- rt28xx_get_wireless_stats
[ 5357.415563] rt28xx_get_wireless_stats --->
[ 5357.415566] <--- rt28xx_get_wireless_stats
[ 5363.413863] rt28xx_get_wireless_stats --->
[ 5363.413865] <--- rt28xx_get_wireless_stats
[ 5369.409982] rt28xx_get_wireless_stats --->
[ 5369.409984] <--- rt28xx_get_wireless_stats
[ 5375.408499] rt28xx_get_wireless_stats --->
[ 5375.408502] <--- rt28xx_get_wireless_stats
[ 5381.403733] rt28xx_get_wireless_stats --->
[ 5381.403735] <--- rt28xx_get_wireless_stats
[ 5387.404197] rt28xx_get_wireless_stats --->
[ 5387.404203] <--- rt28xx_get_wireless_stats
[ 5393.400507] rt28xx_get_wireless_stats --->
[ 5393.400513] <--- rt28xx_get_wireless_stats
[ 5400.601189] rt28xx_get_wireless_stats --->
[ 5400.601192] <--- rt28xx_get_wireless_stats
[ 5405.390727] rt28xx_get_wireless_stats --->
[ 5405.390733] <--- rt28xx_get_wireless_stats
[ 5411.388265] rt28xx_get_wireless_stats --->
[ 5411.388271] <--- rt28xx_get_wireless_stats
[ 5417.383865] rt28xx_get_wireless_stats --->
[ 5417.383870] <--- rt28xx_get_wireless_stats
[ 5423.382926] rt28xx_get_wireless_stats --->
[ 5423.382931] <--- rt28xx_get_wireless_stats
[ 5429.378387] rt28xx_get_wireless_stats --->
[ 5429.378393] <--- rt28xx_get_wireless_stats
[ 5435.375749] rt28xx_get_wireless_stats --->
[ 5435.375751] <--- rt28xx_get_wireless_stats
[ 5441.372936] rt28xx_get_wireless_stats --->
[ 5441.372942] <--- rt28xx_get_wireless_stats
[ 5447.368575] rt28xx_get_wireless_stats --->
[ 5447.368581] <--- rt28xx_get_wireless_stats
[ 5453.365345] rt28xx_get_wireless_stats --->
[ 5453.365351] <--- rt28xx_get_wireless_stats
[ 5471.357529] rt28xx_get_wireless_stats --->
[ 5471.357532] <--- rt28xx_get_wireless_stats
[ 5477.359782] rt28xx_get_wireless_stats --->
[ 5477.359788] <--- rt28xx_get_wireless_stats
[ 5483.353796] rt28xx_get_wireless_stats --->
[ 5483.353798] <--- rt28xx_get_wireless_stats
[ 5489.348627] rt28xx_get_wireless_stats --->
[ 5489.348629] <--- rt28xx_get_wireless_stats
[ 5495.347357] rt28xx_get_wireless_stats --->
[ 5495.347362] <--- rt28xx_get_wireless_stats
[ 5501.341356] rt28xx_get_wireless_stats --->
[ 5501.341358] <--- rt28xx_get_wireless_stats
[ 5507.339118] rt28xx_get_wireless_stats --->
[ 5507.339120] <--- rt28xx_get_wireless_stats
[ 5513.335643] rt28xx_get_wireless_stats --->
[ 5513.335649] <--- rt28xx_get_wireless_stats
[ 5519.332538] rt28xx_get_wireless_stats --->
[ 5519.332540] <--- rt28xx_get_wireless_stats
[ 5525.329521] rt28xx_get_wireless_stats --->
[ 5525.329526] <--- rt28xx_get_wireless_stats
[ 5531.325551] rt28xx_get_wireless_stats --->
[ 5531.325557] <--- rt28xx_get_wireless_stats
[ 5543.320174] rt28xx_get_wireless_stats --->
[ 5543.320176] <--- rt28xx_get_wireless_stats
[ 5549.317052] rt28xx_get_wireless_stats --->
[ 5549.317057] <--- rt28xx_get_wireless_stats
[ 5562.422189] RT28xxPciMlmeRadioOFF===>
[ 5562.435368] RT28xxPciAsicRadioOff ===> Lv= 1, TxCpuIdx = 36, TxDmaIdx = 36. RxCpuIdx = 83, RxDmaIdx = 84.
[ 5566.943413] ===> rt28xx_close
[ 5566.949048] RT28xxPciAsicRadioOff ===> Lv= 2, TxCpuIdx = 36, TxDmaIdx = 36. RxCpuIdx = 83, RxDmaIdx = 84.
[ 5566.949288] <=== rt28xx_close 
```

---

### Post by chili555 on 2012-11-08
I just built the driver on a kernel 3.2.xx system; there are a lot of warnings for sure. Can you confirm you did this step in the README?> 3> In os/linux/config.mk 
	
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.And this?> 5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat Did you have similar trouble with the built-in rt2800pci? Or did it not work at all? Firmware??

---

### Post by ZOMFG on 2012-11-09
Hi,

I have set the two supplicant lines as "Y" before make/make install; I only did it because there was another thread on that specific driver, saying this should be done.

I have copied over the files as per your reply. Going to leave the wifi on and see how it performs. 

The whole reason why I opted to install this driver is because i had the disconnection problem with the original pre-installed driver.

When you mentioned firmware, you wanted to know which fw it's running specifically?

---

### Post by ZOMFG on 2012-11-09
Small update - the wifi has now been running happily for the past 15~ minutes, without disconnecting. Not sure if it's early to celebrate, but seems stable enough.

[EDIT] - After several disconnetions (intentional and manual), and reconnecting, it seems it's stable enough to use. 
Not sure exactly which part of our troubleshooting jogged it into working, but it seems it is working.

---

### Post by chili555 on 2012-11-09
I asked about firmware because I wondered if Mint installed the firmware by default. If you connected at all, the firmware was present.

In order for the driver to recognize the .dat file, unload and reload it:```
sudo modprobe -r rt3562sta && sudo modprobe rt3562sta
```We wonder if it will make a difference.

---

