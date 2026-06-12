---
title: "RTL8187L wireless device will not load"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by maxvdh on 2012-08-04
Hi - I'm a new member and equally new to linux so I would appreciate a little hand holding.

I have a machine I recently put together for use with LinuxCNC and it runs Ubuntu 10.04.  I keep the machine in the garage and thus I wanted to use a long-range USB wireless device to get a connection to the router inside the house.  I chose an Alfa AWUS036h because it seemed to fit the bill.

I downloaded and installed drivers from Realtek for it and it seemed to work initially but it would not load up when I booted the computer.  I had to disconnect it and reconnect it and then it would work.  I fiddled around a little bit based on advice from friends and now I can't seem to get it to load the driver at all.

The relevant output of dmesg when the machine boots looks like this:
[   12.926208] Linux kernel driver for RTL8187L based WLAN cards
[   12.926214] Copyright (c) 2004-2005, Realtek
[   12.926219] rtl8187L: Initializing module
[   12.926224] rtl8187L: Wireless extensions version 22
[   12.926229] rtl8187L: Initializing proc filesystem
[   12.957672] type=1505 audit(1338433546.729:3):  operation="profile_load" pid=534 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.958179] type=1505 audit(1338433546.729:4):  operation="profile_load" pid=534 name="/usr/lib/connman/scripts/dhclient-script"
[   12.976791] Initializing USB Mass Storage driver...
[   12.979307] rtl8187L: Reported EEPROM chip is a 93c56 (2Kbit)
[   24.248806] rtl8187L: Card MAC address is 00:00:00:00:00:01
[   38.253094] rtl8187L: WW:Unknown RF module 0
[   38.253101] rtl8187L: WW:Exiting...
[   38.253105] rtl8187L: Initialization failed
[   38.253309] rtl8187L: wlan driver load failed
[   38.253312] 
[   38.253403] usbcore: registered new interface driver rtl8187L

dmesg gave me this when it successfully loaded after being unplugged and reconnected:
[   61.161004] usb 1-8: USB disconnect, address 5
[   63.984026] usb 1-8: new high speed USB device using ehci_hcd and address 9
[   64.144025] usb 1-8: device descriptor read/64, error -71
[   64.408027] usb 1-8: device descriptor read/64, error -71
[   64.624025] usb 1-8: new high speed USB device using ehci_hcd and address 10
[   64.784024] usb 1-8: device descriptor read/64, error -71
[   65.044024] usb 1-8: device descriptor read/64, error -71
[   65.260531] usb 1-8: new high speed USB device using ehci_hcd and address 11
[   65.696021] usb 1-8: device not accepting address 11, error -71
[   65.808041] usb 1-8: new high speed USB device using ehci_hcd and address 12
[   65.840317] usb 1-8: device descriptor read/8, error -71
[   65.972436] usb 1-8: device descriptor read/8, error -71
[   66.076032] hub 1-0:1.0: unable to enumerate USB device on port 8
[   66.344028] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   66.515376] usb 5-2: configuration #1 chosen from 1 choice
[   66.528297] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
[   67.578010] rtl8187L: Card MAC address is 00:c0:ca:53:12:8a
[   68.927964] rtl8187L: Card reports RF frontend Realtek 8225
[   68.927972] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[   70.250902] rtl8187L: This seems a new V2 radio: rtl8225_zebra2
[   70.251916] rtl8187L: PAPE from CONFIG2: 0
[   70.402915] rtl8187L: EEPROM Customer ID: FF
[   70.402919] 
[   70.406188] =====================>rtl8180_proc_init_one
[   70.406382] rtl8187L: Driver probe completed
[   70.406387] 
[   70.412913] rtl8187L: Now Radio On
[   70.434949] udev: renamed network interface wlan0 to wlan1
[   70.448055] rtl8187L: rtl8180_open process
[   71.070893] rtl8187L: Card successfully reset

Now, when I unplug it and plug it in, all I get is this:
[   1488.278615] usb 1-4: USB disconnect, address 2
[   1489.576027] usb 1-4: New high speed USB device using ehci_hcd and address 6
[   1489.708023] usb 1-4: device descriptor read/64 error -71
[   1489.957210] usb 1-4: configuration #1 chosen from 1 choice
[   1489.979912] rtl8187L: Report EEPROM chip is a 93c46 (1Kbit)
[   1498.484112] rtl8187L: No channels, aborting
[   1498.484121] rtl8187L: Initialization failed
[   1498.484306] rtl8187L: wlan driver load failed

This is the relevant output of lsusb:
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

Can I please get some suggestions about how to proceed to diagnose the problem and get the wireless adapter to work when I boot the computer?  Thanks in advance.

---

### Post by maxvdh on 2012-08-05
Bump... I'd really appreciate some help.  Chili555?

---

### Post by chili555 on 2012-08-07
Why did you compile a driver from Realtek? What was wrong with the rtl8187 built in to the 10.04 kernel? Did you blacklist the built-in in order to properly use the compiled version?

Were there any interesting errors or warnings when you compiled? You can see them again with:```
cd Desktop/RTL8187file  [COLOR="Red"]<--or whatever was extracted[/COLOR]
sudo su
make clean
make
make install
exit
```Copy and paste the warnings, etc. to a text document and post it here.

Since 12.04 is also a LTS release and there have been remarkable strides made in drivers in the last two years, why not upgrade to 12.04?

---

### Post by maxvdh on 2012-08-08
I compiled the driver from realtek simply because I knew no better and that's what some internet guide to installing the AWUS036H recommended doing. I believe I had also read that there were reliability issues with the built-in driver.  I never tried using the built-in driver so I can't say for sure whether it was ever really there.  I did try blacklisting some things based on some of the things I read but I've since deleted those lines since they didn't seem to have any effect.

There were no big warnings that I noticed but I'll copy the results of that procedure here:
> maxvdh@LinuxCNC-box:~/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012$ sudo su
[sudo] 
password for maxvdh: 
root@LinuxCNC-box:/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012# make clean
make[1]: Entering directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Module.symvers
rm -fr modules.order
rm -fr Module.markers
rm -rf tags
make[1]: Leaving directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187'
make[1]: Entering directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/ieee80211'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/ieee80211/tmp
rm -fr Module.symvers
rm -fr modules.order
rm -fr Module.markers
make[1]: Leaving directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/ieee80211'
root@LinuxCNC-box:/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-122-rtai'
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_93cx6.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_wx.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_led.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_pm.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8180_dm.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_rx.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_tx.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_wx.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_module.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.mod.o
  LD [M]  /home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187/r8187l.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-122-rtai'
root@LinuxCNC-box:/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012# make install
No system rtl8187.ko file found, Now we will install the new driver rtl8187.ko into system
No system rtl8187.ko file found, Now we will install the new driver rtl8187.ko into system
make[1]: Entering directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187'
make -C /lib/modules/2.6.32-122-rtai/build M=/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-122-rtai'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-122-rtai'
find /lib/modules/2.6.32-122-rtai -name "r8187.ko" -exec ls -l {} \;
find /lib/modules/2.6.32-122-rtai -name "r8187.ko" -exec rm {} \;
install -p -m 644 r8187l.ko /lib/modules/2.6.32-122-rtai/kernel/drivers/net/wireless
depmod -a
make[1]: Leaving directory `/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012/rtl8187'
root@LinuxCNC-box:/home/maxvdh/alfa-wireless-driver/rtl8187L_linux_1041.0209.2012# 

I don't upgrade to 12.04 because I don't know how it plays with LinuxCNC.  I used a prepackaged LiveCD installation for LinuxCNC.

Thanks a lot for your help.

---

### Post by chili555 on 2012-08-08
> No system rtl8187.ko file found, Now we will install the new driver rtl8187.ko into systemInteresting; my 10.04 system has it. However:> install -p -m 644 [COLOR="Red"]r8187l[/COLOR].ko /lib/modules/2.6.32-122-rtai/kernel/drivers/net/wirelessAs you can see, the module being loaded is named r8187l. I'm confident it's a lower-case L at the end. Please reboot and check:```
lsmod | grep 818
```Is it rtl8187 or r8187l that's loaded? If there *was* an rtl8187 and it's loaded, remove it and blacklist it:```
sudo su
modprobe -r rtl8187
modprobe r8187l
echo "blacklist rtl8187" >> /etc/modprobe.d/blacklist.conf
exit
```Then load r8187l and see if things improve.

If r8187l was loaded and rtl8187 was not, are the symptoms the same? Is dmesg the same?

EDIT: I am pleasantly surprised to see that CNC in this case really does refer to computer numerical control!

---

### Post by maxvdh on 2012-08-08
Thank you again - rebooted and:
> maxvdh@LinuxCNC-box:~$ lsmod | grep 818
r8187l                136240  0 

Now the symptoms are a little different this time but still I see no attempts to connect to my wireless network.  This is what I saw immediately after booting the computer:

> maxvdh@LinuxCNC-box:~$ dmesg | grep 818
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-122-rtai root=UUID=7dc83cd1-fe81-4818-ac69-7f43bcb629e4 ro quiet splash
[    0.334818]   alloc irq_desc for 25 on node -1
[    0.781815] ata1.00: configured for UDMA/133
[    1.213327] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   12.943603] Linux kernel driver for RTL8187L based WLAN cards
[   12.943614] rtl8187L: Initializing module
[   12.943620] rtl8187L: Wireless extensions version 22
[   12.943626] rtl8187L: Initializing proc filesystem
[   13.009408] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
[   13.936174] rtl8187L: Card MAC address is 00:c0:00:53:12:01
[   14.685084] rtl8187L: WW:Unknown RF module 0
[   14.685091] rtl8187L: WW:Exiting...
[   14.685097] rtl8187L: Initialization failed
[   14.685330] rtl8187L: wlan driver load failed
[   14.685437] usbcore: registered new interface driver rtl8187L

Then, after unplugging the adapter and plugging it back in, I saw this:
> [  225.513568] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
[  226.594809] rtl8187L: Card MAC address is 00:c0:f2:53:12:01
[  227.024876] rtl8187L: Card reports RF frontend Realtek 8225
[  227.024884] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[  228.998658] rtl8187L: This seems a legacy 1st version radio:rtl8225_zebra
[  228.998876] rtl8187L: PAPE from CONFIG2: 0
[  229.017751] rtl8187L: EEPROM Customer ID: FF
[  229.021099] =====================>rtl8180_proc_init_one
[  229.021299] rtl8187L: Driver probe completed
[  229.025495] rtl8187L: Now Radio On
[  229.182967] rtl8187L: rtl8180_open process
[  229.893333] rtl8187L: Card successfully reset
Note that this is very different than what I saw when the card successfully loaded, which I posted earlier. 8225??

The green light on the card had turned on but still no wireless connection.  In case it's of interest:
> maxvdh@LinuxCNC-box:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     802.11bg  Mode:Managed  Channel=7  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   Sensitivity=4/6  
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any more ideas how to proceed?  Thanks

---

### Post by chili555 on 2012-08-08
I'm sorry, I don't have the driver on my 10.04 system, so we'll have to depend on your readings. Please post:```
modinfo r8187l | grep parm 
```We might also see if the original rtl8187 is actually present:```
sudo updatedb
locate rtl8187.ko
```updatedb will take a few moments; please be patient.

If it is actually present, let's try it momentarily:```
sudo modprobe  -r r8187l
sudo modprobe rtl8187
```Any improvement?```
dmesg | tail -n20
```I will be away for a while so I can grep some parm: Chicken Parm!

---

### Post by maxvdh on 2012-08-08
Thanks for bearing with me.  Hope you enjoyed your chicken parm!

> maxvdh@LinuxCNC-box:~$ modinfo r8187l | grep parm
parm:           ifname:charp
parm:           devname: Net interface name,ath%d=default
parm:           channels: Channel bitmask for specific locales. NYI (int)
Not sure what to make of that

> maxvdh@LinuxCNC-box:~$ sudo updatedb
[sudo] password for maxvdh: 
maxvdh@LinuxCNC-box:~$ locate rtl8187.ko
Nothing there

> maxvdh@LinuxCNC-box:~$ dmesg | tail -n20
[  136.767338] ADDRCONF(NETDEV_UP): wlan3: link is not ready
[  166.200036] usb 1-7: new high speed USB device using ehci_hcd and address 6
[  166.344293] usb 1-7: configuration #1 chosen from 1 choice
[  166.401530] Initializing USB Mass Storage driver...
[  166.401888] scsi2 : SCSI emulation for USB Mass Storage devices
[  166.402376] usbcore: registered new interface driver usb-storage
[  166.402388] USB Mass Storage support registered.
[  166.407722] usb-storage: device found at 6
[  166.407731] usb-storage: waiting for device to settle before scanning
[  171.404381] usb-storage: device scan complete
[  171.405025] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler II  1.13 PQ: 0 ANSI: 0 CCS
[  171.408419] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  171.669485] sd 2:0:0:0: [sdb] 250880 512-byte logical blocks: (128 MB/122 MiB)
[  171.670092] sd 2:0:0:0: [sdb] Write Protect is off
[  171.670099] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  171.670104] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  171.673970] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  171.673982]  sdb: sdb1
[  171.678503] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  171.678518] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Not sure what to make of that either

And finally, yet more interesting dmsg outputs from booting the computer this time:
> maxvdh@LinuxCNC-box:~$ dmesg | grep 818
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-122-rtai root=UUID=7dc83cd1-fe81-4818-ac69-7f43bcb629e4 ro quiet splash
[    1.190168] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   12.894197] Linux kernel driver for RTL8187L based WLAN cards
[   12.894208] rtl8187L: Initializing module
[   12.894213] rtl8187L: Wireless extensions version 22
[   12.894218] rtl8187L: Initializing proc filesystem
[   12.943510] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
[   13.350369] rtl8187L: Card MAC address is 00:c0:ca:53:12:4d
[   13.730734] rtl8187L: Card reports RF frontend Realtek 8225
[   13.730744] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[   14.885904] rtl8187L: This seems a new V2 radio: rtl8225_zebra2
[   14.887035] rtl8187L: PAPE from CONFIG2: 0
[   14.935802] rtl8187L: EEPROM Customer ID: FF
[   14.937835] =====================>rtl8180_proc_init_one
[   14.937866] rtl8187L: Driver probe completed
[   14.937957] usbcore: registered new interface driver rtl8187L
[   14.940915] rtl8187L: Now Radio On
[   15.190161] rtl8187L: rtl8180_open process
[   15.935364] rtl8187L: Card successfully reset
[   17.268183]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   25.404612] rtl8187L: Now Radio Off
[   31.277563] rtl8187L: Now Radio On
[   47.400603] rtl8187L: Now Radio Off
[   55.273202] rtl8187L: Now Radio On
[  105.149000] rtl8187L: Now Radio Off
[  114.417653] rtl8187L: Now Radio On
[  119.412640] rtl8187L: Now Radio Off
[  129.549248] rtl8187L: Now Radio On
[  134.950094] rtl8187L: Now Radio Off
maxvdh@LinuxCNC-box:~$ 

I have noticed that since I did that driver reinstall, the computer boots really slowly.  I don't see why those things are related but it's the only thing I did before that happened.  It boots to the kind of "home screen" but it looks different than usual with no icons on the desktop.  It hangs there for a couple minutes then reverts back to normal and works fine.  And again, when I booted this time, the light turned on on the wireless card but it doesn't connect.

Any ideas of where to go from here?

---

### Post by chili555 on 2012-08-09
> [ 14.940915] rtl8187L: Now Radio On
[ 15.190161] rtl8187L: rtl8180_open process
[ 15.935364] rtl8187L: Card successfully reset
[ 17.268183] groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[ 25.404612] rtl8187L: Now Radio Off
[ 31.277563] rtl8187L: Now Radio On
[ 47.400603] rtl8187L: Now Radio Off
[ 55.273202] rtl8187L: Now Radio On
[ 105.149000] rtl8187L: Now Radio Off
[ 114.417653] rtl8187L: Now Radio On
[ 119.412640] rtl8187L: Now Radio Off
[ 129.549248] rtl8187L: Now Radio On
[ 134.950094] rtl8187L: Now Radio OffUgly. I found this: [http://support.data-alliance.net/alfa-awus036h-power-problem-fix-realtek-rtl8187l-chipset/](http://support.data-alliance.net/alfa-awus036h-power-problem-fix-realtek-rtl8187l-chipset/)> 	

High power requirements of Realtek RTL8187L chipset, found in the ALFA AWUS036H USB wireless adapter, can cause ”on and off cycling” and/or dropping of connections and performance issues (see details below). Of course, you could buy some powered device to help your wireless device along or, more sensibly, in my view, check the many threads here for supported out-of-the-box USB wireless devices and be all set.

This is also very informative: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455354)

---

### Post by maxvdh on 2012-08-09
Yeah I did initially suspect power had something to do with this but the driver behavior seems weird.  It's tempting to see what happens with a powered USB hub as they suggest, but I can probably get another adapter for around the same price.  I would like to find something with similar range and physical configuration.  Will see what I can find.

Thanks for your time.

---

### Post by maxvdh on 2012-08-09
So, out of curiosity I snipped the power wires from the cable to the wifi adapter and powered the adapter with an external 5VDC supply.  It drew 300 mA and its light came on but the computer doesn't seem to like this either.   When I connected it, the machine was somewhat unresponsive and the keyboard wouldn't work.  The mouse did though.  I shut off the supply and checked the dmesg info:

> [85352.804080] usb 1-8: new high speed USB device using ehci_hcd and address 8
[85352.944294] usb 1-8: configuration #1 chosen from 1 choice
[85352.971378] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
[85353.230243] rtl8187L: Card MAC address is 00:c0:ca:53:12:8a
[85353.522235] rtl8187L: Card reports RF frontend Realtek 8225
[85353.522245] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[85354.680902] rtl8187L: This seems a new V2 radio: rtl8225_zebra2
[85354.681208] rtl8187L: PAPE from CONFIG2: 0
[85354.715899] rtl8187L: EEPROM Customer ID: FF
[85354.715903] 
[85354.718333] =====================>rtl8180_proc_init_one
[85354.720289] rtl8187L: Driver probe completed
[85354.720295] 
[85354.722400] rtl8187L: Now Radio On
[85354.753223] udev: renamed network interface wlan0 to wlan1
[85354.760880] rtl8187L: rtl8180_open process
[85355.496722] rtl8187L: Card successfully reset
[85365.145241] rtl8187L: Now Radio Off
[85369.310103] rtl8187L: Now Radio On
[85423.424248] rtl8187L: Now Radio Off
[85424.962651] rtl8187L: Now Radio On
[85476.894767] usb 1-8: USB disconnect, address 8
[85476.968463] rtl8187L: EE:cannot submit RX command. URB_STATUS 0
[85476.998708] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[85477.022951] Error TX URB 0, error -19Error TX URB 0, error -19
[85477.028899] rtl8187L: rtl8180_close process
[85477.039074] rtl8187L: Now Radio Off
[85477.072406] =====================>rtl8180_proc_remove_one
[85477.671630] rtl8187L: WW:Card reset timeout!
[85477.880481] rtl8187L: wlan driver removed
[85477.880486] 


Don't know if this helps at all.  I think I still need to find myself another long-range plug-n-play wireless adapter

---

### Post by chili555 on 2012-08-10
> [85365.145241] rtl8187L: Now Radio Off
[85369.310103] rtl8187L: Now Radio On
[85423.424248] rtl8187L: Now Radio Off
[85424.962651] rtl8187L: Now Radio On
[85476.894767] usb 1-8: USB disconnect, address 8
[85476.968463] rtl8187L: EE:cannot submit RX command. URB_STATUS 0
[85476.998708] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[85477.022951] Error TX URB 0, error -19Error TX URB 0, error -19
[85477.028899] rtl8187L: rtl8180_close process
[85477.039074] rtl8187L: Now Radio OffThat's an unhappy wireless device!>  I think I still need to find myself another long-range plug-n-play wireless adapter I agree.

---

