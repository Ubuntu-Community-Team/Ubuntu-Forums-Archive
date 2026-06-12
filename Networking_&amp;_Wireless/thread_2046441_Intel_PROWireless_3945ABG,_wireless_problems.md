---
title: "Intel PRO/Wireless 3945ABG, wireless problems"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by pbice on 2012-08-23
I have a Dell Latitude D420 which has an Intel PRO/Wireless 3945ABG wireless card.  I can't get wireless internet, i says Firmware Missing.  Can someone please help me out?

---

### Post by 2F4U on 2012-08-23
Did you try the Additional Drivers application? Does it suggest drivers to be installed?

---

### Post by 2F4U on 2012-08-23
You may want to look into these posts and see if it helps:

[http://ubuntuforums.org/showthread.php?t=1758290](http://ubuntuforums.org/showthread.php?t=1758290)

---

### Post by carldhickman on 2012-08-23
I had the same problem...fixed it with a USB wirelesss adaptor: ASUS USB-N10 - 150Mbps Wireless Lan USB Adapter. 802.11n, MIFA antenna, (Win 7,Linux,MAC OS 10.6), worked out of the packet

---

### Post by chili555 on 2012-08-23
> **pbice said:**
> I have a Dell Latitude D420 which has an Intel PRO/Wireless 3945ABG wireless card.  I can't get wireless internet, i says Firmware Missing.  Can someone please help me out?Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by kupa8806 on 2012-08-23
I have simillar problems, I'm new to Ubuntu and I can't connect with my wifi, I can see my network available but when I try to connect to it, it is connecting for a while, but never gets connected and after about 2min it asks me for a password. My wire connection is working fine, can someone help? 

dmesg | grep iwl:

 ```
tomasz@tomasz-U41JF:~$ dmesg | grep iwl
[    9.261604] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.261614] iwlwifi 0000:03:00.0: setting latency timer to 64
[    9.261641] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    9.261644] iwlwifi 0000:03:00.0: pci_resource_base = f8860000
[    9.261646] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[    9.262226] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[    9.262261] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.262328] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    9.282924] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.282928] iwlwifi 0000:03:00.0: Device SKU: 0X50
[    9.282930] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.284889] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    9.414186] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[    9.416729] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.491485] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.550866] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.596696] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[   24.882706] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[   33.132806] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[   47.090724] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[   55.328799] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[   69.254755] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  129.131701] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  151.647467] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  176.809390] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  190.727410] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  251.997732] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  271.525895] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  280.874619] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  294.793514] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  308.732527] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  316.998512] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  336.626468] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  373.305818] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  381.587657] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  389.821632] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  398.039589] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  707.788734] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  721.798582] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  735.792513] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  761.070364] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  771.355038] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  779.681006] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  787.967092] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  796.197119] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  821.558865] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[ 1134.529591] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[ 1142.855671] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[ 1156.829580] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[ 1165.091665] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[ 1190.433369] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
tomasz@tomasz-U41JF:~$ 

```rfkill list all: 

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tomasz@tomasz-U41JF:~$ 

```

Oh and I'm using ASUS U41JF

---

### Post by chili555 on 2012-08-23
> iwlwifi 0000:03:00.0: fail to flush all tx fifo queuesUgly.

Please try this temporary fix:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi  wd_disable=1 11n_disable=1
```If it helps, we'll need to write a file to make it persistent.

*PLEASE NOTE*: My proposed fix is specific to stuck queues only. If you don't have this device and this message in dmesg, it is unlikely to help you.

---

### Post by kupa8806 on 2012-08-23
> **chili555 said:**
> Ugly.

Please try this temporary fix:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi  wd_disable=1 11n_disable=1
```

Unfortunately it didin't fix. Still connecting but never gets connected 

```
tomasz@tomasz-U41JF:~$ sudo modprobe -r iwlwifi
[sudo] password for tomasz: 
tomasz@tomasz-U41JF:~$ sudo modprobe iwlwifi wd_disable=1 11n_disable=1
tomasz@tomasz-U41JF:~$ 

```

I've found the solution on [http://askubuntu.com/questions/115315/i-cant-use-my-wifi-on-my-asus-please-help](http://askubuntu.com/questions/115315/i-cant-use-my-wifi-on-my-asus-please-help) and now it's working. 
Thanks chili555 for Your effort

---

### Post by chili555 on 2012-08-23
Excellent! Did you figure out how to write the file to make it permanent? Post back if you need help.

---

### Post by kupa8806 on 2012-08-24
> **chili555 said:**
> Excellent! Did you figure out how to write the file to make it permanent? Post back if you need help.

Oh, If You could help me I would be grateful, cause I have to fix it everytime I reboot and for now I'm a huge newbie in Linux. Here is what I write

```
tomasz@tomasz-U41JF:~$ sudo rmmod iwlwifi
[sudo] password for tomasz: 
tomasz@tomasz-U41JF:~$ sudo modprobe iwlwifi bt_coex_active=0
```

---

### Post by WishForHelp on 2012-08-24
I have the same problem also with the  Intel PRO/Wireless 3945ABG, so i'll keep an eye on this also....

---

### Post by chili555 on 2012-08-24
Here's how to write a file to make it permanent:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```If you don't have the text editor gedit, use leafpad or kate; any text editor will do. A new empty text file will open. Add one line:```
options iwlwifi bt_coex_active=0
```Proofread, save and close the text editor. You should be all set with the option already loaded on boot.

Glad it's working!

---

### Post by kupa8806 on 2012-08-24
I did it, but it's not working, still have to write it each time I reboot, any solutions?
Thanks!

---

### Post by chili555 on 2012-08-24
Please note:> $ modinfo iwlwifi
filename:       /lib/modules/3.4.0-030400-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
<snip>
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) ([COLOR="Red"]bool[/COLOR])'boolean' is a letter and not a number. Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Change to:```
options iwlwifi bt_coex_active=[COLOR="Red"]N[/COLOR]
```Proofread, save and close gedit. Now do:```
sudo su
echo iwlwifi >> /etc/modules
exit
```Now reboot and let us know the result.

---

### Post by kupa8806 on 2012-08-24
> **chili555 said:**
> Change to:```
options iwlwifi bt_coex_active=[COLOR=Red]N[/COLOR]
```Proofread, save and close gedit. Now do:```
sudo su
echo iwlwifi >> /etc/modules
exit
```Now reboot and let us know the result.

chilii555 You're the man!! It worked, thanks a lot:)

---

### Post by chili555 on 2012-08-24
> **kupa8806 said:**
> chilii555 You're the man!! It worked, thanks a lot:)Sorry I didn't catch the boolean thing right off. Glad it's working.

So that the searchers with stuck queues can find the fix, please use thread tools at the top to mark Solved.

---

