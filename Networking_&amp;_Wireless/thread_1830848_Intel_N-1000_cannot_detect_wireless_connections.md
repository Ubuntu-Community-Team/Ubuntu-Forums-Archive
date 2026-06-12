---
title: "Intel N-1000 cannot detect wireless connections"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by mahendrakariya on 2011-08-22
I have Intel Centrino N-1000 wireless card.
When I check is the driver is loaded, I am getting this output.

```

lsmod | grep iwlagn
iwlagn                225129  1 
mac80211              267522  1 iwlagn
cfg80211              163232  2 iwlagn,mac80211
compat                 18253  5 iwlagn,mac80211,btusb,bluetooth,cfg80211
led_class               2633  2 iwlagn,compat

```
But still, it is not detecting any wireless connections. I am using Ubuntu 10.10... Any solution?

---

### Post by praseodym on 2011-08-22
Can you show:

```
iwconfig
sudo iwlist scan
rfkill list
iwlist chan
dmesg | grep iwl
```
The driver can be updated through the backports-modules:

```
sudo apt-get install --reinstall linux-backports-modules-wireless-$(uname -r)
```and reboot

---

### Post by mahendrakariya on 2011-08-26
I reinstalled the drivers. But no use.

```

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

```

```

iwlist chan
lo        no frequency information.

eth1      no frequency information.

ppp0      no frequency information.

```

```


[code]
rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```

dmesg | grep iwl
[   12.135742] iwlagn 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.135753] iwlagn 0000:09:00.0: setting latency timer to 64
[   12.135781] iwlagn 0000:09:00.0: pci_resource_len = 0x00002000
[   12.135785] iwlagn 0000:09:00.0: pci_resource_base = f8f04000
[   12.135787] iwlagn 0000:09:00.0: HW Revision ID = 0x34
[   12.135882] iwlagn 0000:09:00.0: irq 48 for MSI/MSI-X
[   12.135917] iwlagn 0000:09:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   12.135995] iwlagn 0000:09:00.0: L1 Disabled; Enabling L0S
[   12.153488] iwlagn 0000:09:00.0: device EEPROM VER=0x71a, CALIB=0x6
[   12.153491] iwlagn 0000:09:00.0: Device SKU: 0X150
[   12.153493] iwlagn 0000:09:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.153517] iwlagn 0000:09:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.202717] iwlagn 0000:09:00.0: request for firmware file 'iwlwifi-6000g2b-5.ucode' failed.
[   12.204176] iwlagn 0000:09:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[   12.204275] iwlagn 0000:09:00.0: no suitable firmware found!
[   12.205120] Modules linked in: iwlagn aes_i586 aes_generic mac80211 snd_hda_intel(+) i915(+) snd_hda_codec snd_hwdep drm_kms_helper snd_pcm drm snd_seq_midi snd_rawmidi btusb(+) snd_seq_midi_event snd_seq bluetooth cfg80211 uvcvideo snd_timer snd_seq_device compat xhci_hcd dell_wmi led_class videodev v4l1_compat snd dell_laptop dcdbas intel_agp psmouse i2c_algo_bit video serio_raw output agpgart soundcore snd_page_alloc lp parport usb_storage r8169 ahci mii libahci
[   12.207019] Pid: 964, comm: firmware/iwlwif Not tainted 2.6.35-22-generic #33-Ubuntu 0JK86R/Vostro 3550
[   12.207551] Process firmware/iwlwif (pid: 964, ti=f4e3a000 task=f6b858d0 task.ti=f4e3a000)
[   12.209800]  [<f8e6b7a7>] ? iwl_pci_remove+0x2c/0x90 [iwlagn]
[   12.210325]  [<f8e490ea>] ? iwl_ucode_callback+0x9fa/0x1000 [iwlagn]

```


BTW it is N-1300 and not N-1000. Sorry for that.

---

### Post by garvinrick4 on 2011-08-26
You have to add a config file for iwlagn driver to work. First set router in 2.4 ghz
to mixed g and n so will pick up "G" will not work in "N" this driver in 2.6 kernels.
Will give you config file :
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]```
 gksudo gedit /etc/modprobe.d/iwlagn.conf
```[/SIZE][/FONT][/COLOR] 
 
Now put this line below  inside the file and hit save. (Will be only line in config file you are making a new one.)
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 
Now Reboot

#Is my card and driver also
Maverick will install the 3.0 kernel and the "iwlagn driver will work in "N" with 3.0 and up kernel
If you want to install 3.0 kernel in Maverick let me no will tell you how.

---

### Post by praseodym on 2011-08-26
> ```
[   12.202717] iwlagn 0000:09:00.0: request for firmware file 'iwlwifi-6000g2b-5.ucode' failed.
[   12.204176] iwlagn 0000:09:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[   12.204275] iwlagn 0000:09:00.0: no suitable firmware found!
```

Install the package **linux-firmware** and reload the driver:

```
sudo modprobe -rf iwlagn
sudo modprobe -v iwlagn
```
Control:

```
dmesg | tail -n20
iwconfig
```

Adding the module parameter as garvinrick4 posted activates the N-mode with this module, which is deactivated by default from Intel.

---

### Post by garvinrick4 on 2011-08-26
> Adding the module parameter as garvinrick4 posted activates the N-mode  with this module, which is deactivated by default from Intel.When you add this config file.
Your bgn or abgn card will now show up as a
bg or abg in
iwconfig.
I use the iwlagn driver and it will not work in "N" mode has to be removed with config file. (2.6 kernels) (It has been discussed for years and intel has admitted to failing.)
and 2.4 ghz used in mixed mode in router settins. If it is in N only mode will work for short period then
depreciate until failing if you do not add config file. Only fix is to use the card and driver in "G" only. Unless you use 3.0 and up kernel in Maverick or Natty with upgrade in module-init-tools to 3.13 Cannot use 3.0 kernels in lucid.
OP has also tried to install compat-wireless was not needed, kernel drivers are just fine.
#If OP Wants to work in N install 3.0 and up.
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 
and module-init-tools 3.13
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)
All are built so in .deb and easy to install.

---

### Post by mahendrakariya on 2011-08-26
Thanks all.
I updraded Ubuntu to 11.04 and its is working fine now... :)

---

