---
title: "No wireless with Intel Link 5100"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by 01mf02 on 2009-10-08
Hi, thanks for looking at my problem!

I've got a brand-new Dell Studio 15 laptop and can't figure out how to set up my wireless card.

lspci:
```
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
```

dmesg output:
```

[ 2676.670948] iwlagn 0000:04:00.0: PCI INT A disabled
[ 2679.740376] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 2679.740383] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[ 2679.740499] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2679.740516] iwlagn 0000:04:00.0: setting latency timer to 64
[ 2679.740595] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 2679.761291] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2679.761386] iwlagn 0000:04:00.0: irq 2297 for MSI/MSI-X
[ 2679.763919] phy5: Selected rate control algorithm 'iwl-agn-rs'
[ 2684.407777] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-1.ucode
[ 2684.428158] iwlagn: Radio disabled by HW RF Kill switch
[ 2684.431189] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Installing linux-backports-modules-jaunty led to following error:

```

michi@michi-laptop:~$ sudo modprobe iwlagn
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-15-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-15-generic/updates/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Some more stuff I tried:
```
michi@michi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michi@michi-laptop:~$ sudo ifconfig wlan0 up
michi@michi-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

NetworkManager also always tells me "wireless is disabled" (roughly translated from German :)).

I'm running Jaunty with all updates applied. Trying the same on Karmic Beta just brought out a new problem, after which I went back to Jaunty.

Could it be that wireless is just disabled on the laptop to save power? In that case the problem would be that I don't find a key or switch to enable it. :P
Well, a key actually exists, but it doesn't do anything. I also didn't find any network-related option in the BIOS that wasn't set to 'on'.

---

### Post by 01mf02 on 2009-10-09
If it helps something, on Karmic Beta I got following output:
```

michi@michi-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I don't like the look of this "Hard blocked: yes".
"rfkill unblock all" and others didn't change anything.

---

### Post by tenmoi on 2009-10-09
Try this:
sudo nano /etc/network/interfaces and add these two lines (They should be at least 1 new line from the one right above)

auto wlan0
iface wlan0 inet dhcp 

then
CTR + X -> Y -> enter

then 
sudo apt-get install wifi-radar

sudo /etc/init.d/networking restart

sudo wifi-radar

And now you have your wireless networks to choose.

THis was what I did on a toshiba satellite with an intel 5100 wireless Nic.

---

### Post by 01mf02 on 2009-10-09
Thanks for your response, tenmoi.
I tried your tips, but although NetworkManager reported a slightly different thing afterwards, the general behaviour stayed the same. That was on Ubuntu Karmic however, and because I found a bug report that promised to solve the problem shortly after, I didn't try that on Jaunty anymore.

After updating all packages (yesterday a fix was released for this problem) sudo iwlist scan shows me some networks now (:guitar:) and sudo wifi-radar does as well, but a simple iwlist scan without root rights doesn't show anything, and so does NetworkManager. NetworkManager also tells me something like "Device is not being managed" (again, translated from German).

I feel this is a breakthrough; I only have to get NetworkManager detect connections with user rights now. (I don't want to use wifi-radar with root rights all the time.) Do you know how to do that?

---

### Post by ArcaVex on 2009-10-09
I'd remove networkmanager and perhaps use WICD instead. A few users have had more luck with this

---

### Post by 01mf02 on 2009-10-09
Hi ArcaVex, thanks for your suggestion.


Strangely, the problem has solved itself, it seems that two reboots were needed to make everything work. I'm posting this over WLAN now! :P


Anyway, thanks to you both for all your help!

---

### Post by Antares784 on 2009-10-25
Posted this in the wrong place. Created new thread: [http://ubuntuforums.org/showthread.php?p=8161907#post8161907](http://ubuntuforums.org/showthread.php?p=8161907#post8161907)

Thanks!

---

