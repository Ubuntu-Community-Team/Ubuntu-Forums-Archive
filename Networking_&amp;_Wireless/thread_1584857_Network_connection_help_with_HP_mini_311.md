---
title: "Network connection help with HP mini 311"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by cacrooks on 2010-09-29
Hi guys,

New to ubuntu.  I love the OS.  Everything works great except for the network connection.  
It tells me I need to activate the b43 drivers with fwcutter, but here are the following problems:

1) I can't download and install the drivers b/c i can't connect to the internet wired or wireless.
2) I can't find the website to download the appropriate drivers (I've looked for hours)
3)I'm not too sure how to install them since I don't have a background in coding.

I hope one of you can point me in the right direction.  I really like ubuntu, i just need help with the network.

Thanks so much!

Carlos

---

### Post by chili555 on 2010-09-29
The driver b43 is installed by default, however, the driver requires proprietary firmware to work properly. The firmware needs to be installed now.

May I assume you have another computer and a USB drive in order to grab some files? First get these files and transfer them to your desktop. [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Right-click the second one and select 'Extract here.'

Also grab this file: [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb)

Open Applications > Accessories > Terminal and enter these commands in order, one at a time.```
cd ~/Desktop
sudo dpkg -i b43-fwcutter*
```It will try and fail to go out on the internet to grab the firmware. Don't worry, we will point it at the firmware ahead.```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43
```Reboot and let us know if your wireless is now working.

---

### Post by cacrooks on 2010-09-30
Thanks for the reply! I'm in class and I'll check when i get home.

---

### Post by cacrooks on 2010-09-30
So I followed the instructions perfectly, but I'm not sure it's working right. I run the fwcutter command:sudo dpkg -i b43-fwcutter*
And it asks me to check for the firmware online. I say yes, it can't find it so I continue on.
I enter the other codes:
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
 
But all it does is extracs them. For ex: "Extracting b43/b0g0initvals5.fw"
Is that installing the firmware? 
I then enter the "sudo chmod o+rx /lib/firmware/b43" code, but nothing happens.
 
I restarted anyways, but no luck. Any suggestions?
 
**EDIT I'm running the system from a USB stick

---

### Post by chili555 on 2010-09-30
Let's do some diagnostics:```
dmesg | grep b43
```> Is that installing the firmware? Yes; when you extracted the firmware, you asked that it be placed in the folder */lib/firmware*:> sudo b43-fwcutter -w [COLOR="Red"]/lib/firmware[/COLOR] wl_apsta-3.130.20.0.o
sudo b43-fwcutter --unsupported -w [COLOR="Red"]/lib/firmware[/COLOR] broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
Thanks.

---

### Post by cacrooks on 2010-09-30
Hey, 
 
ok the results from the command are below:
 
[FONT=Calibri][SIZE=3]dmesg | grep b43[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][    5.904823] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[AX3A] -> GSI 16 (level, low) -> IRQ 16[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][    5.904970] b43-pci-bridge 0000:03:00.0: setting latency timer to 64[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   37.420681] b43-phy0: Broadcom 4312 WLAN found (core revision 15)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.064118] Registered led device: b43-phy0::tx[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.064180] Registered led device: b43-phy0::rx[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.064252] Registered led device: b43-phy0::radio[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.344895] b43 ssb0:0: firmware: requesting b43/ucode15.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.493053] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.506878] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.506890] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.506900] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.533337] b43 ssb0:0: firmware: requesting b43/ucode15.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.553534] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.604818] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.604831] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][   38.604841] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] I've been to the website suggested from the diagnostics, but I wasn't sure where the download for my firmware is located.[/SIZE][/FONT]
Thanks

---

### Post by chili555 on 2010-09-30
Please post:```
ls /lib/firmware
ls /lib/firmware/b43
```We'll get to the bottom of this!

---

### Post by cacrooks on 2010-09-30
I hope so! :)
 
So I put in the commands you asked me to and came up with the following:
 
First command output:
[FONT=Calibri][SIZE=3]ubuntu@ubuntu:~$ ls /lib/firmware[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2.6.32-24-generic         i2400m-fw-usb-1.4.sbcf  rt2870.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3com                      intelliport2.bin        rt3070.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]acenic                    ipw2100-1.3.fw          rt3071.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]adaptec                   ipw2100-1.3-i.fw        rt73.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]advansys                  ipw2100-1.3-p.fw        RTL8192E[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]agere_ap_fw.bin           ipw2200-bss.fw          RTL8192SE[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]agere_sta_fw.bin          ipw2200-ibss.fw         sb16[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]aic94xx-seq.fw            ipw2200-sniffer.fw      scripts[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ar9170-1.fw               iwlwifi-1000-3.ucode    slicoss[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ar9170-2.fw               iwlwifi-3945-2.ucode    sun[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ar9170.fw                 iwlwifi-4965-2.ucode    sxg[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]asihpi                    iwlwifi-5000-1.ucode    tehuti[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ath3k-1.fw                iwlwifi-5000-2.ucode    ti_3410.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c502_3com.bin   iwlwifi-5150-2.ucode    ti_5052.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c502.bin        iwlwifi-6000-4.ucode    tigon[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c502d.bin       kaweth                  tr_smctr.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c502e.bin       keyspan                 ttusb-budget[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c504_2958.bin   keyspan_pda             usbdux[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c504a_2958.bin  korg                    usbduxfast_firmware.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c504.bin        libertas                usbdux_firmware.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmel_at76c506.bin        matrox                  v4l-cx231xx-avcore-01.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]atmsar11.fw               mts_cdma.fw             v4l-cx23418-apu.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]av7110                    mts_edge.fw             v4l-cx23418-cpu.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bnx2                      mts_gsm.fw              v4l-cx23418-dig.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bnx2x-e1-4.8.53.0.fw      mwl8k                   v4l-cx2341x-dec.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bnx2x-e1-5.2.7.0.fw       myricom                 v4l-cx2341x-enc.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bnx2x-e1h-4.8.53.0.fw     NPE-B                   v4l-cx2341x-init.mpg[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bnx2x-e1h-5.2.7.0.fw      NPE-C                   v4l-cx23885-avcore-01.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]cis                       ositech                 v4l-cx23885-enc.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]cpia2                     ql2100_fw.bin           v4l-cx25840.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]cxgb3                     ql2200_fw.bin           v4l-pvrusb2-24xxx-01.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]dabusb                    ql2300_fw.bin           v4l-pvrusb2-29xxx-01.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]dsp56k                    ql2322_fw.bin           vicam[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]dvb-fe-xc5000-1.6.114.fw  ql2400_fw.bin           whiteheat.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]dvb-usb-dib0700-1.20.fw   ql2500_fw.bin           whiteheat_loader.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]e100                      qlogic                  yam[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ea                        r128                    yamaha[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]edgeport                  radeon                  zd1201-ap.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]emi26                     rt2561.bin              zd1201.fw[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]emi62                     rt2561s.bin             zd1211[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ess                       rt2661.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]i2400m-fw-usb-1.3.sbcf    rt2860.bin[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]And I didn't have much luck with the second:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ls: cannot access /lib/firmware/b43: No such file or directory
[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I think it's odd to not have a directory for b43... That can only mean it wasn't installed correctly right?              [/SIZE][/FONT]

---

### Post by chili555 on 2010-09-30
I'll probably get drummed out of the community for this. Don't tell anyone!

Please take the attached file and download it to your desktop. Right click it and select 'Extract here.' Now do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/ucode15.fw /lib/firmware/b43
sudo chmod 644 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
```Now reboot and let me have a good report.

---

### Post by cacrooks on 2010-10-01
Haha, well I appreciate your help.
 
I followed your instructions, but the only change I see is that it now attepts to connect to the ineternet when I connect an ethernet cord to it. But it fails to connect.
 
Wireless?
My wireless button is still orange (meaning it's not active) and it still promps me to download/install drivers from the update manager. 
 
It looks like using Ubuntu is harder than I thought...
 
What was the code that you gave me to extract to my desktop?
And i guess running the Desktop version on my netbook & installed on my USB has no effect on why it's not working right?
P.S running 10.04
 
Best

---

### Post by chili555 on 2010-10-01
Please let me see:```
ls /lib/firmware/b43
dmesg | grep b43
iwconfig
```Thanks.> And i guess running the Desktop version on my netbook & installed on my USB has no effect on why it's not working right?It shouldn't. I have two laptops on which I've installed the desktop version and they both work perfectly.

---

### Post by saurabhgeo on 2010-11-01
I am following your instructions but I find the error message while issuing command 
dpkg -i b43-fwcutter*

error package architecture (i386) doesnot match system ( amd64)

Could you let me know where is this relevant file can be found

---

### Post by saurabhgeo on 2010-11-01
i found the relevant file [http://packages.debian.org/squeeze/b43-fwcutter](http://packages.debian.org/squeeze/b43-fwcutter) but still your recipe doesnot work 

Any suggestions ?

---

### Post by chili555 on 2010-11-01
How about we shortcut the whole thing and try the recipe in post #9 above?

---

### Post by saurabhgeo on 2010-11-01
I have tried that as well 

but no success. 

Just to mention wireless internet is working on Windows

---

### Post by chili555 on 2010-11-01
Please let me see:```
lspci -nn | grep Broadcom
dmesg | grep -e b43 -e wlan
```Thanks.

---

### Post by saurabhgeo on 2010-11-02
for first command 

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


for second 

[    0.985686] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.985703] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   10.414865] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.577824] Registered led device: b43-phy0::tx
[   10.577839] Registered led device: b43-phy0::rx
[   10.577854] Registered led device: b43-phy0::radio
[   11.602678] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   25.431406] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.360873] wlan0: authenticate with 00:1a:e3:74:25:00 (try 1)
[   36.362269] wlan0: authenticated
[   36.362609] wlan0: associate with 00:1a:e3:74:25:00 (try 1)
[   36.365447] wlan0: RX AssocResp from 00:1a:e3:74:25:00 (capab=0x431 status=0 aid=1)
[   36.365450] wlan0: associated
[   36.367162] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.272609] wlan0: deauthenticating from 00:1a:e3:74:25:00 by local choice (reason=3)
[   40.590671] wlan0: authenticate with 00:1a:e3:74:25:00 (try 1)
[   40.592368] wlan0: authenticated
[   40.592383] wlan0: associate with 00:1a:e3:74:25:00 (try 1)
[   40.595516] wlan0: RX AssocResp from 00:1a:e3:74:25:00 (capab=0x431 status=0 aid=1)
[   40.595519] wlan0: associated
[   46.500057] wlan0: no IPv6 routers present
[   50.302762] wlan0: deauthenticating from 00:1a:e3:74:25:00 by local choice (reason=3)
[   51.613202] wlan0: authenticate with 00:1a:e3:74:24:10 (try 1)
[   51.614958] wlan0: authenticated
[   51.615191] wlan0: associate with 00:1a:e3:74:24:10 (try 1)
[   51.618100] wlan0: RX AssocResp from 00:1a:e3:74:24:10 (capab=0x431 status=0 aid=1)
[   51.618103] wlan0: associated
[   55.292747] wlan0: deauthenticating from 00:1a:e3:74:24:10 by local choice (reason=3)
[   56.600848] wlan0: authenticate with 00:1a:e3:74:24:10 (try 1)
[   56.604206] wlan0: authenticated
[   56.604440] wlan0: associate with 00:1a:e3:74:24:10 (try 1)
[   56.800259] wlan0: associate with 00:1a:e3:74:24:10 (try 2)
[   57.000260] wlan0: associate with 00:1a:e3:74:24:10 (try 3)
[   57.202548] wlan0: association with 00:1a:e3:74:24:10 timed out
[   68.053176] wlan0: authenticate with 00:1a:a2:fa:6a:40 (try 1)
[   68.054569] wlan0: authenticated
[   68.054894] wlan0: associate with 00:1a:a2:fa:6a:40 (try 1)
[   68.250232] wlan0: associate with 00:1a:a2:fa:6a:40 (try 2)
[   68.450227] wlan0: associate with 00:1a:a2:fa:6a:40 (try 3)
[   68.650225] wlan0: association with 00:1a:a2:fa:6a:40 timed out
[   79.520975] wlan0: authenticate with 00:1a:a2:fa:6a:40 (try 1)
[   79.528699] wlan0: authenticated
[   79.529045] wlan0: associate with 00:1a:a2:fa:6a:40 (try 1)
[   79.720272] wlan0: associate with 00:1a:a2:fa:6a:40 (try 2)
[   79.920274] wlan0: associate with 00:1a:a2:fa:6a:40 (try 3)
[   80.120272] wlan0: association with 00:1a:a2:fa:6a:40 timed out
[   90.990808] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[   90.994695] wlan0: authenticated
[   90.995044] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[   91.190167] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 2)
[   91.390271] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 3)
[   91.590271] wlan0: association with 00:1a:a2:f9:f8:b0 timed out
[  326.230914] wlan0: direct probe to 00:1a:a2:f9:f8:b0 (try 1)
[  326.234676] wlan0: direct probe responded
[  326.250113] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  326.252183] wlan0: authenticated
[  326.252491] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  326.255408] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  326.255417] wlan0: associated
[  328.950474] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  335.400976] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  335.402428] wlan0: authenticated
[  335.403085] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  335.406268] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  335.406276] wlan0: associated
[  337.312770] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  343.760985] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  343.769243] wlan0: authenticated
[  343.769591] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  343.772752] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  343.772755] wlan0: associated
[  344.352766] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  350.800963] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  350.809456] wlan0: authenticated
[  350.809799] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  350.812806] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  350.812809] wlan0: associated
[  353.712776] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  360.161276] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  360.163431] wlan0: authenticated
[  360.163779] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  360.167593] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  360.167602] wlan0: associated
[  360.442769] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  366.890978] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  366.898959] wlan0: authenticated
[  366.899259] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  366.903476] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  366.903479] wlan0: associated
[  368.965611] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  375.440948] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  375.450080] wlan0: authenticated
[  375.450425] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  375.455078] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  375.455081] wlan0: associated
[  379.412776] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  411.370907] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  411.377095] wlan0: authenticated
[  411.377441] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  411.380509] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  411.380517] wlan0: associated
[  413.652771] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  420.100885] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  420.106701] wlan0: authenticated
[  420.107046] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  420.110827] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  420.110836] wlan0: associated
[  420.552774] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  427.000940] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  427.007902] wlan0: authenticated
[  427.008248] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  427.011308] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  427.011316] wlan0: associated
[  428.962694] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  435.420900] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  435.426935] wlan0: authenticated
[  435.427278] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  435.429964] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  435.429972] wlan0: associated
[  436.532776] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  442.980911] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  442.987142] wlan0: authenticated
[  442.987446] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  442.991039] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  442.991047] wlan0: associated
[  445.362777] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  451.810890] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  451.817468] wlan0: authenticated
[  451.817731] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  451.820576] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  451.820584] wlan0: associated
[  452.707418] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  459.150894] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  459.157228] wlan0: authenticated
[  459.157532] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  459.160386] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  459.160394] wlan0: associated
[  461.502774] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  467.950883] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  467.958584] wlan0: authenticated
[  467.958928] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  467.961683] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  467.961691] wlan0: associated
[  469.542800] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  475.990878] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  476.000345] wlan0: authenticated
[  476.000693] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  476.003738] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  476.003742] wlan0: associated
[  480.192756] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  486.640821] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  486.648615] wlan0: authenticated
[  486.648961] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  486.651748] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  486.651756] wlan0: associated
[  486.832775] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  493.280910] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  493.289922] wlan0: authenticated
[  493.290646] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  493.293988] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  493.293991] wlan0: associated
[  493.612771] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  500.061004] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  500.062470] wlan0: authenticated
[  500.062930] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  500.065964] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  500.065971] wlan0: associated
[  503.032778] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  509.480809] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  509.488974] wlan0: authenticated
[  509.489320] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  509.492096] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  509.492104] wlan0: associated
[  512.293520] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  518.790875] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  518.795045] wlan0: authenticated
[  518.795391] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  518.798115] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  518.798123] wlan0: associated
[  519.092776] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  525.540844] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  525.548684] wlan0: authenticated
[  525.549032] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  525.552718] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  525.552726] wlan0: associated
[  526.022826] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  532.470796] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  532.472267] wlan0: authenticated
[  532.472647] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  532.475514] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  532.475522] wlan0: associated
[  537.512759] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  543.960792] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  543.968512] wlan0: authenticated
[  543.968858] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  543.971954] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  543.971962] wlan0: associated
[  544.510272] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  550.960789] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  550.966281] wlan0: authenticated
[  550.966607] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  550.970506] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  550.970515] wlan0: associated
[  552.832775] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  559.280810] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  559.288334] wlan0: authenticated
[  559.288679] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  559.291898] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  559.291906] wlan0: associated
[  561.762867] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  568.210795] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  568.217155] wlan0: authenticated
[  568.217501] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  568.220732] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  568.220740] wlan0: associated
[  576.102770] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  582.553313] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  582.554773] wlan0: authenticated
[  582.555085] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  582.558195] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  582.558203] wlan0: associated
[  590.162770] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  596.620745] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  596.626342] wlan0: authenticated
[  596.626646] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  596.629708] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  596.629716] wlan0: associated
[  608.252772] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  614.700937] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  614.707257] wlan0: authenticated
[  614.707560] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  614.710602] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  614.710610] wlan0: associated
[  617.952775] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  624.430924] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  624.432376] wlan0: authenticated
[  624.432836] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  624.436406] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  624.436414] wlan0: associated
[  630.442773] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  636.890911] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  636.898616] wlan0: authenticated
[  636.898920] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  636.901938] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  636.901946] wlan0: associated
[  639.962872] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  646.442562] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  646.444830] wlan0: authenticated
[  646.445176] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  646.450462] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  646.450465] wlan0: associated
[  656.480265] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=3)
[  657.800903] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  657.802373] wlan0: authenticated
[  657.802683] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  657.806180] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  657.806189] wlan0: associated
[  659.302684] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  665.750874] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  665.752319] wlan0: authenticated
[  665.752714] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  665.755753] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  665.755761] wlan0: associated
[  666.272771] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  672.720878] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  672.722333] wlan0: authenticated
[  672.722907] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  672.725661] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  672.725669] wlan0: associated
[  681.542804] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  688.010918] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  688.018016] wlan0: authenticated
[  688.018321] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  688.021394] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  688.021402] wlan0: associated
[  693.272769] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  699.723395] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  699.725416] wlan0: authenticated
[  699.725720] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  699.728834] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  699.728843] wlan0: associated
[  700.612774] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=1)
[  707.070835] wlan0: authenticate with 00:1a:a2:f9:f8:b0 (try 1)
[  707.072336] wlan0: authenticated
[  707.072597] wlan0: associate with 00:1a:a2:f9:f8:b0 (try 1)
[  707.077543] wlan0: RX AssocResp from 00:1a:a2:f9:f8:b0 (capab=0x431 status=0 aid=1)
[  707.077551] wlan0: associated
[  717.110157] wlan0: deauthenticating from 00:1a:a2:f9:f8:b0 by local choice (reason=3)
[  718.420821] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  718.428877] wlan0: authenticated
[  718.429228] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  718.432751] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  718.432754] wlan0: associated
[  721.892853] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  728.340811] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  728.342844] wlan0: authenticated
[  728.362714] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  728.365769] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  728.365775] wlan0: associated
[  729.032770] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  735.480767] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  735.490319] wlan0: authenticated
[  735.490623] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  735.493779] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  735.493782] wlan0: associated
[  735.970214] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  742.420972] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  742.423189] wlan0: authenticated
[  742.423499] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  742.427458] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  742.427466] wlan0: associated
[  743.932899] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  750.383331] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  750.384806] wlan0: authenticated
[  750.402697] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  750.405552] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  750.405558] wlan0: associated
[  751.842767] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  758.290797] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  758.297329] wlan0: authenticated
[  758.297675] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  758.301629] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  758.301638] wlan0: associated
[  762.292918] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  768.740911] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  768.743112] wlan0: authenticated
[  768.743456] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  768.747702] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  768.747710] wlan0: associated
[  779.150224] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  785.620836] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  785.624970] wlan0: authenticated
[  785.625234] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  785.628184] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  785.628192] wlan0: associated
[  788.072773] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)
[  794.520886] wlan0: authenticate with 00:1a:a2:fa:71:20 (try 1)
[  794.523123] wlan0: authenticated
[  794.523717] wlan0: associate with 00:1a:a2:fa:71:20 (try 1)
[  794.526688] wlan0: RX AssocResp from 00:1a:a2:fa:71:20 (capab=0x431 status=0 aid=1)
[  794.526697] wlan0: associated

---

### Post by chili555 on 2010-11-02
You have the required firmware. Your issue is that your wireless card is connecting and, almost immediately disconnecting. The fact that it tries and succeeds at connecting shows that the driver and firmware are in place correctly. Here, for example, you were connected for about 2 1/2 seconds!> [ 785.628192] wlan0: associated
[ 788.072773] wlan0: deauthenticating from 00:1a:a2:fa:71:20 by local choice (reason=1)Let's try to add a parameter to the driver b43. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/b43.conf
```Add a single line:```
options b43 qos=0 nohwcrypt=1
```Proofread carefully, save and close gedit.

Reboot and give us your report. If there is no improvement, please post:```
dmesg | grep -e b43 -e wlan | tail -n10
```Thanks.

---

### Post by saurabhgeo on 2010-11-02
Here is the output 

[  233.658328] wlan0: associate with 00:1a:e3:74:25:00 (try 1)
[  233.661388] wlan0: RX AssocResp from 00:1a:e3:74:25:00 (capab=0x431 status=0 aid=4)
[  233.661395] wlan0: associated
[  234.982767] wlan0: deauthenticating from 00:1a:e3:74:25:00 by local choice (reason=1)
[  241.410836] wlan0: authenticate with 00:1a:e3:74:25:00 (try 1)
[  241.412318] wlan0: authenticated
[  241.412627] wlan0: associate with 00:1a:e3:74:25:00 (try 1)
[  241.415712] wlan0: RX AssocResp from 00:1a:e3:74:25:00 (capab=0x431 status=0 aid=4)
[  241.415720] wlan0: associated
[  243.180084] wlan0: deauthenticating from 00:1a:e3:74:25:00 by local choice (reason=3)


it is still not connected.

---

### Post by chili555 on 2010-11-02
Do you, by chance, have a wired ethernet connection running all this time. Network Manager is designed to not allow a wireless connection if you have wired.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themIf so, please detach the wire and reboot; run the test again _with no ethernet connection_.> [ [COLOR="Red"]243[/COLOR].180084] wlan0: deauthenticating Did you reboot?

---

### Post by saurabhgeo on 2010-11-02
no

Right now I only have wireless. But on wired internet works fine 

Thanks

---

### Post by chili555 on 2010-11-02
No, meaning you didn't reboot? Why? How are the changes to the b43 module going to take place?

---

### Post by saurabhgeo on 2010-11-02
by no I meant I do not have wired internet now . it was yesterday at home. Right now I only have wireless available to which I am trying to connect.

I did reboot as you instructed before 

Thanks

---

### Post by chili555 on 2010-11-02
Is your network WPA protected or what type of encryption? I am starting to think it's a Network Manager issue.

---

### Post by chili555 on 2010-11-02
May I see:```
lsmod | grep -e b43 -e wl
```Thanks.

---

### Post by saurabhgeo on 2010-11-02
Connection - New
Network Name - eduroam
Wireless Security - WPA & WPA2 Enterprise
Authentication - Protected EAP (PEAP)
Anonymous identity - [email]anonymous@tudelft.nl[/email]
CA Certificate - (none)
PEAP version-  Automatic
Inner Authentication - MSCHAPv2
User Name - <netid>@tudelft.nl
Password - <password>

This what the manual of my uni say to connect to internet and I am following it for the settings

---

### Post by saurabhgeo on 2010-11-02
here is the output of the command you asked 

Thanks for you support

b43                   187931  0 
mac80211              266657  1 b43
cfg80211              170293  2 b43,mac80211
led_class               3393  2 b43,sdhci
ssb                    46169  1 b43

---

### Post by saurabhgeo on 2010-11-02
seems it is bit out of column order

so here again 

b43                   187931  0 
mac80211              266657  1 b43
cfg80211              170293  2 b43,mac80211
led_class               3393  2 b43,sdhci
ssb                    46169  1 b43

---

### Post by chili555 on 2010-11-02
I read this: [http://art.ubuntuforums.org/showpost.php?p=9996629&postcount=814](http://art.ubuntuforums.org/showpost.php?p=9996629&postcount=814)> The solution for this particular type of h/w was actually going for a different version of the firmware as outlined in wireless.kernel.org/en/users/Drivers/b43. The version you're looking for is 4.178.10.4. Once you've followed the instructions and installed the low-power firmware with fw-cutter, the interface works after a suitable reboot.
Then I read this: [http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)> You are using the b43 driver with an LP-PHY card (e.g. BCM4312)

Follow these instructions if you are using the b43 driver from linux-2.6.32 and newer or compat-wireless-2.6, or from any current GIT tree, and have a device with a low-power PHY.

Install b43-fwcutter, then use version 4.174.64.19 of Broadcom's proprietary driver. (The tarball is mislabeled as "4.178.10.4", but it is actually 4.174.64.19.)
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.oI suggest you follow the directions to install the lower-powered firmware. You will need an internet connection.

The last instrution is faulty. It should read:```
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

```Reboot and let me have your report.

---

### Post by saurabhgeo on 2010-11-03
Well 

I have done all the steps as you mentioned below 

but it is still not connecting after rebooting

Thanks

---

### Post by chili555 on 2010-11-03
Please do:```
dmesg > saura.txt
sudo cat /var/log/syslog | grep wlan >> saura.txt
iwconfig wlan0 >> saura.txt
zip saura.zip saura.txt
```In your home directory, you will find a file called saura.zip. Please attach it to your reply.

Are you setting up the WPA enterprise and PEAP details in Netwoork Manager? When you try to connect, are you asked for the details?

---

### Post by saurabhgeo on 2010-11-03
yes I did set up details in network manager.

Kindly find the attached zip file 

Thanks

---

### Post by chili555 on 2010-11-03
Your dmesg starts here:> ndwidth), (max_antenna_gain, max_eirp)
[ 5301.260900]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 5301.260912] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[ 5301.260920] cfg80211: Current regulatory domain updated by AP to: NL
[ 5301.260924]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5301.260931]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 5302.102768] wlan0: deauthenticating from 00:1a:e3:74:25:00 by local choice (reason=1)Mine starts here:> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:I wonder why your file doesn't start at boot, that is, at 0.000.

Would you care to reboot and try again with dmesg only?```
dmesg > saura2.txt
zip saura2.zip saura2.txt
```Your logs are filled with authenticate -> associate -> disconnect. This is very interesting:> Nov  3 15:08:29 saurabh-Inspiron-1525 NetworkManager[1019]: <info> (wlan0): supplicant connection state:  associating -> associated
Nov  3 15:08:32 saurabh-Inspiron-1525 NetworkManager[1019]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  3 15:08:32 saurabh-Inspiron-1525 NetworkManager[1019]: <info> (wlan0): supplicant connection state:  [COLOR="Red"]4-way handshake -> disconnected[/COLOR]
Nov  3 15:08:32 saurabh-Inspiron-1525 kernel: [ 5960.122765] wlan0: deauthenticating from 00:1a:e3:74:24:10 by local choice (reason=1)That suggests to me that the WPA-Enterprise details are not quite correct and the access point keeps kicking you out.

Have you double-checked all the details?

I have no experience with WPA-Enterprise so I am not sure I can help setting it up.

---

### Post by saurabhgeo on 2010-11-03
I did checked all the details 

I am also sendin you pdf manual ( 3pages ) from my uni.

Another thing I notice that after GRUB and before log in screen appears I get a message 

modprobe : Fatal Error Occurred Could not load lib/modules/2-6-35-22-generic/modules.dep No such file or directory

It might be that the syntax or spelling are wrong in above statement since this message stays for less than a second and I had to reboot 3 times to note it down in parts 

Is this serious issue ?

---

### Post by chili555 on 2010-11-03
> Could not load lib/modules/2-6-35-22-generic/modules.dep No such file or directoryI found this: [http://ubuntuforums.org/showthread.php?t=1592062&page=3](http://ubuntuforums.org/showthread.php?t=1592062&page=3)

See posts #28 and 29.

I am studying the zip files, but I have to go out for a while. Back later.

---

### Post by chili555 on 2010-11-03
This is interesting:> b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   30.131037] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.Please amend the b43.conf file we created earlier (post #18) to read:```
options b43 qos=0 pio=1 nohwcrypt=1
```Proofread, save and close gedit and reboot. If it is working, post back so we all know what worked, if not, make me another dmesg > sauro3.txt and zip it.

---

### Post by saurabhgeo on 2010-11-03
not working still

Here is the report

Thanks

---

### Post by chili555 on 2010-11-03
We have fixed the PIO issue.

I am out of ideas. I saw this: [https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/334052](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/334052)

And this:  [http://ubuntuforums.org/showthread.php?t=1226032&highlight=eduroam](http://ubuntuforums.org/showthread.php?t=1226032&highlight=eduroam)

The key seems to be Wicd and a corresponding template.

I am convinced that the card and driver are working properly.

Are you able to connect to other non-WPA-Enterprise networks, at the cyber cafe or library, for example?

---

### Post by jmullagh on 2010-11-13
I was able to solve this issue on my mini by simply employing the Synaptic Package Manager as follows:
 In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

---

### Post by raylavers on 2012-09-12
> **jmullagh said:**
> I was able to solve this issue on my mini by simply employing the Synaptic Package Manager as follows:
 In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

Hey Guys, Had a similar issue when first installing the operating system . However the only step I went though was this one above. It worked like a charm. I recommend this to HP Mini 311 owners!

---

