---
title: "How to enable the WiFi in compaq presario b2000"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by petersze on 2011-02-28
Hi all,
  I just installed the ubuntu 10.10 version to my old notebook (compaq presario b2000). However, the wifi is still disable. It is  no button for turn it on. I already enable the wake on lan in BIOS, but still not working.
  Anyone can help.

  Remarks: I am using a USB wifi for internet now.

---

### Post by petersze on 2011-03-03
This is output from my PC, please help everyone.


peter@peter-Presario-B2000-PD257PA-AB5:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:06.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
peter@peter-Presario-B2000-PD257PA-AB5:~$ modprobe ipw2200 hwcrypto=0 qos_enable=0 qos_burst_enable=0

---

### Post by chili555 on 2011-03-03
I see nothing in your lspci that is a wireless device and certainly not an ipw2200 device. Wake on LAN has no effect on wireless. Are you sure there is a built-in wireless device?

---

### Post by petersze on 2011-03-03
Yes, I am sure, because I was use it when I am using Windows XP. The wireless care is Intel Pro/Wireless LAN 2100 3B Mini PCI. However, the major problem that no way to turn it on manually.

---

### Post by chili555 on 2011-03-04
Even if the wireless switch was defective or even if there is no switch or key combination, it ought to show up in lspci. I strongly doubt that there is no key combination, such as Fn+F5, because the wireless radio is a big consumer of electricity. In order to get better battery life, laptop manufacturers almost always include some method or other to turn the wireless radio off and back on.> modprobe ipw2200 hwcrypto=0 qos_enable=0 qos_burst_enable=0 In order to load a module, you would need to preceed the command with sudo:> sudo modprobe somemoduleAlso, the correct driver for the Intel Pro/Wireless LAN 2100 3B Mini PCI is ipw2[COLOR="Red"]1[/COLOR]00. I don't know why you added all those parameters: hwcrypto=0 qos_enable=0 qos_burst_enable=0 if you have no indication they are needed.

Let's try again:```
lspci -nn | grep Wireless
sudo modprobe ipw2100
```Please post the result.

---

### Post by petersze on 2011-03-06
After I tried the command, the wifi light is turn on, but still cannot connect to internet by it. Following is the output now. Anyway, many thanks.


peter@peter-Presario-B2000-PD257PA-AB5:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:06.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
peter@peter-Presario-B2000-PD257PA-AB5:~$

---

### Post by petersze on 2011-03-06
So strange........after reboot the notebook....the wifi light is turn off again, even I type the command again.........

---

### Post by chili555 on 2011-03-07
Let's see if there are any interesting kernel messages:```
dmesg | grep -e iwl -e ntel -e eth
```I must admit; this is a bit weird.

---

### Post by petersze on 2011-03-07
The result is


peter@peter-Presario-B2000-PD257PA-AB5:~$ dmesg | grep -e iwl -e ntel -e eth
[   22.834074] intel_rng: FWH not detected
[   23.324829] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   23.325244] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   23.335022] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   23.752569] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   23.752610] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   24.752072] intel8x0_measure_ac97_clock: measured 55388 usecs (2668 samples)
[   24.752077] intel8x0: clocking to 48000
[   25.550468] eth0:  setting half-duplex.
[   25.550601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.294936] fb0: inteldrmfb frame buffer device
peter@peter-Presario-B2000-PD257PA-AB5:~$

---

### Post by chili555 on 2011-03-07
Nothing whatever in there about Intel or ipw2100 or eth1, the interface that's created by older Intel cards and drivers. Please try this:```
sudo tail -f /var/log/messages
```Leave that terminal open and watch it. Open another terminal and do:```
sudo modprobe ipw2100
```Any activity on the first terminal; any recognition that a wireless driver was loaded and an interface created?

---

### Post by petersze on 2011-03-07
The result is...


peter@peter-Presario-B2000-PD257PA-AB5:~$ sudo tail -f /var/log/messages
[sudo] password for peter: 
Mar  7 22:03:23 peter-Presario-B2000-PD257PA-AB5 kernel: [   28.047866] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar  7 22:03:23 peter-Presario-B2000-PD257PA-AB5 kernel: [   28.331763] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  7 22:03:29 peter-Presario-B2000-PD257PA-AB5 kernel: [   33.519163] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar  7 22:03:40 peter-Presario-B2000-PD257PA-AB5 pulseaudio[1628]: ratelimit.c: 1 events suppressed
Mar  7 22:03:54 peter-Presario-B2000-PD257PA-AB5 kernel: [   58.116684] lo: Disabled Privacy Extensions
Mar  7 22:03:58 peter-Presario-B2000-PD257PA-AB5 kernel: [   62.717635] lo: Disabled Privacy Extensions
Mar  7 22:04:05 peter-Presario-B2000-PD257PA-AB5 kernel: [   69.479544] lo: Disabled Privacy Extensions
Mar  7 22:06:48 peter-Presario-B2000-PD257PA-AB5 kernel: [  232.014245] handle_rx_packet: invalid, small RX packet : 1
Mar  7 22:23:45 peter-Presario-B2000-PD257PA-AB5 kernel: [ 1249.345904] handle_rx_packet: invalid, small RX packet : 1
Mar  7 22:35:49 peter-Presario-B2000-PD257PA-AB5 kernel: [ 1973.540205] handle_rx_packet: invalid, small RX packet : 1
Mar  7 22:37:28 peter-Presario-B2000-PD257PA-AB5 kernel: [ 2072.314276] lib80211: common routines for IEEE802.11 drivers
Mar  7 22:37:28 peter-Presario-B2000-PD257PA-AB5 kernel: [ 2072.473228] libipw: 802.11 data/management/control stack, git-1.1.13
Mar  7 22:37:28 peter-Presario-B2000-PD257PA-AB5 kernel: [ 2072.473233] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Mar  7 22:37:28 peter-Presario-B2000-PD257PA-AB5 kernel: [ 2072.594619] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Mar  7 22:37:28 peter-Presario-B2000-PD257PA-AB5 kernel: [ 2072.594624] ipw2100: Copyright(c) 2003-2006 Intel Corporation

---

### Post by chili555 on 2011-03-07
It loaded the driver module without complaint or error; that's good. However, we don't see an interface, usually eth1, being created. Let's check a bit further:```
iwconfig
```

---

### Post by petersze on 2011-03-07
peter@peter-Presario-B2000-PD257PA-AB5:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Peter"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:13:10:E7:F7:92   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=51/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@peter-Presario-B2000-PD257PA-AB5:~$

---

### Post by chili555 on 2011-03-07
Unbelievable. Simply unbelievable. You have a wireless interface, unexpectedly wlan0, and, moreover, it looks like you are ***connected***!!!

Let's see:```
sudo iwlist wlan0 scan
ifconfig
```I'm stunned.

---

### Post by petersze on 2011-03-07
Please check the result from attachment, because I couldn't post it directly.

---

### Post by chili555 on 2011-03-07
It looks like you are connected. Can you open Firefox and load web pages? Are we done here? SOLVED?

---

### Post by petersze on 2011-03-08
I don't think so... I still need to use the USB wifi for connect internet last night. I will try it again tonight without USB wifi and let you know the result.

Many thanks.....

---

### Post by petersze on 2011-03-08
I removed the USB Wifi this time and it is still cannot detect the Wifi card, please see the attachment for the details.

---

### Post by chili555 on 2011-03-08
Here is what I suggest you do. First, let's get ipw2100 to load on boot every time:```
sudo su
echo ipw2100 >> /etc/modules
exit
```Remove the USB device. Reboot. Now do:```
dmesg | grep ipw > result2.txt
iwconfig >> result2.txt
sudo iwlist wlan0 scan >> result2.txt
rfkill list all >> result2.txt
zip result2.zip result2.txt
```In your user directory, you will find a file, result2.zip. Attach it to your reply.

Are you certain the connected wlan0 above is not actually the USB device?

---

### Post by petersze on 2011-03-08
I removed the USB device today and please see the result.

---

### Post by chili555 on 2011-03-08
Please try again. I only got four lines. Did you reboot before you ran all the commands?

---

### Post by petersze on 2011-03-08
I tried again, but still got four lines, so I also copied the command in Terminal.

---

### Post by chili555 on 2011-03-08
It appears that ipw2100 did not load and there is no sign of a wireless interface. I am even more suspicious now that the wireless card, if it's present, is electrically defective. It won't appear in lspci and the only wireless connection you've had involves wlan0 which I feel is actually the USB device. Older Intel cards using the ipw suite of drivers create an eth1 interface, not wlan0. I have both an Intel 2200 and a 2915. They show up as eth1, as well as dozens of others I've had experience with on this forum. I'm not sure what else we can do.

---

### Post by petersze on 2011-03-08
OIC... anyway... thanks a lot your help....it is a good experience to me... many thanks

---

