---
title: "New solo natty install, good signal...no wireless connect-Help!"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by mejbr2003 on 2011-08-22
I just installed 11.04 on an acer aspire desktop. I'm using a belkin usb wireless adapter. it is recognizing the network and shows excellent signal strength. 
so why no internet?
please help.
thanks

---

### Post by Basher101 on 2011-08-22
we need more info in order to help you. To post your entire network configuration type in a terminal ```
ifconfig
``` and paste the output here (please use the code function)

---

### Post by mejbr2003 on 2011-08-22
thanks

josh@mydamncomputerstill:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:72:b5:4d:37
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:41 Base address:0xa000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4216 errors:0 dropped:0 overruns:0 frame:0
TX packets:4216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:337192 (337.1 KB) TX bytes:337192 (337.1 KB)
wlan0 Link encap:Ethernet HWaddr 08:86:3b:0a:d0:7f
inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::a86:3bff:fe0a:d07f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:107 errors:0 dropped:0 overruns:0 frame:0
TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:11813 (11.8 KB) TX bytes:23573 (23.5 KB)
josh@mydamncomputerstill:~$

---

### Post by praseodym on 2011-08-22
Can you show the following outputs:

```
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by mejbr2003 on 2011-08-22
josh@mydamncomputerstill:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:72:b5:4d:37
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:41 Base address:0xa000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4216 errors:0 dropped:0 overruns:0 frame:0
TX packets:4216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:337192 (337.1 KB) TX bytes:337192 (337.1 KB)
wlan0 Link encap:Ethernet HWaddr 08:86:3b:0a:d0:7f
inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::a86:3bff:fe0a:d07f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:107 errors:0 dropped:0 overruns:0 frame:0
TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:11813 (11.8 KB) TX bytes:23573 (23.5 KB)
josh@mydamncomputerstill:~$ lsusb
Bus 004 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 004 Device 004: ID 046d:c506 Logitech, Inc. MX700 Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard
Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 050d:945a Belkin Components
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
josh@mydamncomputerstill:~$ lsmod
Module Size Used by
nls_iso8859_1 12617 0
nls_cp437 12751 0
vfat 17335 0
fat 55505 1 vfat
r8712u 281937 0
nls_utf8 12493 0
isofs 39571 0
parport_pc 32111 0
ppdev 12849 0
snd_hda_codec_hdmi 27479 1
snd_hda_codec_realtek 255820 1
snd_hda_intel 24140 2
binfmt_misc 13213 1
nouveau 621970 2
snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80244 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev 17322 0
acer_wmi 23123 0
sparse_keymap 13666 1 acer_wmi
snd_seq_midi 13132 0
ttm 65184 1 nouveau
drm_kms_helper 40745 1 nouveau
snd_rawmidi 25269 1 snd_seq_midi
drm 180037 4 nouveau,ttm,drm_kms_helper
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
hid_microsoft 12745 0
snd_timer 28659 2 snd_pcm,snd_seq
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit 13184 1 nouveau
snd 55295 14
snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_
rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse 73312 0
shpchp 32345 0
serio_raw 12990 0
k8temp 12872 0
soundcore 12600 1 snd
i2c_nforce2 12906 0
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
video 18951 1 nouveau
lp 13349 0
parport 36746 3 parport_pc,ppdev,lp
usb_storage 43946 0
uas 17676 0
usbhid 41704 0
hid 77084 2 hid_microsoft,usbhid
firewire_ohci 31504 0
ahci 21591 2
forcedeth 58190 0
firewire_core 56138 1 firewire_ohci
crc_itu_t 12627 1 firewire_core
pata_amd 13762 0
libahci 25548 1 ahci
josh@mydamncomputerstill:~$ xfkill list
No command 'xfkill' found, did you mean:
Command 'rfkill' from package 'rfkill' (main)
Command 'rfkill' from package 'wireless-tools' (main)
Command 'xkill' from package 'x11-utils' (main)
xfkill: command not found
josh@mydamncomputerstill:~$ rfkill list
0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
josh@mydamncomputerstill:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"NETGEAR" Nickname:"rtl_wifi"
Mode:Managed Frequency:2.447 GHz Access Point: 00:22:3F:B5:89:26
Bit Rate:54 Mb/s Sensitivity:0/0
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=100/100 Signal level=57/100 Noise level=0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
josh@mydamncomputerstill:~$

---

### Post by praseodym on 2011-08-22
This driver makes some problems with kernel 2.6.38. Try another driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/RTL8191SU_usb_linux_v2.6.6.0.20101111.zip](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/RTL8191SU_usb_linux_v2.6.6.0.20101111.zip)
unzip -x RTL8191SU_usb_linux_v2.6.6.0.20101111.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver
tar xvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111
make
sudo make install 
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
If "sudo make install" causes errors, move the module "by hand" instead:
```
sudo cp 8712u.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a
sudo update-initramfs -u
```
Reboot.
For a kernel upgrade you have to compile again.

From [here]("http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#post-2844083").

Alternatively you can try a mainline-kernel from version 2.6.39-rc5 and on. Dont forget the corresponding kernel headers, because the proprietary video drivers have to be reinstalled in that case..

---

### Post by mejbr2003 on 2011-08-22
how can i download when I cant get online on that computer?
how do I do this on other computer? and save to flash drive?
I'm not quite up to that speed...I'm just out of the newb-stage.
thanks

---

### Post by praseodym on 2011-08-22
Can you show the output of:

```
uname -a
```
The Metapackage build-essential can be installed from CD. Just insert the CD and add it as a package source. I will give you the links you need afterwards.

---

### Post by mejbr2003 on 2011-08-22
josh@mydamncomputerstill:~$ uname -a
Linux mydamncomputerstill 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
athlon i386 GNU/Linux
josh@mydamncomputerstill:~$

---

### Post by praseodym on 2011-08-22
Here are the packages of the kernel headers for your kernel 2.6.38-8 and unzip for Natty 32bit:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8-generic_2.6.38-8.42_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8_2.6.38-8.42_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-8_2.6.38-8.42_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-4ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_6.0-4ubuntu1_i386.deb)

(German mirrors, I dont know where you come from :wink: )
Save the packages on your Desktop and install via:
```
sudo dpkg -i ~/Desktop/*.deb
```
You were able to install **build-essential**?
Link to the driver inside of the "wget" command. Save the file to your /home-folder and open a new terminal. Now you should be able to compile the module beginning with the "unzip" line.

If you have any connection and you update your system, there will be a kernel upgrade to 2.6.38-11, so you will need these kernel headers and the corresponding metapackage, too, to compile again:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic_2.6.38-11.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic_2.6.38-11.48_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.11.26_i386.deb)

Install these files only if you have the new kernel installed.

---

