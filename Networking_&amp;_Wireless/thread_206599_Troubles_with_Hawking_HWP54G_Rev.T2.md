---
title: "Troubles with Hawking HWP54G Rev.T2"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by VirtuAlex on 2006-06-30
I followed the [Acx111 howto]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111") step by step and everything was nice and smooth exactly as described in there until the last step.
When I rebooted my computer wlan0 disappeared completely and lsmod does not show any acx modules loaded.
If I try to load the module manually by
```
cd ~/ACX/
sudo insmod acx.ko
```
nothing useful happens but the following appears in dmesg:
```
[17182450.280000] acx: this driver is still EXPERIMENTAL
[17182450.280000] acx: reading README file and/or Craig's HOWTO is recommended, visit http://acx100.sf.net in case of further questions/discussion
[17182450.280000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17182450.280000] running on a little-endian CPU
[17182450.280000] PCI module v0.3.35 initialized, waiting for cards to probe...
[17182450.280000] PCI: Enabling device 0000:01:0b.0 (0004 -> 0006)
[17182450.280000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17182450.284000] acx: found ACX111-based wireless network card at 0000:01:0b.0, irq:11, phymem1:0x40100000, phymem2:0x40000000, mem1:0xc8ba0000, mem1_size:8192, mem2:0xc8d80000, mem2_size:131072
[17182450.284000] initial debug setting is 0x000A
[17182450.284000] using IRQ 11
[17182450.284000] requesting firmware image 'tiacx111c16'
[17182450.756000] acx: firmware image 'tiacx111c16' was not provided. Check your hotplug scripts
[17182450.756000] requesting firmware image 'tiacx111'
[17182450.768000] acx: firmware image 'tiacx111' was not provided. Check your hotplug scripts
[17182450.768000] acx: reset_dev() FAILED
[17182450.768000] ACPI: PCI interrupt for device 0000:01:0b.0 disabled
[17182450.784000] acx_pci: probe of 0000:01:0b.0 failed with error -5
[17182450.784000] USB module v0.3.35 initialized, probing for devices...
[17182450.784000] usbcore: registered new driver acx_usb
```

It is obviously having hard time to find the firmware. How do I troubleshoot that?

---

### Post by VirtuAlex on 2006-07-10
Okay, I managed somehow to make it work. I am able to connect to unsecure network. Now I need WPA. I installed network-manager-gnome, but there is no WPA option in the wireless security list. Only three types of WEP...

What is wrong?

---

### Post by VirtuAlex on 2006-07-11
Well, I've had it. Wireless card for sale, best offer, free shipping...

I tried ndiswrapper-utils from repository. It gives me segmentation fault. I tried to compile ndiswrapper 1.9. The driver has trouble to allocate memory. Even if I help it to allocate this memory by tweaking some files, it still can't connect with WPA. It is going to be easier to wire my whole house than to make this paperweight work in ubuntu.

---

### Post by paridoth on 2006-07-12
if your still interested with going hi-gain via hawking, you can buy antenas that conect to any pci or most pcmcia wireless cards that give it the high gain signal but doesnt change the card, ie go with a linux freindly card then get the high gain anetenna and conect it to it.

---

### Post by VirtuAlex on 2006-07-12
The signal strength is not the problem here. It would help only if one of my nextdoor neighbors had unsecure network to connect to. I'm able to detect about nine networks, all of them on 6-th channel  and all of them are secured. My router for this reason works on 1st channel and I use WPA which I won't downgrade to wep. And wpa supplicant does not work with acx driver. It have to work with ndiswrapper, but ndiswrapper does not work properly on my machine.

---

### Post by proteusdeimos on 2006-07-21
i was having the exact problem that you were having,  I also have the same card. I could get the card to see networks "some of the time"  then i went through the several websites and found that this card definitely has a problem with ACPI.  I really dont use ACPI so i turned it off.

I did this by removing "acpi-support out of /etc/init.d:

```
sudo /etc/init.d/acpi-support stop
cd /home/user
mkdir acpikill
sudo mv /etc/init.d/acpi-support /home/user/acpikill
```

ACPI support should be disabled now, and also should be disabled from running at boot.

I hope this helps.

edit: just as a side note. i downloaded the latest ndiswrapper and built it from the source.  also make sure you have no acx kernel modules listed, as IT WILL conflict with the ndiswrapper module

---

### Post by VirtuAlex on 2006-08-17
Okay, I managed to make it work. It was quite a while since I last time messed with this ugly card. Many things changed. I have added 256M of memory, there is new kernel 2.6.15-26 and there is new ndiswrapper 1.23. Here is the approximate procedure:
0. Get new kernel headers.
1. Get rid of acx drivers and update modules.
2. Compile and install ndiswrapper.
3. Install windows driver (was already there from the last time)
4. Accomodate /etc/network/interfaces for wpa

```
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid hackme
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk heregoesthatnicelongwpakeygeneratedbywpa_passphrase
```

I've tried to put all that stuff into wpa_supplicant.conf, but it did not work for some reasons. Pretty much end of story. At least until next kernel upgrade.

---

