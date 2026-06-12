---
title: "RT5370 or RT3572 compat wireless drivers Access Point mode"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by mehta_4v on 2012-11-26
Hi all,

    I have two USB sticks one with Ralink RT5370 chip and the other with RT3572 chip. I want to make them work in the access point mode. Unfortunately the drivers from the Ralink site do not support the Access Point mode. I read somewhere that the compat wireless modules have the support for access point mode for the Ralink drivers. So I downloaded the latest compat wireless package. But when I do ./scripts/driver-select Ralink drivers for the chips I mentioned are not listed there. My kernel version is 2.6.38.

Does anybody have any experience in compat wireless with these chips.
Also anywhere else I could get drivers for these which would support the access point mode ?

- Charvi

---

### Post by chili555 on 2012-11-26
> Does anybody have any experience in compat wireless with these chips.No. These devices are not supported by compat-wireless. Period.> Also anywhere else I could get drivers for these which would support the access point mode ?None that I know of.

Not all wireless devices and their associated drivers do all things.

---

### Post by mehta_4v on 2012-11-26
> **chili555 said:**
> No. These devices are not supported by compat-wireless. Period.None that I know of.



Thanks chili555 for your reply.
Based on your conclusions I switched to a realtek USB stick which has rt8192c chipset. I already had the access point mode in it working with the driver I took from the official realtek site. But then I wanted to add the multiple ssid support in it. Unfortunately the driver is not based on mac80211 (its a 2011 driver). From the following post ([http://comments.gmane.org/gmane.linux.kernel.wireless.general/95135](http://comments.gmane.org/gmane.linux.kernel.wireless.general/95135)) I gathered that i could achieve what I want from compat wireless driver. So then I downloaded compat wireless source (compat-wireless-3.4-rc3-1.tar.bz2) and build it according to the instructions from ([http://wiki.backbox.org/index.php/Compat-wireless_aircrack_patched](http://wiki.backbox.org/index.php/Compat-wireless_aircrack_patched)). The package build successfully and I got following modules which I inserted in the same order:

compat.ko
cfg80211.ko
mac80211.ko
rtlwifi.ko
rtl8192c-common.ko
rtl8192cu.ko

Now When I insert my stick I get following error:
rtlwifi: Firmware rtlwifi/rtl8192cufw.bin not available 
:(

Where do I get this from ?

Regards,
Charvi

---

### Post by chili555 on 2012-11-26
What, exactly do you have installed?```
lsb_release -a
``` On recent Ubuntu distributions, it's installed by default. Let's dig around a bit:```
ls /lib/firmware | grep rtlwifi
```Does the directory exist? If so, let's see what's in there:```
ls -al /lib/firmware/rtlwifi
```I may have a few things here if we don't find what we need.

---

### Post by mehta_4v on 2012-11-27
Sorry for late reply chili555.
Thankyou so much for looking into this.

I looked into the /lib/firmware and founf no directory like rtlwifi. So basically there was no firmware, so I got the linux-firware tar ball from the git (git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git). I untar it and got firware images like following:

Wifi/linux-firmware/linux-firmware-e0836e6# ls rtlwifi/
rtl8192cfw.bin 
rtl8192cfwU_B.bin 
rtl8192cfwU.bin 
rtl8192cufw.bin 
rtl8192defw.bin 
rtl8192sefw.bin 
rtl8712u.bin

So I copied the rtl8192cufw.bin  to /lib/firmware. Then when I inserted my USB stick i got the following:

usb 1-1: New USB device found, idVendor=0bda, idProduct=8176
usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-1: Product: Wireless N USB Adapter
usb 1-1: Manufacturer: Realtek
usb 1-1: SerialNumber: 00e04c000001
rtl8192cu: Chip version 0x10
rtl8192cu: MAC address: 00:21:2f:3a:b8:fe
rtl8192cu: Board Type 0
rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
rtlwifi: wireless switch is on

and on iwconfig I got the following:

wlan1     IEEE 802.11bgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:Off
          Power Management:On

Uptil here its good. Now when I run the hostapd with following configuration:
**********************************
          hostapd.conf
**********************************
interface=wlan1
driver=nl80211
ssid=rtwap
channel=6
channel=6
wpa=2
wpa_passphrase=87654321
eap_server=1
wps_state=2
uuid=12345678-9abc-def0-1234-56789abcdef0
device_name=RTL8192CU
manufacturer=Realtek
model_name=RTW_SOFTAP
model_number=WLAN_CU
serial_number=12345
device_type=6-0050F204-1
os_version=01020300
config_methods=label display push_button keypad
beacon_int=100
hw_mode=g
ieee80211n=1
wme_enabled=1
ht_capab=[SHORT-GI-20][SHORT-GI-40][HT40+]
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
max_num_sta=8
wpa_group_rekey=86400

it gives me this:
wlan1     IEEE 802.11bgn  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:Off
          Power Management:On

mon.wlan1  IEEE 802.11bgn  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:Off
          Power Management:On

without any ssid :( :(

Any Idea why ????

---

### Post by mehta_4v on 2012-11-27
Okay I tried to do some futile digging and here is the output of my hostapd command with the -dd switch:

root@10.99.14.100:/bin/wifi# ./hostapd minimalistic.conf -B
Configuration file: minimalistic.conf
########conf->driver = wpa_drivers[0] = nl80211

########bss->ssid.ssid = Charvi

rfkill: Cannot open RFKILL control device

OOOOOOOOOOOO#########inside wpa_driver_rtl8192cu: MAC auto ON okay!
nl80211_finish_drv_init

rtl8192cu: Tx queue select: 0x05
#######setup_interface

#######hostapd_validate_bssid_configuration

#######hostapd_setup_interface_complete

#######hostapd_setup_bss

Using interface wlan0 with hwaddr 00:21:2f:3a:b8:f0 and ssid 'Charvi'
random: Cannot read from /dev/random: Resource temporarily unavailable
random: Only 0/20 bytes of strong random data available from /dev/random
random: Not enough entropy pool available for secure operations
WPA: Not enough entropy in random pool for secure operations - update keys later when the first station connects

and then when I run iwconfig I get:

root@10.99.14.100:/bin/wifi# iwconfig
lo        no wirnet eth0: DaVinci EMAC: ioctl not supported
eless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 21.
Some things may be broken...

wlan0     IEEE 802.11bgn  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

No SSID....

---

### Post by chili555 on 2012-11-27
I'm sorry, hostap is outside my limited experience. I suspect you'll have better luck in a new thread with hostap in the title.

---

