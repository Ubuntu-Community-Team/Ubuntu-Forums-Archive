---
title: "How-to: Setup Linksys WUSB600N v2 (chip RT3572)"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by joho500 on 2011-02-18
Hi all,

It took me some time to find information to setup the Linksys WUSB600N version 2 wireless adapter. To save others the time searching the internet I hereby post in short what steps I took.

[LIST=1]
[*]Check your device to verify it's the WUSB600N version 2
```
lsusb |grep 1737
```
This should return:
```
...: ID 1737:0079 Linksys
```
[*]Download and unpack the driver
Go to [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2") and download the driver for chipset RT3572.

[*]Edit the file .../os/linux/config.mk" in the downloaded package to get wpa_supplicant and Networkmanager support
    I did the following changes:
```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
HAS_QOS_DLS_SUPPORT=y
HAS_DOT11N_DRAFT3_SUPPORT=y
HAS_DOT11_N_SUPPORT=y
HAS_STATS_COUNT=y
```

[*]Add the USB ID of the adapter in file ".../common/rtusb_dev_id.c" under section: #ifdef RT35xx
See below (second last line) for detailed information:

```
#ifdef RT35xx
 {USB_DEVICE(0x148F,0x3572)}, /* Ralink 3572 */
 {USB_DEVICE(0x1740,0x9801)}, /* EnGenius 3572 */
 {USB_DEVICE(0x0DF6,0x0041)}, /* Sitecom 3572 */
 {USB_DEVICE(0x0DF6,0x0042)},
 {USB_DEVICE(0x04BB,0x0944)}, /* I-O DATA 3572 */
 {USB_DEVICE(0x1690,0x0740)}, /* 3572 */
 {USB_DEVICE(0x1690,0x0744)}, /* 3572 */
 {USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
 {USB_DEVICE(0x167B,0x4001)}, /* 3572 */
 **{USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600Nv2 */**
#endif // RT35xx //
```

[*]Enter the main directory of the package. Make and install the driver.
```
make
sudo make install
```

[*]Create file /etc/udev/rules.d/10-wusb600nv2.rules
Add the following lines:
```
# UDEV-Rule for wusb-600Nv2 ID 1737:0079
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0079", RUN+="/sbin/modprobe rt3572sta"
```

[*]Create the file /etc/modprobe.d/rt3572sta.conf
Add the following line:
```
install rt3572sta modprobe --ignore-install rt3572sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id
```

[*]Blacklist other drivers
Open /etc/modprobe.d/blacklist.conf
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Put the following lines at the end of the file:

```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870
```

[*]Reboot
[/LIST]

You have to recompile on every kernel update. You can use DKMS to automate this process. See [https://help.ubuntu.com/community/DKMS]("https://help.ubuntu.com/community/DKMS") for more info on this topic.

This worked for me.

Cheers,
Joost

---

### Post by Afiso on 2011-02-21
Hi joho500,

I'm using backtrack4 with vmware. I can see the WUSB600Nv2 with the option lsusb | grep 1737 and is the same like yours.
I did every thing you told, but i think when i add the codes to the blacklist the WUSB600N doen's work at all.
I then see this wiht iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA

if i don't add the line rt2800usb to the blacklist i see this when i type iwconfig

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

and if i type ifconfig wlan0 up, the bluelight turns on.
airmon-ng start wlan0
airodump-ng mon0 Is running but can't find no wirelessstations.
Help me please. I bin working, googling for 2 weeks right now. 
:(
Sorry about my bad English. I'm from the Netherlands

---

### Post by joho500 on 2011-03-09
My own setup is broken again too. I think because of a kernel update. I'll look into it this weekend.

---

### Post by joho500 on 2011-05-01
I found out that you have to recompile the driver after every kernel update. It is possible to automate this by using DKMS (see the first post for a link to documentation on that topic).

I've added some additional steps to the first post that should help to load the driver automatically and to get it back up after suspend.

Cheers,
Joost

---

### Post by Gunner2677 on 2011-05-03
So I've hit a problem where I can now see the Wireless Networks, however I cannot connect. A number of other users have hit this problem as well in other forums.

---

