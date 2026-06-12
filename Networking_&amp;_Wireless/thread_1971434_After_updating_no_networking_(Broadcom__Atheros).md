---
title: "After updating no networking (Broadcom / Atheros)"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by b1gag3 on 2012-05-02
Hi there,

after upgrading Ubuntu 11.10 to 12.04 my wlan doesn't worked. But before I could try any solution provided by different threads here, I thought I should get the acutal updates for 12.04. So I did. No now even the wired network is not working anymore.

I'm using Ubuntu on my Acer Aspire One 722.

Solutions I tried and didnt worked.
```

sudo rmmod ssb
-ERROR: Module ssb does not exist in /proc/modules

sudo modprobe wl
- FATAL: Module wl not found.

``````
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe iwlwifi
```Some info:

dmesg | grep iwl 
rfkill list
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```Please help :/
regards,
b1gag3 | Chris

---

### Post by chili555 on 2012-05-02
Dr. "I have a headache and her name is Broadcom" is here. So we can narrow down the fixes, please post:```
lspci -nn | grep -e 0200 -e 0280
```This file is not relevant to anything you have; please remove it:```
sudo rm /etc/modprobe.d/iwlwifi.conf
```Thanks.

---

### Post by b1gag3 on 2012-05-02
Thank you for your reply. Yea, I saw several posts about broadcom adapters ..

lspci -nn | grep -e 0200 -e 0280
```
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```The file has been already deleted, because it didn't worked.

---

### Post by chili555 on 2012-05-02
In order to fix the wired ethernet, please do:```
sudo modprobe atl1c
```Hook up the ethernet cable and do:```
ifconfig
```Now do you have an ethernet interface; eth0 ideally? If not, let's check the message files and see why not.```
dmesg | grep atl1
```

The wireless is a very interesting case; we'll get to it after the wired is fixed.

---

### Post by b1gag3 on 2012-05-02
Thanks again :)

ifconfig (sorry for the german parts)
```
lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:34808 (34.8 KB)  TX-Bytes:34808 (34.8 KB)
```dmesg | grep atl1
```
[    2.371753] atl1c 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.371779] atl1c 0000:06:00.0: setting latency timer to 64
[    2.501898] atl1c 0000:06:00.0: version 1.0.1.0-NAPI
```

---

### Post by chili555 on 2012-05-02
> sorry for the german partsDas ist nicht zu stören.

This is very curious. The correct module is loaded early in the boot process and yet no ethernet interface is created. So far, we see no errors or warnings. I love a mystery. Let's dig deeper and look at the bus number:```
dmesg | grep -e 06:00 -e eth
```Let's try the wireless:```
rfkill list all
sudo modprobe -r bcma
sudo modprobe brcmsmac
iwconfig
```If there are errors or warnings, it will be helpful information, so please post them.

---

### Post by b1gag3 on 2012-05-02
> Das ist nicht zu stören.
Looks like google translator :D
Sorry for the long delay. But I must reboot the hole system to change to ubuntu ...

So far no errors occured and no warning or something was displayed.

dmesg | grep -e 06:00 -e eth
```
[    0.405377] pci 0000:06:00.0: [1969:2062] type 0 class 0x000200
[    0.405418] pci 0000:06:00.0: reg 10: [mem 0xf0200000-0xf023ffff 64bit]
[    0.405441] pci 0000:06:00.0: reg 18: [io  0x2000-0x207f]
[    0.405607] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.405618] pci 0000:06:00.0: PME# disabled
[    0.445656] i2c-core: driver [aat2870] using legacy suspend method
[    0.445661] i2c-core: driver [aat2870] using legacy resume method
[    2.374118] atl1c 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.374144] atl1c 0000:06:00.0: setting latency timer to 64
[    2.505690] atl1c 0000:06:00.0: version 1.0.1.0-NAPI
[   22.204942] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

rfkill list all
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

sudo modprobe -r bcma
sudo modprobe brcmsmac
iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-05-02
Yeah, I admit the google translation; caught me.

We got a wireless interface wlan0; does it scan?```
sudo iwlist wlan0 scan
```Dare I say, does it connect?

When you run this with the cable connected, what does it say about link, speed, etc.?```
sudo lshw -C network
```For example:> link=yes multicast=yes port=twisted pair speed=100Mbit/s

---

### Post by b1gag3 on 2012-05-02
Oh ok you edited your post, while I was rebooting..

here's the first part:
sudo iwlist wlan0 scan
```
wlan0     Interface doesn't support scanning : Network is down
```

And part #2
sudo lshw -C network
```
  *-network DISABLED      
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:74:37:04
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:f0200000-f023ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:82:7a:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f0100000-f0103fff
```

---

### Post by chili555 on 2012-05-02
There is some real question about whether wl, bcma or brcmsmac is correct for 14e4:4727. Also, since they all claim the device, there is a likelihood of conflicting drivers being loaded. Please check:```
lsmod | grep -e wl -e bcma -e brcmsmac
```Ideally,only brcmsmac and its dependencies mac80211, brcmutil, cfg80211, cordic and crc8 are present. If otherwise, unload the wrong driver(s):```
sudo modprobe -r wl
sudo modprobe -r bcma
```Until we do some blacklisting, all this goes away on reboot. Once we figure out what does and doesn't work, we'll blacklist.> wlan0     Interface doesn't support scanning : Network is down^^^ probably a driver conflict.

---

### Post by chili555 on 2012-05-02
As we sometmes say here in the back woods, the thick plottens. Please see: [http://ubuntuforums.org/showpost.php?p=11899259&postcount=24](http://ubuntuforums.org/showpost.php?p=11899259&postcount=24)

[https://help.ubuntu.com/community/AspireOne522](https://help.ubuntu.com/community/AspireOne522)> Works fine, as long as the BIOS option(netboot) discussed earlier is set correctly. Look at hibernate for specific issue.It sounds like we may never get the ethernet to work and that you need to change a setting in the BIOS. They also discuss the wireless driver:> In case of Broadcom wifi hardware, on newer releases of Ubuntu and Mint and maybe others, the brcmsmac open source driver handles the BCM4313 wireless card and does a decent job. However, it is interfered with by an older one: bcma. If you're seeing frequent random disconnections for wireless networks, try disabling bcma by blacklisting it:

sudo gedit /etc/modprobe.d/blacklist-bcma.conf

blacklist bcma

---

### Post by b1gag3 on 2012-05-02
lsmod | grep -e wl -e bcma -e brcmsmac
shows nothing. none of these modules are loaded. loading one of them (except of wl - which is not available) doesn't change anything, except its loaded then.

To get a running network on 11.04 it was necessary to enable "Boot on LAN" etc. This is still active. While reading ->[this thread]("http://ubuntuforums.org/showthread.php?t=1811178")<- I enabled this several months ago.

I already tried to blacklist bcma, but this seemed to be has no effect. So I removed it from the blacklist.

The curious thing is, that the wired-connection worked till the last updates. Then even this was dead.

Some random stuff, which could be helpful:
- If the login-form was loaded a "hint"-sound is played. Like if there's a system warning popup, but nothing is displayed. Even after the login no error-message appears.
- Before the last updates the wlan-led was dimmed. Like "wlan is on, but not connected". Now the led is off.
- The keyboard-shortcuts for toggling the wifi- and bluetooth-connection seems to work, even there's no "popup" where you can see what kind of toggling you're doing. By hitting the buttons I'm sure I'm not only toggling the bluetooth connection. It takes four key-presses for a full toggle-cycle (1 - wifi off / bluetooth off, 2 - wifi on / bt off, 3 - wifi on / bt on, 4 - wifi off / bt on). So I actually does, even I'm not seeing any wifi-activity. I hope you know, what I mean :D

---

### Post by chili555 on 2012-05-02
> It takes four key-presses for a full toggle-cycle (1 - wifi off / bluetooth off, 2 - wifi on / bt off, 3 - wifi on / bt on, 4 - wifi off / bt off). So I actually does, even I'm not seeing any wifi-activity. I hope you know, what I meanI do. That's the purpose of rfkill list all; to see if the wireless radio is turned of either in hardware or software. Your readings said not:> 0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: noAs a matter of fact the older version of acer-wmi, the module that translates key presses to commands the kernel acts upon, has been troublesome. In the old days, that is, a year ago, wireless was often enabled by removing the faulty acer-wmi. That doesn't appear to be your issue.

I strongly suspect that wireless is not going to work without blacklisting bcma; I suggest you restore it. It seems worth a few keystrokes to blacklist atl1c and reboot to see if it has any bearing on wireless. An indicator will be 'scan.' Is it still saying the network is down?

---

### Post by b1gag3 on 2012-05-03
here we go again...

I dont know why I should blacklist a module which is not loaded anyway, but I did.

I blacklisted bcma and atl1c with the following commands

- sudo gedit /etc/modprobe.d/blacklist-bcma.conf
and inserted:
```
blacklist bcma
```- sudo gedit /etc/modprobe.d/blacklist-atl1c.conf
and inserted:
```
blacklist atl1c
```and rebooted after that.

lsmod told me that bcma was not loaded, but atl1c was. so I removed it with
- sudo modprobe -r atl1c

atl1c was now unloaded but nothing happend after pluging in the ethernetcable or trying to scan the wifi with 
- sudo iwlist wlan0 scan

But I discoverd something strange. So while toggling the wifi/bluetooth with the function-keys, "rfkill list all" displayed at first the already mentioned state. but then it showed
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Its switching a second bluetooth-device cO

---

### Post by jcruiz on 2012-05-03
Hi there,

I'm following this topic closely given that I have a similar error on my lenovo T420. I don't know if it's relevant or not but I get the following after dmesg | grep iwl

[  117.304530] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[  117.304533] iwlwifi 0000:03:00.0: Status: 0x000412E4, count: 6
[  117.304536] iwlwifi 0000:03:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[  117.304538] iwlwifi 0000:03:00.0: 0x00020DE0 | uPc
[  117.304539] iwlwifi 0000:03:00.0: 0x00020DA8 | branchlink1
[  117.304541] iwlwifi 0000:03:00.0: 0x00020DA8 | branchlink2
[  117.304542] iwlwifi 0000:03:00.0: 0x0000D1F2 | interruptlink1
[  117.304544] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[  117.304546] iwlwifi 0000:03:00.0: 0x00000001 | data1
[  117.304547] iwlwifi 0000:03:00.0: 0x0100006D | data2
[  117.304548] iwlwifi 0000:03:00.0: 0x00000ACA | line
[  117.304550] iwlwifi 0000:03:00.0: 0xCE013480 | beacon time
[  117.304551] iwlwifi 0000:03:00.0: 0x6E5B3B80 | tsf low
[  117.304553] iwlwifi 0000:03:00.0: 0x00000024 | tsf hi
[  117.304555] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[  117.304556] iwlwifi 0000:03:00.0: 0x057874ED | time gp2
[  117.304558] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[  117.304559] iwlwifi 0000:03:00.0: 0x000111A8 | uCode version
[  117.304561] iwlwifi 0000:03:00.0: 0x000000B0 | hw version
[  117.304562] iwlwifi 0000:03:00.0: 0x00480303 | board version
[  117.304563] iwlwifi 0000:03:00.0: 0x0100006D | hcmd
[  117.304565] iwlwifi 0000:03:00.0: CSR values:
[  117.304566] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  117.304596] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  117.304622] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  117.304648] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[  117.304675] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  117.304701] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  117.304728] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000030
[  117.304754] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[  117.304782] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  117.304808] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X000000b0
[  117.304834] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X63670ffd
[  117.304861] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[  117.304888] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[  117.304913] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[  117.304940] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00007ede
[  117.304966] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  117.305003] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  117.305028] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  117.305054] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000058
[  117.305080] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X8820aae8
[  117.305105] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  117.305131] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  117.305157] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  117.305182] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[  117.305184] iwlwifi 0000:03:00.0: FH register values:
[  117.305220] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X1f0dc200
[  117.305235] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01f0dc60
[  117.305251] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f0
[  117.305266] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  117.305282] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  117.305297] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  117.305313] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  117.305328] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  117.305344] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000

I'm also having both interfaces not working. I tried to run the commands as suggested. Doing the appropriate adjustments such as using iwlwifi and such. But so far no luck on getting the network up. 

Both networks worked for a day, but after that everytime I start there is not network connection to internet (I get IP address on both interfaces, but no connection) and then I get a system crash which at this point I don't know if it's related or not. 

Thanks,

JC

---

### Post by chili555 on 2012-05-03
> **jcruiz said:**
> Hi there,

I'm following this topic closely given that I have a similar error on my lenovo T420. I don't know if it's relevant or not but I get the following after dmesg | grep iwl
<snip>

JCYou have a very different error. You apparently have neither an Atheros nor a Broadcom. Please start your own new thread.

---

### Post by jcruiz on 2012-05-03
will do.

Thanks,

---

### Post by chili555 on 2012-05-03
> I dont know why I should blacklist a module which is not loaded anyway, but I did.Your device is this:> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)It is claimed by three drivers:```
chili@LAPTOP60:~$ modinfo wl | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo bcma | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo brcmsmac | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*

```Three drivers will compete and conflict; they will not result in a smoothly running wireless connection. So far, my experience in 12.04 *suggests* that brcmsmac is correct for 14e4:4727. Until you or some other poster on the forum proves otherwise, that's what I'm aiming for, to load one and only one driver for your device, brcmsmac. 

Let's unravel a possible problem. Please do:```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/blacklist-atl1c.conf
sudo rm /etc/modprobe.d/blacklist-bcma.conf
sudo gedit /etc/modprobe.d/blacklist.conf
```Be sure these lines appear:```
blacklist wl
blacklist bcma
blacklist atl1c
```If there is any other blacklist in there involving Broadcom, make a note and ask here. Be sure to proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modules
```Add at the end:```
brcmsmac
```Be sure to proofread carefully, save and close gedit. Now reboot and show us:```
lsmod | grep -e wl -e bcma -e brcmsmac
dmesg | grep brcm
iwconfig
```Thanks.

---

### Post by b1gag3 on 2012-05-03
Thank you for your reply. Ok then the module is loaded if you say so :D

I deleted all mentioned blacklists except of "/etc/modprobe.d/broadcom-sta-common.conf". This file was not present.

Other blacklists in this directory doesn't mentioned anything like "bc**".

After that I edited /etc/modules and rebooted the system.

lsmod | grep -e wl -e bcma -e brcmsmac
```
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
```dmesg | grep brcm
```
[   22.437446] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 11
[   22.437600] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.437615] brcmsmac 0000:07:00.0: setting latency timer to 64
```iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

---

### Post by AdrianP on 2012-05-03
You might be interested in this thread [http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096) . It helped me earlier and relates to BCM4313 and driver blacklisting.

---

### Post by chili555 on 2012-05-03
> **AdrianP said:**
> You might be interested in this thread [http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096) . It helped me earlier and relates to BCM4313 and driver blacklisting.I don't see brcm80211 in 12.04.```
chili@LAPTOP60:~$ modinfo brcm80211
ERROR: modinfo: could not find module brcm80211
```

---

### Post by chili555 on 2012-05-03
> iwconfig
Code:

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

Very good so far. Now when you click the Network Manager icon, do you see networks? Let's see:```
dmesg | grep wlan
```

---

### Post by b1gag3 on 2012-05-03
Since the updates there's no network manager icon anymore :/

At the network connections window no networks are displayed.

dmesg | grep wlan shows me nothing.

---

### Post by chili555 on 2012-05-04
It would be at this point that I'd suggest that, contrary to evidence elsewhere on this forum, maybe the bcmwl-kernel-source driver *is* best for good old 14e4:4727. It is hard but not impossible to install without an ethernet connection: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

Scroll down to here: **STA - No Internet access**

When you've finished, you'll need to remove wl from blacklist and add brcmsmac. Remove brcmsmac for /etc/modules and add wl.

---

### Post by b1gag3 on 2012-05-04
Thanks a lot for your patience and help.

And after downloading and burning at first the wrong ubuntu image and then the right one, I'm back again.

> **Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. This Driver was already available before doing Step 1. But I followed the instructions of Step 1 and all seemed to work.
```
chris@Roncarli:/media/Ubuntu 12.04 LTS i386/pool$ sudo dpkg -i restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb 
dpkg: Warnung: Version 5.100.82.38+bdcom-0ubuntu6.1 des Paketes bcmwl-kernel-source wird durch ältere Version 5.100.82.38+bdcom-0ubuntu6 ersetzt.
(Lese Datenbank ... 221272 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (durch .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb) ...
Removing all DKMS Modules
Done.
Ersatz für bcmwl-kernel-source wird entpackt ...
bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) wird eingerichtet ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

depmod.........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
```

 and tried to activate the driver at Step 2.

But guess what, it doesn't worked. Additional drivers crashed with the hint to take a log at the jockey.log:
```
2012-05-04 20:32:04,059 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c>
2012-05-04 20:32:09,778 DEBUG: reading modalias file /lib/modules/3.2.0-24-generic-pae/modules.alias
2012-05-04 20:32:10,156 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-04 20:32:10,161 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-04 20:32:10,366 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-04 20:32:10,445 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-04 20:32:10,463 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-04 20:32:10,467 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:10,698 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-04 20:32:10,699 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-04 20:32:10,708 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-04 20:32:10,725 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-04 20:32:10,728 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:10,827 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-04 20:32:10,836 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-04 20:32:10,854 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-04 20:32:10,856 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:10,957 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-04 20:32:10,967 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-04 20:32:10,985 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-04 20:32:10,988 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:11,036 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-04 20:32:11,037 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-04 20:32:11,046 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-04 20:32:11,064 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-04 20:32:11,066 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:11,116 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-04 20:32:11,117 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-04 20:32:11,126 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-04 20:32:11,143 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-04 20:32:11,146 DEBUG: nvidia.available: falling back to default
2012-05-04 20:32:11,195 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-04 20:32:11,196 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-04 20:32:11,196 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-04 20:32:11,271 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-04 20:32:11,273 DEBUG: Firmware for DVB cards not available
2012-05-04 20:32:11,273 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-04 20:32:11,340 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-04 20:32:11,341 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-04 20:32:11,341 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-04 20:32:11,356 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-04 20:32:11,372 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-04 20:32:11,461 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-04 20:32:11,462 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-04 20:32:11,512 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-04 20:32:11,547 DEBUG: Software modem not available
2012-05-04 20:32:11,548 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-04 20:32:11,563 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-04 20:32:11,564 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-04 20:32:11,565 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-04 20:32:11,565 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-04 20:32:11,576 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-04 20:32:11,577 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-04 20:32:11,628 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-04 20:32:11,628 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-04 20:32:11,644 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-04 20:32:11,662 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-04 20:32:11,663 DEBUG: fglrx.available: falling back to default
2012-05-04 20:32:11,772 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-04 20:32:11,781 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-04 20:32:11,799 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-04 20:32:11,800 DEBUG: fglrx.available: falling back to default
2012-05-04 20:32:11,900 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-04 20:32:11,901 DEBUG: all custom handlers loaded
2012-05-04 20:32:11,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-05-04 20:32:12,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-04 20:32:13,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-04 20:32:13,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-04 20:32:13,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-04 20:32:13,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-05-04 20:32:13,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-05-04 20:32:13,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-04 20:32:13,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-04 20:32:13,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-04 20:32:13,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-04 20:32:13,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-04 20:32:13,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-05-04 20:32:13,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-05-04 20:32:13,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,215 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-04 20:32:13,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-04 20:32:13,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-05-04 20:32:13,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:acer-wmi')
2012-05-04 20:32:13,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-05-04 20:32:13,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-05-04 20:32:13,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-05-04 20:32:13,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:SYN1B4E:SYN1B00:SYN0002:PNP0F13:')
2012-05-04 20:32:13,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-04 20:32:13,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00009804sv00001025sd00000598bc03sc00i00')
2012-05-04 20:32:13,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-05-04 20:32:13,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,245 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-05-04 20:32:13,280 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:13,280 DEBUG: fglrx_updates is not the alternative in use
2012-05-04 20:32:13,245 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-04 20:32:13,290 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-04 20:32:13,308 DEBUG: fglrx.available: falling back to default
2012-05-04 20:32:13,405 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:13,405 DEBUG: fglrx_updates is not the alternative in use
2012-05-04 20:32:13,370 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-04 20:32:13,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-05-04 20:32:13,439 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:13,440 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-04 20:32:13,406 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-04 20:32:13,449 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-04 20:32:13,467 DEBUG: fglrx.available: falling back to default
2012-05-04 20:32:13,559 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:13,559 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-04 20:32:13,523 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-04 20:32:13,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-04 20:32:13,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-04 20:32:13,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-04 20:32:13,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-04 20:32:13,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc02ip00')
2012-05-04 20:32:13,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-05-04 20:32:13,582 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-05-04 20:32:13,583 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,583 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-05-04 20:32:13,583 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-04 20:32:13,585 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,585 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0003v0402p7675e0004-e0,1,kD4,ramlsfw')
2012-05-04 20:32:13,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-04 20:32:13,588 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,588 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,588 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-05-04 20:32:13,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.01:bd03/25/2011:svnAcer:pnAO722:pvrV1.01:rvnAcer:rnAO722:rvrV1.01:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2012-05-04 20:32:13,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-05-04 20:32:13,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-04 20:32:13,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-05-04 20:32:13,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-04 20:32:13,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-04 20:32:13,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'usb:v0E8Dp1836d0000dc00dsc00dp00ic08isc02ip50')
2012-05-04 20:32:13,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-04 20:32:13,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-04 20:32:13,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v000014E4d00004727sv000014E4sd00000510bc02sc80i00')
2012-05-04 20:32:13,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-05-04 20:32:13,790 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:13,789 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-04 20:32:13,791 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:13,791 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-04 20:32:13,791 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-05-04 20:32:13,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-05-04 20:32:13,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,792 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-05-04 20:32:13,793 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:13,793 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-04 20:32:13,793 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:13,793 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-04 20:32:13,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-04 20:32:13,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-05-04 20:32:13,806 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-05-04 20:32:13,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-05-04 20:32:13,818 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-04 20:32:13,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-04 20:32:13,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:eisa')
2012-05-04 20:32:13,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-04 20:32:13,821 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,822 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-04 20:32:13,822 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-04 20:32:13,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-04 20:32:13,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-05-04 20:32:13,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc01ip00')
2012-05-04 20:32:13,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-05-04 20:32:13,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-05-04 20:32:13,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-05-04 20:32:13,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'platform:regulatory')
2012-05-04 20:32:13,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-04 20:32:13,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-04 20:32:13,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-04 20:32:13,855 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-04 20:32:13,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,856 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-04 20:32:13,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-04 20:32:13,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-04 20:32:13,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-04 20:32:13,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-04 20:32:13,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-04 20:32:13,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7211d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-04 20:32:13,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-05-04 20:32:13,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-04 20:32:13,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-04 20:32:13,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-04 20:32:13,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-05-04 20:32:13,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:pcspkr')
2012-05-04 20:32:13,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-04 20:32:13,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-04 20:32:13,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-04 20:32:13,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-05-04 20:32:13,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-04 20:32:13,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-05-04 20:32:13,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-05-04 20:32:13,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:acer-wmi')
2012-05-04 20:32:13,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-05-04 20:32:13,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-05-04 20:32:13,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-05-04 20:32:13,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:SYN1B4E:SYN1B00:SYN0002:PNP0F13:')
2012-05-04 20:32:13,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-05-04 20:32:13,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00009804sv00001025sd00000598bc03sc00i00')
2012-05-04 20:32:13,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-04 20:32:13,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-04 20:32:13,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-04 20:32:13,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-04 20:32:13,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc02ip00')
2012-05-04 20:32:13,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-05-04 20:32:13,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-04 20:32:13,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0003v0402p7675e0004-e0,1,kD4,ramlsfw')
2012-05-04 20:32:13,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-04 20:32:13,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-05-04 20:32:13,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.01:bd03/25/2011:svnAcer:pnAO722:pvrV1.01:rvnAcer:rnAO722:rvrV1.01:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2012-05-04 20:32:13,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-05-04 20:32:13,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-04 20:32:13,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-05-04 20:32:13,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-04 20:32:13,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-04 20:32:13,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'usb:v0E8Dp1836d0000dc00dsc00dp00ic08isc02ip50')
2012-05-04 20:32:13,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-04 20:32:13,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-04 20:32:13,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v000014E4d00004727sv000014E4sd00000510bc02sc80i00')
2012-05-04 20:32:13,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-04 20:32:13,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-05-04 20:32:13,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-05-04 20:32:13,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:eisa')
2012-05-04 20:32:13,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-04 20:32:13,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-05-04 20:32:13,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc01ip00')
2012-05-04 20:32:13,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-05-04 20:32:13,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'platform:regulatory')
2012-05-04 20:32:13,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-05-04 20:32:13,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-04 20:32:13,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-04 20:32:13,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-05-04 20:32:13,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-04 20:32:13,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-04 20:32:13,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6906f6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-04 20:32:13,993 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:13,993 DEBUG: fglrx_updates is not the alternative in use
2012-05-04 20:32:14,073 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:14,147 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:14,148 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-04 20:32:14,230 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:14,231 DEBUG: fglrx_updates is not the alternative in use
2012-05-04 20:32:14,361 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:14,362 DEBUG: fglrx_updates is not the alternative in use
2012-05-04 20:32:14,407 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:14,496 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-04 20:32:14,497 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-04 20:32:18,079 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:20,122 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:26,435 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-04 20:32:26,794 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```Then I followed your instructions, rebooted and tried again to activate the driver. Again it failed. Same reason as above.

But now the Wifi-LED is on. But "sudo iwlist wlan0 scan" doesn't worked and the network manager icon at the taskbar is still missing.

---

### Post by chili555 on 2012-05-04
Under Step 1, did you install the files mentioned off of the install CD? Which are loaded now?```
lsmod | grep -e wl -e bcma -e brcmsmac
```If any except wl are loaded, unload:```
sudo modprobe -r bcma
sudo modprobe -r brcmsmac
```And load wl:```
sudo modprobe wl
```If there are warnings or errors about wl, they will be helpful and please post them. Now post:```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by b1gag3 on 2012-05-04
Chili, we or rather you are getting closer. 

> Under Step 1, did you install the files mentioned off of the install CD? Which are loaded now?
Yes I installed all files without any errors or warnings. Take a look at my post above. There you see the last installation.

No other modules are loaded.
```
chris@Roncarli:~$ lsmod | grep -e wl -e bcma -e brcmsmac
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
```

And now the mystery begins:
```
chris@Roncarli:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```
Because there's no wlan0 I tried to scan eth1 and it worked! and now? :D

---

### Post by chili555 on 2012-05-04
Oops! I forgot, the driver wl creates an interface eth1 and not wlan0. It's been a long day.

Temporarily, let's try to scare up the Network Manager icon. Of course, if we do, try to connect; if not, as always, post any errors or warnings.```
nm-applet &
```Leave the terminal open and click the icon and connect. If you're successful (yay!) we'll work out how to restore it permanently.

---

### Post by b1gag3 on 2012-05-04
at first I must investigate a new problem ...

```
** (nm-applet:2903): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:2903): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:2903): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
```

---

### Post by chili555 on 2012-05-04
Is Network Manager installed?```
sudo dpkg -s network-manager
sudo dpkg -s nm-applet 
```

---

### Post by b1gag3 on 2012-05-04
Gosh this is this stressing ...

Yes it is installed. I used the manpage to get the general command for the networkmanager.
```
sudo NetworkManager 
[sudo] password for chris: 
Unbekannte Protokollstufe »ERR,WARN«.  Verwenden Sie --help, um eine Liste der verfügbaren Optionen zu erhalten.

```So I extended the command
```
sudo NetworkManager --log-level=DEBUG
```and the nm started up with its applet. As soon as started he connected to my wifi and now I'm online! Thank you so far, Chili

Maybe purging the networkmanager will fix the problem with it :/

---

### Post by chili555 on 2012-05-04
> Maybe purging the networkmanager will fix the problem with it :/I would open Synaptic package manager and search for Network Manager. Mark each and every NM package that's installed (indicated with a green box) for re-installation. If Synaptic isn't installed, please do:```
sudo apt-get install synaptic
```It may take a reboot, but the icon and all functionality should re-appear.

Please see attached.

---

### Post by b1gag3 on 2012-05-04
Thanks for the details explanation, but I found it by my own *pride* :D

But reinstalling the packages named with "Network-Manager" doesn't fix the problem.

---

### Post by chili555 on 2012-05-04
What does this say?```
nm-applet &
```Is there any change or improvement since you re-installed the parents?

---

### Post by b1gag3 on 2012-05-05
After a fresh reboot its still the same:
```
chris@Roncarli:~$ nm-applet &
[1] 2711
chris@Roncarli:~$ 
** (nm-applet:2711): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:2711): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:2711): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files

```Stopping this process with STRG + C and starting then with "sudo NetworkManager --log-level=DEBUG" causing the appearance of two NetworkManager-Applets in the taskbar. Weird...

---

### Post by chili555 on 2012-05-05
I wonder if this will help: [http://askubuntu.com/questions/118420/network-manager-applet-disappeared-after-upgrade](http://askubuntu.com/questions/118420/network-manager-applet-disappeared-after-upgrade)

---

### Post by b1gag3 on 2012-05-05
No changing the configuration changes nothing.
Even if I add DEBUG (because this helps to start the NetworkManager manually) to
```
[logging]
level=ERR,WARN
```it won't work.

I'll try some other or similiar fixes ([http://www.krishnasunuwar.com.np/2011/02/screw-network-manager-nm-applet-in-ubuntu/](http://www.krishnasunuwar.com.np/2011/02/screw-network-manager-nm-applet-in-ubuntu/) / [http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html](http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html)) even if they're not for 12.04

---

### Post by chili555 on 2012-05-05
I doubt you have to start NM manually; it's probably already running; check here:```
ps aux | grep etwork
```It is the top panel *applet* that's not running correctly, isn't it?

---

### Post by b1gag3 on 2012-05-05
You're right. The Networkmanager (and logically the applet) is not loaded after the startup. Or maybe its crashing while the startup (the mentioned warning sound on the logon-screen some posts above).

---

### Post by chili555 on 2012-05-05
After a reboot so you have a clean slate, do either dmesg or syslog have any clues?```
dmesg | grep etwork
sudo cat /var/log/syslog | grep etwork
```syslog keeps its log for several days so you may  need to look at the timestamps to figure out what happened, or not, after the latest boot.

You might also try:```
sudo /etc/init.d/network-manager stop
sudo /etc/init.d/network-manager start
```What are the errors or warnings in the terminal when you stop and start NM?

---

### Post by b1gag3 on 2012-05-06
Seems like the networkmanager is causing the invisible warning.
```
chris@Roncarli:~$ dmesg | grep etwork
[   18.433317] udevd[356]: renamed network interface eth0 to eth1
[   18.470800] type=1400 audit(1336301912.281:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
[   19.816343] init: network-manager main process (683) terminated with status 1
[   19.816439] init: network-manager main process ended, respawning
[   20.387274] type=1400 audit(1336301914.197:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
``````
chris@Roncarli:~$ sudo cat /var/log/syslog | grep etwork
May  6 12:58:33 Roncarli avahi-daemon[739]: Network interface enumeration completed.
May  6 12:58:33 Roncarli kernel: [   18.470800] type=1400 audit(1336301912.281:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
May  6 12:58:33 Roncarli kernel: [   19.816343] init: network-manager main process (683) terminated with status 1
May  6 12:58:33 Roncarli kernel: [   19.816439] init: network-manager main process ended, respawning
May  6 12:58:34 Roncarli kernel: [   20.387274] type=1400 audit(1336301914.197:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
```Stopping and restarting the networkmanager didn't worked for me.
```
chris@Roncarli:~$ sudo /etc/init.d/network-manager stop
[sudo] password for chris: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
network-manager stop/waiting

chris@Roncarli:~$ sudo /etc/init.d/network-manager stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager

chris@Roncarli:~$ stop network-manager
stop: Unknown instance: 

chris@Roncarli:~$ start network-manager
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.76" (uid=1000 pid=3277 comm="start network-manager ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```

---

### Post by chili555 on 2012-05-06
> Stopping and restarting the networkmanager didn't worked for me.I'm not sure that's the case. This merely suggests a different way to do so:> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-managerAnd this part says it is, indeed, stopped:> network-manager stop/waitingThe second time, it said:> stop: Unknown instance:...simply because it was already stopped. There was no remaining process to stop.> init: network-manager main process (683) terminated with status 1That, on the other hand, is troubling. I notice the problem may be with init. init  is  the  parent of all processes on the system, it is executed by the kernel and is responsible for starting all other processes; it is the  parent  of all processes whose natural parents have died and it is responsible for reaping those when they die. Sounds gruesome, doesn't it?

I wonder if init is causing errors elsewhere:```
sudo cat /var/log/syslog | grep init | tail -n25
```We hope we are *not* seeing some kind of problem in the system that's killing many processes including NM.

I am encouraged by the fact that NM respawned, apparently trouble-free, in a few milli-seconds.

---

### Post by b1gag3 on 2012-05-06
Thanks for your help and explanations. This helps me a lot to understand.

```
chris@Roncarli:~$ sudo cat /var/log/syslog | grep init | tail -n25
May  6 13:07:12 Roncarli kernel: [    0.000000] Memory: 3833196k/4440064k available (5825k kernel code, 77300k reserved, 2850k data, 740k init, 2997548k highmem)
May  6 13:07:12 Roncarli kernel: [    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
May  6 13:07:12 Roncarli kernel: [    0.004080] Security Framework initialized
May  6 13:07:12 Roncarli kernel: [    0.004121] AppArmor: AppArmor initialized
May  6 13:07:12 Roncarli kernel: [    0.164970] devtmpfs: initialized
May  6 13:07:12 Roncarli kernel: [    0.170136] Trying to unpack rootfs image as initramfs...
May  6 13:07:12 Roncarli kernel: [    0.441742] SCSI subsystem initialized
May  6 13:07:12 Roncarli kernel: [    0.467462] pnp: PnP ACPI init
May  6 13:07:12 Roncarli kernel: [    0.757383] audit: initializing netlink socket (disabled)
May  6 13:07:12 Roncarli kernel: [    0.757408] type=2000 audit(1336309613.756:1): initialized
May  6 13:07:12 Roncarli kernel: [    0.878813] fuse init (API version 7.17)
May  6 13:07:12 Roncarli kernel: [    1.050418] Freeing initrd memory: 13792k freed
May  6 13:07:12 Roncarli kernel: [    1.644317] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May  6 13:07:12 Roncarli kernel: [   18.749286] Bluetooth: HCI device and connection manager initialized
May  6 13:07:12 Roncarli kernel: [   18.749295] Bluetooth: HCI socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.749301] Bluetooth: L2CAP socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.757638] Bluetooth: SCO socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.838445] Bluetooth: RFCOMM TTY layer initialized
May  6 13:07:12 Roncarli kernel: [   18.838464] Bluetooth: RFCOMM socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.839339] init: network-manager main process (588) terminated with status 1
May  6 13:07:12 Roncarli kernel: [   18.839430] init: network-manager main process ended, respawning
May  6 13:07:13 Roncarli kernel: [   19.428796] init: failsafe main process (682) killed by TERM signal
May  6 13:07:14 Roncarli kernel: [   20.918302] init: gdm main process (963) killed by TERM signal
May  6 13:12:41 Roncarli NetworkManager[3750]:    SCPlugin-Ifupdown: init!
May  6 13:12:41 Roncarli NetworkManager[3750]:    SCPlugin-Ifupdown: end _init.

```
Beneath the networkmanager failsafe and gdm main process is killed on startup. The networkmanager tries to respawn (I guess this means restart). Maybe the other crashing processes are necessary for the networkmanager?

---

### Post by chili555 on 2012-05-06
> Maybe the other crashing processes are necessary for the networkmanager?I doubt it. I don't think this is entirely normal:> [   18.839339] init: [COLOR="Red"]network-manager[/COLOR] main process (588) terminated with status 1
[   19.428796] init: [COLOR="Red"]failsafe[/COLOR] main process (682) killed by TERM signal
[   20.918302] init: [COLOR="Red"]gdm[/COLOR] main process (963) killed by TERM signalI am googling and found this for a start: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539)

I checked another computer here with NM installed for more information. There were no init terminations.

In the meantime, we might both google.

---

### Post by chili555 on 2012-05-06
I saw this and wonder if it's related: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539)

A similar message is noted:> Oct 16 09:23:18 joseph-desktop kernel: [ 21.054926] init: failsafe main process (912) killed by TERM signal
Oct 16 09:23:18 joseph-desktop kernel: [ 21.109535] init: apport pre-start process (1048) terminated with status 1
Oct 16 09:23:18 joseph-desktop kernel: [ 21.115034] init: apport post-stop process (1084) terminated with status 1
Oct 16 09:23:19 joseph-desktop kernel: [ 21.372693] init: lightdm main process (1075) killed by TERM signalPost #14 suggests a fix.

Please check carefully before you start changing things.

I am not at all experienced in init, failsafe, and gdm. I suggest you inquire over on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

It does seem to me that init is incorrectly killing NM and several other processes. It may, in fact, be harmless; I just don't know.

PS- Could it be part of the shutdown process???

---

### Post by b1gag3 on 2012-05-07
It seemed to be a problem with gdm. But I didn't tried the mentioned fix, because in /user/sbin/ are both directories present. And at the bugreports its sound like, that only one of this directories should be there.

I opened up a new thread -> [http://ubuntuforums.org/showthread.php?t=1975511](http://ubuntuforums.org/showthread.php?t=1975511) Maybe someone knows more about this problem.

So far, chili555, thank you so much for your support at this neverending thread :)

---

### Post by awinw on 2012-05-18
> **b1gag3 said:**
> It seemed to be a problem with gdm. But I didn't tried the mentioned fix, because in /user/sbin/ are both directories present. And at the bugreports its sound like, that only one of this directories should be there.

I opened up a new thread -> [http://ubuntuforums.org/showthread.php?t=1975511](http://ubuntuforums.org/showthread.php?t=1975511) Maybe someone knows more about this problem.

So far, chili555, thank you so much for your support at this neverending thread :)

I am a new comer here this thread,
I suffered from almost the same problems this thread mentioned.
I can now go surfing on internet.
Here is my story summed up:
Wired connection (not DSL), two desktops sharing same modem.  Both desktops had 10.04 working well.
Newer desktop had 12.04 newly installed and working well, but older desktop had a failed 12.04 without access to internet.

my solution: 

1) remove PAE in 12.04 LTS
2) then modify /etc/network/interfaces and /etc/networkmanager/networkmanager.conf
3) now I can go online, but the networkmanager icon still shows "you are offline, cable unpluggedK"
  but in fact, I can surf on internet now.

I home this help.

---

### Post by b1gag3 on 2012-05-22
> **awinw said:**
> [...]
2) then modify /etc/network/interfaces and /etc/networkmanager/networkmanager.conf
[...]
Thanks for your hint, but what did you edit/modify in there?

---

### Post by awinw on 2012-05-22
> **b1gag3 said:**
> Thanks for your hint, but what did you edit/modify in there?

1) networkmanager.conf

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

2) networking/interfaces 

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

---

