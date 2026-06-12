---
title: "Having trouble connecting to WPA after upgrade to 11.10"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by peejaroni on 2011-10-16
Hi all, 
I just upgraded to 11.10, and ubuntu seems to be having trouble connecting to my University's wireless. 
After about an hour of timing-out and restarting it, the card did connect to the internet for about 5 minutes before cutting out. 
I have a thinkpad t420, with the intel 6205 wireless card. I tried switching to WICD but that didn't help. 

Thanks for your help!

---

### Post by wildmanne39 on 2011-10-16
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by peejaroni on 2011-10-17
Sure thing, thanks for taking a look: 


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
	Kernel driver in use: iwlagn

---

### Post by wildmanne39 on 2011-10-17
Hi, disconnect your wired connection and try this if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
Run the commands one line at a time.
Thank you

---

### Post by peejaroni on 2011-10-17
Nope, that didn't seem to do it.

---

### Post by wildmanne39 on 2011-10-17
Hi, have you disabled ipv6?
Thank you

---

### Post by peejaroni on 2011-10-17
Yup, ipv6 is set to "ignore"

---

### Post by wildmanne39 on 2011-10-17
Hi, please post the results of these commands here: you will need to be at the location you are having trouble connecting too.
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n35
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by peejaroni on 2011-10-18
nm-tool
```


NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:21:CC:62:2B:7B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Northwestern 4] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connecting (configuring)
  Default:           no
  HW Address:        A0:88:B4:7C:0F:80

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HPD110a.77696F:  Ad-Hoc, 02:2D:AD:B2:F0:B1, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    HPD110a.8F9581:  Ad-Hoc, 02:2F:2F:7B:78:7A, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    Northwestern:    Infra, 00:1A:1E:84:D3:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    Northwestern:    Infra, 00:24:6C:13:F6:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A1:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA2 Enterprise
    HPC53AD2:        Ad-Hoc, F6:74:EE:A9:19:9F, Freq 2462 MHz, Rate 11 Mb/s, Strength 20
    hpsetup:         Ad-Hoc, 2E:22:64:D2:12:73, Freq 2437 MHz, Rate 11 Mb/s, Strength 22
    Apple Network 82762f: Infra, 10:9A:DD:82:76:30, Freq 5220 MHz, Rate 54 Mb/s, Strength 22
    HP084497:        Ad-Hoc, 02:20:90:70:DC:6B, Freq 2457 MHz, Rate 11 Mb/s, Strength 42
    HPJ610a.FA2A68:  Ad-Hoc, 02:2A:1A:9A:8E:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    Apple Network 82762f: Infra, 10:9A:DD:82:76:2F, Freq 2412 MHz, Rate 54 Mb/s, Strength 57
    Milk:            Infra, F8:1E:DF:FB:E0:FC, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Northwestern:    Infra, 00:1A:1E:8A:4B:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    CplusJsBigMistake: Infra, E0:46:9A:70:23:AF, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Northwestern:    Infra, 00:1A:1E:8A:44:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:E2:F0, Freq 5805 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:4D:10, Freq 5200 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:E1:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:D0:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8D:71:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:4C:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:42:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:0E:D0, Freq 5220 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:4C:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:50:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    Milk:            Infra, F8:1E:DF:FB:E0:FB, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Northwestern:    Infra, 00:1A:1E:8A:A1:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:51:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:E3:70, Freq 5745 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A2:B0, Freq 5240 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A1:B0, Freq 5200 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A2:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:95:70, Freq 5220 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A1:10, Freq 5765 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:4D:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:E2:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:84:E3:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:0E:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:95:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    Northwestern:    Infra, 00:1A:1E:8A:A1:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise

```




iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

rfkill list all
```

4: phy4: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod | grep iwl
```



iwlagn                333716  0 
iwlcore               167502  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
cfg80211              178528  3 iwlagn,iwlcore,mac80211
```



sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n35
```


Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0/wireless): connection 'Auto Northwestern' has security, and secrets exist.  No new secrets needed.
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 18 00:37:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 18 00:37:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 18 00:37:55 pj-ThinkPad-T420 kernel: [26808.333440] wlan0: authenticate with 00:1a:1e:8a:a1:00 (try 1)
Oct 18 00:37:55 pj-ThinkPad-T420 kernel: [26808.335136] wlan0: 00:1a:1e:8a:a1:00 denied authentication (status 17)
Oct 18 00:38:52 pj-ThinkPad-T420 NetworkManager[1004]: <warn> Activation (wlan0/wireless): association took too long.
Oct 18 00:38:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 18 00:38:52 pj-ThinkPad-T420 NetworkManager[1004]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct 18 00:38:52 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0/wireless): connection 'Auto Northwestern' has security, and secrets exist.  No new secrets needed.
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 18 00:38:55 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 18 00:38:58 pj-ThinkPad-T420 kernel: [26871.093985] wlan0: direct probe to 00:1a:1e:8a:a1:a0 (try 1/3)
Oct 18 00:38:58 pj-ThinkPad-T420 NetworkManager[1004]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 18 00:38:58 pj-ThinkPad-T420 kernel: [26871.290146] wlan0: direct probe to 00:1a:1e:8a:a1:a0 (try 2/3)
Oct 18 00:38:58 pj-ThinkPad-T420 kernel: [26871.489930] wlan0: direct probe to 00:1a:1e:8a:a1:a0 (try 3/3)
Oct 18 00:38:59 pj-ThinkPad-T420 kernel: [26871.689550] wlan0: direct probe to 00:1a:1e:8a:a1:a0 timed out
Oct 18 00:39:07 pj-ThinkPad-T420 kernel: [26879.904907] wlan0: authenticate with 00:1a:1e:8a:a1:00 (try 1)
Oct 18 00:39:07 pj-ThinkPad-T420 kernel: [26879.906989] wlan0: 00:1a:1e:8a:a1:00 denied authentication (status 17)
Oct 18 00:39:12 pj-ThinkPad-T420 kernel: [26885.316974] wlan0: authenticate with 00:1a:1e:8a:a1:00 (try 1)
Oct 18 00:39:12 pj-ThinkPad-T420 kernel: [26885.318733] wlan0: 00:1a:1e:8a:a1:00 denied authentication (status 17)


```

---

### Post by wildmanne39 on 2011-10-18
Hi, the only work around that has been found is to downgrade the kernel to 2.6.38. Look at post 42 in this link.
[http://ubuntuforums.org/showthread.php?t=1862484&page=5](http://ubuntuforums.org/showthread.php?t=1862484&page=5)
After you do make sure to open open synaptic and lock that kernel from being upgraded.
Thank you

---

### Post by peejaroni on 2011-10-18
Thanks, I think that helped, the wireless is still flakey but seems to connect a little more frequently than before. 
How do I lock the kernel version?

---

### Post by wildmanne39 on 2011-10-18
Hi, please click on synaptic then the name of the linux kernel header you are using then go to the top of the window, in package click lock.

Also try what is in post 4 and I think that will help now.

It is only for one boot so after you restart that option will be gone, but if it helps we can make it permanent.
Thank you

---

### Post by praseodym on 2011-10-18
Install the package "startupmanager" and choose "your" kernel as default.
Maybe you want to install the latest driver and firmware for kernel 3 (you need to boot into this kernel!):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make clean
make
sudo make install 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```
and reboot. The driver needs to be installed again after a kernel upgrade.

---

### Post by androscelta on 2011-10-18
Exactly the same problem on MSI U270 with Unversity wifi.
I'll try to get results of comands.

---

### Post by peejaroni on 2011-10-18
It looks like I spoke too soon, it disconnected less than an hour after I connected that one time. I tried praseodym's commands, and that didn't help either. Here is the output of installing those drivers though, it gave some errors as I was installing:


```
pj@pj-ThinkPad-T420:~$ cd compat-wireless*
pj@pj-ThinkPad-T420:~/compat-wireless-2011-10-18$ make clean
/home/pj/compat-wireless-2011-10-18/config.mk:213: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
pj@pj-ThinkPad-T420:~/compat-wireless-2011-10-18$ make
/home/pj/compat-wireless-2011-10-18/config.mk:213: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.38-11-generic/build M=/home/pj/compat-wireless-2011-10-18 modules
make: *** /lib/modules/2.6.38-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
pj@pj-ThinkPad-T420:~/compat-wireless-2011-10-18$ sudo make install
[sudo] password for pj: 
/home/pj/compat-wireless-2011-10-18/config.mk:213: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
kernel/drivers/staging/brcm80211/brcm80211.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl1251/wl1251.ko
kernel/drivers/net/wireless/wl12xx/wl12xx.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/sco.ko

make -C /lib/modules/2.6.38-11-generic/build M=/home/pj/compat-wireless-2011-10-18 modules
make: *** /lib/modules/2.6.38-11-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

---

### Post by praseodym on 2011-10-19
The file with "wget" was downloaded 100%? Try the link directly

---

### Post by peejaroni on 2011-10-23
I tried re-installing it a few times, and it still won't work. I randomly can connect to wifi at a few places on campus if I keep trying for 15-20 minutes, but not at all at others.

---

### Post by vacaloca on 2012-01-18
Since this thread has no apparent resolution, I thought I'd share what worked for me:

[http://ubuntuforums.org/showpost.php?p=11619702&postcount=4](http://ubuntuforums.org/showpost.php?p=11619702&postcount=4)

I also posted the solution here, since all of the symptoms seem to be related:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754)

---

