---
title: "ath9k does not work in latest Ubuntu 12.04 Kernel"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by ajMac on 2012-08-17
I have a Dlink DWA-556 pci express wireless card that uses AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express).

This card works in the older ubuntu kernel 3.0.17 but it does not in the newer kernels and certainly not in the 3.2.0.29 - SAME MACHINE! 

Here is the ```
dmesg | grep ath
``` output for 3.2.0.29 

> [   11.047317] ath9k 0000:01:00.0: Refused to change power state, currently in D3
[   11.047326] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.150910] ath: Couldn't reset chip
[   11.150913] ath: Unable to initialize hardware; initialization status: -5
[   11.150916] ath9k 0000:01:00.0: Failed to initialize device
[   11.150937] ath9k 0000:01:00.0: PCI INT A disabled
[   11.150942] ath9k: probe of 0000:01:00.0 failed with error -5

And the same for the older 3.0.17-030017-generic kernel
> [   17.547883] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.547891] ath9k 0000:01:00.0: setting latency timer to 64
[   17.681297] ath: EEPROM regdomain: 0x10
[   17.681299] ath: EEPROM indicates we should expect a direct regpair map
[   17.681301] ath: Country alpha2 being used: CO
[   17.681302] ath: Regpair used: 0x10
[   17.736460] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.736852] Registered led device: ath9k-phy0

I can give any other info you want, but the above seems to say it all. 

When I boot into the newer kernel, network manager or  'lshw -C network' does not even show the wireless interface.

Any ideas? Thanks for your help.

---

### Post by wildmanne39 on 2012-08-17
, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by ajMac on 2012-08-17
Thanks for your time Wild Man.

I am enclosing both the working & the not working versions of the output.

---

### Post by wildmanne39 on 2012-08-18
Hi, does it have the same error's on 3.2.0.28 and 3.2.0.27?

You can also reinstall the linux-image and see if that helps.
Thanks

---

### Post by bakegoodz on 2012-08-18
I'm curious to see why the ath9k module is not loading on the 3.2 kernel. Will you run the following?
```
sudo modprobe -v ath9k
```
I have the same chipset and kernel and it works. Maybe ath9k project accidentally dropped detecting your devices pci id. I recently ask a question to the ath9k mailing list and someone very helpful responded. If you ask on the mailing list I would give detailed information about your adapter, like this:
```
lspci -nnk | grep -iA2 atheros
02:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168c:0024] (rev 01)
	Subsystem: Apple Inc. AR5BXB72 802.11abgn Mini PCIe Card [AR5008E-3NX] [106b:0087]
	Kernel driver in use: ath9k
```

Ath9k Mailing list: [http://linuxwireless.org/en/users/Drivers/ath9k/#Mailing_list](http://linuxwireless.org/en/users/Drivers/ath9k/#Mailing_list)


My output of that script
[ATTACH]222867[/ATTACH]

---

### Post by ajMac on 2012-08-18
Wild Man .. 
****I will try to reinstall these kernels and try. It never worked with these newer kernels. 
I am curious as well, since something like this might have been the reason why it worked in 3.0.17. Let me explain. I had 3.0.11 when it was working and it never worked with the newer kernels that were installed through the update manager. But once I manually installed the 3.0.17 kernel and it worked in it. So, perhaps, if I manually install the latest kernel it might just work. 

Thanks. I will try and post an update.

---

### Post by ajMac on 2012-08-20
> **Wild Man said:**
> Hi, does it have the same error's on 3.2.0.28 and 3.2.0.27?

You can also reinstall the linux-image and see if that helps.
Thanks

I tried this, but it did not work. Thanks for your time.

---

### Post by wildmanne39 on 2012-08-20
Hi, you can install linux-backports modules-cw-3.3 then reboot and see if that helps.
Thanks

---

### Post by ajMac on 2012-10-04
I have tried the backports as well, but it did not fix. 

I'm now confident this is something to do with the kernel. I have tried a clean install and every time even with Fedora Core 17, OpenSuse 12, and live cds of Ubuntu or Linux mint it has failed. I tried debian 6 and it worked, but the kernel is 2.6.32 in debian. 

Now I am back with Ubuntu 12.04 and I moved to kernel 3.1.10, and its working. 
But not with any 3.2.x or the latest!

I think like bakegoodz suggested I will have to write to ath9k project.

Thanks.

---

### Post by uncaspi on 2012-10-05
Sorry to interrupt, but have you read this bug about 12.04 LTS and ath9k driver?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379)

---

### Post by BarryDocks on 2012-11-18
This solved the problemn for me on my Satalie Pro
[http://wireless.kernel.org/en/users/Download/stable/#Recommended]("http://wireless.kernel.org/en/users/Download/stable/#Recommended")

---

### Post by iokhahon on 2013-01-02
I have the exact same problem/symptoms running 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux did you ever resolve this issue?
Thanks

---

### Post by Pjotr123 on 2013-01-02
> **iokhahon said:**
> I have the exact same problem/symptoms running 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux did you ever resolve this issue?
Thanks

Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Driver-ath9k:-disable-hardware-encryption](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Driver-ath9k:-disable-hardware-encryption)
(item 2.2, right column)

---

