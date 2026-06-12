---
title: "Broadcom 4311 / Oneiric / Dell Latitude d820 &gt; no wireless"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by jaredscribe on 2011-12-02
Hi all

This installation had wireless working before - I had a strange shutdown failure last week involving ecryptfs, and after recoverying from it everything works fine except wireless.

Broadcom STA driver (proprietary) installed and activated from the additional drivers menu.  
lsmod shows that only wl kernel module is installed, not b43, ssb which are, I understand, the free drivers and which the proprietary one conflicts with.

However lspci shows:
Kernel modules: wl, ssb

I've tried rmmod ssb and get error:
ERROR: Module ssb doesn't exist in /proc/modules
Also tried blacklisting it in /etc/modprobe.d/blacklist.conf and it's still loaded at boot time.

GUI panel doesn't show that wireless is enabled.  
ip addr / iwconfig doesn't show that there is a wlan interface, just loopback and ethernet

Questions
1. How do I get my wireless working?  The hang up seems to be removing ssb module
I already tried b43-cutter and it didn't work
2. Is there anything I'm missing here? 

Thanks!

---

### Post by TBABill on 2011-12-02
STA will not work with 11.04 or 11.10 with the bcm4311. To enable it you will need the b43 driver. To do so correctly just ```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` To disable the wl module from the STA driver you installed previously, just ```
sudo modprobe -r wl
``` Then to enable the b43, just ```
sudo modprobe b43
``` 

To make sure you disable the wl module permanently just ```
gksudo gedit /etc/modules
``` and make sure b43 IS listed and wl is NOT listed. Then ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and add ```
blacklist wl
``` to the end of the list in that file. Save and enjoy.

---

### Post by praseodym on 2011-12-02
Alternatively to black- and whitelisting, just deactivate the STA driver and/or uninstall it:

```
sudo apt-get remove --purge bcmwl-kernel-source
```
after installing the firmware as described.

---

### Post by jaredscribe on 2011-12-02
This looks great!

However,

```
sudo apt-get install firmware-b43-installer                                           0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

```

I have all the default repos in my sources.list ...

---

### Post by TBABill on 2011-12-02
Did you try enabling the partner repository in the software sources app? And any others that could apply? Not sure which it is located in. And don't forget to ```
sudo apt-get update
``` first

---

### Post by jaredscribe on 2011-12-03
The partners repository was enabled, in fact I enabled all repositories including restricted and multiverse, except for pre-release proposed and unsupported backports.
and did apt-get update, and still got the same error message when running 
```
sudo apt-get install firmware-b43-installer
```

I could probably get the .deb archive somewhere and install it to solve the original problem, but it seems like this part shouldn't be happening.

---

### Post by praseodym on 2011-12-03
Which Ubuntu version is that? "firmware-b43-installer" if from Natty and on.

---

### Post by bkratz on 2011-12-03
> **jaredscribe said:**
> The partners repository was enabled, in fact I enabled all repositories including restricted and multiverse, except for pre-release proposed and unsupported backports.
and did apt-get update, and still got the same error message when running 
```
sudo apt-get install firmware-b43-installer
```

I could probably get the .deb archive somewhere and install it to solve the original problem, but it seems like this part shouldn't be happening.


You are in good hands, but here is the entire methodology for the BCM4311 in case it is needed.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by jaredscribe on 2011-12-04
Ok, I have two issues ..
1. Could the ssb module be conflicting, or if b43 is already installed what would the problem be? This is the most pressing issue for me.
2. why can't my computer apt-get the package for firmware-b43-installer like everyone else? (this may be a moot point now ..)
3. If b43 is already in use as the commands below indicate, do I even need it?


Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

```

me@mymachine:~$ lsmod | grep b43                                                                    100
b43                   341198  0 
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
ssb                    52752  1 b43

```

```

me@mymachine:~$ lspci -vvnn
...

Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at ecffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

```

I'm scanning the sticky thread on this issue at [http://ubuntuforums.org/showthread.php?t=1604868&page=51](http://ubuntuforums.org/showthread.php?t=1604868&page=51)

---

### Post by praseodym on 2011-12-04
Hi,

can you show:

```
lsmod #completely
dmesg | grep b43
rfkill list
```

---

### Post by jaredscribe on 2011-12-06
```

freedman:~$ lsmod                                                                      0
Module                  Size  Used by
usb_storage            57901  1 
uas                    18027  0 
iptable_filter         12810  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
ipt_REDIRECT           12549  0 
xt_tcpudp              12603  0 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_REDIRECT,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_owner               12498  0 
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  6 iptable_filter,ipt_REDIRECT,xt_tcpudp,iptable_nat,xt_owner,ip_tables
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  0 
arc4                   12529  2 
b43                   341198  0 
nvidia              11713772  34 
mac80211              310872  1 b43
pcmcia                 49378  0 
cfg80211              199587  2 b43,mac80211
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
joydev                 17693  0 
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_hda_codec_idt      70553  1 
psmouse                73882  0 
serio_raw              13166  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
ssb                    52752  1 b43
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 dell_wmi
snd                    68266  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
video                  19412  0 


```

```

freedman:~$ dmesg | grep b43                                                                      0
[   25.362526] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.362542] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   26.667567] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   26.781754] Registered led device: b43-phy0::tx
[   26.781778] Registered led device: b43-phy0::rx
[   26.781803] Registered led device: b43-phy0::radio
[   27.670534] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.670539] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.670543] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[12280.128487] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[12282.190448] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[12282.190477] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecffc000)
[12282.190485] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12282.190494] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[12282.192305] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[12287.818909] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[12287.818915] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[12287.818919] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[33904.448331] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[33906.510775] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[33906.510804] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecffc000)
[33906.510812] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[33906.510821] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[33906.517604] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[33912.570674] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[33912.570678] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[33912.570682] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[34083.796696] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[34085.850652] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[34085.850682] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecffc000)
[34085.850689] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[34085.850699] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[34085.903283] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[34092.494603] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[34092.494608] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[34092.494612] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[43946.288950] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[43948.340041] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[43948.340071] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xecffc000)
[43948.340078] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[43948.340088] b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[43948.346950] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[43954.248814] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[43954.248819] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[43954.248823] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

```

freedman:~$ rfkill list                                                                           
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Thanks for the help.

---

### Post by praseodym on 2011-12-06
Firmware still missing, take the file attached, save it in "Downloads" and unpack it via terminal:

```
sudo tar xvf ~/Downloads/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Do you need a firewall? Iptables are active...

---

### Post by jaredscribe on 2011-12-06
Ok, I used this tar you provided, installed the following firmware:
[CODE]
[sudo] password for freedman: 
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
[CODE/]

The kernel must have immediately detected it and load it because within a second my wireless connection appeared in the control panel, and a wlan interface appeared in ifconfig.  Nice.

I tested which firmware package I needed by moving the /b43legacy directory back out of /lib/firmware and the connections still good, so will keep /b43 only.  Thanks

---

### Post by praseodym on 2011-12-06
:popcorn:

---

### Post by intruderukr on 2011-12-07
Thank you!
I lost my wired connection today while trying to fix wireless, now thanks to your directions and the Broadcom tar package I have wireless!
intruderukr

---

### Post by intruderukr on 2011-12-24
I used computerjanitor yesterday, and have no wireless today, but this fix helped me...again...
Will Oneiric always be this uhm, unstable...?

---

### Post by praseodym on 2011-12-24
Dont use the computerjanitor! If you want to clean up use:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```
I also recommend to install synaptic package manager (which is not installed by default from 11.10):
```
sudo apt-get install synaptic
```
and clean up by hand

---

### Post by omghahalol on 2012-01-26
Thank you! I was wasting time with ndiswrapper but this solved everything.

---

### Post by cph416 on 2012-01-29
Thank you! Of all of the fixes I've tried, this one worked immediately. Running a Dell Inspiron E1505 with a Broadcom 4311. 

I didn't have to edit the blacklists, or remove anything from Synaptic Package Manager.

Cheers!

---

### Post by baslug on 2012-02-07
good stuff.  

running a Dell D820 w/the same Broadcom 4311.  Followed the directions in Post #2 and all is well.

thanks!
~Ben

---

