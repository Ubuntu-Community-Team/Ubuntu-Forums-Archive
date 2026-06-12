---
title: "Netgear WNDA3100 v2 USB wireless adapter"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by duffsterlp on 2011-11-29
Hi Ubuntu users. I'm a newbie here so I apologize if this is in the wrong thread.

I just installed ubuntu the other day and I'm trying to connect to a wireless network with a Netgear WNDA3100 v2 wireless adapter. I installed ndis GUI and found various drivers online. Some drivers installed correctly and recognized the device when it plugged in. (One of them caused a system crash). Anyway, when the driver is loaded and the device is installed, the problem is that I cannot see any options to connect to a wireless network. The command iwconfig yields "no wireless extensions" and the command sudo lshw -C network does not produce any information for the wireless interface (only shows info for my ethernet adapter). Can anyone help me get this device installed? Are there other commands I can run at the terminal to help me debug whether it's the driver or some other issue? Can anyone find a valid driver? I've tried them from various websites. The CD that came included with the device did not have the raw inf driver included. I tried the drivers that got installed in my windows partition but those did not register as valid drivers in Ubuntu.

Running Ubuntu 11.10 (running from wubi) 64 bit. Again, Netgear WNDA3100 v2 USB wireless adapter. 

Thanks!

---

### Post by jim_deadlock on 2011-12-01
Usually the best thing to do is first make sure you have a wired connection, then run 'Additional Drivers' and it should find/install the correct driver automatically, then you just activate it on the same screen. After that, unplug your ethernet cable and right-click the Network Manager icon on your taskbar and see if your router is listed.

If you don't see the Network Manager icon then you may need to install network-manager-gnome

---

### Post by praseodym on 2011-12-01
Hi,

try the 64bit driver attached. Remove the current config and try it again:

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Draft-N/dualband does **not** work with it!

---

### Post by duffsterlp on 2011-12-01
Jim, the driver was not in that list.

praseodym, The 64 bit version did not recognize the hardware when it plugged in. The 32 bit version actually did. But the same problem persists, I look in the network manager and there are no options for connecting to wireless...

---

### Post by praseodym on 2011-12-02
Check:

```
iwconfig
lsmod
rfkill list
dmesg | grep ndis
sudo iwlist scan
iwlist chan
```

---

### Post by duffsterlp on 2011-12-02
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
radeon               1016085  3 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
joydev                 17693  0 
sp5100_tco             13791  0 
i2c_algo_bit           13423  1 radeon
psmouse                73882  0 
edac_core              53746  0 
shpchp                 37345  0 
i2c_piix4              13301  0 
serio_raw              13166  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
wmi                    19256  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 

rfkill list

no output


dmesg | grep ndis

no output


sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


iwlist chan

lo        no frequency information.

eth0      no frequency information.




I'm thinking about giving up and buying another wireless adapter. But I don't know if that would fix the problem. Would buying a compatible wireless adapter magically make the wireless options show up? Or is the problem separate from the adapter itself?

---

### Post by praseodym on 2011-12-02
The driver is not loaded. Try it by hand:

```
sudo modprobe ndiswrapper
```

---

### Post by duffsterlp on 2011-12-02
Still didn't do anything. Do I have to do anything after this? Reboot or something?

On a side note: Which wireless adapters do work for Ubuntu 11.10? There is a list of adapters that generally work for linux, but I didn't see a specific list for 11.10 ubuntu.

---

### Post by praseodym on 2011-12-02
Try this:

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```
and reboot. If it doesnt work, remove the ndiswrapper config

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
and install the driver via terminal:
```
sudo ndiswrapper -i [COLOR="Red"]/path/to/driver.inf[/COLOR]
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
sudo modprobe ndiswrapper
sudo ndiswrapper -ma
```
and replug the stick. Check:
```
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
iwconfig
dmesg | grep ndis
sudo iwlist scan
```

---

### Post by kurt18947 on 2011-12-02
> **duffsterlp said:**
> Still didn't do anything. Do I have to do anything after this? Reboot or something?

On a side note: Which wireless adapters do work for Ubuntu 11.10? There is a list of adapters that generally work for linux, but I didn't see a specific list for 11.10 ubuntu.

I hope you can get your existing adapter to work.  If not, I have two that are plug & play on Ubuntu, Mint and PCLinuxOS - and probably other distros but these I've used.

[LIST]
[*]Netgear WNA1100.  You may feel snakebit by Netgear but the WNA1100 uses an Atheros chip, not the Broadcom of the WNDA 3100.  It's recognized OOB and works no tweaking required.
[*]TrendNet TEW-649UB.  This uses a RealTek 8192SU chip. DO NOT get the TrendNet TEW-64**8**UB, you may in a similar situation to what you're in now.  They look alike but use different chipsets, v1 of the TEW-648 uses a RealTek 8188SU.  I know some RealTek 8188 series chips are problem children and I know the TEW-649UB works.
[/LIST]
Both these adapters are plug & play since 11.04.  Prior to 11.04 they'd both work but needed additional software/tweaks.

---

### Post by duffsterlp on 2011-12-04
praseodym: Thanks for all the help. As much fun as it is to debug wireless issues, I ended up buying the WNA 1100. :)
kurt18947: Netgear WNA1100 worked like a charm!

Thanks everyone!

---

### Post by kurt18947 on 2011-12-05
I'm glad you were able to get it to work.  I've learned since using Linux to do a little research when shopping.  It's laudable for people to expand the hardware that is usable with Ubuntu/Linux but I don't have the technical skills to be of any real use there so I tend to find out what works well and buy that.

---

