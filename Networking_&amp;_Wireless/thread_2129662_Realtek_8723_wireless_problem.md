---
title: "Realtek 8723 wireless problem"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by c.pfarher on 2013-03-26
This are the output of the commands you post in differents posts of this thread: [http://pastebin.com/yDpERxQR](http://pastebin.com/yDpERxQR)

christian@toshichri:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
christian@toshichri:~$ sudo iwlist wlan0 scan
[sudo] password for christian: 
wlan0 No scan results

----

christian@toshichri:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
christian@toshichri:~$ sudo modprobe rtl8723e
[sudo] password for christian: 
christian@toshichri:~$ modinfo rtl8723e | head -n5
filename:       /lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko
firmware:       rtlwifi/rtl8723efw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
christian@toshichri:~$

---

### Post by chili555 on 2013-03-27
Please detach the ethernet cable and run and post:```
dmesg | grep -e firm -e rtl
sudo iwlist wlan0 scan
```It seems like you have the right driver for the right device!

---

### Post by c.pfarher on 2013-03-28
christian@toshichri:~$ dmesg | grep -e firm -e rtl
[   21.233456] firemare: rtl8723fw_B.bin
[   21.266038] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   21.266177] rtlwifi: wireless switch is on
christian@toshichri:~$ sudo iwlist wlan0 scan
[sudo] password for christian: 
wlan0     No scan results


Thank you.

---

### Post by chili555 on 2013-03-29
This looks a bit suspicious:> christian@toshichri:~$ modinfo rtl8723e | head -n5
filename: /lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko
[COLOR="#FF0000"]firmware: rtlwifi/rtl8723efw.bin[/COLOR]
description: Realtek 8723E 802.11n PCI wireless
license: GPL
author: Realtek WlanFAE <wlanfae@realtek.com>However, the firmware it grabs during bootup is:> christian@toshichri:~$ dmesg | grep -e firm -e rtl
[ 21.233456] [COLOR="#FF0000"]firemare: rtl8723fw_B.bin[/COLOR]
[ 21.266038] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 21.266177] rtlwifi: wireless switch is onI wonder if that is part or all of our trouble both here and in a few other cases. I am unable to find the file in a Google search. Also, the packages I have and that, evidently you compiled, also don't contain it. The file sw.c says, in part:> 173:		fw_name = "rtlwifi/rtl8723fw.bin";
176:		printk("firemare: rtl8723fw_B.bin\n");
177:		fw_name = "rtlwifi/rtl8723fw_B.bin";
270:	.fw_name = "rtlwifi/rtl8723efw.bin",
370:MODULE_FIRMWARE("rtlwifi/rtl8723efw.bin");
In fact, both firmware files and more are referenced, so this may be trivial. I've included this in my reply so I and other searchers can see it.

Which version did you compile? rtl_92ce_92se_92de_8723ae_linux_mac80211_[COLOR="#FF0000"]0007.0809.2012[/COLOR], I hope. What version of Ubuntu are you running?```
lsb_release -d
```Were there any unusual warnings when you compiled?

---

### Post by c.pfarher on 2013-03-29
> **chili555 said:**
> This looks a bit suspicious:However, the firmware it grabs during bootup is:I wonder if that is part or all of our trouble both here and in a few other cases. I am unable to find the file in a Google search. Also, the packages I have and that, evidently you compiled, also don't contain it. The file sw.c says, in part:In fact, both firmware files and more are referenced, so this may be trivial. I've included this in my reply so I and other searchers can see it.

Which version did you compile? rtl_92ce_92se_92de_8723ae_linux_mac80211_[COLOR="#FF0000"]0007.0809.2012[/COLOR], I hope. What version of Ubuntu are you running?```
lsb_release -d
```Were there any unusual warnings when you compiled?

christian@toshichri:~$ lsb_release -d
Description:	Ubuntu-Secure-Remix 12.10 30nov2012

The file name is: rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012

about warnings on compile... mmmm I don´t remember ;(

---

### Post by chili555 on 2013-03-29
> The wireless work fine when power on the PC the first one start, but when restarted it wasn´t work...By this do you mean it worked one time and then never again? Is the module loaded?```
lsmod | grep rtl
```Is there any error or warning if you load it explicitly?```
sudo modprobe rtl8723e
iwconfig
lspci -nn | grep 0280
```I am getting low on ideas.

---

### Post by c.pfarher on 2013-04-01
The first boot always work, but when I restart it isn't working anymore. I need to shut down the computer and then power on again for working properly

I think it is loaded:
christian@toshichri:~$ lsmod |grep rtl
rtl8723e              175717  0 
rtlwifi               118776  1 rtl8723e
mac80211              540032  2 rtl8723e,rtlwifi
cfg80211              206797  2 rtlwifi,mac80211
christian@toshichri:~$ 



There isn´t any error or warning if I load it explicitly:
christian@toshichri:~$ sudo modprobe rtl8723e 
[sudo] password for christian: 
christian@toshichri:~$
christian@toshichri:~$ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
christian@toshichri:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
christian@toshichri:~$ 

Thank You!

---

### Post by chili555 on 2013-04-01
If the driver is properly loaded on restart, then we next suspect the wireless switch or key combination. Please reboot so it isn't working and run:```
rfkill list all
```Post the result here.

---

### Post by c.pfarher on 2013-04-04
christian@toshichri:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
christian@toshichri:~$

---

### Post by chili555 on 2013-04-07
Let's see if we can help it start on reboot. This is all experimental, hit and miss, so we may need a couple of tries:```
gksudo gedit /etc/rc.local
```Above the last line exit 0, please add these three lines:```
modprobe -r rtl8723e
sleep 3
modprobe rtl8723e
```Proofread carefully, save and close gedit. Reboot, cross your fingers, and tell us if it has improved.

---

### Post by c.pfarher on 2013-04-25
Hello, sorry for the gap... nop :( that modifications doesn´t work...
I attached here the dmesg.txt[ATTACH]241767[/ATTACH]

Thank you

---

### Post by chili555 on 2013-04-25
> **c.pfarher said:**
> Hello, sorry for the gap... nop :( that modifications doesn´t work...
I attached here the dmesg.txt[ATTACH]241767[/ATTACH]

Thank youPlease undo the changes to /etc/rc.local. Edit the file as above and completely remove:```
modprobe -r rtl8723e
sleep 3
modprobe rtl8723e
```Proofread carefully, save and close gedit. Now let's write a new file:```
gksudo gedit /etc/modprobe.d/rtl8723e.conf
```Add a single line:```
options rtl8723e ips=0
```Proofread carefully, save and close gedit. Reboot, cross your fingers again, and tell us if it has improved. 

The exact driver parameter or combination is a bit experimental. It may take a few tries to find it.

---

