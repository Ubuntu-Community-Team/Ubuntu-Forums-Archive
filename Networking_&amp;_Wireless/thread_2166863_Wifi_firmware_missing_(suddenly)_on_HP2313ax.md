---
title: "Wifi firmware missing (suddenly) on HP2313ax"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by drgor on 2013-08-11
Found wifi not working on starting my laptop today, alond with amd64-microcode error during booting (Error: microcode failed to load file amd-ucode/microcode_amd )
I solved amd64-microcode with--

sudo apt-get install amd64-microcode

still wifi was not woriking

sudo update-initramfs -u

above command showed missing firmware for module r8169

I downloaded linux_firmware_1.106_all.deb and copied required files with
sudo cp -r linux-firmware/rtl_nic/ /lib/firmware/

next no errors were found on "sudo update-initramfs -u" but still wifi not working

sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ dmesg | grep -ie firm 
[    0.005265] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.198688] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.211878] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.225059] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.250638] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.396377] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[B][   23.031474] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[  167.867356] phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.[/B]

---

### Post by chili555 on 2013-08-11
This firmware issue:> Error: microcode failed to load file amd-ucode/microcode_amd...is different from this:> above command showed missing firmware for module r8169...and both are different from this!```
rt2x00lib_request_firmware: Error - Failed to request Firmware.
```This makes me wonder if your entire firmware setup is somehow corrupted. Do you have internet access? If so, please do:```
sudo apt-get install --reinstall linux-firmware
sudo apt-get install --reinstall linux-firmware-nonfree
```Reboot and then post:```
dmesg | grep -i -e firmware -e ucode
```By the way, some but not all firmware messages are harmless.

---

### Post by drgor on 2013-08-11
sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install -reinstall linux-firmware
E: Command line option 'r' [from -reinstall] is not known.


I tried to install linux-firmware-nonfree from synaptic/apt-get both but it failed

sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,943 kB of archives.
After this operation, 8,982 kB of additional disk space will be used.
(Reading database ... 302718 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-firmware-nonfree_1.14ubuntu1_all.deb (--unpack):
 trying to overwrite '/lib/firmware/b43/lcn1bsinitvals26.fw', which is also in package linux-firmware 2.0-bt7
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware-nonfree_1.14ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chili555 on 2013-08-11
> **drgor said:**
> sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install -reinstall linux-firmware
E: Command line option 'r' [from -reinstall] is not known.


did I do something wrong?Nope; I did something wrong. I apologize for my mis-step. Please try:```
sudo apt-get install --reinstall linux-firmware
sudo apt-get install --reinstall linux-firmware-nonfree
```In other words, it is not -reinstall; it is --reinstall.

Sorry.

---

### Post by drgor on 2013-08-11
sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install --reinstall linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-firmware is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by chili555 on 2013-08-11
Please see: [http://askubuntu.com/questions/118749/package-system-broken-how-to-fix](http://askubuntu.com/questions/118749/package-system-broken-how-to-fix)>  Had the same problem, an

```
sudo apt-get clean
```

followed by an

```
sudo apt-get update
```

followed by an

```
sudo apt-get upgrade -f
```

fixed it. I hope this helps!
I suggest you try the same sequence. Post back a successful result, please!

---

### Post by drgor on 2013-08-11
Did as suggested all 3 steps in sequence, but what now? firmware is still missing.

Posting last step

sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Then I did repeat this (I thought it as a logical next step)
sharad@sharad-HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get install --reinstall linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-firmware is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Unsuccessful yet

---

### Post by drgor on 2013-08-11
SOLVED

removed linux-firmware from synaptic, then reinstalled it, which required removal of amd64-microcode and firmware-realtake (i earlier installed that two packages to solve other problems). Due to these two conflicts apt-get was failing to reinstall linux-firmware

thanks a lot chili555

---

### Post by chili555 on 2013-08-11
Glad it's working. Have fun!

---

### Post by vanquishedangel on 2014-04-19
I had this very same problem, I installed amd64-microcode from synaptic, this will uninstall linux-firmware and linux-image-generic. This caused issues with wireless (Realtek RTL8188SU, stopped working altogether) and plug-n-play functions seemed to also stop, my scandisk 4gb usb card was no longer seen when attached to my computer if my computer was booted but worked if it was attached then booted.

What I did to fix this issue was to go to another computer and download linux-firmware and linux-image-generic and save them to the scandisk, then plug it into my computer and turn my computer on to boot. Then removed amd64-microcode and installed linux-firmware and linux-image-generic with gdebi (software center might work to).

I wish there was a way to install both amd64-microcode and still have wireless working and plug-n-play functions for my flash disk.

---

### Post by chili555 on 2014-04-19
> **vanquishedangel said:**
> I had this very same problem, I installed amd64-microcode from synaptic, this will uninstall linux-firmware and linux-image-generic. This caused issues with wireless (Realtek RTL8188SU, stopped working altogether) and plug-n-play functions seemed to also stop, my scandisk 4gb usb card was no longer seen when attached to my computer if my computer was booted but worked if it was attached then booted.

What I did to fix this issue was to go to another computer and download linux-firmware and linux-image-generic and save them to the scandisk, then plug it into my computer and turn my computer on to boot. Then removed amd64-microcode and installed linux-firmware and linux-image-generic with gdebi (software center might work to).

I wish there was a way to install both amd64-microcode and still have wireless working and plug-n-play functions for my flash disk.I don't know much about flash disks but I think we can help your wireless. In order to know what firmware you need, please tell us about your device; from the terminal:```
lspci -nn | grep 0280
```Thanks.

---

