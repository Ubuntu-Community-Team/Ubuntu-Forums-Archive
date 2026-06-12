---
title: "EDIMAX EW7811un installation"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by rhyssarge on 2013-04-01
Hey guys, 

I am new to Ubuntu and not at all familiar with the terminal and the commands but my windows has started becoming slow and wanted to try this out.  However, I can only connect to the internet using my EdimaX ew7811un wireless usb adapter because my laptop is that bad! 

The problem is,  I cannot find the disk to install the edimax software on my ubuntu (linux) and do not have a clue where to go from here when it comes to downloading drivers or using commands etc. I'm using Ubuntu 12.10 if that helps.

If anyone can help me, it would be soooo great!

Cheers,
Rhys

---

### Post by praseodym on 2013-04-01
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -r
lsusb
rfkill list
iwconfig
lsmod
```
Copy the outputs to a text file and upload the content. Do you have the chance to connect via cable?

---

### Post by rhyssarge on 2013-04-01
yoo man, I have attached a file with all my details from the termianl.  And to your question, I cannot use a wired connection as the lead is too small!  

Im using wireless now, but i wont have it for long in my bedroom!

Thanks for the help man

Rhys

---

### Post by praseodym on 2013-04-01
Obviously, there is a wireless card inside? Module "b43" is for Broadcom devices. Lets check:
```

lspci -nnk | grep -iA2 net
```

---

### Post by rhyssarge on 2013-04-01
rhyssarge@ubuntu:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

---

### Post by praseodym on 2013-04-01
Here we are ;)

```
sudo apt-get install firmware-b43-lpphy-installer
```
Wireless card should work now.

---

### Post by rhyssarge on 2013-04-01
cheers mate, what else will i need to do now?

---

### Post by praseodym on 2013-04-01
Unplug the stick and setup a new wireless connection after reloading the driver (or rebooting):
```

sudo modprobe -rfv b43
sudo modprobe -v b43
```
For the stick you may want to update the driver. Please show:
```

uname -r
```

---

### Post by rhyssarge on 2013-04-01
"rhyssarge@ubuntu:~$ uname -r
3.5.0-17-generic"

and 

[sudo] password for rhyssarge: 
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/bcma/bcma.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/ssb/ssb.ko

This is all that happened..

I'm sorry if im doing stuff wrong haha

---

### Post by rhyssarge on 2013-04-01
oh, and

"rhyssarge@ubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/b43/b43.ko"

---

### Post by praseodym on 2013-04-01
Did you unplug the stick and create a new wireless connection? Check:
```

dmesg | grep b43
lsmod
iwconfig
rfkill list
```

---

### Post by rhyssarge on 2013-04-01
rhyssarge@ubuntu:~$ dmesg | grep b43
[   39.094412] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   40.151995] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   40.152024] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   40.152026] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5519.499208] b43-phy3: Broadcom 4312 WLAN found (core revision 15)
[ 5519.576193] Registered led device: b43-phy3::tx
[ 5519.576234] Registered led device: b43-phy3::rx
[ 5519.576268] Registered led device: b43-phy3::radio
[ 5519.892288] b43-phy3: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 5795.808268] b43-phy3: Radio hardware status changed to DISABLED
[ 5815.828306] b43-phy3: Radio hardware status changed to ENABLED
[ 5816.412298] b43-phy3: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 5826.832264] b43-phy3: Radio hardware status changed to DISABLED
[ 5846.852277] b43-phy3: Radio hardware status changed to ENABLED
[ 5847.440300] b43-phy3: Loading firmware version 478.104 (2008-07-01 00:50:23)
[ 5872.816256] b43-phy3: Radio hardware status changed to DISABLED
[ 5877.828305] b43-phy3: Radio hardware status changed to ENABLED
[ 5878.016319] b43-phy3: Loading firmware version 478.104 (2008-07-01 00:50:23)
rhyssarge@ubuntu:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12798  0 
b43                   369753  0 
bcma                   35656  1 b43
ssb                    52036  1 b43
nls_iso8859_1          12713  1 
coretemp               13400  0 
arc4                   12529  2 
gpio_ich               13383  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14438  1 dell_laptop
snd_hda_codec_idt      70209  1 
microcode              22803  0 
bnep                   18140  2 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_idt,snd_hda_intel
parport_pc             32688  0 
snd_hwdep              13602  1 snd_hda_codec
rfcomm                 46619  0 
ppdev                  17073  0 
rtl8192cu              67616  0 
lp                     17759  0 
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
parport                46345  3 parport_pc,ppdev,lp
bluetooth             209199  10 bnep,rfcomm
psmouse                95552  0 
serio_raw              13215  0 
rtl8192c_common        48779  1 rtl8192cu
rtlwifi                74705  1 rtl8192cu
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
joydev                 17457  0 
lpc_ich                17061  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              539908  4 b43,rtl8192cu,rtl8192c_common,rtlwifi
mac_hid                13205  0 
snd_seq                61521  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
cfg80211              206566  3 b43,rtlwifi,mac80211
radeon                895653  3 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
video                  19335  0 
i2c_algo_bit           13413  1 radeon
snd                    78734  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  1 dell_wmi
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
ums_realtek            17949  0 
uas                    17844  0 
sky2                   58111  0 
usb_storage            48838  2 ums_realtek
rhyssarge@ubuntu:~$ iwconfig
wlan1     IEEE 802.11bg  ESSID:"TALKTALK-ADEAA6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: BC:F6:85:AD:EA:A6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2490  Invalid misc:26101   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

rhyssarge@ubuntu:~$ rfkill list
2: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2013-04-02
Obviously, some firmware file missing. Install the package "linux-firmware-nonfree" and try again

---

### Post by rhyssarge on 2013-04-02
how do i do this?? Is there a command that I need to write? thanks again for all this help man

---

### Post by praseodym on 2013-04-02
Either via Software-Center or via terminal

```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by mikewhatever on 2013-04-02
I am pretty sure that EDIMAX EW7811un has nothing to do with Broadcom 4312. The former is a USB wireless adapter, while the latter is an internal wireless card. 
You can get both working: [Edimax]("http://ubuntuforums.org/showthread.php?t=2104061&p=12451316#post12451316"), [Broadcom]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

---

### Post by praseodym on 2013-04-02
I know that :rolleyes:

The Realtek driver can be updated later. I was wondering about the module b43 showing up...

---

### Post by rhyssarge on 2013-04-02
> **praseodym said:**
> Either via Software-Center or via terminal

```
sudo apt-get install linux-firmware-nonfree
```

I have done this, now what? :)

---

### Post by mikewhatever on 2013-04-02
> **praseodym said:**
> I know that :rolleyes:

The Realtek driver can be updated later. I was wondering about the module b43 showing up...

Ah, ok, thought I'd mention.
b43 shows up because the OP installed firmware-b43-lpphy-installer, probably without internet access, so there is no firmware.

---

### Post by rhyssarge on 2013-04-02
> **mikewhatever said:**
> Ah, ok, thought I'd mention.
b43 shows up because the OP installed firmware-b43-lpphy-installer, probably without internet access, so there is no firmware.

im not gonna lie Mikewhatever, i have no idea what any of this means :\ im at the learning stages.  Any help from both of you would be greatly appreciated.

cheers,
rhys

---

### Post by mikewhatever on 2013-04-02
> **rhyssarge said:**
> im not gonna lie Mikewhatever, i have no idea what any of this means :\ im at the learning stages.  Any help from both of you would be greatly appreciated.

cheers,
rhys

Can you connect an ethernet cable, and re-run the command from post #6. Is it possible? If it is, you may as well post the output, and if not, we'll need to resort to offline installation. Internet connection is require to download firmware and dependencies.

---

### Post by rhyssarge on 2013-04-03
Heyy man, I'm not able to connect via ethernet cable. At the moment i have my wireless router in my room so i can pick up the signal but it wont be here for long as I'm in a shared house. Would i be able to do post 6 with the wireless? If not, what do i need to do? Offline?

---

### Post by rhyssarge on 2013-04-03
i lied! i can use ethernet here, what will i need to do once i have connected via ethernet cable?

Plus, do i need to install any edimax software for it to work? :D 

Thanks again,
Rhys

---

### Post by mikewhatever on 2013-04-03
> **rhyssarge said:**
> i lied! i can use ethernet here, what will i need to do once i have connected via ethernet cable?
I told you what to do in post #21 above. ;)
Note, that part is about getting the BCM4312 internal wireless to work.

> 
Plus, do i need to install any edimax software for it to work? :D 

Thanks again,
Rhys
As for the Edimax, yes, you'll .need to download and install software, as outlined [-->here<--]("http://ubuntuforums.org/showthread.php?t=2104061&p=12451316#post12451316").

---

### Post by rhyssarge on 2013-04-03
> **mikewhatever said:**
> I told you what to do in post #21 above. ;)
Note, that part is about getting the BCM4312 internal wireless to work.


As for the Edimax, yes, you'll .need to download and install software, as outlined [-->here<--]("http://ubuntuforums.org/showthread.php?t=2104061&p=12451316#post12451316").

ive done what you said in the #21 and it said that my firmware is up to date..anything more i need?

i will try this from edimax now thanks, but again i do not know how to do all the processes for installing  on Linux (extracting etc) if you could help?

---

### Post by rhyssarge on 2013-04-03
Just clicked on the realtek.com link you sent me and i cannot find the one i need 7811un.. &#55357;&#56866;

---

### Post by praseodym on 2013-04-03
Please download this package:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb)

Save it to "downloads" and install it via:
```

sudo dpkg -i ~/Downloads/*.deb
```
Reload the driver if necessary (without stick):
```
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Check your wireless connection:
```
iwconfig
dmesg | grep b43
rfkill list
```

---

### Post by mikewhatever on 2013-04-03
> **rhyssarge said:**
> ive done what you said in the #21 and it said that my firmware is up to date..anything more i need?
Nope. If everything was done right, the firmware should have been installed, and the internal bcm4312 card should now be working. I assume it does, since you've not posted any outputs.

> i will try this from edimax now thanks, but again i do not know how to do all the processes for installing  on Linux (extracting etc) if you could help?

Extracting is easy, right click the file, select 'extract here'.
The Edimax EW7811un is just branding, a name on the box, so to speak. The actual hardware is by Realtek, and according to the attached file from post #3, it is:
> Bus 002 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [**Realtek RTL8188CUS**] 

...so, you need to download the driver for **Realtek RTL8188CUS**,  which is what the link points to.

---

### Post by rhyssarge on 2013-04-03
""bash: ./RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh: No such file or directory
""

AHHHHH, this is annoying me now haha i have no idea whats goping on :|! ive downloaded to the home like it said and blacklisted etc.  hmmm

---

### Post by mikewhatever on 2013-04-03
Are you sure the folder is in the topmost directory of the home folder? Not on the Desktop or in Documents, or something like that. Firefox puts stuff into Downloads by default. Can you post the output of **ls** to varify that.
You can also try the installation in two steps:
 ```

cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105

sudo bash ./install.sh

```

---

### Post by rhyssarge on 2013-04-04
> **mikewhatever said:**
> Are you sure the folder is in the topmost directory of the home folder? Not on the Desktop or in Documents, or something like that. Firefox puts stuff into Downloads by default. Can you post the output of **ls** to varify that.
You can also try the installation in two steps:
 ```

cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105

sudo bash ./install.sh

```

This is what happened after the two steps:

92C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c:22:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c: In function ‘process_p2p_group_negotation_confirm’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c:2599:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘size_t’ [-Wformat]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c:33:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c: In function ‘skb_pull_and_merge’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c:129:16: warning: comparison between pointer and integer [enabled by default]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c: In function ‘dhcp_flag_bcast’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c:1636:45: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c:1636:27: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c:1642:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h:25,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c:21:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c:56:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c:47:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c:33:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c:23:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c:25:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c:25:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c:22:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h:26,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c:21:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c:26:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c:31:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c:25:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c: In function ‘indicate_wx_custom_event’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c:146:3: warning: format ‘%u’ expects argument of type ‘unsigned int’, but argument 3 has type ‘size_t’ [-Wformat]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c: In function ‘rtw_p2p_set_go_nego_ssid’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c:3868:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘size_t’ [-Wformat]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c:26:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c:24:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  CC [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.o
In file included from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h:69:0,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h:25,
                 from /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c:26:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h:626:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  LD [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.mod.o
  LD [M]  /home/rhyssarge/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.5.0-26-generic
##################################################
The Setup Script is completed !
##################################################

---

### Post by rhyssarge on 2013-04-04
And in response to my **ls** : 

rhyssarge@ubuntu:~$ ls
Desktop           RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
Documents         Templates
Downloads        
examples.desktop  Ubuntu One
Music             Videos
Pictures          xbmc_crashlog-20130401_181547.log
Public

---

### Post by praseodym on 2013-04-04
Reboot after the installation.

---

### Post by rhyssarge on 2013-04-04
rebooted. what next?? :)

---

### Post by mikewhatever on 2013-04-04
I think we are done. The Edimax should be working now.

---

### Post by ppjdee on 2013-04-07
Does this work for 13.04 as well?

---

### Post by praseodym on 2013-04-07
I dont think so, maybe the driver does not work with kernel 3.8?! You can check it via Live-CD/USB

---

### Post by mikewhatever on 2013-04-07
> **ppjdee said:**
> Does this work for 13.04 as well?

Building the driver in 13.04 fails, but a proper fix (not workaround) may be expected sometime soon, according to this [bug report]("https://bugs.launchpad.net/linux/+bug/852190").

---

### Post by ppjdee on 2013-04-07
thanks, maye it will be soon. then i can finally move my comp back to the other room lol

---

### Post by rhyssarge on 2013-04-08
> **mikewhatever said:**
> I think we are done. The Edimax should be working now.

Only just seen this, Thanks a lot for your help guys.  appreciate it loads! :) 

Rhys

---

### Post by rhyssarge on 2013-04-08
Another quick question - every 10-15 minutes it asks me whether i want to use Broadcom internet or Realtek adapter..

How do I set it to use the Realtek adapter all the time??

Cheers again,
Rhys

---

### Post by mikewhatever on 2013-04-08
You can disable the Broadcom card till the next reboot by removing the module: **sudo rmmod b43**. 
To permanently disable it, blacklist the module: **echo 'blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf'**.

After blacklisting, you won't have the second (Broadcom) interface, but if you ever need it, run **sudo modprobe b43**.

---

### Post by rhyssarge on 2013-04-10
> **mikewhatever said:**
> You can disable the Broadcom card till the next reboot by removing the module: **sudo rmmod b43**. 
To permanently disable it, blacklist the module: **echo 'blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf'**.

After blacklisting, you won't have the second (Broadcom) interface, but if you ever need it, run **sudo modprobe b43**.

yoo mate, u done this and now my internet wont work at all :/:/:/

---

### Post by mikewhatever on 2013-04-11
> **rhyssarge said:**
> yoo mate, u done this and now my internet wont work at all :/:/:/

It sounds unrealistic that you'd have your own private Internet just for you, so I don't know about that. If you have any problems with the stuff you've discussed earlier, you'll need to provide some info.

For example, what do you get from **sudo modprobe -v b43** ?
How about **ifconfig** and **lsmod | grep 8192** ?

Remember that you have to rebuild the realtek driver after kernel updates.

---

### Post by rhyssarge on 2013-04-15
> **mikewhatever said:**
> It sounds unrealistic that you'd have your own private Internet just for you, so I don't know about that. If you have any problems with the stuff you've discussed earlier, you'll need to provide some info.

For example, what do you get from **sudo modprobe -v b43** ?
How about **ifconfig** and **lsmod | grep 8192** ?

Remember that you have to rebuild the realtek driver after kernel updates.

sorry about the late reply .the sudo modprobe does nothing..

the ifconfig says a lot of stuff but i cannot paste as I'm using my phone for internet.

the lsmod grep 8192 also does nothing :/

---

