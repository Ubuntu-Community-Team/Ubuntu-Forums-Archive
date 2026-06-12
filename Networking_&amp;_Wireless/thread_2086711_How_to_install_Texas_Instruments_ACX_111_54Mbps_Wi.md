---
title: "How to install Texas Instruments ACX 111 54Mbps Wireless Interface"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by MXzor on 2012-11-21
Hi, recently i install ubuntu-server (32bits) last version and after i installed to xubuntu-desktop, i have Texas Instruments ACX 111 54Mbps Wireless Interface for wireless network,but unfortunally didn't found in the system, i have been trying to install it but nothing, someone can help me?i can give more information...
Best Regards for all:)

---

### Post by ahallubuntu on 2012-11-21
I have one of these cards in a box somewhere - had it for years, never found an easy way to make it work in Ubuntu.  I'll probably just give it away.  I have other wireless cards that are faster and can be purchased for under $10 USD anyway (USB dongle).

---

### Post by varunendra on 2012-11-22
Welcome to the forums *MXzor* !
> **MXzor said:**
> ..i have Texas Instruments ACX 111 54Mbps Wireless Interface for wireless network,but unfortunally didn't found in the system..
Since *ahallubuntu* just shared his 'first-hand' experience with the card (and he is an experienced user), maybe I can't (or shouldn't) give you much hope. But let's just take a few shots before throwing it away :)

Let's see if it is detected at all, please post outputs of -
```
lspci -nnk | grep -iA2 net
```

If it is a USB dongle, then-
```
lsusb
```

---

### Post by MXzor on 2012-11-22
> **varunendra said:**
> Welcome to the forums *MXzor* !

Since *ahallubuntu* just shared his 'first-hand' experience with the card (and he is an experienced user), maybe I can't (or shouldn't) give you much hope. But let's just take a few shots before throwing it away :)

Let's see if it is detected at all, please post outputs of -
```
lspci -nnk | grep -iA2 net
```

If it is a USB dongle, then-
```
lsusb
```

Thanks Varunendra :P

Let`s see the outputs:

```
$ lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)
	Subsystem: Hewlett-Packard Company Device [103c:1296]
	Kernel driver in use: e100
--
03:09.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
	Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter [1186:3b04]
03:0b.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k HSFi Modem [14f1:2f00] (rev 01)
```


```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

thanks in advance!

---

### Post by ahallubuntu on 2012-11-22
> **varunendra said:**
> Since *ahallubuntu* just shared his 'first-hand' experience with the card (and he is an experienced user), maybe I can't (or shouldn't) give you much hope. But let's just take a few shots before throwing it away :)

I'm not saying it's impossible to get this card working.  I'm just saying, I couldn't find an easy way, and it's a very old card/chipset.  If there isn't built-in kernel support by now there never will be.

Ndiswrapper is probably the best approach.

---

### Post by varunendra on 2012-11-22
> **ahallubuntu said:**
> I'm not saying it's impossible to get this card working.  I'm just saying, I couldn't find an easy way, and it's a very old card/chipset..I was actually trying to just emphasize your point that maybe the card is not worth putting too much effort in it. If you felt anything bad about my comment, please take it as my lack of command over English *(although I try to be extra-careful with that**[I] for the same reason*, but sometimes..)[/I].

@MXzor,
I found a native kernel driver that seems to be meant specifically for your device, not sure why it wasn't loaded automatically, so let's just try and see if it works at all. Please try -
```
sudo modprobe -v wl1251_sdio
```
And see if the wireless gets enabled.

If not, please post back results from instructions in this post : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

I also found a driver on sourceforge.net ([http://sourceforge.net/projects/acx100/](http://sourceforge.net/projects/acx100/)) but couldn't compile it myself, so let's just hope the above one works.

---

### Post by MXzor on 2012-11-22
> **varunendra said:**
> I was actually trying to just emphasize your point that maybe the card is not worth putting too much effort in it. If you felt anything bad about my comment, please take it as my lack of command over English *(although I try to be extra-careful with that**[I] for the same reason*, but sometimes..)[/I].

@MXzor,
I found a native kernel driver that seems to be meant specifically for your device, not sure why it wasn't loaded automatically, so let's just try and see if it works at all. Please try -
```
sudo modprobe -v wl1251_sdio
```
And see if the wireless gets enabled.

If not, please post back results from instructions in this post : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

I also found a driver on sourceforge.net ([http://sourceforge.net/projects/acx100/](http://sourceforge.net/projects/acx100/)) but couldn't compile it myself, so let's just hope the above one works.

i try the first command but i think dont work, so i try the second and here is:

[https://www.dropbox.com/s/xcfoz0sa1dwe1p1/netinfo.txt](https://www.dropbox.com/s/xcfoz0sa1dwe1p1/netinfo.txt)

thanks for help :)

---

### Post by chili555 on 2012-11-22
> I couldn't find an easy way, and it's a very old card/chipset. If there isn't built-in kernel support by now there never will be.

*Ndiswrapper is probably the best approach*.The doctor concurs.

Subscribed.

---

### Post by varunendra on 2012-11-23
Hi,
Sorry for being so late, I wasn't ready with a useful reply. Hopefully, now I am.

After doing a lot of searching on the net, it seems that indeed we may have to resort to ndiswrapper. Although there are references to the *wl1251* driver that suggest it works with this card, but needs a firmware (**wl1251-fw.bin**) which is proprietary, and so not included by default in Ubuntu. Almost all the external links to it I found were dead (maybe because it is really too old). However, I did find a link which still works.

So before trying ndiswrapper, I want to give the native driver one more shot (or two ?). Please try this -

[LIST=1]
[*]download the "ti-wl1251-firmware_0.4.tar.bz2" file from this page : [https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900](https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900)[]("https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900")  (Here's the [direct link]("https://api.pub.meego.com/public/source/CE:Adaptation:N900/ti-wl1251-firmware/ti-wl1251-firmware_0.4.tar.bz2?rev=3a5bcff15024a50be09a4ed04eafab64&") to avoid confusion)
[*]Extract the **wl1251-fw.bin** file from the archive to your desktop.
[*]Copy the file to your **/lib/firmware** directory by - ```
sudo cp ~/Desktop/wl1251-fw.bin /lib/firmware/
```
[*]Now reload the driver -
[/LIST]
```
sudo modprobe -rfv wl1251_sdio
sudo modprobe -v wl1251_sdio
```
And see if the adapter becomes active. If not, please post output of -
```
dmesg | grep 1251
```


Interestingly, while digging up the firmware, I found that the same driver set (wl1251_sdio, wl1251) included in kernel 2.6.32-38-generic (which is part of 10.04.4 - 32 bit iso) does not ask for any firmware (verified by *modinfo wl1251* command). So if, by any coincidence, you have the cd or iso of Ubuntu 10.04.4, I'd suggest to try it in live mode to see if the card works in it.

However, if you don't already have the cd or iso of 10.04.4, I doubt if it is worth bearing the trouble of downloading and burning a cd, especially when we are not sure it'll work and besides, 10.04 is going to reach its EOL *(End Of Life - meaning no active support after that)* in April next year.

---

### Post by MXzor on 2012-11-25
> **varunendra said:**
> Hi,
Sorry for being so late, I wasn't ready with a useful reply. Hopefully, now I am.

After doing a lot of searching on the net, it seems that indeed we may have to resort to ndiswrapper. Although there are references to the *wl1251* driver that suggest it works with this card, but needs a firmware (**wl1251-fw.bin**) which is proprietary, and so not included by default in Ubuntu. Almost all the external links to it I found were dead (maybe because it is really too old). However, I did find a link which still works.

So before trying ndiswrapper, I want to give the native driver one more shot (or two ?). Please try this -

[LIST=1]
[*]download the "ti-wl1251-firmware_0.4.tar.bz2" file from this page : [https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900](https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900)[]("https://build.pub.meego.com/package/files?package=ti-wl1251-firmware&project=CE%3AAdaptation%3AN900")  (Here's the [direct link]("https://api.pub.meego.com/public/source/CE:Adaptation:N900/ti-wl1251-firmware/ti-wl1251-firmware_0.4.tar.bz2?rev=3a5bcff15024a50be09a4ed04eafab64&") to avoid confusion)
[*]Extract the **wl1251-fw.bin** file from the archive to your desktop.
[*]Copy the file to your **/lib/firmware** directory by - ```
sudo cp ~/Desktop/wl1251-fw.bin /lib/firmware/
```
[*]Now reload the driver -
[/LIST]
```
sudo modprobe -rfv wl1251_sdio
sudo modprobe -v wl1251_sdio
```
And see if the adapter becomes active. If not, please post output of -
```
dmesg | grep 1251
```


Interestingly, while digging up the firmware, I found that the same driver set (wl1251_sdio, wl1251) included in kernel 2.6.32-38-generic (which is part of 10.04.4 - 32 bit iso) does not ask for any firmware (verified by *modinfo wl1251* command). So if, by any coincidence, you have the cd or iso of Ubuntu 10.04.4, I'd suggest to try it in live mode to see if the card works in it.

However, if you don't already have the cd or iso of 10.04.4, I doubt if it is worth bearing the trouble of downloading and burning a cd, especially when we are not sure it'll work and besides, 10.04 is going to reach its EOL *(End Of Life - meaning no active support after that)* in April next year.

Hi, no problem it's good receive help from you really, thanks a lot for the time expended with me :)

I make what you did to do and here it is the output:
```
mine@user:~$ dmesg | grep 1251
[147750.534512] wl1251: unloaded
```

The file are in the firmware directory like you said to put...about the live cd of ubuntu 10.04 i can burn one CDRW i think i have somes, so what about the output, while i'm searching one CDRW.

thanks in advance ;)

---

### Post by varunendra on 2012-11-25
> **MXzor said:**
> so what about the output, while i'm searching one CDRW.
I would like to see -
```
lspci -nnk | grep -iA2 net
dmesg | tail -20
dmesg | grep -i firm
ls -l | /lib/firmware/wl1251-fw.bin
lsmod | grep 1251
```

---

### Post by MXzor on 2012-12-02
> **varunendra said:**
> I would like to see -
```
lspci -nnk | grep -iA2 net
dmesg | tail -20
dmesg | grep -i firm
ls -l | /lib/firmware/wl1251-fw.bin
lsmod | grep 1251
```

```
$ lspci -nnk | grep -iA2 net
03:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)
	Subsystem: Hewlett-Packard Company Device [103c:1296]
	Kernel driver in use: e100
--
03:09.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
	Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter [1186:3b04]
03:0b.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k HSFi Modem [14f1:2f00] (rev 01)

```

```
$ dmesg | tail -20
[   22.866154] snd_intel8x0 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   22.866230] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   23.368134] intel8x0_measure_ac97_clock: measured 54707 usecs (2636 samples)
[   23.368142] intel8x0: clocking to 48000
[   23.900260] init: failsafe main process (801) killed by TERM signal
[   24.326565] type=1400 audit(1354403035.353:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1009 comm="apparmor_parser"
[   24.342997] type=1400 audit(1354403035.369:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1010 comm="apparmor_parser"
[   24.344563] type=1400 audit(1354403035.373:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   24.345176] type=1400 audit(1354403035.373:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   24.417476] type=1400 audit(1354403035.445:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1011 comm="apparmor_parser"
[   25.835947] Bridge firewalling registered
[   25.926429] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.421557] nf_conntrack version 0.5.0 (7803 buckets, 31212 max)
[   26.822073] ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   31.432063] eth0: no IPv6 routers present
[   33.205662] Ebtables v2.0 registered
[   33.313540] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   36.047966] init: plymouth-stop pre-start process (1816) terminated with status 1
[  344.004340] e100 0000:03:08.0: eth0: NIC Link is Down
[  362.004174] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
```

```
$ dmesg | grep -i firm
[    0.191138] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling

```

```
# ls -l | /lib/firmware/wl1251-fw.bin
bash: /lib/firmware/wl1251-fw.bin: Permissão negada

```

```
# lsmod | grep 1251
xt_state               12514  1 
ipt_REJECT             12512  2 
```

sorry for the waiting...

---

