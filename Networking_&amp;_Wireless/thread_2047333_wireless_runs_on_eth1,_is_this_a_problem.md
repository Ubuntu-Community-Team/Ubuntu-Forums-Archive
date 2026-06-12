---
title: "wireless runs on eth1, is this a problem?"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by abo0ody on 2012-08-24
Hello ubuntu forums
just before a couple of days my wireless interface was wlan0, and now when i run iwconfig it says that my wireless is running on eth1, i didn't change any hardware. So is this normal? because I'm facing some problems with putting it into monitor mode.
This is my iwconfig output
```

user@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:214  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```and this is my lspci output:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] (rev ff)
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series] (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```Any help would be very appreciated.
Thanks in advance

---

### Post by chili555 on 2012-08-24
Certain drivers, including Broadcom, run perfectly well as eth1. Likewise, certain cards, including Broadcom, refuse to do monitor mode.

Did it do monitor mode previously?

---

### Post by Finnicella on 2012-08-24
I have the same wireless card 
> Broadcom Corporation BCM4313
and also it is running on eth1.
I never had any problems.
Bye and sorry for my english. ):P

---

### Post by abo0ody on 2012-08-24
> **chili555 said:**
> Certain drivers, including Broadcom, run perfectly well as eth1. Likewise, certain cards, including Broadcom, refuse to do monitor mode.

Did it do monitor mode previously?
it was doing monitor mode just fine when the interface was wlan0 
 but now . . . 
 this is the output of iwconfig eth1 mode monitor
```
 
sudo iwconfig eth1 mode monitor 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

---

### Post by chili555 on 2012-08-24
Let's see:```
lspci -nn | grep 0280
lsmod | grep -e wl -e b43
```Is the behavior the same if you do:```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
```

---

### Post by abo0ody on 2012-08-24
> **chili555 said:**
> Let's see:```
lspci -nn | grep 0280
lsmod | grep -e wl -e b43
```Is the behavior the same if you do:```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
```
well
this is the output of "lspci -nn | grep 0280"
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```and this is what "lsmod | grep -e wl -e b43" says:
```

wl                   2568210  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

```I ran the "sudo ifconfig eth1 down" command and it didn't output anything which means it went well.
but the output of  "sudo iwconfig eth1 mode monitor" is still:
```

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

---

### Post by chili555 on 2012-08-25
I think your device works better on a different driver. Please do:```
sudo modprobe -r wl
sudo modprobe -r lib80211 [COLOR="Red"]<--it may or may not still be present[/COLOR]
sudo modprobe brcmsmac
```Does the interface change to wlan0? Can it do monitor mode? If so, you'll need to remove wl:```
sudo su
apt-get remove --purge bcmwl-kernel-source
echo brcmsmac >> /etc/modules
exit
```

---

### Post by hranmuthu on 2012-09-10
Hi chili555,

I had somewhat similar experience. Now I'm using brcmsmac module. I can put my card to monitor mode without any issue. But when I try to capture, I don't get any packets (like a silent network). 
I also have an issue putting the card back to managed mode. When I try that the whole machine gets stuck on ifconfig wlan0 up command.

Thanks,
Harshana

---

### Post by bunglestone on 2013-06-05
> **chili555 said:**
> I think your device works better on a different driver. Please do:```
sudo modprobe -r wl
sudo modprobe -r lib80211 [COLOR=Red]<--it may or may not still be present[/COLOR]
sudo modprobe brcmsmac
```Does the interface change to wlan0? Can it do monitor mode? If so, you'll need to remove wl:```
sudo su
apt-get remove --purge bcmwl-kernel-source
echo brcmsmac >> /etc/modules
exit
```


Great [COLOR=#DD4814][COLOR=#000000][hranmuthu]("http://ubuntuforums.org/member.php?u=1729591") [/COLOR][/COLOR]!!!
that's works for me in the same problem !!

Excelent!!

---

