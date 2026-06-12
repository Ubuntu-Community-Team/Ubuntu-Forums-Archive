---
title: "Pls HELP, no internet connection, lan or Wlan"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Alromaiky on 2012-12-02
[COLOR=#800000][COLOR=Black]hallo everybody
[/COLOR][COLOR=Black]
Internet not working in wireless and LAN cable
in my new laptop 
[/COLOR][/COLOR][COLOR=#800000][COLOR=Black][COLOR=#800000]**Lenovo G580, i5, 3210M, win7**[/COLOR]
i installed  fresh Ubuntu 12.04 beside the Win7

also more other versions of Ubuntu, Xubuntu 
and Kubuntu live CDs are the same case.

both working automatically and perfect in Mandriva 2011 live CD and Win7

in the first, after installing Ubuntu the wireless was working but very
weak and always stop and asking for password and don't accept it and never 
comeback till i restart the Ubuntu and so on, but now 
nothing working entirely with Ubuntu , the LAN cable or WLan

p.s.

i saw that driver name of Wlan in win7 is different like follow
(win7)
    Broadcom 802.11n network adapter
(ubuntu)
    Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
[/COLOR][B]
please help me to fix this problem 
thanks 
[/B][/COLOR]

---

### Post by Bucky Ball on 2012-12-02
The Win and Ubuntu output both indicate the same card, the Ubuntu output just has more detail so no problem there.

---

### Post by Alromaiky on 2012-12-02
[LEFT] lspci[/LEFT]
    [LEFT]00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)[/LEFT]
    [LEFT]00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)[/LEFT]
    [LEFT]00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)[/LEFT]
    [LEFT]00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)[/LEFT]
    [LEFT]00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)[/LEFT]
    [LEFT]00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)[/LEFT]
    [LEFT]00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)[/LEFT]
    [LEFT]00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)[/LEFT]
    [LEFT]00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)[/LEFT]
    [LEFT]00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)[/LEFT]
    [LEFT]00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)[/LEFT]
    [LEFT]00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)[/LEFT]
    [LEFT]00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)[/LEFT]
    [LEFT]00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)[/LEFT]
    [LEFT]01:00.0 VGA compatible controller: NVIDIA Corporation Device 1058 (rev a1)[/LEFT]
    [LEFT]03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)[/LEFT]
    [LEFT]04:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)[/LEFT]

---

### Post by chili555 on 2012-12-02
> 03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)Please run and post:```
lspci -nn
```Tell us the exact details of your wireless device. Also, get your install CD ready to go in case we need it.

---

### Post by Alromaiky on 2012-12-02
[LEFT] lspci -nn[/LEFT]
    [LEFT]00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)[/LEFT]
    [LEFT]00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)[/LEFT]
    [LEFT]00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)[/LEFT]
    [LEFT]00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)[/LEFT]
    [LEFT]00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)[/LEFT]
    [LEFT]00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)[/LEFT]
    [LEFT]00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)[/LEFT]
    [LEFT]00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)[/LEFT]
    [LEFT]00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)[/LEFT]
    [LEFT]00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)[/LEFT]
    [LEFT]00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)[/LEFT]
    [LEFT]00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)[/LEFT]
    [LEFT]00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)[/LEFT]
    [LEFT]00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)[/LEFT]
    [LEFT]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1058] (rev a1)[/LEFT]
    [LEFT]03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)[/LEFT]
    [LEFT]04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)[/LEFT]

---

### Post by chili555 on 2012-12-02
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] This device uses the Broadcom proprietary driver. Please drop your install CD in the tray and navigate to pool > restricted > b > bcmwl and drag and drop bcmwl-kernel-source to your desktop. Now navigate to pool > main > d > dkms and drag and drop dkms to your desktop. Now let's reinstall from the terminal:```
sudo dpkg -P dkms
sudo dpkg -P bcmwl-kernel-source
sudo dpkg -i Desktop/*.deb
```Now see if the driver loads:```
sudo modprobe wl
```Is it now working?

---

### Post by Alromaiky on 2012-12-02
dpkg: warning: there's no installed package matching dkms
dpkg: warning: there's no installed package matching bcmwl-kernel-source

and then the rest lines working  ok 
but nothing happened , i restart, also nothing.

i wanna mention here that the wireless icon already in sys-try shown and wl is ON but he can't see any routers however there are 2 routers around

---

### Post by chili555 on 2012-12-02
Let's see the result of these commands:```
sudo modprobe wl
dmesg | grep wl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Alromaiky on 2012-12-02
[LEFT]orion@orion:~$ sudo modprobe wl[/LEFT]
    [LEFT][sudo] password for orion: [/LEFT]
    [LEFT]orion@orion:~$ dmesg | grep wl[/LEFT]
    [LEFT][   13.323317] wl: module license 'MIXED/Proprietary' taints kernel.[/LEFT]
    [LEFT][   14.711799] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/LEFT]
    [LEFT][   14.712144] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/LEFT]
    [LEFT][  489.103692] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/LEFT]
    [LEFT]orion@orion:~$ rfkill list all[/LEFT]
    [LEFT]0: ideapad_wlan: Wireless LAN[/LEFT]
    [LEFT]    Soft blocked: no[/LEFT]
    [LEFT]    Hard blocked: no[/LEFT]
    [LEFT]1: ideapad_bluetooth: Bluetooth[/LEFT]
    [LEFT]    Soft blocked: no[/LEFT]
    [LEFT]    Hard blocked: no[/LEFT]
    [LEFT]2: phy0: Wireless LAN[/LEFT]
    [LEFT]    Soft blocked: no[/LEFT]
    [LEFT]    Hard blocked: no[/LEFT]
    [LEFT]orion@orion:~$ [/LEFT]

---

### Post by chili555 on 2012-12-02
May we see:```
lsmod | grep -e b43 -e brcmsmac -e ssb -e wl
sudo iwlist wlan0 scan
```Generally, the wireless interface created by bcmwl is eth1, not wlan0.

---

### Post by Alromaiky on 2012-12-02
chili555 thank u so much for your help and support, u r really so kind.

i really get off with this problem, so i removed the ubuntu and installed kubuntu 12.10 
and this time 64 bit, and w-less worked just since 15 min perfect.

and I'm still test it but i didn't test the LAN cable yet. 
and sure if something wrong happened 'll back to u again.
thanks a lot Chili

---

### Post by Bucky Ball on 2012-12-02
Yes, chilli is very helpful! 

If this issue is solved then please mark it that way to help others from 'Thread Tools'.

Please post a new thread with any further problems and perhaps post a link back here. This will increase your chances of further help with issues that may not be related to this thread title and your post will also not be buried a dozen deep.

---

