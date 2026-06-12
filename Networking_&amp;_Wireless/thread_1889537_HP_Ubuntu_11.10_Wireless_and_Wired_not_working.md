---
title: "HP Ubuntu 11.10 Wireless and Wired not working"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by mdb224 on 2011-12-01
Hi, I am new to ubuntu--I used a different linux OS about 8 years ago for a year or two but have been on windows ever since. I have a HP Pavillion dv6 laptop that is a few years old and has always worked great. However, it had been getting a little sluggish, so I decided to do a system restore to original factory settings. Something went wrong in the process, and I couldn't get windows vista reinstalled no matter what I tried. So instead I decided to put on ubuntu. It installed great and the computer is up and running again, which is a big improvement. However, I can't get connected to the internet, no matter what I try. If I try to connect it directly with an ethernet cable, then the system keeps on toggling between connecting and disconnected (over and over again in a loop), but never connects. Argh! The wireless and connecting an ethernet cable directly into my wife's laptop (windows vista) works fine, so I know the problem is on my end.

On the other hand, wireless is not working either. The laptop has a touch button to turn on the wireless, and when I press it it stays amber (off) color, but the message on ubuntu switches from "device is disabled by hardware switch" to "device not ready (firmware missing)." It seems I need to update the drivers, which I can't do with the internet, but I tried to do manually by downloading the driver on a different computer and putting it on the ubuntu computer. However, when I run the makefile to install the driver, it tells me that the MODULE_LICENSE() is missing.

I am lost! What can I do to get connected to the internet? Ultimately I want wireless connectivity, but if I can even start by getting the wired connection working, that would be a step in the right direction. I have been trying for hours, scouring the message boards for hints, but nothing works.

Thanks in advance for any help or advice you can give me, I really appreciate it.

Best,
Matt

---

### Post by mdb224 on 2011-12-01
Here are the results of the various potentially applicable tests:

** sudo lshw -C network**
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:cf:fe:4b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:25:56:40:79:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


[B]
 lspci[/B]
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


**lsmod**
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
serio_raw              13166  0 
rc_rc6_mce             12502  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
snd_seq_midi           13324  0 
ir_rc6_decoder         12546  0 
snd_rawmidi            30547  1 snd_seq_midi
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rc_core                26963  9 rc_rc6_mce,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566711  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
drm_kms_helper         42558  1 i915
wmi                    19256  1 hp_wmi
drm                   236330  4 i915,drm_kms_helper
input_polldev          13896  1 lis3lv02d
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
b43                   341198  0 
soundcore              12680  1 snd
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
ssb                    52752  1 b43
r8169                  52788  0

---

### Post by mdb224 on 2011-12-01
Update, I now have it working on the wired ethernet connection. The problem there was that I needed to restart my DSL modem--that was it. Oops.

I still have the same problems with wireless though--device not ready (firmware is missing). At least I can now try updates, etc. to try to get the driver to work...any thoughts on what is wrong?

thanks

---

### Post by BC59 on 2011-12-01
I don't know if you installed the wireless drivers.

You have to be connected through the wire. Then in the upper left corner click and on the search box write Jockey. Click on the icon and Jockey is searching your hardware and finds the appropriate drivers.

If you are lucky it's that easy.

---

### Post by mdb224 on 2011-12-01
Thanks BC59--I checked the drivers using Jockey, and it said that

Broadcom STA Wireless Driver:

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

So it looks like the driver is installed, right? But then it still says device not ready (firmware missing)

---

### Post by BC59 on 2011-12-01
I don't understand, did you click on the driver you need and then push Activate?

This is done manually only.

Choose the driver of your wireless, activate it and then restart.

---

### Post by BC59 on 2011-12-01
You have to choose the BCM4312 which is yours.

---

### Post by mdb224 on 2011-12-01
Thanks! I had to do that but I also had to make this change: 

gksudo gedit /etc/modules

and see if it says both wl and lp or just lp. If just lp we will probably have to add the wl here so it will load when booting.

as recommended by bkratz [here]("http://ubuntuforums.org/showthread.php?t=1701070")

Thanks for your help! Just glad it is all working

---

### Post by BC59 on 2011-12-01
You are welcome.

---

