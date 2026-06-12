---
title: "wireless randomly is fine or does not show any networks at all"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by goseph on 2010-06-07
Hi all!

Sometimes my wireless is absolutely fine, sometimes it doesn't detect networks at all. It seems to be randomly one way or the other on each boot. It is probably fine about one boot in four.

Here is some diagnostic information gathered when it did not work:

```

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux luke-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver %%%.%%%.%.%%1
nameserver %%%.%%%.%.%%2
==================================================================================================================
*** cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	luke-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xa000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8640 (8.6 KB)  TX bytes:8640 (8.6 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
==================================================================================================================
*** lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| 8139cp          | 8139too         | ac97_bus        | agpgart         | binfmt_misc      |
| bitblit         | crc_ccitt       | drm             | drm_kms_helper  | fbcon            |
| font            | i2c_algo_bit    | ieee1394        | intel_agp       | ipw2200          |
| irda            | led_class       | lib80211        | libipw          | lp               |
| mii             | ohci1394        | pcmcia_core     | ppdev           | radeon           |
| rsrc_nonstatic  | serio_raw       | shpchp          | snd_ac97_codec  | snd_intel8x0     |
| snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi    | snd_seq_oss      |
| softcursor      | tileblit        | ttm             | vga16fb         | vgastate         |
| yenta_socket    |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
19:13:25 2010-06-07
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages:Jun  7 18:49:47 luke-laptop kernel: [   22.946929] ipw2200: Radio Frequency Kill Switch is On:
/var/log/messages.1:Jun  5 23:17:32 luke-laptop kernel: [   21.315419] ipw2200: Radio Frequency Kill Switch is On:
/var/log/messages.1:Jun  5 23:28:32 luke-laptop kernel: [   21.311524] ipw2200: Radio Frequency Kill Switch is On:
/var/log/messages.1:Jun  5 23:38:29 luke-laptop kernel: [   21.470389] ipw2200: Radio Frequency Kill Switch is On:
/var/log/messages.1:Jun  6 16:37:04 luke-laptop kernel: [   21.439133] ipw2200: Radio Frequency Kill Switch is On:
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   22.946929] ipw2200: Radio Frequency Kill Switch is On:
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
Jun  7 18:49:47 luke-laptop kernel: [   22.968621] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Jun  6 16:37:04 luke-laptop kernel: [   20.379808] intel_rng: Firmware space is locked read-only. If you can't or
Jun  6 16:37:04 luke-laptop kernel: [   20.379813] intel_rng: don't want to disable this in firmware setup, and if
Jun  6 16:37:04 luke-laptop kernel: [   20.986263] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Jun  6 16:37:04 luke-laptop kernel: [   21.153003] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | bnx2                     |
| bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw     |
| cis                     | cpia2                   | cxgb3                   | dabusb                   |
| dsp56k                  | dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                     |
| ea                      | edgeport                | emi26                   | emi62                    |
| ess                     | i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin         |
| ipw2100-1.3.fw          | ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw           |
| ipw2200-ibss.fw         | ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode     |
| iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode     |
| iwlwifi-6000-4.ucode    | kaweth                  | keyspan                 | keyspan_pda              |
| korg                    | libertas                | matrox                  | mts_cdma.fw              |
| mts_edge.fw             | mts_gsm.fw              | mwl8k                   | myricom                  |
| NPE-B                   | NPE-C                   | ositech                 | ql2100_fw.bin            |
| ql2200_fw.bin           | ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin            |
| ql2500_fw.bin           | qlogic                  | r128                    | radeon                   |
| rt2561.bin              | rt2561s.bin             | rt2661.bin              | rt2860.bin               |
| rt2870.bin              | rt73.bin                | RTL8192SE               | sb16                     |
| scripts                 | slicoss                 | sun                     | sxg                      |
| tehuti                  | ti_3410.fw              | ti_5052.fw              | tigon                    |
| tr_smctr.bin            | ttusb-budget            | usbdux                  | usbduxfast_firmware.bin  |
| usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw       |
| v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg     |
| v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw  |
| v4l-pvrusb2-29xxx-01.fw | vicam                   | whiteheat.fw            | whiteheat_loader.fw      |
| yam                     | yamaha                  | zd1201-ap.fw            | zd1201.fw                |
| zd1211                  |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:0 FALON:0 

```

Please help!!

---

### Post by tgalati4 on 2010-06-07
If this is a laptop, then I would suspect a bad antenna.  The wire that runs through the hinge sometimes gets worn and shorts out to the case.  If this is a laptop, how old is it?

---

### Post by goseph on 2010-06-08
> **tgalati4 said:**
> If this is a laptop, then I would suspect a bad antenna.  The wire that runs through the hinge sometimes gets worn and shorts out to the case.  If this is a laptop, how old is it?

Actually it is a laptop and it is quite an old laptop (nearly 6 years!), but when I boot into winXP the wireless is fine every time.

---

### Post by tgalati4 on 2010-06-08
Try an older version of Ubuntu or Mint.  Make a Live CD and boot from that and see if the wireless is stable.  If it is, then install that version.  It could be a regression in the kernel or the wireless driver or both.  Try karmic first and if that doesn't work, then go to jaunty.  I don't see anything in your logs that looks problematic, except the suspicious "Radio Frequency Kill Switch".  

Since this is an Intel wireless chipset, look at the source code for the ipw2200 module and see what triggers the "Radio Frequency Kill Switch".  It could be a bug in the driver that causes the module to shut the wireless card down--for safety reasons?  Who knows?

Since this is an older laptop, I would start with an older distro.  I'm not aware of ipw2200 problems.  I'm running one myself in my T43p thinkpad for the past year with no problems under Jaunty.  I've booted with a Live Karmic CD and I know that works as well, but I haven't used it for long periods of time.  Have not tried Lucid on this laptop yet.

---

