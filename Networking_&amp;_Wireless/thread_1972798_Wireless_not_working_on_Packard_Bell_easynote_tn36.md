---
title: "Wireless not working on Packard Bell easynote tn36 ubunto 12.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by SAJA4 on 2012-05-03
[SIZE=3]**Hi everyone, I need your help. **

**I installed Ubuntu 12.04 on my laptop **[/SIZE][B][SIZE=3]( Packard Bell easynote tn36 ) but the wireless networking disabled and when I press on Enable wireless nothing changed. 

what can i do ?[/SIZE]
[/B]

---

### Post by wildmanne39 on 2012-05-03
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sigurdkaare on 2012-05-09
Hi! 

I have the same problem with a Packard Bell easyenote w3332. This is my output from the code above:

```
haaret@haaret-Packard-Bell-EasyNote:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux haaret-Packard-Bell-EasyNote 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 athlon i386 GNU/Linux
haaret@haaret-Packard-Bell-EasyNote:~$ lspci -nnk | grep -iA2 net
00:11.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
	Subsystem: Ralink corp. RT2500 Wireless 802.11bg [1814:2560]
	Kernel driver in use: rt2500pci
--
00:1b.0 Ethernet controller [0200]: ALi Corporation ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 50)
	Subsystem: Packard Bell B.V. Device [1631:c00a]
	Kernel driver in use: uli526x
haaret@haaret-Packard-Bell-EasyNote:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 047b:000f Silitek Corp. 
Bus 002 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 004: ID 047b:000e Silitek Corp. 
haaret@haaret-Packard-Bell-EasyNote:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

haaret@haaret-Packard-Bell-EasyNote:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
haaret@haaret-Packard-Bell-EasyNote:~$ lsmod^C
haaret@haaret-Packard-Bell-EasyNote:~$ ^C
haaret@haaret-Packard-Bell-EasyNote:~$ 

```

---

### Post by SAJA4 on 2012-05-17
sorry for late this is my output 

```
saja@saja-EASYNOTE-TN36:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux saja-EASYNOTE-TN36 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
saja@saja-EASYNOTE-TN36:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Packard Bell B.V. Device [1631:c216]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k
saja@saja-EASYNOTE-TN36:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 090c:e371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
saja@saja-EASYNOTE-TN36:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

saja@saja-EASYNOTE-TN36:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
saja@saja-EASYNOTE-TN36:~$ lsmod

```

thanks

---

### Post by wildmanne39 on 2012-05-17
Hi SAJA4, please copy and paste the following command.
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then reboot.
Thanks

---

### Post by SAJA4 on 2012-05-18
[COLOR=Blue]**wildmanne39 thanks a lot for helping me. it's work perfectly now *_***[/COLOR]
[]("http://ubuntuforums.org/member.php?u=508533")

---

### Post by wildmanne39 on 2012-05-18
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

