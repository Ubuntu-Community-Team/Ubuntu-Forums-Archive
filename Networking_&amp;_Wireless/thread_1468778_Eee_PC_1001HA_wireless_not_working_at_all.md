---
title: "Eee PC 1001HA wireless not working at all"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by marclurr on 2010-05-01
Hello there,

I treated myself to a netbook today and of course proceeded to install the latest version (10.4 Netbook edition) my favourite OS :) Unfortunately though, I'm having some difficulties configuring the wireless card. 

I've noticed that a lot of people seem to be having problems with their wireless cards and v10.4, but I haven't seen anyone mention this particular issue.

Basically my wireless card doesn't work. 

Running iwlist gives the following output:

```

marclurr@marclurr-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

```Running lspci gives the following (the interesting line is at the bottom, but I pasted the whole output in case it helps someone diagnose the problem):

```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

```Hopefully someone will be able to help me. 

Thanks

Mark

---

### Post by framplinux on 2010-05-01
You already provided some PD info.  [This ]("http://www.linux-tips-and-tricks.e/collectnwdata")[script http://www.linux-tips-and-tricks.de/collectnwdata#english]("http://www.linux-tips-and-tricks.de/collectnwdata#english") collects much more info and even does some analysis for common networking problems ;-)

---

### Post by marclurr on 2010-05-01
Thank for very much for that!

I ran the script and here is the output:

```

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: v#r#i#

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux marclurr-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver 192.168.2.1
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    marclurr-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          inet addr:192.168.2.128  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe0a:8d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:1238465 (1.2 MB)  TX bytes:204481 (204.4 KB)
          Interrupt:28 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 OK
ping: unknown host [www.suse.de]("http://www.suse.de")
Ping of [www.suse.de]("http://www.suse.de") failed
==================================================================================================================
*** lspci
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
==================================================================================================================
*** lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| agpgart         | ahci            | atl1c           | binfmt_misc     | bitblit          |
| drm             | drm_kms_helper  | fbcon           | font            | i2c_algo_bit     |
| i915            | intel_agp       | lp              | output          | ppdev            |
| rt3090sta       | serio_raw       | snd_hda_codec   | snd_hda_codec_realtek| snd_hda_intel    |
| snd_hwdep       | snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi     |
| snd_seq_oss     | softcursor      | tileblit        | uvcvideo        | v4l1_compat      |
| vga16fb         | vgastate        | video           |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     RT2860 Wireless  ESSID:""# #i#k#a#e#"#T#8#0#T#"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
22:44:36 2010-05-01
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw     |
| bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                      |
| cpia2                   | cxgb3                   | dabusb                  | dsp56k                   |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                    | ea                       |
| edgeport                | emi26                   | emi62                   | ess                      |
| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |
| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |
| ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| libertas                | matrox                  | mts_cdma.fw             | mts_edge.fw              |
| mts_gsm.fw              | mwl8k                   | myricom                 | NPE-B                    |
| NPE-C                   | ositech                 | ql2100_fw.bin           | ql2200_fw.bin            |
| ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin            |
| qlogic                  | r128                    | radeon                  | rt2561.bin               |
| rt2561s.bin             | rt2661.bin              | rt2860.bin              | rt2870.bin               |
| rt73.bin                | RTL8192SE               | sb16                    | scripts                  |
| slicoss                 | sun                     | sxg                     | tehuti                   |
| ti_3410.fw              | ti_5052.fw              | tigon                   | tr_smctr.bin             |
| ttusb-budget            | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:0 FALON:0 

```

I had a brief scan myself and the one thing that sticks out is the result of iwconfig. It's saying that the driver for wlan0 is for the RT2860 chipset wireless card, but the card in this machine is actually RT3090. Do you have any idea how I can upgrade this to the correct version?

Thanks

Mark

edit: Added code tags

---

### Post by pdc on 2010-05-01
you will have to wait for the experts but I note you have the firmware already loaded

> rt2860.bin

[http://www.ab9il.net/linuxwireless/rt2860.html](http://www.ab9il.net/linuxwireless/rt2860.html)

this thread for older kernels says you need three files

/etc/Wireless/RT2860STA/RT2860STA.dat (configuration data)
/lib/firmware/rt2860.bin (firmware)
/lib/modules/*yourkernel*/extra/rt2860sta.ko (RT2860 driver)

If you type

> gedit /etc/Wireless/RT2860STA/RT2860STA.dat 

do you get any answers: 

can I suggest from the above post that you issue the command

> sudo modprobe rt2860 

if successful, the RT2860 wireless driver should load, and you should be able to configure?

_______________________

hmmmmmmmmmm

and maybe life is more complicated than we think 

this thread offers advice on the rt2860 *if the above does not work *

[http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)

it comes from post #9 here

[http://ubuntuforums.org/showthread.php?t=1466455](http://ubuntuforums.org/showthread.php?t=1466455)

---

### Post by marclurr on 2010-05-02
Hey there,

I managed to get it working last night at about 0200h :\ To do this I downloaded the source code for the RaLink RT3090, built the driver and replaced the original module with the new one (All outlined in the README file contained), the was one extra step however, and this was to modify the /etc/Wireless/RT2860STA/RT2860STA.dat file, and setting the AuthMode property to WPAPSK instead of the default which was WPA2PSK (I think).

Thanks for your consideration. Hopefully this will help others facing this problem.

Thanks

Mark

---

### Post by flashback_rtk on 2011-04-06
Hello there,
I had exactly the same problem with the same machine and the same ubuntu version. I solved it in the same way: I downloaded the rt3090sta driver from ralink, compiled it as root and tried to load the module. Eventually it would load but the network didn't come up until I rebooted. The first time the network came up it got my cursor frozen until I connected an external USB mouse O.O, apart from that no more problems, but I've got some questions.
1. lspci tells me I've got a PCIe network adapter with the Ralink rt3090 chipset while iwconfig lists it with the nickname RT2860STA. I suppose they are almost the same hardware but does anyone know if I picked the correct driver? Would the rt2860 driver have worked better?
2. In the Ralink website there's a file labeled as firmware called rt2860.bin. Everything is working so far but I've read in some forums about rt2860 users having to copy that file to /lib/firmware. Should I (well, we) do it too?
3. When compiling the driver I did sudo make but not sudo make install, was that correct?
I am following the "if it's not broken don't fix it" motto here that's why I haven't tried those things, but the process left me with this questions. I would like it not to break in the future. If anyone can add some light to this similar hardware with diferences mess it will be really appreciated.

Thank you for your help and excuse my english.

edit: even the readme of the rt3090sta driver states that the process will build the rt2860sta.ko object when in fact it builds rt3090sta.ko, and the configuration file is named RT2860STA.dat :S

---

