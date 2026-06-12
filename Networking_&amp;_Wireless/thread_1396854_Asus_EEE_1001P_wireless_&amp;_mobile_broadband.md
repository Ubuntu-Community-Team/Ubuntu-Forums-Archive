---
title: "Asus EEE 1001P wireless &amp; mobile broadband"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by zweiundzwei on 2010-02-02
I just got a new Asus Eee 1001P, and the wireless isn't working at all. I had an Asus EEE 1005HA before that and since both use the AR8132 network card I hoped it would be the same problem as with that, where installing the backports fixed the problem. However, that doesn't do anything. With the 1005HA the connection was only flaky and disconnected a lot, but the 1001P doesn't find any networks to connect to at all. Also, the mobile wireless will connect only once and after disconnecting every attempt to reconnect ends in that connection symbol spinning wildly until I tell the network manager to disconnect. On Kubuntu it doesn't even connect once.
I never had that problem with the 1005.


```
$ lspci
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by pdc on 2010-02-02
if you now ask

> lspci -n

it may something like 00:01.0 0601: 10de:0548 (rev a2)

the final VendorID: product ID may help identify your device more clearly

---

### Post by zweiundzwei on 2010-02-02
Yay, help's coming :)

I wasn't sure which one of those you'd need, here's the full output

$ lspci -n 
00:00.0 0600: 8086:a010
00:02.0 0300: 8086:a011
00:02.1 0380: 8086:a012
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1c.3 0604: 8086:27d6 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27bc (rev 02)
00:1f.2 0106: 8086:27c1 (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
01:00.0 0200: 1969:1062 (rev c0)
02:00.0 0280: 168c:002c (rev 01)

---

### Post by pdc on 2010-02-02
I think your device is this

> 02:00.0 0280: 168c:002c (rev 01)

and if you then google on that Vendor ID: Product ID

..... seems like folks are using ndiswrapper;

ideal though if you could find a linux driver

but see here

[http://georgia.ubuntuforums.org/showthread.php?t=1396074](http://georgia.ubuntuforums.org/showthread.php?t=1396074)

this thread is running concurrently 

and 

[http://swiss.ubuntuforums.org/showthread.php?p=8652151](http://swiss.ubuntuforums.org/showthread.php?p=8652151)

and particularly post #3

here

[http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304)

someone suggests the device is an ar2427

google on ubuntu ndiswrapper for how to install but I think several of these threads give the commands, if that is the route seems the best to you

---

### Post by pdc on 2010-02-02
actually

[http://www.linuxforums.org/forum/suse-linux-help/156054-opensuse-11-2-acer-aspire-one-wireless.html](http://www.linuxforums.org/forum/suse-linux-help/156054-opensuse-11-2-acer-aspire-one-wireless.html)

looks like your device uses the 

> ath5k driver

If you google 

> ubuntu ath5k  and see how you get along 

eg

[http://ubuntuforums.org/showthread.php?t=987955](http://ubuntuforums.org/showthread.php?t=987955)

but this is an old post ...........

suspect this driver may be available in the kernel? experts please?

what does 

> lsmod | grep athgive you?

or 

> lsmod | grep ath*

---

### Post by zweiundzwei on 2010-02-02
Awesome. Thanks for all those links, they were really helpful.
[http://georgia.ubuntuforums.org/showthread.php?t=1396074](http://georgia.ubuntuforums.org/showthread.php?t=1396074) did the trick -- I'd tried ndiskgtk before, but I always used the drivers from the Atheros website, and they didn't work. 

However, now the network manager doesn't seem to recognize my mobile broadband stick at all anymore. This has never been a problem before, it would at least notice the stick, if not connect. Any ideas? It's a Huawai S4011.

---

### Post by pdc on 2010-02-02
so you used ndiswrapper?

for your mobile broadband, it was working on 9.10 before this wireless install?

either way, copy and paste the results of 

> lsusb back here with the Huawei device plugged in to a USB port

---

### Post by zweiundzwei on 2010-02-02
Yes, ndiswrapper with the Wlan_NE785H_GE112H-V7_7_0_377_XP driver.

The mobile broadband was working before, even though I could only successfully connect once per reboot. But the network manager detected it fine. On my Asus Eee 1005ha, which was also running ubuntu 9.10, it worked without any problems.

$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 003: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by pdc on 2010-02-03
folks suggest one should have the latest kernel version installed

what does 

> uname -r give: if you copy and paste the results back

---

### Post by zweiundzwei on 2010-02-03
I think I've got the newest one -- 2.6.31-17-generic.

---

### Post by DarkCanis on 2010-02-03
Got the Asus EEE 1001P on Monday and was running into the same issues.

The card is the Azurewave AR5B95 it's a half minipci-e card.  

I encountered some issues with the ndiswrapper because at the moment that is the only method that was working, I was then running into this issue

```
ndiswrapper (iw_set_auth:1602): invalid cmd 12
```[FONT=Verdana]
[/FONT] [FONT=Verdana]Then went here:[/FONT][I][FONT=Arial]

[/FONT][/I][http://ubuntuforums.org/showthread.php?p=8426311](http://ubuntuforums.org/showthread.php?p=8426311)

---

### Post by zweiundzwei on 2010-02-03
I'm now using the patched version of ndiswrapper. The network manager recognizes the usb stick again but I can still only connect once, so when I lose the connection I have to restart ubuntu to reconnect.

---

### Post by kspeed on 2010-02-04
New here to the forum. Want to say a big thanks for all the info posted here! It came in handy.

Just bought the 1001P and it came pre-loaded with Win7 blah. Wiped it and installed Xubuntu 9.10 desktop and loaded the WindowsXP LAN driver. Works beautifully! Overall so far I am very pleased with this netbook. Going to use it for school mainly.

-Matt

---

### Post by olaf-g on 2010-04-02
I solved the issues with the wireless and the screen brightness control. As I am writing down my experiences and fixes in a blog you can find the exact steps over there:

[http://linuxon1001p.blogspot.com]("http://linuxon1001p.blogspot.com/2010/03/fixing-wireless.html")

For wireless I use a self compiled native driver which was really not difficult to do and the brightnes issue is fixed completely including on screen notifications and auto dimming working.

---

### Post by khunter1 on 2010-04-08
> **kspeed said:**
> New here to the forum. Want to say a big thanks for all the info posted here! It came in handy.

Just bought the 1001P and it came pre-loaded with Win7 blah. Wiped it and installed Xubuntu 9.10 desktop and loaded the WindowsXP LAN driver. Works beautifully! Overall so far I am very pleased with this netbook. Going to use it for school mainly.

-Matt

ndiswrapper (and the XP driver) gives me bad signal quality.

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967)

---

### Post by dionblundell on 2010-04-18
This is a better way of getting your wireless to work.

It is better than using the windows drivers:
1) better link quality
2) GNU linux module, rather than windows
3) easy

Go here:
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)
and download the latest drivers, for example:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2)

Now extract these files
Open a SHELL, and change into the directory created with the archive,    it's probably something like:
```
cd ~/Downloads/compat-wireless-2010-04-18

```now select the driver
```
./scripts/driver-select ath9k
```You now need to build the    drivers
```
make
```Now install them with this
```
sudo make install
sudo make unload
sudo modprobe ath9k
```You will need to do ALL the above EACH TIME  the kernel is   updated.
Networking works perfectly for me on my ASUS 1005PE now

---

### Post by tenkenx on 2010-04-21
Hey there, after going through the steps you have listed, the modprobe command gives me a large set of errors and when I reboot my machine the kernel won't boot.  I have to revert to the old kernel in order to even get into the OS.  Have you heard of anything similar to this happening?

---

### Post by dionblundell on 2010-04-22
How about copying and pasting the large amount of errors into a post, there should be a clue there as to what is going wrong.

---

### Post by tenkenx on 2010-04-27
Sorry for the slow reply.

When issuing the command sudo modprobe ath9k, I get the following errors:

sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: Error inserting pcmcia_core (/lib/modules/2.6.31-20-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting compat (/lib/modules/2.6.31-20-generic/updates/compat/compat.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-20-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Nothing crashes after this, however when I reboot it will not boot into the OS and I have to revert to an older kernel.

---

### Post by khunter1 on 2010-04-27
I get errors on your last command:


                 ```
asus@Asus:~/Downloads/compat-wireless-2010-04-26$   sudo modprobe ath9k
 WARNING: Error inserting ath9k_hw  (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko):   Unknown symbol in module, or unknown parameter (see dmesg)
 WARNING: Error inserting ath9k_common  (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko):   Unknown symbol in module, or unknown parameter (see dmesg)
 WARNING: Error inserting mac80211  (/lib/modules/2.6.31-20-generic/updates/cw/mac80211.ko):  Unknown symbol  in module, or unknown parameter (see dmesg)
 FATAL: Error inserting ath9k  (/lib/modules/2.6.31-20-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko):   Unknown symbol in module, or unknown parameter (see dmesg)
 asus@Asus:~/Downloads/compat-wireless-2010-04-26$

```

---

### Post by dionblundell on 2010-04-28
tenkenx:
the clue is the line:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it  will be ignored in a future release.
``` Obviously you also have the windows driver installed too using ndiswrapper?
You'll need to uninstall it, the method above is an alternate to ndiswrapper.

[khunter1]("http://ubuntuforums.org/member.php?u=1049972"):
It sounds like the module ath9k did not compile correctly, did it give errors as it completed? have you tied rebooting, it is important to unload the old modules first, and rebooting is the easiest way to do this.

---

### Post by khunter1 on 2010-04-29
> **dionblundell said:**
> 
[khunter1]("http://ubuntuforums.org/member.php?u=1049972"):
It sounds like the module ath9k did not compile correctly, did it give errors as it completed? have you tied rebooting, it is important to unload the old modules first, and rebooting is the easiest way to do this.


How can I tell the Terminal to put the Verbose in another text file...because the Terminal truncates everything after a certain length...then I will run all commands again...and post output here.

---

### Post by tenkenx on 2010-04-30
Hey there,

I just reinstalled the latest release of ubuntu and followed your steps and wireless is up and running.  I thought the 1001p wireless was supposed to be supported by default in the newest release.  It wasn't for me anyway but your steps worked so everything is good for now.

Thanks again

---

### Post by khunter1 on 2010-04-30
```
asus@Asus:~/Downloads$ tar jxvf compat-wireless-2010-04-26.tar.bz2
```Output

```
compat-wireless-2010-04-26/
compat-wireless-2010-04-26/.gitignore
compat-wireless-2010-04-26/COPYRIGHT
compat-wireless-2010-04-26/Makefile
compat-wireless-2010-04-26/README
compat-wireless-2010-04-26/config.mk
compat-wireless-2010-04-26/patches/
compat-wireless-2010-04-26/patches/01-netdev.patch
compat-wireless-2010-04-26/patches/02-ksize.patch
compat-wireless-2010-04-26/patches/03-rfkill.patch
compat-wireless-2010-04-26/patches/04-netns.patch
compat-wireless-2010-04-26/patches/05-usb.patch
compat-wireless-2010-04-26/patches/06-header-changes.patch
compat-wireless-2010-04-26/patches/07-change-default-rate-alg.patch
compat-wireless-2010-04-26/patches/08-rename-iwl4965-config.patch
compat-wireless-2010-04-26/patches/09-threaded-irq.patch
compat-wireless-2010-04-26/patches/10-add-wext-handlers-to-netdev.patch
compat-wireless-2010-04-26/patches/11-dev-pm-ops.patch
compat-wireless-2010-04-26/patches/12-iw_handler-changes.patch
compat-wireless-2010-04-26/patches/14-device-type.patch
compat-wireless-2010-04-26/patches/15-symbol-export-conflicts.patch
compat-wireless-2010-04-26/patches/16-bluetooth.patch
compat-wireless-2010-04-26/patches/17-netdev-queue.patch
compat-wireless-2010-04-26/patches/18-rename-usb-net-symbols.patch
compat-wireless-2010-04-26/patches/19-kfifo.patch
compat-wireless-2010-04-26/patches/98-add-compat-wireless.patch
compat-wireless-2010-04-26/patches/99-change-makefiles.patch
compat-wireless-2010-04-26/patches/README
compat-wireless-2010-04-26/patches/20-pcidev.patch
compat-wireless-2010-04-26/patches/21-capi-proc_fops.patch
compat-wireless-2010-04-26/patches/22-multiqueue.patch
compat-wireless-2010-04-26/patches/24-pcmcia.patch
compat-wireless-2010-04-26/patches/25-multicast-list_head.patch
compat-wireless-2010-04-26/patches/26-sdio-quirks.patch
compat-wireless-2010-04-26/scripts/
compat-wireless-2010-04-26/scripts/admin-clean.sh
compat-wireless-2010-04-26/scripts/admin-refresh.sh
compat-wireless-2010-04-26/scripts/admin-update.sh
compat-wireless-2010-04-26/scripts/athenable
compat-wireless-2010-04-26/scripts/athload
compat-wireless-2010-04-26/scripts/b43enable
compat-wireless-2010-04-26/scripts/b43load
compat-wireless-2010-04-26/scripts/btload.sh
compat-wireless-2010-04-26/scripts/btunload.sh
compat-wireless-2010-04-26/scripts/check_config.sh
compat-wireless-2010-04-26/scripts/check_depmod
compat-wireless-2010-04-26/scripts/compress_modules
compat-wireless-2010-04-26/scripts/driver-select
compat-wireless-2010-04-26/scripts/gen-compat-autoconf.sh
compat-wireless-2010-04-26/scripts/gen-stable-release.sh
compat-wireless-2010-04-26/scripts/iwl-enable
compat-wireless-2010-04-26/scripts/iwl-load
compat-wireless-2010-04-26/scripts/load.sh
compat-wireless-2010-04-26/scripts/madwifi-unload
compat-wireless-2010-04-26/scripts/modlib.sh
compat-wireless-2010-04-26/scripts/unload.sh
compat-wireless-2010-04-26/scripts/update-initramfs
compat-wireless-2010-04-26/scripts/wlload.sh
compat-wireless-2010-04-26/scripts/wlunload.sh
compat-wireless-2010-04-26/include/
compat-wireless-2010-04-26/include/linux/
compat-wireless-2010-04-26/include/linux/usb/
compat-wireless-2010-04-26/include/linux/usb/usbnet.h
compat-wireless-2010-04-26/include/linux/usb/rndis_host.h
compat-wireless-2010-04-26/include/linux/unaligned/
compat-wireless-2010-04-26/include/linux/unaligned/access_ok.h
compat-wireless-2010-04-26/include/linux/unaligned/be_byteshift.h
compat-wireless-2010-04-26/include/linux/unaligned/be_memmove.h
compat-wireless-2010-04-26/include/linux/unaligned/be_struct.h
compat-wireless-2010-04-26/include/linux/unaligned/generic.h
compat-wireless-2010-04-26/include/linux/unaligned/le_byteshift.h
compat-wireless-2010-04-26/include/linux/unaligned/le_memmove.h
compat-wireless-2010-04-26/include/linux/unaligned/le_struct.h
compat-wireless-2010-04-26/include/linux/unaligned/memmove.h
compat-wireless-2010-04-26/include/linux/unaligned/packed_struct.h
compat-wireless-2010-04-26/include/linux/spi/
compat-wireless-2010-04-26/include/linux/spi/wl12xx.h
compat-wireless-2010-04-26/include/linux/spi/libertas_spi.h
compat-wireless-2010-04-26/include/linux/ieee80211.h
compat-wireless-2010-04-26/include/linux/nl80211.h
compat-wireless-2010-04-26/include/linux/pci_ids.h
compat-wireless-2010-04-26/include/linux/eeprom_93cx6.h
compat-wireless-2010-04-26/include/linux/ath9k_platform.h
compat-wireless-2010-04-26/include/linux/ssb/
compat-wireless-2010-04-26/include/linux/ssb/ssb.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_driver_chipcommon.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_driver_extif.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_driver_gige.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_driver_mips.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_driver_pci.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_embedded.h
compat-wireless-2010-04-26/include/linux/ssb/ssb_regs.h
compat-wireless-2010-04-26/include/linux/rfkill_backport.h
compat-wireless-2010-04-26/include/linux/bitops.h
compat-wireless-2010-04-26/include/linux/compat-2.6.14.h
compat-wireless-2010-04-26/include/linux/compat-2.6.18.h
compat-wireless-2010-04-26/include/linux/compat-2.6.19.h
compat-wireless-2010-04-26/include/linux/compat-2.6.21.h
compat-wireless-2010-04-26/include/linux/compat-2.6.22.h
compat-wireless-2010-04-26/include/linux/compat-2.6.23.h
compat-wireless-2010-04-26/include/linux/compat-2.6.24.h
compat-wireless-2010-04-26/include/linux/compat-2.6.25.h
compat-wireless-2010-04-26/include/linux/compat-2.6.26.h
compat-wireless-2010-04-26/include/linux/compat-2.6.27.h
compat-wireless-2010-04-26/include/linux/compat-2.6.28.h
compat-wireless-2010-04-26/include/linux/compat-2.6.29.h
compat-wireless-2010-04-26/include/linux/compat-2.6.30.h
compat-wireless-2010-04-26/include/linux/compat-2.6.31.h
compat-wireless-2010-04-26/include/linux/compat-2.6.32.h
compat-wireless-2010-04-26/include/linux/compat-2.6.33.h
compat-wireless-2010-04-26/include/linux/compat-2.6.34.h
compat-wireless-2010-04-26/include/linux/compat-2.6.35.h
compat-wireless-2010-04-26/include/linux/compat-2.6.h
compat-wireless-2010-04-26/include/linux/compat_autoconf.h
compat-wireless-2010-04-26/include/linux/pm_qos_params.h
compat-wireless-2010-04-26/include/linux/tracepoint.h
compat-wireless-2010-04-26/include/linux/wireless.h
compat-wireless-2010-04-26/include/net/
compat-wireless-2010-04-26/include/net/bluetooth/
compat-wireless-2010-04-26/include/net/bluetooth/hci_core.h
compat-wireless-2010-04-26/include/net/bluetooth/l2cap.h
compat-wireless-2010-04-26/include/net/bluetooth/bluetooth.h
compat-wireless-2010-04-26/include/net/bluetooth/rfcomm.h
compat-wireless-2010-04-26/include/net/bluetooth/hci.h
compat-wireless-2010-04-26/include/net/cfg80211.h
compat-wireless-2010-04-26/include/net/ieee80211_radiotap.h
compat-wireless-2010-04-26/include/net/mac80211.h
compat-wireless-2010-04-26/include/net/lib80211.h
compat-wireless-2010-04-26/include/net/regulatory.h
compat-wireless-2010-04-26/include/net/net_namespace.h
compat-wireless-2010-04-26/include/trace/
compat-wireless-2010-04-26/include/trace/define_trace.h
compat-wireless-2010-04-26/net/
compat-wireless-2010-04-26/net/mac80211/
compat-wireless-2010-04-26/net/mac80211/aes_ccm.c
compat-wireless-2010-04-26/net/mac80211/aes_ccm.h
compat-wireless-2010-04-26/net/mac80211/aes_cmac.c
compat-wireless-2010-04-26/net/mac80211/aes_cmac.h
compat-wireless-2010-04-26/net/mac80211/agg-rx.c
compat-wireless-2010-04-26/net/mac80211/agg-tx.c
compat-wireless-2010-04-26/net/mac80211/cfg.c
compat-wireless-2010-04-26/net/mac80211/cfg.h
compat-wireless-2010-04-26/net/mac80211/debugfs.c
compat-wireless-2010-04-26/net/mac80211/debugfs.h
compat-wireless-2010-04-26/net/mac80211/debugfs_key.c
compat-wireless-2010-04-26/net/mac80211/debugfs_key.h
compat-wireless-2010-04-26/net/mac80211/debugfs_netdev.c
compat-wireless-2010-04-26/net/mac80211/debugfs_netdev.h
compat-wireless-2010-04-26/net/mac80211/debugfs_sta.c
compat-wireless-2010-04-26/net/mac80211/debugfs_sta.h
compat-wireless-2010-04-26/net/mac80211/driver-ops.h
compat-wireless-2010-04-26/net/mac80211/driver-trace.c
compat-wireless-2010-04-26/net/mac80211/driver-trace.h
compat-wireless-2010-04-26/net/mac80211/event.c
compat-wireless-2010-04-26/net/mac80211/ht.c
compat-wireless-2010-04-26/net/mac80211/ibss.c
compat-wireless-2010-04-26/net/mac80211/ieee80211_i.h
compat-wireless-2010-04-26/net/mac80211/iface.c
compat-wireless-2010-04-26/net/mac80211/key.c
compat-wireless-2010-04-26/net/mac80211/key.h
compat-wireless-2010-04-26/net/mac80211/led.c
compat-wireless-2010-04-26/net/mac80211/led.h
compat-wireless-2010-04-26/net/mac80211/main.c
compat-wireless-2010-04-26/net/mac80211/mesh.c
compat-wireless-2010-04-26/net/mac80211/mesh.h
compat-wireless-2010-04-26/net/mac80211/mesh_hwmp.c
compat-wireless-2010-04-26/net/mac80211/mesh_pathtbl.c
compat-wireless-2010-04-26/net/mac80211/mesh_plink.c
compat-wireless-2010-04-26/net/mac80211/michael.c
compat-wireless-2010-04-26/net/mac80211/michael.h
compat-wireless-2010-04-26/net/mac80211/mlme.c
compat-wireless-2010-04-26/net/mac80211/offchannel.c
compat-wireless-2010-04-26/net/mac80211/pm.c
compat-wireless-2010-04-26/net/mac80211/rate.c
compat-wireless-2010-04-26/net/mac80211/rate.h
compat-wireless-2010-04-26/net/mac80211/rc80211_minstrel.c
compat-wireless-2010-04-26/net/mac80211/rc80211_minstrel_debugfs.c
compat-wireless-2010-04-26/net/mac80211/rc80211_minstrel.h
compat-wireless-2010-04-26/net/mac80211/rc80211_pid_algo.c
compat-wireless-2010-04-26/net/mac80211/rc80211_pid_debugfs.c
compat-wireless-2010-04-26/net/mac80211/rc80211_pid.h
compat-wireless-2010-04-26/net/mac80211/rx.c
compat-wireless-2010-04-26/net/mac80211/scan.c
compat-wireless-2010-04-26/net/mac80211/spectmgmt.c
compat-wireless-2010-04-26/net/mac80211/sta_info.c
compat-wireless-2010-04-26/net/mac80211/sta_info.h
compat-wireless-2010-04-26/net/mac80211/status.c
compat-wireless-2010-04-26/net/mac80211/tkip.c
compat-wireless-2010-04-26/net/mac80211/tkip.h
compat-wireless-2010-04-26/net/mac80211/tx.c
compat-wireless-2010-04-26/net/mac80211/util.c
compat-wireless-2010-04-26/net/mac80211/wep.c
compat-wireless-2010-04-26/net/mac80211/wep.h
compat-wireless-2010-04-26/net/mac80211/wme.c
compat-wireless-2010-04-26/net/mac80211/wme.h
compat-wireless-2010-04-26/net/mac80211/work.c
compat-wireless-2010-04-26/net/mac80211/wpa.c
compat-wireless-2010-04-26/net/mac80211/wpa.h
compat-wireless-2010-04-26/net/mac80211/Makefile
compat-wireless-2010-04-26/net/wireless/
compat-wireless-2010-04-26/net/wireless/chan.c
compat-wireless-2010-04-26/net/wireless/core.c
compat-wireless-2010-04-26/net/wireless/core.h
compat-wireless-2010-04-26/net/wireless/debugfs.c
compat-wireless-2010-04-26/net/wireless/debugfs.h
compat-wireless-2010-04-26/net/wireless/ethtool.c
compat-wireless-2010-04-26/net/wireless/ethtool.h
compat-wireless-2010-04-26/net/wireless/ibss.c
compat-wireless-2010-04-26/net/wireless/lib80211.c
compat-wireless-2010-04-26/net/wireless/lib80211_crypt_ccmp.c
compat-wireless-2010-04-26/net/wireless/lib80211_crypt_tkip.c
compat-wireless-2010-04-26/net/wireless/lib80211_crypt_wep.c
compat-wireless-2010-04-26/net/wireless/mlme.c
compat-wireless-2010-04-26/net/wireless/nl80211.c
compat-wireless-2010-04-26/net/wireless/nl80211.h
compat-wireless-2010-04-26/net/wireless/radiotap.c
compat-wireless-2010-04-26/net/wireless/reg.c
compat-wireless-2010-04-26/net/wireless/regdb.h
compat-wireless-2010-04-26/net/wireless/reg.h
compat-wireless-2010-04-26/net/wireless/scan.c
compat-wireless-2010-04-26/net/wireless/sme.c
compat-wireless-2010-04-26/net/wireless/sysfs.c
compat-wireless-2010-04-26/net/wireless/sysfs.h
compat-wireless-2010-04-26/net/wireless/util.c
compat-wireless-2010-04-26/net/wireless/wext-compat.c
compat-wireless-2010-04-26/net/wireless/wext-compat.h
compat-wireless-2010-04-26/net/wireless/wext-core.c
compat-wireless-2010-04-26/net/wireless/wext-priv.c
compat-wireless-2010-04-26/net/wireless/wext-proc.c
compat-wireless-2010-04-26/net/wireless/wext-sme.c
compat-wireless-2010-04-26/net/wireless/wext-spy.c
compat-wireless-2010-04-26/net/wireless/Makefile
compat-wireless-2010-04-26/net/rfkill/
compat-wireless-2010-04-26/net/rfkill/core.c
compat-wireless-2010-04-26/net/rfkill/input.c
compat-wireless-2010-04-26/net/rfkill/rfkill.h
compat-wireless-2010-04-26/net/rfkill/Makefile
compat-wireless-2010-04-26/net/bluetooth/
compat-wireless-2010-04-26/net/bluetooth/af_bluetooth.c
compat-wireless-2010-04-26/net/bluetooth/hci_conn.c
compat-wireless-2010-04-26/net/bluetooth/hci_core.c
compat-wireless-2010-04-26/net/bluetooth/hci_event.c
compat-wireless-2010-04-26/net/bluetooth/hci_sock.c
compat-wireless-2010-04-26/net/bluetooth/hci_sysfs.c
compat-wireless-2010-04-26/net/bluetooth/l2cap.c
compat-wireless-2010-04-26/net/bluetooth/lib.c
compat-wireless-2010-04-26/net/bluetooth/sco.c
compat-wireless-2010-04-26/net/bluetooth/Makefile
compat-wireless-2010-04-26/net/bluetooth/bnep/
compat-wireless-2010-04-26/net/bluetooth/bnep/bnep.h
compat-wireless-2010-04-26/net/bluetooth/bnep/core.c
compat-wireless-2010-04-26/net/bluetooth/bnep/netdev.c
compat-wireless-2010-04-26/net/bluetooth/bnep/sock.c
compat-wireless-2010-04-26/net/bluetooth/bnep/Makefile
compat-wireless-2010-04-26/net/bluetooth/cmtp/
compat-wireless-2010-04-26/net/bluetooth/cmtp/capi.c
compat-wireless-2010-04-26/net/bluetooth/cmtp/cmtp.h
compat-wireless-2010-04-26/net/bluetooth/cmtp/core.c
compat-wireless-2010-04-26/net/bluetooth/cmtp/sock.c
compat-wireless-2010-04-26/net/bluetooth/cmtp/Makefile
compat-wireless-2010-04-26/net/bluetooth/rfcomm/
compat-wireless-2010-04-26/net/bluetooth/rfcomm/core.c
compat-wireless-2010-04-26/net/bluetooth/rfcomm/sock.c
compat-wireless-2010-04-26/net/bluetooth/rfcomm/tty.c
compat-wireless-2010-04-26/net/bluetooth/rfcomm/Makefile
compat-wireless-2010-04-26/net/bluetooth/hidp/
compat-wireless-2010-04-26/net/bluetooth/hidp/core.c
compat-wireless-2010-04-26/net/bluetooth/hidp/hidp.h
compat-wireless-2010-04-26/net/bluetooth/hidp/sock.c
compat-wireless-2010-04-26/net/bluetooth/hidp/Makefile
compat-wireless-2010-04-26/drivers/
compat-wireless-2010-04-26/drivers/ssb/
compat-wireless-2010-04-26/drivers/ssb/b43_pci_bridge.c
compat-wireless-2010-04-26/drivers/ssb/driver_chipcommon.c
compat-wireless-2010-04-26/drivers/ssb/driver_chipcommon_pmu.c
compat-wireless-2010-04-26/drivers/ssb/driver_extif.c
compat-wireless-2010-04-26/drivers/ssb/driver_gige.c
compat-wireless-2010-04-26/drivers/ssb/driver_mipscore.c
compat-wireless-2010-04-26/drivers/ssb/driver_pcicore.c
compat-wireless-2010-04-26/drivers/ssb/embedded.c
compat-wireless-2010-04-26/drivers/ssb/main.c
compat-wireless-2010-04-26/drivers/ssb/pci.c
compat-wireless-2010-04-26/drivers/ssb/pcihost_wrapper.c
compat-wireless-2010-04-26/drivers/ssb/pcmcia.c
compat-wireless-2010-04-26/drivers/ssb/scan.c
compat-wireless-2010-04-26/drivers/ssb/sdio.c
compat-wireless-2010-04-26/drivers/ssb/sprom.c
compat-wireless-2010-04-26/drivers/ssb/ssb_private.h
compat-wireless-2010-04-26/drivers/ssb/Makefile
compat-wireless-2010-04-26/drivers/net/
compat-wireless-2010-04-26/drivers/net/usb/
compat-wireless-2010-04-26/drivers/net/usb/Makefile
compat-wireless-2010-04-26/drivers/net/usb/rndis_host.c
compat-wireless-2010-04-26/drivers/net/usb/cdc_ether.c
compat-wireless-2010-04-26/drivers/net/usb/usbnet.c
compat-wireless-2010-04-26/drivers/net/wireless/
compat-wireless-2010-04-26/drivers/net/wireless/ath/
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/debug.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/debug.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/hw.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/main.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/regd.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/regd_common.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/regd.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/reg.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/ar9170.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/cmd.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/cmd.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/hw.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/led.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/mac.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/main.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/phy.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/usb.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/usb.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ar9170/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/ani.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/ani.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/ath5k.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/attach.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/base.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/base.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/caps.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/debug.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/debug.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/desc.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/desc.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/dma.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/eeprom.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/gpio.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/initvals.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/led.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/pcu.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/phy.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/qcu.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/reg.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/reset.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/rfbuffer.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/rfgain.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/rfkill.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath5k/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ahb.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ani.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ani.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/beacon.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/btcoex.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/btcoex.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/calib.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/calib.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/common.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/common.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/debug.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/debug.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_4k.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_9287.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_def.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/gpio.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hif_usb.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hif_usb.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_beacon.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_init.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_main.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_txrx.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_hst.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_hst.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hw.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hw.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/init.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/initvals.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/mac.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/mac.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/main.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/pci.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/phy.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/phy.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/rc.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/rc.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/recv.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/reg.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/virtual.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/wmi.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/wmi.h
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/xmit.c
compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/b43/
compat-wireless-2010-04-26/drivers/net/wireless/b43/b43.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/debugfs.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/dma.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/dma.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/leds.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/leds.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/lo.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/lo.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/main.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/main.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/pcmcia.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/pcmcia.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_a.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_a.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_common.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_common.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_g.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_g.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_lp.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_lp.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_n.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/phy_n.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/pio.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/pio.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/rfkill.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/rfkill.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/sdio.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/sdio.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/sysfs.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/sysfs.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables_lpphy.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables_lpphy.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables_nphy.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/tables_nphy.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/wa.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/wa.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/xmit.c
compat-wireless-2010-04-26/drivers/net/wireless/b43/xmit.h
compat-wireless-2010-04-26/drivers/net/wireless/b43/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/b43legacy.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/debugfs.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/dma.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/dma.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/ilt.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/ilt.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/leds.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/leds.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/main.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/main.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/phy.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/phy.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/pio.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/pio.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/radio.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/radio.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/rfkill.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/rfkill.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/sysfs.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/sysfs.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/xmit.c
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/xmit.h
compat-wireless-2010-04-26/drivers/net/wireless/b43legacy/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-1000.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl3945-base.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945-fh.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945-hw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945-led.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945-led.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-3945-rs.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-4965.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-4965-hw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-5000.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-5000-hw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-6000.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-6000-hw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-hcmd.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-hw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-ict.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-led.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-led.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-lib.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-rs.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-rs.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-tx.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-agn-ucode.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-calib.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-calib.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-commands.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-core.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-core.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-csr.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-debug.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-dev.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-devtrace.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-devtrace.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-eeprom.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-fh.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-hcmd.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-helpers.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-io.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-led.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-led.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-power.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-power.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-prph.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-rx.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-scan.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-spectrum.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-sta.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-sta.h
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/iwl-tx.c
compat-wireless-2010-04-26/drivers/net/wireless/iwlwifi/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2400pci.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2400pci.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2500pci.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2500pci.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2500usb.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2500usb.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800lib.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800lib.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800pci.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800pci.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800usb.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2800usb.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00config.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00crypto.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00debug.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00debug.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00dev.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00dump.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00firmware.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00ht.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00leds.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00leds.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00lib.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00link.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00mac.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00pci.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00pci.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00queue.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00queue.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00reg.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00soc.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00soc.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00usb.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt2x00usb.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt61pci.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt61pci.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt73usb.c
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/rt73usb.h
compat-wireless-2010-04-26/drivers/net/wireless/rt2x00/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_chip.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_chip.h
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_def.h
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_mac.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_mac.h
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf_al2230.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf_al7230b.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf.h
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf_rf2959.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_rf_uw2453.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_usb.c
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/zd_usb.h
compat-wireless-2010-04-26/drivers/net/wireless/zd1211rw/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/libertas/
compat-wireless-2010-04-26/drivers/net/wireless/libertas/assoc.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/assoc.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/cfg.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/cfg.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/cmd.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/cmd.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/cmdresp.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/debugfs.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/decl.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/defs.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/dev.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/ethtool.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/host.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_cs.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_sdio.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_sdio.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_spi.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_spi.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_usb.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/if_usb.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/main.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/mesh.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/mesh.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/radiotap.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/rx.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/scan.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/scan.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/tx.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/types.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/wext.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas/wext.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/p54/
compat-wireless-2010-04-26/drivers/net/wireless/p54/eeprom.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/fwio.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/led.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/lmac.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/main.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/net2280.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54pci.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54pci.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54spi.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54spi_eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54spi.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54usb.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/p54usb.h
compat-wireless-2010-04-26/drivers/net/wireless/p54/txrx.c
compat-wireless-2010-04-26/drivers/net/wireless/p54/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_dev.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_grf5101.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_grf5101.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_max2820.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_max2820.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_rtl8225.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_rtl8225.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_sa2400.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8180_sa2400.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_dev.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_leds.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_leds.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_rfkill.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_rfkill.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_rtl8225.c
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl8187_rtl8225.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/rtl818x.h
compat-wireless-2010-04-26/drivers/net/wireless/rtl818x/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/cmd.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/if_usb.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/if_usb.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/libertas_tf.h
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/main.c
compat-wireless-2010-04-26/drivers/net/wireless/libertas_tf/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/ipw2100.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/ipw2100.h
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/ipw2200.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/ipw2200.h
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw_geo.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw.h
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw_module.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw_rx.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw_tx.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/libipw_wx.c
compat-wireless-2010-04-26/drivers/net/wireless/ipw2x00/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_acx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_acx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_boot.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_boot.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_cmd.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_cmd.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_debugfs.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_event.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_event.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_init.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_init.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_io.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_io.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_main.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_ps.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_ps.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_reg.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_rx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_rx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_sdio.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_spi.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_spi.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_tx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1251_tx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_acx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_acx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_boot.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_boot.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_cmd.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_cmd.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_conf.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_debugfs.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_event.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_event.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_init.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_init.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_io.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_io.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_main.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_ps.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_ps.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_reg.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_rx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_rx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_sdio.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_spi.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_testmode.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_testmode.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_tx.c
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl1271_tx.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/wl12xx_80211.h
compat-wireless-2010-04-26/drivers/net/wireless/wl12xx/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/bus.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/cfg80211.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/cfg80211.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/commands.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/commands.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/debugfs.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/debug.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/eeprom.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/eeprom.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/fw.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/fw.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/hal.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/hal.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/iwm.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/lmac.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/main.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/netdev.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/rx.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/rx.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/sdio.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/sdio.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/trace.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/trace.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/tx.c
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/umac.h
compat-wireless-2010-04-26/drivers/net/wireless/iwmc3200wifi/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/airport.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/cfg.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/cfg.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/fw.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/fw.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hermes.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hermes_dld.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hermes_dld.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hermes.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hermes_rid.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hw.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/hw.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/main.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/main.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/mic.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/mic.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_cs.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_nortel.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_pci.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_pci.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_plx.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/orinoco_tmd.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/scan.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/scan.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/spectrum_cs.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/wext.c
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/wext.h
compat-wireless-2010-04-26/drivers/net/wireless/orinoco/Makefile
compat-wireless-2010-04-26/drivers/net/wireless/adm8211.c
compat-wireless-2010-04-26/drivers/net/wireless/adm8211.h
compat-wireless-2010-04-26/drivers/net/wireless/rndis_wlan.c
compat-wireless-2010-04-26/drivers/net/wireless/mac80211_hwsim.c
compat-wireless-2010-04-26/drivers/net/wireless/at76c50x-usb.c
compat-wireless-2010-04-26/drivers/net/wireless/at76c50x-usb.h
compat-wireless-2010-04-26/drivers/net/wireless/mwl8k.c
compat-wireless-2010-04-26/drivers/net/wireless/Makefile
compat-wireless-2010-04-26/drivers/net/atl1c/
compat-wireless-2010-04-26/drivers/net/atl1c/atl1c_ethtool.c
compat-wireless-2010-04-26/drivers/net/atl1c/atl1c.h
compat-wireless-2010-04-26/drivers/net/atl1c/atl1c_hw.c
compat-wireless-2010-04-26/drivers/net/atl1c/atl1c_hw.h
compat-wireless-2010-04-26/drivers/net/atl1c/atl1c_main.c
compat-wireless-2010-04-26/drivers/net/atl1c/Makefile
compat-wireless-2010-04-26/drivers/net/atl1e/
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e_ethtool.c
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e.h
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e_hw.c
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e_hw.h
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e_main.c
compat-wireless-2010-04-26/drivers/net/atl1e/atl1e_param.c
compat-wireless-2010-04-26/drivers/net/atl1e/Makefile
compat-wireless-2010-04-26/drivers/net/atlx/
compat-wireless-2010-04-26/drivers/net/atlx/atl1.c
compat-wireless-2010-04-26/drivers/net/atlx/atl1.h
compat-wireless-2010-04-26/drivers/net/atlx/atl2.c
compat-wireless-2010-04-26/drivers/net/atlx/atl2.h
compat-wireless-2010-04-26/drivers/net/atlx/atlx.c
compat-wireless-2010-04-26/drivers/net/atlx/atlx.h
compat-wireless-2010-04-26/drivers/net/atlx/Makefile
compat-wireless-2010-04-26/drivers/net/Makefile
compat-wireless-2010-04-26/drivers/net/b44.c
compat-wireless-2010-04-26/drivers/net/b44.h
compat-wireless-2010-04-26/drivers/bluetooth/
compat-wireless-2010-04-26/drivers/bluetooth/ath3k.c
compat-wireless-2010-04-26/drivers/bluetooth/bcm203x.c
compat-wireless-2010-04-26/drivers/bluetooth/bfusb.c
compat-wireless-2010-04-26/drivers/bluetooth/bluecard_cs.c
compat-wireless-2010-04-26/drivers/bluetooth/bpa10x.c
compat-wireless-2010-04-26/drivers/bluetooth/bt3c_cs.c
compat-wireless-2010-04-26/drivers/bluetooth/btmrvl_debugfs.c
compat-wireless-2010-04-26/drivers/bluetooth/btmrvl_drv.h
compat-wireless-2010-04-26/drivers/bluetooth/btmrvl_main.c
compat-wireless-2010-04-26/drivers/bluetooth/btmrvl_sdio.c
compat-wireless-2010-04-26/drivers/bluetooth/btmrvl_sdio.h
compat-wireless-2010-04-26/drivers/bluetooth/btsdio.c
compat-wireless-2010-04-26/drivers/bluetooth/btuart_cs.c
compat-wireless-2010-04-26/drivers/bluetooth/btusb.c
compat-wireless-2010-04-26/drivers/bluetooth/dtl1_cs.c
compat-wireless-2010-04-26/drivers/bluetooth/hci_bcsp.c
compat-wireless-2010-04-26/drivers/bluetooth/hci_h4.c
compat-wireless-2010-04-26/drivers/bluetooth/hci_ldisc.c
compat-wireless-2010-04-26/drivers/bluetooth/hci_ll.c
compat-wireless-2010-04-26/drivers/bluetooth/hci_uart.h
compat-wireless-2010-04-26/drivers/bluetooth/hci_vhci.c
compat-wireless-2010-04-26/drivers/bluetooth/Makefile
compat-wireless-2010-04-26/drivers/misc/
compat-wireless-2010-04-26/drivers/misc/eeprom/
compat-wireless-2010-04-26/drivers/misc/eeprom/eeprom_93cx6.c
compat-wireless-2010-04-26/drivers/misc/eeprom/Makefile
compat-wireless-2010-04-26/compat/
compat-wireless-2010-04-26/compat/compat-2.6.14.c
compat-wireless-2010-04-26/compat/compat-2.6.18.c
compat-wireless-2010-04-26/compat/compat-2.6.19.c
compat-wireless-2010-04-26/compat/compat-2.6.21.c
compat-wireless-2010-04-26/compat/compat-2.6.22.c
compat-wireless-2010-04-26/compat/compat-2.6.23.c
compat-wireless-2010-04-26/compat/compat-2.6.24.c
compat-wireless-2010-04-26/compat/compat-2.6.25.c
compat-wireless-2010-04-26/compat/compat-2.6.26.c
compat-wireless-2010-04-26/compat/compat-2.6.27.c
compat-wireless-2010-04-26/compat/compat-2.6.28.c
compat-wireless-2010-04-26/compat/compat-2.6.29.c
compat-wireless-2010-04-26/compat/compat-2.6.30.c
compat-wireless-2010-04-26/compat/compat-2.6.31.c
compat-wireless-2010-04-26/compat/compat-2.6.32.c
compat-wireless-2010-04-26/compat/compat-2.6.33.c
compat-wireless-2010-04-26/compat/main.c
compat-wireless-2010-04-26/compat/Makefile
compat-wireless-2010-04-26/compat/pm_qos_params.c
compat-wireless-2010-04-26/compat/compat_firmware_class.c
compat-wireless-2010-04-26/compat/scripts/
compat-wireless-2010-04-26/compat/scripts/compat_firmware_install
compat-wireless-2010-04-26/enable-older-kernels/
compat-wireless-2010-04-26/enable-older-kernels/README
compat-wireless-2010-04-26/enable-older-kernels/enable-2.6.21.patch
compat-wireless-2010-04-26/enable-older-kernels/enable-2.6.22.patch
compat-wireless-2010-04-26/enable-older-kernels/enable-2.6.23.patch
compat-wireless-2010-04-26/enable-older-kernels/enable-2.6.24.patch
compat-wireless-2010-04-26/udev/
compat-wireless-2010-04-26/udev/50-compat_firmware.rules
compat-wireless-2010-04-26/udev/compat_firmware.sh
compat-wireless-2010-04-26/udev/ubuntu/
compat-wireless-2010-04-26/udev/ubuntu/50-compat_firmware.rules
compat-wireless-2010-04-26/udev/ubuntu/compat_firmware.sh
compat-wireless-2010-04-26/compat-release
compat-wireless-2010-04-26/git-describe
compat-wireless-2010-04-26/master-tag
compat-wireless-2010-04-26/linux-next-cherry-picks/
compat-wireless-2010-04-26/linux-next-cherry-picks/README
``````
asus@Asus:~/Downloads/compat-wireless-2010-04-26$ ./scripts/driver-select ath9k
``````

[01;33mProcessing new driver-select request...[00m
Backing up makefile: [36mMakefile.bk[00m
Backup exists: [36mMakefile.bk[00m
Backing up makefile: [36mdrivers/net/wireless/Makefile.bk[00m
Backing up makefile: [36mdrivers/net/wireless/ath/Makefile.bk[00m
Backing up makefile: [36mnet/wireless/Makefile.bk[00m
Backing up makefile: [36mdrivers/net/Makefile.bk[00m
Backing up makefile: [36mdrivers/ssb/Makefile.bk[00m
Backing up makefile: [36mdrivers/misc/eeprom/Makefile.bk[00m
``````
asus@Asus:~/Downloads/compat-wireless-2010-04-26$ make
``````
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-21-generic/build M=/home/asus/Downloads/compat-wireless-2010-04-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/compat/built-in.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/main.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat-2.6.32.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat-2.6.33.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat_firmware_class.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/built-in.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/main.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/regd.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/hw.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/built-in.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/beacon.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/gpio.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/init.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/main.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/recv.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/xmit.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/virtual.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/rc.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/pci.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/common.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_hst.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hif_usb.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/wmi.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_txrx.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_main.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_beacon.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/htc_drv_init.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/hw.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_def.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_4k.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/eeprom_9287.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/calib.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ani.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/phy.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/btcoex.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/mac.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_hw.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_common.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_htc.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/built-in.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/main.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/status.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/sta_info.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/wep.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/wpa.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/scan.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/offchannel.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/ht.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/agg-tx.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/agg-rx.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/ibss.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mlme.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/work.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/iface.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rate.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/michael.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/tkip.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/aes_ccm.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/aes_cmac.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/cfg.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rx.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/spectmgmt.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/tx.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/key.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/util.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/wme.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/event.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/led.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/debugfs.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/debugfs_sta.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/debugfs_netdev.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/debugfs_key.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mesh.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mesh_plink.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mesh_hwmp.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/pm.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/rc80211_minstrel_debugfs.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mac80211.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/net/rfkill/built-in.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/built-in.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/core.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/sysfs.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/radiotap.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/util.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/reg.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/scan.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/nl80211.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/mlme.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/ibss.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/sme.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/chan.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/ethtool.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/debugfs.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/wext-compat.o
  CC [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/wext-sme.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/cfg80211.o
  LD      /home/asus/Downloads/compat-wireless-2010-04-26/built-in.o
  Building modules, stage 2.
  MODPOST 9 modules
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat_firmware_class.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat_firmware_class.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_common.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_htc.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_hw.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mac80211.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mac80211.ko
  CC      /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/cfg80211.mod.o
  LD [M]  /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
``````
asus@Asus:~/Downloads/compat-wireless-2010-04-26$ sudo make install
``````

Your old wireless subsystem modules were left intact:

updates/cw/mac80211.ko
updates/cw/cfg80211.ko
updates/cw/lib80211.ko
updates/cw/adm8211.ko
updates/cw/ar9170usb.ko
updates/cw/at76c50x-usb.ko
updates/cw/ath.ko
updates/cw/ath5k.ko
updates/cw/ath9k.ko
updates/cw/b43.ko
updates/cw/b43legacy.ko
updates/cw/b44.ko
updates/cw/cdc_ether.ko
updates/cw/eeprom_93cx6.ko
updates/cw/ipw2100.ko
updates/cw/ipw2200.ko
updates/cw/iwl3945.ko
updates/cw/iwlagn.ko
updates/cw/iwlcore.ko
updates/cw/lib80211_crypt_ccmp.ko
updates/cw/lib80211_crypt_tkip.ko
updates/cw/lib80211_crypt_wep.ko
updates/cw/libertas.ko
updates/cw/libertas_cs.ko
updates/cw/libertas_sdio.ko
updates/cw/libertas_spi.ko
updates/cw/libertas_tf.ko
updates/cw/libertas_tf_usb.ko
updates/cw/libipw.ko
updates/cw/mac80211_hwsim.ko
updates/cw/mwl8k.ko
updates/cw/p54common.ko
updates/cw/p54pci.ko
updates/cw/p54spi.ko
updates/cw/p54usb.ko
updates/cw/rndis_host.ko
updates/cw/rndis_wlan.ko
updates/cw/rt2400pci.ko
updates/cw/rt2500pci.ko
updates/cw/rt2500usb.ko
updates/cw/rt2x00lib.ko
updates/cw/rt2x00pci.ko
updates/cw/rt2x00usb.ko
updates/cw/rt61pci.ko
updates/cw/rt73usb.ko
updates/cw/rtl8180.ko
updates/cw/rtl8187.ko
updates/cw/ssb.ko
updates/cw/usb8xxx.ko
updates/cw/usbnet.ko
updates/cw/zd1211rw.ko

Your old bluetooth subsystem modules were left intact:

kernel/net/bluetooth/hidp/hidp.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/btusb.ko

make -C /lib/modules/2.6.31-21-generic/build M=/home/asus/Downloads/compat-wireless-2010-04-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  Building modules, stage 2.
  MODPOST 9 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make -C /lib/modules/2.6.31-21-generic/build M=/home/asus/Downloads/compat-wireless-2010-04-26 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/compat/compat_firmware_class.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/net/mac80211/mac80211.ko
  INSTALL /home/asus/Downloads/compat-wireless-2010-04-26/net/wireless/cfg80211.ko
  DEPMOD  2.6.31-21-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
Cannot find /lib/modules/2.6.31-wl
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/cw/mac80211.ko
updates/cw/cfg80211.ko
updates/cw/lib80211.ko
updates/cw/adm8211.ko
updates/cw/ar9170usb.ko
updates/cw/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/cw/ath5k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/cw/b43.ko
updates/cw/b43legacy.ko
updates/cw/b44.ko
updates/cw/cdc_ether.ko
updates/cw/eeprom_93cx6.ko
updates/cw/ipw2100.ko
updates/cw/ipw2200.ko
updates/cw/iwl3945.ko
updates/cw/iwlagn.ko
updates/cw/iwlcore.ko
updates/cw/lib80211_crypt_ccmp.ko
updates/cw/lib80211_crypt_tkip.ko
updates/cw/lib80211_crypt_wep.ko
updates/cw/libertas.ko
updates/cw/libertas_cs.ko
updates/cw/libertas_sdio.ko
updates/cw/libertas_spi.ko
updates/cw/libertas_tf.ko
updates/cw/libertas_tf_usb.ko
updates/cw/libipw.ko
updates/cw/mac80211_hwsim.ko
updates/cw/mwl8k.ko
updates/cw/p54common.ko
updates/cw/p54pci.ko
updates/cw/p54spi.ko
updates/cw/p54usb.ko
updates/cw/rndis_host.ko
updates/cw/rndis_wlan.ko
updates/cw/rt2400pci.ko
updates/cw/rt2500pci.ko
updates/cw/rt2500usb.ko
updates/cw/rt2x00lib.ko
updates/cw/rt2x00pci.ko
updates/cw/rt2x00usb.ko
updates/cw/rt61pci.ko
updates/cw/rt73usb.ko
updates/cw/rtl8180.ko
updates/cw/rtl8187.ko
updates/cw/ssb.ko
updates/cw/usb8xxx.ko
updates/cw/usbnet.ko
updates/cw/zd1211rw.ko

Currently detected bluetooth subsystem modules:

kernel/net/bluetooth/hidp/hidp.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/btusb.ko

Now run:

sudo make unload to unload both wireless and bluetooth modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

And then load the wireless or bluetooth module you need. If unsure reboot.
Alternatively use sudo make load/wlload/btload to load modules

```

```
asus@Asus:~/Downloads/compat-wireless-2010-04-26$ sudo make unload
```

```
Stoping bluetooth service..
 * bluetooth is not running
Unloading ath9k...
Unloading rtl8187...
```

```
asus@Asus:~/Downloads/compat-wireless-2010-04-26$ sudo modprobe ath9k
```

```
WARNING: Error inserting ath9k_hw (/lib/modules/2.6.31-21-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/2.6.31-21-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-21-generic/updates/cw/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-21-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by dionblundell on 2010-05-05
@khunter1

I suspect the issue is that your 1001 has a different chipset, the clue is the line:
Unloading rtl8187...

I suspect that you are actually using the module rtl8187 not ath9k

Try this instead:
```
cd ~/Downloads/compat-wireless-2010-04-18
./scripts/driver-select **rtl8187**
make
sudo make install
sudo make unload
sudo modprobe ath9k

```Hope this might help.

---

### Post by khunter1 on 2010-05-05
> **dionblundell said:**
> @khunter1

I suspect the issue is that your 1001 has a different chipset, the clue is the line:
Unloading rtl8187...

I suspect that you are actually using the module rtl8187 not ath9k

Try this instead:
```
cd ~/Downloads/compat-wireless-2010-04-18
./scripts/driver-select **rtl8187**
make
sudo make install
sudo make unload
sudo modprobe ath9k

```Hope this might help.

rtl8187 is my USB wireless dongle...

You want me to install the driver rtl8187, which is how I am connected now to the internet?

---

### Post by -jay- on 2010-05-05
the latest kernel has my wireless working no need to use the xp drivers i used the kernels from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/")

---

### Post by dionblundell on 2010-05-05
Now that I did not know.
I'm going to give that a go on my 1005PE and see if it is all peace-and-light.

---

### Post by pdc on 2010-05-06
hi -jay-

for the benefit of everyone else, can you detail how you installed the 2.6.34 kernel ................

---

### Post by dionblundell on 2010-05-06
I used to use the development version of 2.6.33, but it would only work with less than 2GB of ram, so I gave it up. I never thought to see if there was a newer kernel.

What you need to do is goto:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

click into the newest folder, which at this stage is:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/")

You need to download:
1) the image
     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb")
2) the headers (assuming you do the odd bit of compiling)
     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb")

     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb")

Then start a shell, and do the following:
```
cd ~/Downloads
sudo dpkg -i linux*.deb

```

---

### Post by dionblundell on 2010-05-06
I used to use the development version of 2.6.33, but it would only work with less than 2GB of ram, so I gave it up. I never thought to see if there was a newer kernel.

What you need to do is goto:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

click into the newest folder, which at this stage is:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/")

You need to download:
1) the image
     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb")
2) the headers (assuming you do the odd bit of compiling)
     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb")

     [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb")

Then start a shell, and do the following:
```
cd ~/Downloads
sudo dpkg -i linux*.deb

```

---

### Post by Flens on 2010-05-12
Hi, I'm new to linux/ubuntu and have just installed Easy Peasy 1.6 on my netbook ASUS EEE PC 1001P.
I can't connect to internet by wlan. I followed the steps dionblundell posted but I got an error when I type "make". 

```
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
        Subsystem: ASUSTeK Computer Inc. Device 838a
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atl1c
        Kernel modules: atl1c

02:00.0 Network controller: Atheros Communications Inc. Device 002c (rev 01)
        Subsystem: Device 1a3b:1112
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

./scripts/driver-select ath9k
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/net/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
philipp@philipp-laptop:~/Downloads/compat-wireless-2010-05-11$ make
make: gcc: Command not found
make: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
make -C /lib/modules/2.6.32-22-generic/build M=/home/philipp/Downloads/compat-wireless-2010-05-11 modules
/usr/src/linux-headers-2.6.32-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  LD      /home/philipp/Downloads/compat-wireless-2010-05-11/compat/built-in.o
/bin/sh: ar: not found
make[3]: *** [/home/philipp/Downloads/compat-wireless-2010-05-11/compat/built-in.o] Error 127
make[2]: *** [/home/philipp/Downloads/compat-wireless-2010-05-11/compat] Error 2
make[1]: *** [_module_/home/philipp/Downloads/compat-wireless-2010-05-11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2


```

---

### Post by pdc on 2010-05-13
> **make: gcc: Command not found**

gcc is a GNU c compiler: you need it:

go to synaptic: programme installer; install gcc;

have another go with it installed

---

### Post by dionblundell on 2010-05-13
Sorry, my post assumed you had built things before.
If you do:
```
sudo apt-get install build-essential
```
it will install what you need.

---

### Post by Flens on 2010-05-14
Thank you! Now it works fine :)

---

### Post by dionblundell on 2010-05-23
@khunter1

Hi Khunter1,
I was wondering if you managed to get wireless working, I just re-read the post and realised that I didn't answer your question. Sorry.

I didn't realise that you were acessing the internet through a usb wireless dongle, so no, recompiling something that works is not a good idea as I inadvertantly suggested.

Maybe the compiled module might load when you reboot?
I suspect that the unload/load script is a little too simple to deal with multiple wireless adapters. Let me know if it works. The module that should load is ath9k

Hope this helps, and sorry for the tardy reply.

---

### Post by khunter1 on 2010-05-23
> **dionblundell said:**
> @khunter1

Hi Khunter1,
I was wondering if you managed to get wireless working, I just re-read the post and realised that I didn't answer your question. Sorry.

I didn't realise that you were acessing the internet through a usb wireless dongle, so no, recompiling something that works is not a good idea as I inadvertantly suggested.

Maybe the compiled module might load when you reboot?
I suspect that the unload/load script is a little too simple to deal with multiple wireless adapters. Let me know if it works. The module that should load is ath9k

Hope this helps, and sorry for the tardy reply.

I tried rebooting. Rebooting doesn't work.

---

### Post by diesel_here on 2010-05-26
Hi Everyone

I read this and other forums for information just before I purchased my 1001p, it  came with XP & for information purposes I did the following:

I wanted to avoid altering any anything from a stock install if  possible.

Made XP partition 10gb, deleted restore partition. - if xp dies, i'm not  fussed (I only kept it for old artwork files I may need to convert).
Iinstalled Kubuntu Lucid 64bit edition from usb drive (did not realise  you hit escape to boot from usb)
Install went great, no problems.  Root 10gb, swap 1gb, home rest of  available space.
Then updated install & installed kubuntu-netbook & any updates.
After install Wifi did not work - as everyone knows.  Easily fixed -  install the kernel-rc candidate kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc7-lucid/")

Simply by clicking on the download in dolphin & using the package  installer.

I did use the script alteration for for grub as described in this thread  to allow the screen brightness to be more usable.

Installed other packages as required, inkscape, digikam, forefox,  cairo-dock, etc.

Conclusion:
I have Kubuntu 64bit Lucid working with only one problem, video.  My  vids play with audio only in dragon player but if I import to Kino they  play with no problems.  Also the web cam in skype shows a blank screen  although the camera led illuminates, tried with an external web cam that  works fine on my desktop kubuntu with the same result, again the web  cams both work in Kopete but it will not connect with Skype.
I have cairo working with desktop effects in compiz working, no problems  at all & very smooth.  Looks great, everyone I show loves it. I put  a cool desktop background & altered my colours to the dark theme -  wonton I think.  Been playing so much & changing things to alter the  look & feel.  But seriously - all works great, new kernel gave me  wirless.

Good look & enjoy this great little netbook.

---

### Post by misGnomer on 2010-05-26
Another success story:

Got a 1001P-MU17 (I reckon) the other day, booted from SD-based Lucid UNE (after changing boot priority in BIOS), wiped the whole disk before I'd seen a single MS logo, installed Lucid and, while hooked to an ethernet cable, let it run the updates (~70MB).

WLAN interface didn't show up... so I grabbed the "build-essential" package and proceeded to build current ath9k drivers as mentioned by the [Kiwi Dion in msg #16]("http://ubuntuforums.org/showpost.php?p=9142146&postcount=16").

*Built up-to-date ath9k driver module from the compat-wireless-2010-05-24 tarball (no build errors) and installed it. The WLAN interface came alive and works well, with WPA2 and all.*

Since it might be necessary to rebuild the ath9k module after each upcoming kernel update (unless Ubuntu devs get to include up-to-date ath9k in their new builds!), I'd recommend users of the build method to download recent compat-wireless tarball or two (and maybe keep a copy of the current working one) before rebooting new kernels in case one driver release causes build errors.

Alternatively, having an Ubuntu-signed PPA repository with up-to-date drivers (pre-)compiled for any new kernel releases would really make keeping current and functional practically transparent to users. In fact, this is how driver updates should be made available: No PPA subscription for module updates needed if the driver is mature and in kernel, occasional automatic updates built against new kernel releases when the driver works but is still under regular development (features, stability, power mgmt etc.) and perhaps even daily PPA for the few souls desperate or gracious enough to test each new daily build from the horse's mouth (aka daily source releases).

Cheers all. =D>

---

### Post by dionblundell on 2010-05-30
@misGnomer

I agree, a repository for ath9k would be nice. I have no idea how to do that though.

You're right about recompiling with a kernel update, for example my modules for 2.6.32.21 will not work on 2.6.32.22, so I had to recompile. It take about 5 minutes on my ASUS 1005PE.

---

### Post by mathew42 on 2010-07-12
[Bug 521967]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/+bug/521967") on launchpad, pointed me in the correct direction of installing linux-backports-modules-generic.

A reboot and it fixed it for me.:popcorn:

---

