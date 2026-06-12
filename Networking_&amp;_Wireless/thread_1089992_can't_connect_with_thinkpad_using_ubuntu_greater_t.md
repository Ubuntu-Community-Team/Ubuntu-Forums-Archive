---
title: "can't connect with thinkpad using ubuntu greater than 5"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by rushcamera on 2009-03-07
I have a IBM thinkpad t22 and was able to connect to the internet with Ubuntu 5 but not later releases. With 6 & 8 I can see available networks but when I enter the password it fails to connect. I also have a Lenovo running 8 which has no problems connecting to same network. Can anyone help with this problem. Thanks

---

### Post by utnubuuser on 2009-03-07
wireless?

open a terminal and post output from > iwconfigand> lspciand check the thinkwiki at:[http://www.thinkwiki.org/]("http://www.thinkwiki.org/")

---

### Post by rikudelnorte on 2009-03-10
Here is the output you requested-thanks for your help- this is really perplexing

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Big And Stinky"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:17:F2:E2:56:C5
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-57 dBm  Noise level=-90 dBm
          Rx invalid nwid:17738  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:39583   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"Big And Stinky"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:17:F2:E2:56:C5
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-57 dBm  Noise level=-90 dBm
          Rx invalid nwid:17738  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:39583   Missed beacon:0

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
ubuntu@ubuntu:~$

---

