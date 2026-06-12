---
title: "Slow internet (wired) connection"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by NinthJake on 2012-04-09
Hi again guys, I am dual-booting Ubuntu 11.10 on my Windows 7 PC and I am having problems with the internet connection, it is *unbelievably*slow (couldn't even connect to the uploading test on speedtest.net) in Ubuntu 11.10 while it works just fine on Windows.

Before installing it I had Ubuntu 11.04 running from a USB-stick and I don't remember having any troubles with internet on that version. 

**I do believe I may have tracked down the problem though **(after days of trying different solutions found online), I have a ASUS M5A78L-M USB3 mobo and the CD I got with it includes drivers for Realtek LAN/Ethernet, in Windows I had to install those drivers to even be able to detect my home network. The CD had a folder for linux drivers but the included .bin was not possible to install, it also included a help file which advised me to update my kernels to the latest version, my internet speed increased a little bit after doing that but it's still nowhere close to my real speed. I visited Realtek's site and the drivers available for download there seems to be for 2.6x kernels and those kernels don't seem to be available for me to install?

Thank you in advance.




Or should I just downgrade to 11.04 and see if it fixes all my problems? :lolflag:

---

### Post by NinthJake on 2012-04-10
Sorry for the bump but does this information help any?
```
nj@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
nj@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169
nj@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 008 Device 002: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 008 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
nj@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

nj@ubuntu:~$ rfkill list all
nj@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
zram                   18463  8 
lp                     17799  0 
binfmt_misc            17540  1 
vesafb                 13809  1 
snd_hda_codec_via      71209  1 
ppdev                  17113  0 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
nvidia               8107305  34 
edac_core              53746  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_mce_amd           23709  0 
snd                    68266  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
fam15h_power           13032  0 
serio_raw              13166  0 
k10temp                13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
i2c_piix4              13301  0 
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
asus_atk0110           18078  0 
wmi                    19256  0 
usb_storage            57901  2 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
pata_atiixp            13164  0 
xhci_hcd               82820  0 
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 
nj@ubuntu:~$ 

```

---

### Post by NinthJake on 2012-04-11
No-one able to help?

I re-installed my pc and installed Ubuntu 10.04 LTS via Wubi but I still have the same problem. When I go to speedtest I get 0.75 download speed and the upload test can't even start.

I really need help here guys, this is even my 6'th time trying to post this message.

---

### Post by NinthJake on 2012-04-20
What do I have to do to get some help over here?

I still have those problems, I even had to re-install Ubuntu again because it just lost the internet connection completely (I logged in one day and suddenly had no internet connection)

So I am once again running Ubuntu  LTS via Wubi and still have a ridiculously slow internet speed. Can I please get some help this time? It's been over a week already...

---

### Post by roger_1960 on 2012-04-20
Hi

I'm no expert on wubi installs, but have you tried running from the live CDs or USBs of 10.04 or 11.10?  Are these just as slow? If they are OK its probably wubi related.

---

### Post by wildmanne39 on 2012-04-20
Hi, you need to install this driver for your wired connection and it should fix your problem.

Run the codes one line at a time and watch for errors.
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2
tar xvf r8168-8.025.00.tar.bz2
cd r8168-8.025.00
sudo modprobe -rf r8169
sudo ./autorun.sh
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```
Reboot
Thanks

---

### Post by NinthJake on 2012-04-21
Wildmanne39 you are awesome! That worked, many thanks :D

@Roger_1960 I tried that some time ago and I can't exactly remember but I think it was still slow then, but thanks to wildmanne39 it now works again.

---

### Post by wildmanne39 on 2012-04-21
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

