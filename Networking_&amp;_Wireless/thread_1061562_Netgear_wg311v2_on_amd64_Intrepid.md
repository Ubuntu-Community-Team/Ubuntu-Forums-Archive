---
title: "Netgear wg311v2 on amd64 Intrepid"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by dtsmith1984 on 2009-02-05
I just set up a new computer and installed 8.10 amd64, however the computer would lock up every time it booted.  I've determined that its my wg311v2 (TI acx111 chipset).  I blacklisted acx and now can boot the system just fine.

Has anyone ever gotten this card to work on the amd64 installation? 

I havent been able to find any promising information online and from what I can tell, this card does not support 64-bit systems.  

I havent tried ndiswrapper yet, but I'm pretty sure it will not work since there are no 64bit windows drivers.  Is there any way to get ubuntu to run the module in some sort of 32 bit compatibility mode?

I'm open to any suggestions at this point. I really dont want to go back to a 32 bit install on my new phenom II x4 940 :)

Thanks,
David Smith

---

### Post by pytheas22 on 2009-02-05
Unfortunately there's no way to make ndiswrapper on a 64-bit system work with 32-bit Windows drivers.  Are you positive there are no 64-bit Windows drivers around?  Did you search the [database]("http://burnthesorbonne.com/?page_id=32") by your card's PCI ID?

Also, did you do much investigation as to why the acx module causes the system to crash?  Did you check the logs or anything?  What happens if you boot the computer, then take acx off the blacklist and try modprobing it?

If it's just a bug in the driver, you may be able to recompile an updated version to solve the problem, or you may be able to load it with certain options that will prevent the crashes.  If you could provide some more specific information on why the module is making the system crash (i.e., some lines from the system log), that would give us something to start with to figure this out.

Also, what is the PCI ID of your card?

---

### Post by dtsmith1984 on 2009-02-06
Ok I've modprobe'd acx and surprisingly the system didnt crash, wireless didnt work though.  Here is the information from syslog. 

And the PCI ID is 104c:9066

```
Feb  5 17:34:31 ubuntu kernel: [16157.869413] acx: Loaded combined PCI/USB driver, firmware_ver=default
Feb  5 17:34:31 ubuntu kernel: [16157.869428] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Feb  5 17:34:31 ubuntu kernel: [16157.869542] acx_pci 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  5 17:34:31 ubuntu kernel: [16157.869588] acx: found ACX111-based wireless network card at 0000:03:06.0, irq:20, phymem1:0xFDDFC000, phymem2:0xFDDC0000, mem1:0xffffc20011498000, mem1_size:8192, mem2:0xffffc20013500000, mem2_size:131072
Feb  5 17:34:31 ubuntu kernel: [16157.870605] acx: loading firmware for acx1111 chipset with radio ID 16
Feb  5 17:34:31 ubuntu kernel: [16157.870612] firmware: requesting acx/1.2.1.34/tiacx111c16
Feb  5 17:34:32 ubuntu kernel: [16158.600594] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
Feb  5 17:34:32 ubuntu kernel: [16158.600611] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Feb  5 17:34:32 ubuntu kernel: [16158.600617] AntennaID:00 Len:02 Data:01 02 
Feb  5 17:34:32 ubuntu kernel: [16158.600623] PowerLevelID:01 Len:02 Data:001E 000A 
Feb  5 17:34:32 ubuntu kernel: [16158.600630] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Feb  5 17:34:32 ubuntu kernel: [16158.600640] DomainID:03 Len:06 Data:41 20 30 31 32 40 
Feb  5 17:34:32 ubuntu kernel: [16158.600650] ProductID:04 Len:09 Data:TI ACX100
Feb  5 17:34:32 ubuntu kernel: [16158.600654] ManufacturerID:05 Len:07 Data:TI Test
Feb  5 17:34:32 ubuntu kernel: [16158.660077] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Feb  5 17:34:32 ubuntu kernel: [16158.663048] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-7-generic
Feb  5 17:34:32 ubuntu kernel: [16158.664740] usbcore: registered new interface driver acx_usb
Feb  5 17:34:32 ubuntu nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_0f_b5_4c_94_29, iface: wlan0)
Feb  5 17:34:32 ubuntu NetworkManager: <info>  wlan0: driver is 'acx_pci'. 
Feb  5 17:34:32 ubuntu NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Feb  5 17:34:32 ubuntu NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Feb  5 17:34:32 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_0f_b5_4c_94_29 
Feb  5 17:34:36 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb  5 17:34:36 ubuntu NetworkManager: <info>  (wlan0): bringing up device. 
Feb  5 17:34:36 ubuntu NetworkManager: <info>  (wlan0): preparing device. 
Feb  5 17:34:36 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Feb  5 17:34:36 ubuntu kernel: [16162.889923] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  5 17:34:36 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Feb  5 17:34:37 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 

```

---

### Post by pytheas22 on 2009-02-06
From dmesg, it looks like the acx driver is working after you modprobe it.  I think that the failure to connect is due to a problem with Network Manager--the line about "(wlan0): deactivating device (reason: 2)" seems to be related to that, according to Google.

You'd probably have better luck connecting with [wicd]("(wlan0): deactivating device (reason: 2)") instead of NM.  Could you give that a try?  You can install wicd using [this package]("http://downloads.sourceforge.net/wicd/wicd_1.5.8_all.deb?modtime=1231069687&big_mirror=0"), which you can download and transfer to Ubuntu if you have no Internet connection on it right now.

---

### Post by dtsmith1984 on 2009-02-06
I have run a wire across the room for the time being.  I have to run some errands real quick but when I get back I will try that and post my results. Thanks!

---

### Post by dtsmith1984 on 2009-02-06
Ok, I've set up wicd.  I can load the acx module fine with no crashes so far.  However, it shows "No Wireless Networks Found".

Syslog:
```
Feb  6 11:47:47 ubuntu kernel: [  222.052075] acx: Loaded combined PCI/USB driver, firmware_ver=default
Feb  6 11:47:47 ubuntu kernel: [  222.052088] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Feb  6 11:47:47 ubuntu kernel: [  222.052180] acx_pci 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Feb  6 11:47:47 ubuntu kernel: [  222.052226] acx: found ACX111-based wireless network card at 0000:03:06.0, irq:20, phymem1:0xFDDFC000, phymem2:0xFDDC0000, mem1:0xffffc20011478000, mem1_size:8192, mem2:0xffffc200134c0000, mem2_size:131072
Feb  6 11:47:47 ubuntu kernel: [  222.053249] acx: loading firmware for acx1111 chipset with radio ID 16
Feb  6 11:47:47 ubuntu kernel: [  222.053257] firmware: requesting acx/1.2.1.34/tiacx111c16
Feb  6 11:47:47 ubuntu kernel: [  222.784596] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
Feb  6 11:47:47 ubuntu kernel: [  222.784613] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Feb  6 11:47:47 ubuntu kernel: [  222.784619] AntennaID:00 Len:02 Data:01 02 
Feb  6 11:47:47 ubuntu kernel: [  222.784625] PowerLevelID:01 Len:02 Data:001E 000A 
Feb  6 11:47:47 ubuntu kernel: [  222.784634] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Feb  6 11:47:47 ubuntu kernel: [  222.784643] DomainID:03 Len:06 Data:41 20 30 31 32 40 
Feb  6 11:47:47 ubuntu kernel: [  222.784653] ProductID:04 Len:09 Data:TI ACX100
Feb  6 11:47:47 ubuntu kernel: [  222.784657] ManufacturerID:05 Len:07 Data:TI Test
Feb  6 11:47:47 ubuntu kernel: [  222.844066] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Feb  6 11:47:47 ubuntu kernel: [  222.847035] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-11-generic
Feb  6 11:47:47 ubuntu kernel: [  222.848593] usbcore: registered new interface driver acx_usb
Feb  6 11:47:58 ubuntu kernel: [  233.065918] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by pytheas22 on 2009-02-06
In wicd, press the 'Preferences' button and make sure that the wireless interface is specified as 'wlan0'.  This is probably why you can't see any networks.

Also, what is the output of:
```

sudo iwlist scan
```

If it shows you a list of wireless networks, then your card is definitely able to see them.

---

### Post by dtsmith1984 on 2009-02-06
After playing around with it some, I get it to load up and detect networks.  But when I connect to my network, it keeps dropping the connection.

syslog:
```
Feb  6 14:05:23 ubuntu kernel: [ 5381.723940] r8169: eth0: link up
Feb  6 14:05:24 ubuntu kernel: [ 5382.585906] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  6 14:05:25 ubuntu kernel: [ 5383.036518] wlan0: duplicate address detected!
```

I have tried DHCP and Static.  I've tried IP's that I know are not already assigned.

---

### Post by pytheas22 on 2009-02-06
That's weird.  Does it let you transfer any traffic, or do you get that message immediately after connecting?

---

### Post by dtsmith1984 on 2009-02-06
It only stays up for about 5 seconds.  I tried to ping google.com and got one response back and then it reset itself.


I may just move this computer across the room to get close enough for a wired connection unless you have any more ideas.

It must have something to do with the 64 bit because it worked fine with 32bit intrepid.  

Thank you for all the help though, I will continue to mess with it and maybe at some point I'll be able to get it working.

Thanks!

-David

---

### Post by pytheas22 on 2009-02-06
Actually it seems like this is a well-known issue with the acx driver (google "wlan0: duplicate address detected acx" and you'll see lots of reports dating back to at least Ubuntu 6.10).

Unfortunately I didn't find any solutions (I also didn't google exhaustively; you might have better luck if you put more time into it).  The only encouragement is that someone in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/211670") says that Ubuntu updates (specifically, the update to the 2.6.X-18 build of the Ubuntu 8.04 kernel) fixed it for him.  So if you happen to be on Ubuntu 8.04, run 'sudo apt-get upgrade' and reboot and see if it makes a difference.

I also looked around briefly for 64-bit Windows drivers with no luck, but again, I didn't search everything.  I'd be surprised if there's really no 64-bit driver out there for this chipset; it seems pretty popular.

---

