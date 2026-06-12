---
title: "Wired connection slow to be established &amp; wireless gone"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-09-24
Hi, 

I am running Maverick on my desktop pc.

```

uname -r
[COLOR="Blue"]2.6.35-22-generic[/COLOR]

```

Following recent update to kernel 2.6.35-22-generic, wired connection seems to take forever to be established (Network Manager icon keeps swirling for a long time, until I hit the Firefox icon then I got Internet).  NM does not show wireless connection as active at all.  Then after I pull the cable and restart, I don't get wireless connection even after I blacklisted rt2x00usb, rt2x00pci and rt2800pci. My wireless adapter is Trendnet TEW-642PCI (?) which uses Ralink's rt2860sta driver. By the way, both wired and wireless connections use auto DHCP.

```

lspci -v


03:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	I/O ports at e800 [size=256]
	Memory at febffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:06.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: RaLink Device 2860
	Flags: bus master, slow devsel, latency 64, IRQ 21
	Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta, rt2800pci


```

```

$lsmod

[COLOR="Blue"]rt2860sta             504366  1 [/COLOR]
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
crc_ccitt               1351  1 rt2860sta
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
floppy                 54311  0 
usb_storage            40172  1 
ahci                   19013  0 
[COLOR="Blue"]r8169                  36489  0 
[/COLOR]

```

How should I remedy the wired and wireless problems?

Thanks a lot for your help.

:confused:

---

### Post by iClouseau88 on 2010-09-25
Hi,

I uninstalled network-manager and network-manager-gnome, then installed wicd.  The later seems to have a better user interface, it also gave me a wireless interface with signal strength and SSID, etc., however it kept giving me "bad password" error thus I couldn't connect wirelessly; I found out later that this is because for some unknown reason network-manager and related dependencies were not completely removed.  Anyway I uninstalled wicd then failed to re-install network manager.  I ended up having to re-install Meerkat!

Just a word of warning to those users who attempt to install wicd.

---

### Post by cariboo on 2010-09-25
When removing an application, use the purge option eg:

```
sudo apt-get purge network-manager-gnome
```

Or select Complete Removal in synaptic. I'm not sure what the Software Center does when you click the remove button.

---

### Post by iClouseau88 on 2010-09-25
Thank you cariboo907 for the tip on using the purge option.  I always select "Complete Removal" when using Synaptic.

---

### Post by iClouseau88 on 2010-09-26
Hi,

I re-installed Meerkat and during installation phase put grub boot loader in its [COLOR="Blue"]own root partition[/COLOR]. Then I went inside openSUSE 11.3's /boot/grub/menu.lst to add the following so that I can boot into Ubuntu from openSUSE's main menu regardless whether Ubuntu's kernel is updated:

```

title Ubuntu Meerkat 10.10 Beta [COLOR="Blue"]booting via symlinks[/COLOR]
root (hd1,8)
kernel /vmlinuz root=/dev/sdb9 ro quiet splash
initrd /initrd.img
[COLOR="Blue"]boot[/COLOR]

```

Next step will be to set up wireless connection.

Cheers!

:popcorn:

---

### Post by cariboo on 2010-09-26
Just as a point of interest, I had a harder time getting my D-Link WUSB-1340 working in openSUSE than I did in Maverick and Fedora, as it needed to download and install some firmware before the device would work. With Maverick and Fedora it worked out of the box.

Grub2 does the same thing as you did automagically when it was installed. The only entry I had hand edit was for PCLOS.

---

