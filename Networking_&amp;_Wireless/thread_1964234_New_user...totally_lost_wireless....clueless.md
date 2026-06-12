---
title: "New user...totally lost wireless....clueless"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by jennabug1974 on 2012-04-23
Hey. Recently got a netbook with Ubuntu on it. All was working fine until I let it auto-update to 11.10. Now my touchpad AND my wireless have quit working. Tried to follow some of the other threads, but having problems. I have a AR242X wireless card installed in ASUS EEE PC 900. No CD drive on this model. I went to the ndiswrapper thread, but it appears I don't have that installed and I can not connect my netbook to the wired network here at work..... I need a "help for dummies" lesson, please!:lolflag:

---

### Post by praseodym on 2012-04-23
Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:
```

lspci -nnk | gep -iA2 net
iwconfig
lsmod
rfkill list
```
Edit: Tried to reset the BIOS?

---

### Post by jennabug1974 on 2012-04-23
owner@owner-900:~$ lspci -nnk | gep -iA2 net
No command 'gep' found, but there are 16 similar ones
gep: command not found

owner@owner-900:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

owner@owner-900:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
i915                  509519  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  0 
rfcomm                 38408  0 
lp                     17455  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
videodev               85626  0 
serio_raw              12990  0 
cfg80211              172427  0 
snd_page_alloc         14115  0 
binfmt_misc            17292  1 
sparse_keymap          13658  0 
video                  18908  1 i915
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
atl2                   27979  0 

owner@owner-900:~$ rfkill list
owner@owner-900:~$

---

### Post by dniMretsaM on 2012-04-23
> **jennabug1974 said:**
> owner@owner-900:~$ lspci -nnk | gep -iA2 net
No command 'gep' found, but there are 16 similar ones
gep: command not found

That command should be this:
```
lspci -nnk | grep -iA2 net
```

---

### Post by jennabug1974 on 2012-04-23
owner@owner-900:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AR5007EG 802.11bg Wi-Fi mini PCI express card [1a3b:1026]
    Kernel modules: ath5k
03:00.0 Ethernet controller [0200]: Atheros Communications L2 Fast Ethernet [1969:2048] (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
    Kernel driver in use: atl2
owner@owner-900:~$

---

### Post by jennabug1974 on 2012-04-26
):PHello. I am still clueless....have posted my screen info. Please help.

---

### Post by Bucky Ball on 2012-04-26
Have you plugged in an ethernet cable, done updates and checked 'Additional Drivers?'

Madwifi is suggested for Atheros cards rather than Network Manager. AVOID ndiswrapper. It has been superseded for the majority of cards.

The UPGRADE to a newer release is a release upgrade, not a regular update. ;)

---

### Post by Irihapeti on 2012-04-26
I have an EeePC 900. It doesn't need ndiswrapper. The madwifi drivers have been obsolete for a while now.

I've not used 11.10, so can't quite be sure what's needed in that system. However, 10.04 uses something called "linux-backports-compat-wireless" (or similar name - I can't boot into my 10.04 install at the moment). It's in the repositories. 12.04 doesn't need any additional drivers.

As Bucky Ball says, you'll need an ethernet connect to install any additional packages.

If 11.10 doesn't have the linux-backports-compat-wireless in the repositories, then you should be all right without any additional packages. If wireless isn't working, then it's time to look at other reasons.

---

### Post by Bucky Ball on 2012-04-26
Posted in error ... ;)

---

### Post by NoNameWill on 2012-04-26
From terminal try 

```
ifconfig wlan0 up
```

That atheros wifi card should just work out of the box.

---

### Post by jennabug1974 on 2012-04-26
Thank you all. Have plugged up to cable, and getting 12.. now. I will try other stuff if that doesn't do it.

---

### Post by jennabug1974 on 2012-04-27
Installing 12,04 solved all my problems. THANK YOU!!!! You guys saved me $$$ since I didn't have to take my computer in.:p

---

### Post by Irihapeti on 2012-04-27
You're welcome!

If you run into any other problems, just ask.

---

### Post by Bucky Ball on 2012-04-27
All good. Don't forget to post a new thread with any other issues ... ;)

Enjoy!

---

