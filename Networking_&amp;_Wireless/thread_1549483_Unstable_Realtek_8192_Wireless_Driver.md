---
title: "Unstable Realtek 8192 Wireless Driver"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by ubuntopoly on 2010-08-09
I'm having trouble with my Samsung Netbook N220 and its Realtek 8192 wireless card and could use some help with diagnostics. I would like to use the netbook as a server and after a day or so the system stops responding.

What I'd like to know:

- What do the "========>ieee80211_parse_info_param(): athros AP is exist" spam messages actually say? Does anyone else have this and stability problems?

- Why is the realtek driver package not working?

I'm running Ubuntu Netbook 10.04/Kernel 2.6.32-24-generic.

Initially the card was unable to connect, so I installed the Realtek driver rtl8192se_linux_2.6.0017.0507.2010 which adds a kernel module r8192se_pci.ko. At first my system was hanging during bootup. I then restored /lib/modules/2.6.32-24-generic and now the card is connecting but the system is unstable. The 2.6.32-23-generic kernel, modules listed below, still has modules as installed by the realtek driver and is not working.


Below the drivers supplied by ubuntu
./2.6.32-24-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
./2.6.32-24-generic/kernel/drivers/staging/rtl8192su
./2.6.32-24-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
./2.6.32-24-generic/kernel/drivers/staging/rtl8192e
./2.6.32-24-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko

and the drivers installed by the realtek driver (make; make install)
./2.6.32-23-generic/kernel/ubuntu/rtl8192se
./2.6.32-23-generic/kernel/drivers/net/wireless/r8192se_pci.ko
./2.6.32-23-generic/kernel/drivers/staging/rtl8192su
./2.6.32-23-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko


The firmware: two images sized 88856 come from my installation attempts, all other are part of the ubuntu distro.
fc@bonobo:~$ locate rtl8192sfw.bin | xargs ls -l
-rwxr-xr-x 1 root root 88856 2010-07-15 21:56 /lib/firmware/2.6.32-23-generic/RTL8192SE/rtl8192sfw.bin
-rwxr-xr-x 1 root root 88856 2010-08-08 16:51 /lib/firmware/2.6.32-24-generic/RTL8192SE/rtl8192sfw.bin
-rw-r--r-- 1 root root 80976 2010-05-26 17:10 /lib/firmware/RTL8192SE/rtl8192sfw.bin
fc@bonobo:~$ ls -l /lib/firmware/RTL8192E/boot.img
-rw-r--r-- 1 root root 344 2010-05-26 17:10 /lib/firmware/RTL8192E/boot.img
fc@bonobo:~$ ls -l /lib/firmware/RTL8192E/main.img 
-rw-r--r-- 1 root root 42944 2010-05-26 17:10 /lib/firmware/RTL8192E/main.img
fc@bonobo:~$ ls -l /lib/firmware/RTL8192E/data.img 
-rw-r--r-- 1 root root 848 2010-05-26 17:10 /lib/firmware/RTL8192E/data.img


These are the kernel messages when booting 2.6.32-24-generic:
[   17.743903] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.551175] rtl819xE: PlatformInitFirmware()==>
[   18.551182]
[   18.551233] rtl819xE 0000:05:00.0: firmware: requesting RTL8192E/boot.img
[   18.579311] rtl819xE 0000:05:00.0: firmware: requesting RTL8192E/main.img
[   18.617048] rtl819xE:Download Firmware: Put code ok!
[   18.617055]
[   18.625044] rtl819xE:Download Firmware: Boot ready!
[   18.625050]
[   18.625064] rtl819xE 0000:05:00.0: firmware: requesting RTL8192E/data.img
[   18.639865] rtl819xE:Download Firmware: Firmware ready!
[   18.639872]
[   18.639878] rtl819xE:Firmware Download Success
[   18.639881]
[   18.895324] Netfilter messages via NETLINK v0.30.
[   18.936551] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   18.938442] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   18.938453] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   18.938459] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   19.129975] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.140164] sky2 eth0: enabling interface
[   19.140784] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.398250] ctnetlink v0.93: registering with nfnetlink.
[   19.536491] ========>ieee80211_parse_info_param(): athros AP is exist

The ieee80211 line apears as spam all over my messages and I suppose the system instability is linked to this.


Kernel messages with drivers from realtek package:
[   18.938360] rtl819xSE 0000:05:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.105210] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0^M
[   19.105215]
[   19.112312] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0^M
[   19.112318]
[   19.119540] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
[   19.119546]
[   19.220464] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   19.220481] ===>rtllib_start_scan()
[   19.225050] =====>rtl8192_set_chan()====ch:2
[   19.277799] ADDRCONF(NETDEV_UP): wlan13: link is not ready
[   19.287990] sky2 eth0: enabling interface
[   19.288655] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.333056] =====>rtl8192_set_chan()====ch:3
[   19.395766] =====>rtl8192_set_chan()====ch:1
[   19.509043] =====>rtl8192_set_chan()====ch:2
[   19.621052] =====>rtl8192_set_chan()====ch:3
[   19.733050] =====>rtl8192_set_chan()====ch:4
[   19.845053] =====>rtl8192_set_chan()====ch:5
[   19.957037] =====>rtl8192_set_chan()====ch:6
[   19.978754] Netfilter messages via NETLINK v0.30.
[   20.017503] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.018030] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   20.018039] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   20.018046] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.069080] =====>rtl8192_set_chan()====ch:7
[   20.181052] =====>rtl8192_set_chan()====ch:8
[   20.278227] ctnetlink v0.93: registering with nfnetlink.
[   20.293429] =====>rtl8192_set_chan()====ch:9
[   20.405083] =====>rtl8192_set_chan()====ch:10
[   20.484170] ClusterIP Version 0.8 loaded successfully
[   20.517071] =====>rtl8192_set_chan()====ch:11
[   20.629070] =====>rtl8192_set_chan()====ch:12
[   20.741058] =====>rtl8192_set_chan()====ch:13
[   20.777045] pwrdown, 0x6(BIT6)=00
[   20.777053] GPIOChangeRF  - HW Radio OFF

root@bonobo:~# lshw -C network
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: b4:82:fe:bc:16:61
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE ip=192.168.1.67 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:2000(size=256) memory:f0a00000-f0a03fff

root@bonobo:~# lspci | grep Realtek
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

Thanks any help :KS

---

### Post by ubuntopoly on 2010-08-10
I really think this is a genuine ubuntu distro driver issue. Any help anyone?

My machine crashed after 16h uptime, last messages are:

Aug 10 16:29:34 bonobo kernel: [54471.309518] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 10 16:29:34 bonobo kernel: [54471.309529] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 10 16:29:34 bonobo kernel: [54471.323391] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 10 16:29:34 bonobo kernel: [54471.323402] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 10 16:37:20 bonobo kernel: [54937.353514] ===>rtl819x_watchdog_wqcallback(): AP is power off,connect another one
Aug 10 16:37:20 bonobo kernel: [54937.361746] ===========>RemovePeerTS,00:1d:68:ef:a4:2d
Aug 10 16:37:20 bonobo kernel: [54937.393424] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 10 16:37:20 bonobo kernel: [54937.593195] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 10 16:37:23 bonobo kernel: [54940.094588] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 10 16:37:23 bonobo kernel: [54940.097606] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 10 16:37:23 bonobo kernel: [54940.318041] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 10 16:37:25 bonobo kernel: [54942.484667] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 10 16:37:25 bonobo kernel: [54942.484762] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 10 16:37:25 bonobo kernel: [54942.485876] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 10 16:37:25 bonobo kernel: [54942.504749] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 10 16:37:28 bonobo kernel: [54945.004242] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 10 16:37:28 bonobo kernel: [54945.004255] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 10 16:37:28 bonobo kernel: [54945.019614] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 10 16:37:37 bonobo kernel: [54954.732957] ieee->state is NOT LINKED
Aug 10 16:37:37 bonobo kernel: [54954.764588] ieee->state is NOT LINKED
Aug 10 16:37:37 bonobo kernel: [54954.795713] ieee->state is NOT LINKED
Aug 10 16:37:37 bonobo kernel: [54954.826868] ieee->state is NOT LINKED
Aug 10 19:45:02 bonobo kernel: imklog 4.2.0, log source = /proc/kmsg started.

To me it looks like the wireless driver is killing the box after hours of producing the ieee parse info spam.

See attachments for more complete hardware info etc

---

### Post by ubuntopoly on 2010-08-11
Hope I don't give the impression of being impatient... but I'm tired of crashing every day :roll:


Aug 11 14:16:05 bonobo kernel: [66700.815003] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:16:05 bonobo kernel: [66700.815015] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:16:05 bonobo kernel: [66700.834884] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:16:05 bonobo kernel: [66700.834895] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:19:14 bonobo kernel: [66889.358715] martian source 192.168.1.254 from 192.168.1.67, on dev wlan0
Aug 11 14:19:14 bonobo kernel: [66889.358729] ll header: ff:ff:ff:ff:ff:ff:b4:82:fe:bc:16:61:08:06
Aug 11 14:22:06 bonobo kernel: [67061.477649] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:22:06 bonobo kernel: [67061.477662] ========>ieee80211_parse_info_param(): athros AP is exist
Aug 11 14:29:22 bonobo kernel: [67498.064161] ===>rtl819x_watchdog_wqcallback(): AP is power off,connect another one
Aug 11 14:29:22 bonobo kernel: [67498.064186] ===========>RemovePeerTS,00:1d:68:ef:a4:2d
Aug 11 14:29:22 bonobo kernel: [67498.064306] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 11 14:29:22 bonobo kernel: [67498.080750] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 11 14:29:25 bonobo kernel: [67500.580044] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 11 14:29:25 bonobo kernel: [67500.580057] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 11 14:29:25 bonobo kernel: [67500.595079] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 11 14:29:27 bonobo kernel: [67503.096590] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 11 14:29:27 bonobo kernel: [67503.096603] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 11 14:29:27 bonobo kernel: [67503.112730] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 11 14:29:28 bonobo kernel: [67503.170731] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 11 14:29:28 bonobo kernel: [67503.170829] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 11 14:29:28 bonobo kernel: [67503.171933] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 11 14:29:28 bonobo kernel: [67503.190953] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 11 14:29:30 bonobo kernel: [67505.692059] Linking with DarthVader,channel:1, qos:0, myHT:0, networkHT:0
Aug 11 14:29:30 bonobo kernel: [67505.692072] ===>ieee80211_associate_procedure_wq(), chan:1
Aug 11 14:29:30 bonobo kernel: [67505.708751] =================>ieee80211_authentication_req():auth->algorithm is 0
Aug 11 14:29:42 bonobo kernel: [67518.103510] ieee->state is NOT LINKED
Aug 11 14:29:42 bonobo kernel: [67518.135253] ieee->state is NOT LINKED
Aug 11 14:29:43 bonobo kernel: [67518.166357] ieee->state is NOT LINKED
Aug 11 14:29:43 bonobo kernel: [67518.197448] ieee->state is NOT LINKED
Aug 11 21:46:17 bonobo kernel: imklog 4.2.0, log source = /proc/kmsg started.

---

### Post by Ub28 on 2010-08-21
I have similar problems with the rtl819xE wireless.  It sometimes disconnects for no reason too.

---

### Post by Walther -FI- on 2010-08-30
With Samsung N510, the rtl819xE wlan0 device is very unstable too - disconnects every now and then. Also, "device not ready" error occurs often, disabling wireless access completely.

---

### Post by maestrobwh1 on 2010-09-21
This is still an issue with Ubuntu... In Debian Sid, it is rock solid.  The issue persists in Ubuntu Lucid, even if the driver is compiled from the Realtek source.

---

### Post by richaoj on 2011-01-22
still a problem with maverick and the newest drivers from realtek

filename:       /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/r8192se_pci.ko
license:        GPL
version:        0019.1207.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     B35243106478C16B758F56E
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35.8 SMP mod_unload modversions 686 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

---

### Post by bluemuppet on 2011-01-23
Similar problem here, with the Realtek rtl819xU driver.

I'm running an ASRock ION box, and I've installed the drivers as described [here]("http://forum.xbmc.org/showpost.php?p=688360&postcount=6"). ([Original thread]("http://forum.xbmc.org/showthread.php?p=699692"))

I've had limited success - doesn't seem to work at all on my N-only AP. I get better connectivity to my other mixed mode AP, however I've not left it for a long enough time yet to comment on stability.

---

### Post by SavinovSV on 2011-02-06
> **bluemuppet said:**
> Similar problem here, with the Realtek rtl819xU driver.

I'm running an ASRock ION box, and I've installed the drivers as described [here]("http://forum.xbmc.org/showpost.php?p=688360&postcount=6"). ([Original thread]("http://forum.xbmc.org/showthread.php?p=699692"))

I've had limited success - doesn't seem to work at all on my N-only AP. I get better connectivity to my other mixed mode AP, however I've not left it for a long enough time yet to comment on stability.
Dear all!

I also have had problems with RTL8192DU gongle in Kubuntu 10.10.

One solution is here:
[http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104#comment-333](http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104#comment-333)

My own way was like this:

1. Completely remove NetworkManager (everything!!)
2. Install wicd
3. Make link for proper firmware (see above)
4. Carefully look in wicd config directory for proper configuration (I guess WPA2=WPA/PSK) file to use

Now you can wifi connect. And what is more important you can use hidden SSIDs (almost impossible with NetworkManager, dont kow why it is completely lost in such a case)

Have fun.

Reading dmesg was not very helpful for me. The problem was NM itself.

Hope this post will help someone.

---

### Post by richaoj on 2011-02-06
I think it largely depends on which hardware version you have.  I have rtl8192se, and since the most recent kernel update (I have backports turned on), the wireless has worked perfectly without crashes or complaint.  I did not do a manual re-install of the realtek driver.  Just kernel updatess, and bam . . . perfect.

---

### Post by Peter09 on 2011-04-26
Note that the 'se' device is a different driver to the rtl819xE card. I still have major problems in Natty with this device.

---

### Post by richaoj on 2011-04-27
> **Peter09 said:**
> Note that the 'se' device is a different driver to the rtl819xE card. I still have major problems in Natty with this device.

I did, but it seems to be behaving much better since the most recent kernel updates.  Seems they fixed alot of wireless stuff.  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.3-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.3-natty/)

---

### Post by qpsk1half on 2011-05-01
I am having the same problem with my Toshiba L505D with the RTL8192SE. When I switched to 10.04, I was at my wits end when I wrote in to a Toshiba Linux Users mailing list and they pointed me to this link [here]("http://ubuntuforums.org/showthread.php?t=1460038")

This worked like a champ for me. Flawlessly!! But no joy on the 11.04. Here are the relevant parts of the DMESG.
```
[   17.010066] rtl819xE:Download Firmware: Put code fail!
[   17.010071] 
[   17.010075] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   17.010076] 
[   17.010078] rtl819xE:ERR in init_firmware()
[   17.010079] 
[   17.010082] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   17.010083] 


```

Also, when I try ifconfig wlan0 up I get the message that "rtl8192e_pci.ko already exists." That tells me that it is in the modules folder, but is not loading for whatever reason.

Any help would be greatly appreciated. I know this is an SE chip and thus requires different drivers. The drivers that I am using are thus: rtl8192e_linux_2.6.0014.0401.2010.tar.gz and are found at the above link. Thanks in advance folks.

~~~/)~~~
ArtificialReef

---

### Post by evercam on 2011-05-02
Hi all

I'm also having some stability issues with 11.04 on my Samsung NB30 which also uses the Realtek 8192E wireless adaptor.

My issue is that the wireless doesn't come up in the following circumstances:

 - after a cold restart
 - after coming out of hibernation
 - after selecting "Restart..." from the unity shutdown menu

However, if I issue a sudo reboot from the terminal, it restarts with a perfectly stable wireless connection.

The relevant part of my dmesg file is:

[   23.176891] rtl819xE 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.176909] rtl819xE 0000:05:00.0: setting latency timer to 64

and the relevant part of lspci is:

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)

I've upgraded from 10.10 where wireless worked perfectly with an additional PPA samsung realtek package was also installed.  However, this ppa is not available on 11.04.  The only other change I made to the install was to uncomment the r8192e_pci driver from to /etc/modprobe.d/blacklist.conf:

blacklist amd76x_edac
blacklist r8192se_pci
#blacklist r8192e_pci

(otherwise wireless didn't work at all).

Does anyone have any ideas why the wireless should work flawlessly following a command line reboot but not after a GUI Restart?

---

### Post by qpsk1half on 2011-05-03
bump for help. I have seen a lot of folks with problems, but not a lot of solutions.

---

### Post by northd_tech on 2011-05-04
> **qpsk1half said:**
> I am having the same problem with my Toshiba L505D with the RTL819**2SE**. When I switched to 10.04, I was at my wits end when I wrote in to a Toshiba Linux Users mailing list and they pointed me to this link [here]("http://ubuntuforums.org/showthread.php?t=1460038")

This worked like a champ for me. Flawlessly!! But no joy on the 11.04. Here are the relevant parts of the DMESG.
[   17.010066] rtl81**9xE**:Download Firmware: Put code fail!
[   17.010071] 
[   17.010075] rtl81**9xE**:ERR in CPUcheck_maincodeok_turnonCPU()
[   17.010076] 
[   17.010078] rtl81**9xE**:ERR in init_firmware()
[   17.010079] 
[   17.010082] rtl81**9xE**:ERR!!! _**rtl8192**_up(): initialization is failed!
[   17.010083] 

Any help would be greatly appreciated. I know this is an SE chip and thus requires different drivers. The drivers that I am using are thus: **rtl819[COLOR=Red]2e[/COLOR]**_linux_2.6.0014.0401.2010.tar.gz and are found at the above link. Thanks in advance folks.

I think you are using Realtek 819[COLOR=Red]**2E**[/COLOR] sourcecode for that 819[COLOR=Blue]**2SE**[/COLOR]...

From my research/experience the 8192SE should be MUCH easier- look for threads tagged "realtek 8192SE" on this forum- I've tagged at least 10 or so myself trying to get that 81[COLOR=Red]**92E**[/COLOR] to work under 64-bit.

Honestly, I think your best bet is just to email Realtek directly and get the 819[COLOR=Blue]**2SE**[/COLOR] drivers from their tech support (hopefully from "Kidman-" he seemed like the most Linux-knowledgeable to me, or else he checks his email much more often).

This is the Realtek email contact address:
[EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL]
from:
[http://www.realtek.com.tw/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2](http://www.realtek.com.tw/contact/contentView.aspx?Langid=1&PNid=1&PFid=4&Level=2)

If you are curious, this is the thread where I've recorded much of my 819[COLOR=Red]**2E**[/COLOR] saga:
[http://ubuntuforums.org/showthread.php?t=1689148&page=5](http://ubuntuforums.org/showthread.php?t=1689148&page=5)
EDIT2:  Actually, the 819[COLOR=Red]**2E **[/COLOR]"saga" was more here:
[http://ubuntuforums.org/showthread.php?t=1239342&page=9](http://ubuntuforums.org/showthread.php?t=1239342&page=9)
and here:
[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)

I can probably walk you through compiling/building a new driver module for your 8192SE though.

EDIT:  If you do email Realtek, be sure to send them the responses from the proper diagnostic terminal commands with your email to make sure you have the proper card & driver(s):

```
lspci | grep work

sudo lshw -C network
```

---

### Post by richaoj on 2011-05-04
> **qpsk1half said:**
> bump for help. I have seen a lot of folks with problems, but not a lot of solutions.

I agree with the prior poster .  I have a realtek 8192SE card.  I pulled the driver directly from the realtek site (the 12/20/10 version).  The version in the headers is from 5/07/10.  I have turned on natty-proposed and have gotten and installed all kernel updates.  I then compiled driver from source.  

Wireless works nearly perfectly now . . . . . 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

```

cd Downloads (or wherever you downloaded the file)
sudo cp rtl8192se_linux_2.6.0019.1207.2010.tar.gz /usr/src
cd /usr/src
sudo tar -xvf rtl8192se_linux_2.6.0019.1207.2010.tar.gz
cd rtl8192se_linux_2.6.0019.1207.2010
sudo make
sudo su
make install

```

---

### Post by evercam on 2011-05-06
Just to report I have had some success with the latest version updates on 11.04.  The latest kernel downloads 2.6.38-9 has restored stability to my setup without having to install anything from realtek.

I am running 11.04 on a samsung nb30 netbook. (realtek 8192e wireless).

---

### Post by yungballla6 on 2011-05-08
> **evercam said:**
> Just to report I have had some success with the latest version updates on 11.04.  The latest kernel downloads 2.6.38-9 has restored stability to my setup without having to install anything from realtek.

I am running 11.04 on a samsung nb30 netbook. (realtek 8192e wireless).

Can anyone else confirm this?

---

### Post by Peter09 on 2011-05-08
It is`certainly better than  maverick, but I still get instances of device not ready and on resuming from sleep the wireless device is not there.

---

### Post by Jackster on 2011-05-09
Even after installing the latest updates I'm still having issues with my r8192e wifi chip. It seems to work OK when I start up my Samsung N150 netbook, but if I close the lid and put it to sleep, then wake it up again it says 'device not ready' in the bar at the top. I tried reloading the module but it's not worked - only way to get wireless back is to reboot.

Any ideas?

---

### Post by calande on 2011-05-22
Mine disconnects after some time and won't come back up unless I unplug it and plug it back in physically. I'm using driver rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111.tar.bz2

---

### Post by Peter09 on 2011-05-22
My Samsung N150 has the same problem as Jacksters, has done since Maverick. 

Whatever happened, on upgrade to Maverick caused the problem, Lucid was fine. Since then no progress. Last I heard it was actually a problem in the Kernel.

---

### Post by ikonitas on 2011-05-26
Having the same issue with product: RTL8191SEvB Wireless LAN Controller

---

### Post by my2234 on 2011-07-16
pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.21cm; }  I have gathered together some notes to make it easy for someone with as little knowledge as I have.
 Sorry if it seems oversimplified and thanks to those who did all the hard stuff.
 

 This is for to make the Realtec RTL 8192E (a PCI card internal to the computer) work with UBUNTU 10 on a Samsung NB30 netbook computer.
 

 But provided  file ending .inf is renamed  when doing sudo ndiswrapper it will probably work for other cards needing XP drivers.
 

 

 Step 1 obtain XP drivers from the manufacturers web site.
 These will come in the form of a windows directory called
 819xP_WindowsDriver_1677.1.0708.2009.zip
 This should be unzipped to your home directory.
 

 A directory called RTL819xP_WindowsDriver_1677.1.0708.2009_90P_F1032.P1106_92E_F1032.P1106_ISS_1.00.0115.L
 will be generated.
 Inside this directory is a sub directory called
 RTL819xP_Driver
 Inside this directory is a sub directory called
 WinXP
 Inside this directory are the three files you actually need these are called
 

 net819wp.cat   net819xp.inf  rtl819xp.sys
 

 Copy these 3 files to your home directory. (I think you can now delete everything else that was downloaded and unzipped.)
 

 Now open up the terminal (Applications>>Accessories>>Terminal)
 Type :-   
 sudo ndiswrapper -m sudo ndiswrapper -i net819xp.inf       (do not type this but do use the correct .inf on this line) sudo modprobe ndiswrapper 

 To automatically load it when linux boots up you must edit etc\modules and add the last line
 

 # /etc/modules: kernel modules to load at boot time. # # This file contains the names of kernel modules that should be loaded # at boot time, one per line. Lines beginning with "#" are ignored.  fuse lp sbp2 **ndiswrapper** 

 in the terminal type:-
 sudo gedit /etc/modules  
 

 The editor will now open and the line in bold can be added at the end.
Save and close.


Restart.


Hope it helps someone:)

---

### Post by Dezfor on 2011-08-12
**my2234**, something is wrong in my case. Could someone help me?
I have **RTL8191SEvB Wireless LAN Controller(10EC:8172)** on Lenovo Thinkpad. OS: **Ubuntu 10.04** Lucid LTS
By default, ubuntu uses **r8192se_pci** but this driver is buggy and I decited to test ndiswrapper.
1. I installed needed packages
```
apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
2. Downloaded **[RTL8191SE-VA2 Windows XP driver]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2261")** and extracted it. Copied XP drivers (./91_92_SE_Driver/WinXP/)to home dir.
3. Blacklisted **r8192se_pci** driver and removed this module:
```
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
modprobe -r r8192se_pci
```
4. Installed WinXP drivers:
> ndiswrapper -m 
ndiswrapper -i ~/winXP/net8192se.inf
modprobe ndiswrapper 
5. Checked either driver istalled correctly
```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192se : driver installed
	device (10EC:8172) present (alternate driver: r8192se_pci)

```
fixed warning in such way:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
```
6. Added line to make **ndiswrapper** loading automatically when Ubuntu boots up:
```
echo "ndiswrapper" >> /etc/modules
```

When I try to start wireless with new module have such error:```

ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device wlan0
```
Rebooting laptop doesn't help. Module **ndiswrapper** is loaded and **r8192se_pci** is not loaded. 
What I missed?

---

