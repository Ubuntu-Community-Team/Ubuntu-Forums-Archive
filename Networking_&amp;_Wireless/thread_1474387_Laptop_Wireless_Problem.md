---
title: "Laptop Wireless Problem"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by l3ecl on 2010-05-06
I installed Ubuntu 10.4 in my 5 yr old dell inspiron 2200 however I can't get my wireless working. I'm currently following this [guide]("http://ubuntuforums.org/showthread.php?t=185174") but am stuck at step 4 (alternative methods of installation are welcome). Here's what I have so far:

```
g6@ubuntu:~$ lspci
```> 02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)Below are the errors I'm getting from step 4 of said guide:

```
g6@ubuntu:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~Desktop/BCMWL5.SYS
```> Cannot open input file ~Desktop/BCMWL5.SYS```
g6@ubuntu:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~Desktop/wl_apsta.o
```> Cannot open input file ~Desktop/wl_apsta.o

---

### Post by chili555 on 2010-05-06
Did you do this step?> Use this driver with preference to any other:
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)If you downloaded it, is it placed on your desktop? Or in your Downloads folder? Next do:```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
```If the file is in your Downloads folder, do:```
sudo bcm43xx-fwcutter -w /lib/firmware ~/Downloads/wl_apsta.o
```If it goes well, you will notice the firmware getting extracted and loaded. After a reboot, your wireless should be working. Post back if you get stuck.

---

### Post by l3ecl on 2010-05-06
Glad to see you again chili!
I typed what you wrote and it did extract into my [/lib/firmware]("http://img687.imageshack.us/i/firmwarec.png/") 

however my wireless still does not connect...

```
g6@ubuntu:~$ iwconfig
```
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
```
g6@ubuntu:~$ ifconfig
```
> eth0      Link encap:Ethernet  HWaddr 00:12:3f:1b:fb:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)


---

### Post by chili555 on 2010-05-06
What does this tell us?```
dmesg | grep -e firm -e wlan
```

---

### Post by l3ecl on 2010-05-06
chili i think my computer has gone kaput. i installed this [guy]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source") here, as one of the recommended solutions and now wlan0 doesnt even show up anymore. i feel like my computer got hit with a hammer.

```
g6@ubuntu:~$ iwconfig
```
> lo        no wireless extensions.

eth0      no wireless extensions.

```
g6@ubuntu:~$ ifconfig
```
> eth0      Link encap:Ethernet  HWaddr 00:12:3f:1b:fb:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)


```
g6@ubuntu:~$ dmesg | grep -e firm -e wlan
```

did nothing

---

### Post by nucleuskore on 2010-05-06
Boot from the 10.04 live cd, at boot screen select "try ubuntu without making any changes to your computer", and hit enter
once you get the live desktop, open firefox and attempt to browse to make sure you are connected to the internet
click on **System->Administration->Hardware drivers**[/list]
If it does not mention any restricted drivers try again after a minute. If it does mention a driver make a note of it on a piece of paper, reboot and login to your installed ubuntu, and use synaptic to find and install the driver.

---

### Post by l3ecl on 2010-05-06
> **nucleuskore said:**
> **System->Administration->Hardware drivers**



I get this[ error]("http://img42.imageshack.us/i/screenshotqww.png/") followed by [this]("http://img291.imageshack.us/i/screenshot1cv.png/")

---

### Post by chili555 on 2010-05-06
Please do:```
ls /lib/firmware
sudo modprobe b43
dmesg | grep -e 43 -e wl
```In the firmware command, we are looking for the needed Broadcom firmware. If it's there (e.g., a directory called b43), you can confirm it and not list all the other things. Unless the computer or the wireless card is actually kaput, we can fix this.

---

### Post by l3ecl on 2010-05-06
```
g6@ubuntu:~$ ls /lib/firmware
```
> 2.6.32-21-generic         bcm43xx_initval07.fw      i2400m-fw-usb-1.3.sbcf  NPE-C          ttusb-budget
3com                      bcm43xx_initval08.fw      i2400m-fw-usb-1.4.sbcf  ositech        usbdux
acenic                    bcm43xx_initval09.fw      intelliport2.bin        ql2100_fw.bin  usbduxfast_firmware.bin
adaptec                   bcm43xx_initval10.fw      ipw2100-1.3.fw          ql2200_fw.bin  usbdux_firmware.bin
advansys                  bcm43xx_microcode11.fw    ipw2100-1.3-i.fw        ql2300_fw.bin  v4l-cx231xx-avcore-01.fw
agere_ap_fw.bin           bcm43xx_microcode2.fw     ipw2100-1.3-p.fw        ql2322_fw.bin  v4l-cx23418-apu.fw
agere_sta_fw.bin          bcm43xx_microcode4.fw     ipw2200-bss.fw          ql2400_fw.bin  v4l-cx23418-cpu.fw
aic94xx-seq.fw            bcm43xx_microcode5.fw     ipw2200-ibss.fw         ql2500_fw.bin  v4l-cx23418-dig.fw
ar9170-1.fw               bcm43xx_pcm4.fw           ipw2200-sniffer.fw      qlogic         v4l-cx2341x-dec.fw
ar9170-2.fw               bcm43xx_pcm5.fw           iwlwifi-1000-3.ucode    r128           v4l-cx2341x-enc.fw
ar9170.fw                 bnx2                      iwlwifi-3945-2.ucode    radeon         v4l-cx2341x-init.mpg
ath3k-1.fw                bnx2x-e1-4.8.53.0.fw      iwlwifi-4965-2.ucode    rt2561.bin     v4l-cx23885-avcore-01.fw
atmel_at76c502_3com.bin   bnx2x-e1-5.2.7.0.fw       iwlwifi-5000-1.ucode    rt2561s.bin    v4l-cx23885-enc.fw
atmel_at76c502.bin        bnx2x-e1h-4.8.53.0.fw     iwlwifi-5000-2.ucode    rt2661.bin     v4l-cx25840.fw
atmel_at76c502d.bin       bnx2x-e1h-5.2.7.0.fw      iwlwifi-5150-2.ucode    rt2860.bin     v4l-pvrusb2-24xxx-01.fw
atmel_at76c502e.bin       cis                       iwlwifi-6000-4.ucode    rt2870.bin     v4l-pvrusb2-29xxx-01.fw
atmel_at76c504_2958.bin   cpia2                     kaweth                  rt73.bin       vicam
atmel_at76c504a_2958.bin  cxgb3                     keyspan                 RTL8192SE      whiteheat.fw
atmel_at76c504.bin        dabusb                    keyspan_pda             sb16           whiteheat_loader.fw
atmel_at76c506.bin        dsp56k                    korg                    scripts        yam
atmsar11.fw               dvb-fe-xc5000-1.6.114.fw  libertas                slicoss        yamaha
av7110                    dvb-usb-dib0700-1.20.fw   matrox                  sun            zd1201-ap.fw
bcm43xx_initval01.fw      e100                      mts_cdma.fw             sxg            zd1201.fw
bcm43xx_initval02.fw      ea                        mts_edge.fw             tehuti         zd1211
bcm43xx_initval03.fw      edgeport                  mts_gsm.fw              ti_3410.fw
bcm43xx_initval04.fw      emi26                     mwl8k                   ti_5052.fw
bcm43xx_initval05.fw      emi62                     myricom                 tigon
bcm43xx_initval06.fw      ess                       NPE-B                   tr_smctr.bin

```
g6@ubuntu:~$ sudo modprobe b43
[sudo] password for g6: 

```

```
g6@ubuntu:~$ dmesg | grep -e 43 -e wl
```

> [    0.000000] ACPI: DSDT 1f7d5800 02D9A (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 1f7d43e2 002C2 (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.042859] ftrace: allocating 21771 entries in 43 pages
[    0.087438] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[    0.133543] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.173243] system 00:0b: ioport range 0xbb0-0xbbb has been reserved
[    0.173343] system 00:0b: ioport range 0x3fb0-0x3fbb has been reserved
[    0.173351] system 00:0b: ioport range 0x43b0-0x43bb has been reserved
[    0.173355] system 00:0b: ioport range 0x43c0-0x43df has been reserved
[    0.173432] system 00:0b: ioport range 0x6bb0-0x6bbb has been reserved
[    0.173436] system 00:0b: ioport range 0x6bc0-0x6bdf has been reserved
[    0.173643] system 00:0b: ioport range 0xcbb0-0xcbbb has been reserved
[    0.208543] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.243080] fuse init (API version 7.13)
[    0.243197] msgmni has been set to 961
[    0.254435] Switching to clocksource hpet
[    0.274043] brd: module loaded
[    0.358643] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.994643] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.006437] Write protecting the kernel read-only data: 1840k
[    1.255437] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.810418] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   17.437352] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   92.520135] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   92.654879] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   92.782437] phy0: Selected rate control algorithm 'minstrel'
[   92.788447] Registered led device: b43-phy0::tx
[   92.790104] Registered led device: b43-phy0::rx
[   92.791744] Registered led device: b43-phy0::radio
[   92.793335] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   92.916500] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   92.986400] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   92.995404] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   92.995419] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   92.995429] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   93.084228] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   93.092089] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   93.096984] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   93.096992] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   93.096996] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.




---

### Post by l3ecl on 2010-05-06
[I dont see it anywhere]("http://img687.imageshack.us/i/firmwarec.png/")

Screenshot in link
[IMG]http://img687.imageshack.us/i/firmwarec.png/[/IMG]

---

### Post by chili555 on 2010-05-06
> **l3ecl said:**
> [I dont see it anywhere]("http://img687.imageshack.us/i/firmwarec.png/")

Screenshot in link
[IMG]http://img687.imageshack.us/i/firmwarec.png/[/IMG]Nope, it's not there. I think the correct driver for your card is b43 and not bcm43xx. Unfortunately, we grabbed the wrong firmware for the wrong driver.

If you have an ethernet connection, you should be able to go to System > Administration > Hardware Drivers and install it. If not, see post #17 here: 
[http://ubuntuforums.org/showthread.php?t=1438038&highlight=firmware&page=2](http://ubuntuforums.org/showthread.php?t=1438038&highlight=firmware&page=2)

Before you copy the firmware over, you'll need to do:```
sudo mkdir /lib/firmware/b43
```After you grab and install the firmware as outlined in the post, remove and reload b43 and your wireless should be working:```
sudo rmmod -f b43
sudo modprobe b43
```

---

### Post by l3ecl on 2010-05-06
oh ubuntu, you're like a pet dog that keeps chewing on my shoe

```
g6@ubuntu:~$ sudo rmmod -f b43
```> ERROR: Removing 'b43': No such file or directory```
g6@ubuntu:~$ sudo rmmod -f /lib/firmware/b43
```> ERROR: Removing 'b43': No such file or directory

```



g6@ubuntu:~$ ls /lib/firmware/b43
```> b43-firmware-1.1  b43-firmware_1.1-0cafuego1.tar.gz

---

### Post by l3ecl on 2010-05-06
i just did:

sudo modprobe -r b43
sudo modprobe b43

and rebooted

still nada.

would it be possible all the drivers i installed are conflicting?

---

### Post by nucleuskore on 2010-05-06
> **l3ecl said:**
> I get this[ error]("http://img42.imageshack.us/i/screenshotqww.png/") followed by [this]("http://img291.imageshack.us/i/screenshot1cv.png/")

I have seen both your screenshots. You are not connected to the internet, hence the errors. Please connect your PC to the internet using a physical LAN and repeat the instructions I posted earlier

---

### Post by l3ecl on 2010-05-06
> **nucleuskore said:**
> I have seen both your screenshots. You are not connected to the internet, hence the errors. Please connect your PC to the internet using a physical LAN and repeat the instructions I posted earlier

I connected the ethernet to my laptop and still null (do i have to run a command?. I dont have wirless or wired.

---

### Post by chili555 on 2010-05-06
> 
Code:

g6@ubuntu:~$ ls /lib/firmware/b43

Quote:
b43-firmware-1.1 b43-firmware_1.1-0cafuego1.tar.gz You missed a step in there somewhere, but we can fix it. Run these commands carefully:```
sudo cp /lib/firmware/b43/b43-firmware-1.1/*  /lib/firmware/b43
sudo rm /lib/firmware/b43/b43-firmware_1.1-0cafuego1.tar.gz
sudo chmod 755 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
sudo rmmod -f b43
sudo modprobe b43
iwconfig
```Do you now have a wireless interface?

---

### Post by l3ecl on 2010-05-06
.

---

### Post by l3ecl on 2010-05-06
.

---

### Post by l3ecl on 2010-05-06
g6@ubuntu:~$ sudo cp /lib/firmware/b43/b43-firmware-1.1/* /lib/firmware/b43
> [sudo] password for g6: 
cp: omitting directory `/lib/firmware/b43/b43-firmware-1.1/130'
cp: omitting directory `/lib/firmware/b43/b43-firmware-1.1/150'
cp: omitting directory `/lib/firmware/b43/b43-firmware-1.1/debian'
cp: omitting directory `/lib/firmware/b43/b43-firmware-1.1/firmware'
cp: omitting directory `/lib/firmware/b43/b43-firmware-1.1/upstream'


g6@ubuntu:~$ sudo rm /lib/firmware/b43/b43-firmware_1.1-0cafuego1.tar.gz
g6@ubuntu:~$ sudo chmod 755 /lib/firmware/b43/*
g6@ubuntu:~$ sudo chown root:root /lib/firmware/b43/*
g6@ubuntu:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
g6@ubuntu:~$ sudo cp -r /lib/firmware/b43/b43-firmware-1.1/* /lib/firmware/b43
g6@ubuntu:~$ sudo chmod 755 /lib/firmware/b43/*
g6@ubuntu:~$ sudo chown root:root /lib/firmware/b43/*
g6@ubuntu:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
g6@ubuntu:~$ sudo modprobe b43
g6@ubuntu:~$ iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by nucleuskore on 2010-05-07
> **l3ecl said:**
> I connected the ethernet to my laptop and still null (do i have to run a command?. I dont have wirless or wired.

Method 1:
If you do not have at least temporary access to a wired connection this won't work for you.

[list][*]Before you turn on your pc connect to the physical lan (wired)
[*]Boot from the 10.04 live cd, at boot screen select "try ubuntu without making any changes to your computer", and hit enter
once you get the live desktop, open firefox and attempt to browse to make sure you are connected to the internet
[*]click on **System->Administration->Hardware drivers**[/list]
If it does not mention any restricted drivers try again after a minute. If it does mention a driver make a note of it on a piece of paper, reboot and login to your installed ubuntu, and use synaptic to find and install the driver.

---

### Post by nucleuskore on 2010-05-07
Method two:
As per the output of your lspci, you have a BCM4311 card. The driver package for that is **bcmwl-kernel-source**

So you can just connect through the wired connection, open synaptic and search for and install the above package. After you install, make sure to logout/login before you tell me that this driver does not work.

---

### Post by chili555 on 2010-05-07
Let's see:```
ls -al /lib/firmware/b43
dmesg | grep b43
```Thanks.

---

### Post by l3ecl on 2010-05-07
```
g6@ubuntu:~$ ls -al /lib/firmware/b43
```
> total 32
drwxr-xr-x  8 root root 4096 2010-05-06 19:00 .
drwxr-xr-x 47 root root 4096 2010-05-06 14:27 ..
drwxr-xr-x  2 root root 4096 2010-05-06 19:00 130
drwxr-xr-x  2 root root 4096 2010-05-06 19:00 150
drwxr-xr-x  7 root root 4096 2010-05-06 14:45 b43-firmware-1.1
drwxr-xr-x  2 root root 4096 2010-05-06 19:00 debian
drwxr-xr-x  4 root root 4096 2010-05-06 19:00 firmware
drwxr-xr-x  4 root root 4096 2010-05-06 19:00 upstream

```
g6@ubuntu:~$ dmesg | grep b43
```

---

### Post by l3ecl on 2010-05-07
> **nucleuskore said:**
> Method two:
  **bcmwl-kernel-source**
.

I've tried this route and picture is [here]("http://img203.imageshack.us/i/screenshot2km.png/"). Notice the "reinstall" button since already installed and wireless connection that says "no connection."

P.S. I downloaded the package into a USB and did a manual install (not using synaptic). I would like to use synaptic, but the package does now show when i search for it, I've tried moving it around from the portable to desktop but it still does not show in synaptic.

---

### Post by nucleuskore on 2010-05-07
That means its not installed properly. Connect to the internet using your fixed LAN.

Click on Applications->Accessories->terminal

Type **sudo apt-get update --fix-broken** and press ENTER

Key in your password and press ENTER

This should do the trick

You may have to open that deb file you downloaded and hit reinstall. Just make sure you do it **connected** to the internet so that dpkg can download any required dependencies

---

### Post by l3ecl on 2010-05-08
> **nucleuskore said:**
> That means its not installed properly. Connect to the internet using your fixed LAN.

Click on Applications->Accessories->terminal

Type **sudo apt-get update --fix-broken** and press ENTER

Key in your password and press ENTER

This should do the trick

You may have to open that deb file you downloaded and hit reinstall. Just make sure you do it **connected** to the internet so that dpkg can download any required dependencies

I can't connect to the internet whatsoever. Im going to try reinstalling ubuntu with the ethernet cord connected b/c I heard it automatically configures the network and if it works ill try what you wrote.

---

### Post by nucleuskore on 2010-05-08
wait, I will give you the required packages, please post the entire output of your command lspci

---

### Post by l3ecl on 2010-05-08
I've tried installing it with the ethernet connected, and ubuntu still wont give me internet access. 

I've noticed when I boot from the live cd, ubuntu recognizes my wireless modem (System->Admin->Hardware Drivers) and synaptic manager can see the bcm-kernel-source in my USB flash drive but when I don't boot from the cd (boot regular ubuntu), it does not show the modem in Hardware Drivers and I can't see the bcm-kernel-source in my USB flash via synaptic manager. 

Is this some kind of user restriction preventing me from installing anything? I've set my account as administrator and same result.

---

### Post by l3ecl on 2010-05-08
> **nucleuskore said:**
> lspci

heres my lspci but i still probably can't install them through Synaptic Manager

> g6@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
g6@ubuntu:~$ 

---

### Post by nucleuskore on 2010-05-08
**32 bit drivers**
This aptoncd package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware. Dependencies are included. 

Instructions:

Download iso [http://www.mediafire.com/?mime2dlzjny](http://www.mediafire.com/?mime2dlzjny)
Burn to a cd
insert cd and run synaptic package manager when automatically  prompted
Search and install

**bcmwl-kernel-source**

If it is marked as install, then mark it for reinstallation

As for the LAN card, well the e10001 drivers should be there in the kernel. Funny it doesn't work! At least let us try to get your wireless working :)

---

### Post by l3ecl on 2010-05-08
thanks for the cd but no success. i did install tho! (via synaptic manager) I did a reboot and shutdown but wireless still does not work and Hardware Drivers shows up empty.

one thing i noticed is Hardware Drivers shows this now: [IMG]http://img20.imageshack.us/i/91231248.png/[/IMG]

.... then shows empty.


```
g6@ubuntu:~$ ifconfig
```
> eth0      Link encap:Ethernet  HWaddr 00:12:3f:1b:fb:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
g6@ubuntu:~$ iwconfig
```
> lo        no wireless extensions.

eth0      no wireless extensions.

g6@ubuntu:~$

---

### Post by nucleuskore on 2010-05-08
curious, your eth0 is up, and you say you cannot browse through the LAN?

---

### Post by l3ecl on 2010-05-08
last time i plugged in the ether cable my router died and restarted.

---

### Post by l3ecl on 2010-05-08
this makes me want to buy a cheap laptop, install ubuntu and toss it in my bathtub

---

### Post by nucleuskore on 2010-05-08
Sorry I am really out of options. If I get any ideas I'll let you know.

Just right click on the wireless icon connection near your clock and make sure that Enable Networking, Enable Wireless, Enable Notifications is ticked.

Then try **sudo ifconfig** to see if it is up.

If not, also run **uname -r** in your terminal and install **linux-backports-modules-wireless** for your kernel. If you have kernel 2.6.32-31-generic then install **linux-backports-modules-wireless-2.6.32-31-generic**

---

### Post by l3ecl on 2010-05-08
still doesnt work but thanks for trying. ill try installing 9.10 or 9.04, maybe ill have different luck

---

### Post by nucleuskore on 2010-05-09
[http://ubuntuforums.org/showthread.php?t=1474008&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=1474008&highlight=bcm4311)

maybe you can post here too

---

### Post by l3ecl on 2010-05-09
i saw his post but when i try ubuntu live, i dont have a wired connection. if i could fix my wired connection maybe it would be easier to fix my wireless. 

when i plug in my ethernet cord, am i automatically suppose to have connection?

---

### Post by nucleuskore on 2010-05-09
yes, else click on the network icon near the volume control and click eth0

---

### Post by l3ecl on 2010-05-09
> **nucleuskore said:**
> yes, else click on the network icon near the volume control and click eth0

yesss it works!!  i have wired connection now but still no wireless, but still good progress.

i tried your solution of running a live cd and checking Hardware Drivers. it mentioned b43-fwcutter somewhere, so i installed that by synaptic but it doesnt work. i also installed bcmwl-kernel-source beforehand, and i'm curious they could conflict?

well how should i proceed now that i have wired connection?

---

### Post by nucleuskore on 2010-05-09
you will have to uninstall the bcmwl driver and install b43

---

### Post by l3ecl on 2010-05-10
Oi, finally got it working!! had to put unbuntu in its own partition to make it more receptive and your solution worked. thanks alot man!!

---

### Post by nucleuskore on 2010-05-10
For the benefit of other users and myself I want to know a few things:

[list][*]Were you trying to do all this on the live cd? You never actually installed Ubuntu to a separate paratition?

[*]Did the cd you make from the iso I gave you do the trick. If you mention the post number in this thread it would be helpful.[/list]

---

### Post by l3ecl on 2010-05-10
> **nucleuskore said:**
> For the benefit of other users and myself I want to know a few things:

[list][*]Were you trying to do all this on the live cd? You never actually installed Ubuntu to a separate paratition?

[*]Did the cd you make from the iso I gave you do the trick. If you mention the post number in this thread it would be helpful.[/list]

On my previous installations, I was using Wubi, Ubuntu was installed inside windows.

On my recent installation, I partitioned my HD and gave Ubuntu its own space.

Post #20 helped me specifically. Once Ubuntu was on its own parition (in adittion to a working Ethernet), it started showing the Hardware Driver to be activated.

Cheers!

---

### Post by nucleuskore on 2010-05-10
Thank you for your feedback. I would have never dreamt it was a Wubi install that caused all this hassle. It's quite an eye opener for me as I
[list][*]never tried Wubi[*]and now with this experience will strongly discourage anyone who wants to try Wubi[/list]

As you can see installing the driver was so easy, just as mentioned in post #20 !

---

### Post by l3ecl on 2010-05-11
> **nucleuskore said:**
> 

As you can see installing the driver was so easy, just as mentioned in post #20 !

and i thought linux was harder than chinese calculus =P

---

