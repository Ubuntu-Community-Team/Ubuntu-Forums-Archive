---
title: "Ubuntu 11.10 and Edimax wireless 802.11b/g/n nano USB adaoptor driver issues"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by sprogmeister on 2011-11-19
I am having issues with Ubuntu 11.10 and Edimax wireless 802.11b/g/n nano USB adaoptor. The wireless will work from time to time with Ubuntu-I know it is working as my iPad can connect to the wireless. When it does connect it will soon fall out. Similarly, it often will not work or, if it does, it will not accept the password. I have a disk with Linux drivers on it however, I am unable to install them. Please help!

---

### Post by mikewhatever on 2011-11-20
The question is vague. :~(
Can you provide the exact model of the Edimax adapter, and also, the versions of Ubuntu that you use.

Alternatively, post the outputs of the following:

```

lsusb

lsb_release -a

```

---

### Post by sprogmeister on 2011-11-20
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

---

### Post by sprogmeister on 2011-11-20
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

---

### Post by sprogmeister on 2011-11-20
I am using Ubuntu 11.10 and the wireless usb is the Edimax wireless 802.11b/g/n nano USB adaptor. I thought this information was in the title

---

### Post by mikewhatever on 2011-11-20
Great, thanks.
There is a known problem with this adapter's driver.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

Here's what you can try:
[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

---

### Post by sprogmeister on 2011-11-20
Many thanks, will try it now

---

### Post by sprogmeister on 2011-11-20
Thanks for your help and patience. I am stuck on the following direction:

Go to the download folder and open (using right click, if you followed step 0) the terminal for the folder “RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922&#8243;

I have downloaded the driver but do not understand how to open the folders terminal. Please help and advise

---

### Post by praseodym on 2011-11-20
Change the folder directly in your terminal:
```
cd ~/Downloads/RTL81*
```

---

### Post by sprogmeister on 2011-11-20
Lapse in brain power I do not understand the last comment

---

### Post by praseodym on 2011-11-20
If the unpacked folder is in "Downloads" change to this folder in the terminal without GUI. You need to do this to run "sudo bash install.sh".

---

### Post by sprogmeister on 2011-11-20
Thank you, I tried it and got this: downloads/RTL8192CU_linux_v3.1.2590.20110922.zip: Not a directory
 Please help

---

### Post by praseodym on 2011-11-20
Unzip it with a double click. You may need to install the package "unzip" first

---

### Post by sprogmeister on 2011-11-20
Many thanks carried out the changes and the installation failed because it could not find the file or directory. Thanks for your patience and help though. If you have any idea they will be gratefully received.

---

### Post by praseodym on 2011-11-20
Did you install the kernel-headers and the compilation tools?
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

---

### Post by sprogmeister on 2011-11-21
That I had managed. Did it again just to make sure.

---

### Post by sprogmeister on 2011-11-22
I have followed your advice but the problem persists as described above.

---

### Post by praseodym on 2011-11-22
Build the driver with dkms:
```
sudo apt-get install dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192cu-3.1.2590_11.10_dkms.tar.gz
sudo tar xvf rtl8192cu-3.1.2590_11.10_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.1.2590
sudo dkms build -m rtl8192cu -v 3.1.2590
sudo dkms install -m rtl8192cu -v 3.1.2590 
```and reboot

---

### Post by sprogmeister on 2011-11-22
Many, many thanks for your help and patience, now up and running!

---

### Post by talgalili on 2011-11-29
Follow the instructions from the beginning of the post.
They will allow you to rightclick on a folder and get to the terminal with that folder "open" for you...

> **sprogmeister said:**
> Lapse in brain power I do not understand the last comment

---

### Post by rigel4 on 2012-07-28
I have followed the guide and finished it with out error, but my edimax nano
is still not working, I am using Ubuntu 12.04, can someone help me please.

---

### Post by praseodym on 2012-07-29
Please show:

```
iwconfig
lsmod
rfkill list
sudo iwlist scan
iwlist chan
dmesg | egrep 'rtl8|r8'
modinfo rtl8192cu
locate rtl8192cu.ko | grep lib
```

---

### Post by rigel4 on 2012-07-29
Thanks,

Should i post the output for you?
I really need this to work as the hardware switch is broken on 
the native wireless on my laptop.

This all i have left now, so if i can't get it working , i can't use ubuntu.:(:(

---

### Post by rigel4 on 2012-07-29
Ok here is the out put from the commands you have given me.

```
iwconfig
lsmod
rfkill list
sudo iwlist scan
iwlist chan
dmesg | egrep 'rtl8|r8'
modinfo rtl8192cu
locate rtl8192cu.ko | grep lib



alex@U-Box:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

alex@U-Box:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
joydev                 17393  0 
snd_hda_codec_realtek   174134  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
rtl8192cu              97722  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  4 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
fglrx                2909855  39 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95789  1 rtl8192cu
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8187                56323  0 
mac80211              436455  4 rtl8192cu,rtl8192c_common,rtlwifi,rtl8187
toshiba_acpi           18158  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72919  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
serio_raw              13027  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
usbhid                 41906  0 
hid                    77367  1 usbhid
eeprom_93cx6           12653  1 rtl8187
lp                     17455  0 
k10temp                12990  0 
video                  19068  0 
sp5100_tco             13495  0 
mac_hid                13077  0 
shpchp                 32325  0 
cfg80211              178679  3 rtlwifi,rtl8187,mac80211
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13093  0 
parport                40930  3 parport_pc,ppdev,lp
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
pata_atiixp            12999  0 
r8169                  56321  0 
alex@U-Box:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
alex@U-Box:~$ sudo iwlist scan
[sudo] password for alex: 
lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

alex@U-Box:~$ iwlist chan
lo        no frequency information.

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.

alex@U-Box:~$ dmesg | egrep 'rtl8|r8'
[    2.551047] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.551075] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.551114] r8169 0000:04:00.0: setting latency timer to 64
[    2.551175] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    2.551766] r8169 0000:04:00.0: eth0: RTL8102e at 0xf8420000, 00:1e:33:6e:7d:a6, XID 14a00000 IRQ 43
[   17.024386] ieee80211 phy0: hwaddr 00:21:63:82:86:69, RTL8187BvE V0 + rtl8225z2, rfkill mask 4
[   17.050796] rtl8187: Customer ID is 0x04
[   17.050872] Registered led device: rtl8187-phy0::radio
[   17.050902] Registered led device: rtl8187-phy0::tx
[   17.050935] Registered led device: rtl8187-phy0::rx
[   17.053411] rtl8187: wireless switch is off
[   17.053535] usbcore: registered new interface driver rtl8187
[   17.228765] rtl8192cu: MAC address: 80:1f:02:3f:5c:93
[   17.228773] rtl8192cu: Board Type 0
[   17.330640] usbcore: registered new interface driver rtl8192cu
[   17.849700] r8169 0000:04:00.0: eth0: link down
alex@U-Box:~$ modinfo rtl8192cu
filename:       /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     10D1B1055E55921BDAAD523
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.2.0-27-generic-pae SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
alex@U-Box:~$ locate rtl8192cu.ko | grep lib
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
alex@U-Box:~$ 

```

---

### Post by praseodym on 2012-07-29
Try to reset the BIOS to default settings.

The switch is really broken?

Maybe useful:

> sudo rfkill unblock all
Check after these:

> rfkill list

---

### Post by rigel4 on 2012-07-29
Sadly the switch is really broken!

I loaded the default bios values and ran the command 
you left me.

here is the output, sadly no change.

```
alex@U-Box:~$ sudo rfkill unblock all 
[sudo] password for alex: 
alex@U-Box:~$ sudo rfkill unblock all 
alex@U-Box:~$ rfkill list 
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
alex@U-Box:~$ 

```

---

### Post by rigel4 on 2012-07-29
I re ran the install and i have found an error, hope someone knows what it means.

This is just the last few lines of the install script running.

```
  CC      /home/alex/Downloads/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/8192cu.mod.o
  LD [M]  /home/alex/Downloads/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/driver/rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-27-generic-pae'
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-27-generic-pae
##################################################
The Setup Script is completed !
##################################################

```

---

### Post by praseodym on 2012-07-30
Did you run the script with "sudo"?

---

### Post by rigel4 on 2012-07-30
Yes, but the odd thing is it doesn't prompt for a password.
I just right click the decompressed folder, and then 

sudo bash install.sh

---

