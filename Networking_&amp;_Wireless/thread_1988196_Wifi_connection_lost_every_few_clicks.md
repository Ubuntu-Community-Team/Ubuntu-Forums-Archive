---
title: "Wifi connection lost every few clicks"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by kozhi on 2012-05-27
I just done a fresh install of Ubuntu 12.04 LTS on my Compaq Pressario laptop. It uses Atheros wireless adapter. Problem is that I am losing wifi connection every few minutes or after a few clicks, although the wireless icon on the panel continues to show that wifi is connected. So I have to reconnect every few minutes, when it detects the connection and then runs for sometime. This is not a problem with the router as the connection on my desktop is on all the time. Is this a bug or is there some other problem? Any suggestions are welcome. Thanks in advance.

---

### Post by praseodym on 2012-05-27
Deactivate the hardware encryption of the driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Change to **ath9k**, if its the right driver for you.

---

### Post by kozhi on 2012-05-27
Thanks a lot praseodym, for this prompt reply. Before I try your suggestion, could you also tell me:

(a) how to know if ath9k is the right driver. For information, sudo lshw -C network retuns product as AR242x / AR542x Wireless Network Adapter (PCI-Express), vendor as Atheros Communications Inc.

(b) if ath9k is indeed the right driver for this device, then how to change it?

I also got something here - [http://www.pclinuxos.com/forum/index.php?topic=99325.0](http://www.pclinuxos.com/forum/index.php?topic=99325.0) advising that madwifi works better. In fact with earlier versions of ubuntu, i had used madwifi and this problem wasn't there. What do you think?

Thanks a lot.

---

### Post by praseodym on 2012-05-27
Check:

> lspci -nnk | grep -iA2 net
lsmod | grep ath
For ath9k:
> echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

---

### Post by jon zendatta on 2012-05-27
I use Ath9k. After a 12.04 clean install I had the same problem. I disabled IPv6 in Network Manager and this fixed the problem:KS

---

### Post by kozhi on 2012-05-28
Thanks Jon - shall get to your part once I am able to change the driver to ath9k.

@ praseodym:- Here the results 

lspci -nnk | grep -iA2 net returns
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137b]
	Kernel driver in use: ath5k
lsmod | grep ath
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211

Regarding the commands related to ath5k and ath9k as in your posts, well I ran them, but nothing seems to have changed - the connection information still shows ath5k as the driver. BTW, I notice that the commands to deactivate ath5k are the same as those for ath9k (i.e. replacing ath5k with ath9k) . So is one to be deactivated and another activated with the same commands? Thanks.

---

### Post by praseodym on 2012-05-28
Check:

> grep ath /etc/modprobe.d/*
iwconfig
rfkill list
Deactivate IPv6 in the NM-applet.

---

### Post by praseodym on 2012-05-28
Double post

---

### Post by praseodym on 2012-05-28
triple post

---

### Post by praseodym on 2012-05-28
quadruple post

---

### Post by kozhi on 2012-05-28
As advised:

:~$ grep ath /etc/modprobe.d/*
/etc/modprobe.d/ath5k.conf:options ath5k nohwcrypt=1
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/ath9k.conf~:options ath9k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci

:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DSLFD6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:7E:E5:0B:C7:BF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:68   Missed beacon:0

eth0      no wireless extensions.

:~$ rfkill list 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

---

### Post by kozhi on 2012-05-28
not sure why the emoticons should come...I didn't put them as I can't understand the codes...please ignore them

---

### Post by praseodym on 2012-05-28
To prevent the emoticons, mark the text and klick on the "#"-button in Advanced Mode for code tags.

Change the encryption mode to WPA2-AES if possible. After that, check:
```

cat /etc/resolv.conf
cat /etc/network/interfaces
ifconfig -a
sudo iwlist scan
```

---

