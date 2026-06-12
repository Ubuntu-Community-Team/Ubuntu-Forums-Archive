---
title: "Wireless not found: Nvidia MCP79 chipset"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by homemadev on 2011-07-30
I'm dying here.. I can't find the wireless adapter on my brand new Giada nettop.

Machine: Giada N10U (slim)
Intel Atom 330 
Nvidia Ion MCP79

I can't see anything like a wireliess card on lspci or lsusb.. I wonder if there's a trick I don't know about.. can you see it (below)? Also, iwconfig and ifconfig don't seem to help. I'm in Fedora 15 now, but I started with Ubuntu Natty, and I'll switch back as necessary. 

I did manage to install the current Nvidia graphics drivers from the Nvidia website.. Not sure if that has any bearing on this problem. Everything else seems to be working pretty well.. XBMC etc..

Thanks for any help!

```
$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fae80000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Capabilities: <access denied>

00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
    I/O ports at c080 [size=8]
    I/O ports at c000 [size=4]
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=16]
    Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: faf00000-fbffffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f7ffffff
    Capabilities: <access denied>

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000f9f00000-00000000f9ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at e800 [size=256]
    Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Memory at f9ffc000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

``````
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 005: ID 0cf2:6238 ENE Technology, Inc. 
Bus 003 Device 002: ID 17ef:6008 Lenovo 
Bus 003 Device 003: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 002: ID 08e4:0150 Pioneer Corp. 
Bus 002 Device 003: ID 05e1:0100 Syntek Semiconductor Co., Ltd 

``````
$ iwconfig
lo        no wireless extensions.

p35p1     no wireless extensions.

[fred@gbox ~]$ 
[fred@gbox ~]$ 
[fred@gbox ~]$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 b)  TX bytes:240 (240.0 b)

p35p1     Link encap:Ethernet  HWaddr 00:E0:4C:68:76:0B  
          inet addr:192.168.3.119  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe68:760b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59871552 (57.0 MiB)  TX bytes:3539869 (3.3 MiB)
          Interrupt:41 Base address:0x4000 

$ uname -r
2.6.38.8-35.fc15.i686

 
```

---

### Post by chili555 on 2011-07-30
I know I'm gonna hate myself in the morning, but I love a mystery. Is this your device?> ID 05e1:0100 Syntek Semiconductor Co., LtdPlease see: [http://www.stk.com.tw/product-01.asp?Product_Type=58](http://www.stk.com.tw/product-01.asp?Product_Type=58)

Is it an actual USB dongle or an internal device attached to a USB bus?

Also, I am interested in this:> $ ifconfig

[COLOR="Red"]p35p1[/COLOR]     Link encap:Ethernet  HWaddr 00:E0:4C:68:76:0B  
          inet addr:192.168.3.119  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe68:760b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1How are you connected to the internet?

---

### Post by homemadev on 2011-07-31
Hey chili555, thanks for your response! 

I'm not home.. Still going after a wedding. But to answer your question, I'm connected via wired internet. I wonder if--since my nettop is tiny--the ethernet and wifi devices are confused together...?

---

### Post by homemadev on 2011-07-31
And the wifi adapter is internal. It may be connected to a usb internally but its not an external dongle.

---

### Post by chili555 on 2011-07-31
Which version are you running? The manufacturer has drivers for 10.04 and 10.10, but I have not yet found later.```
cat /etc/lsb-release
```Enjoy the wedding!


[ftp://3dsp.com.cn/Ubuntu/](ftp://3dsp.com.cn/Ubuntu/)

---

### Post by homemadev on 2011-07-31
I was in Fedora 15 in earlier posts (lspci and lsusb give the same results in Ubuntu and Fedora). Now I'm back in Ubuntu.. I'll give the same information again to double check..

EDIT: and I'm in natty..

```
ubuntu@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:68:76:0b  
          inet addr:192.168.3.119  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe68:760b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1791724 (1.7 MB)  TX bytes:221382 (221.3 KB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2316 (2.3 KB)  TX bytes:2316 (2.3 KB)

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c529 Logitech, Inc. 
Bus 003 Device 002: ID 17ef:6008 Lenovo 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0cf2:6238 ENE Technology, Inc. 
Bus 001 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

---

### Post by chili555 on 2011-07-31
In the link I gave, it says the latest version is for Maverick 10.10. Maybe it will work. Please go to [ftp://3dsp.com.cn/](ftp://3dsp.com.cn/), click the Ubuntu link and get BlueW-2310U_2.5.2_101229_Ubuntu10.10_withouthotkey.tar.gz.

I have no idea what the significance of hotkey is. Is there a wifi/bluetooth hotkey on your netbook? Maybe you need *withhotkey*.

I suggest you download the package to your desktop. Right-click and select Extract Here. Open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/BlueW-2310U_2.5.2_101229_Ubuntu10.10_withouthotkey
sudo Install_3DSPUSB.sh
```Then, according to the README, if all has gone well go to Applications -> 3DSP WiFi Radar. I'd assume you will see your network and connect.

If it installs its own version of Wifi Radar, it may conflict with Network Manager, but let's see how it goes before we amputate.

This is the first of these I've ever encountered, so we are on unplowed ground here. Post back any errors or warnings.

---

### Post by homemadev on 2011-07-31
hmm.. any ideas? I suppose there is always ndiswrapper, right?

```
ubuntu@ubuntu:~/Downloads$ sudo apt-get install build-essential linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~/Downloads/BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey$ chmod a+x Install_3DSPUSB.sh 
ubuntu@ubuntu:~/Downloads/BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey$ sudo ./Install_3DSPUSB.sh 
 * Checking user...                    [ Ok ]
 * Verifying kernel...                    [Fail]
Notice: The kernel "2.6.38-8-generic" is NOT supported by this package.
Exit.
```

---

### Post by homemadev on 2011-07-31
also, I just found this, which I can try..

[http://ubuntuforums.org/showthread.php?t=1234213&page=2](http://ubuntuforums.org/showthread.php?t=1234213&page=2)

> success!

we know its a pcie card... problem is it thinks its a usb one.

download the usb minicard drivers, unpack it.
i had to edit the kernal number in the install shell script to match my  kernal (the .17-generic) and also renamed the kernal dir in drivers to  match

install

reboot

icon appears, (three green bars)
click co-exist

BT icon appears
click it and it asks you to enable it.
it works (paired with mouse and working)

to use the wifi you need to use the scanner app, not network manager (will try this tonight)


next steps
1. need to work out how to make card default to co-exist not unplugged
2. need to make bt default to on

---

### Post by chili555 on 2011-07-31
It looks like step 1 is to amend the Install script for your kernel version. Are you up to it and/or do you want my suggestion? Go to lines 135 et seq and change this:> case "${CURRENTKERNEL}" in
     "2.6.35-22-generic"| "2.6.35-22-generic-pae" | "2.6.35-23-generic" | "2.6.35-23-generic-pae" |"2.6.35-24-generic" | "2.6.35-24-generic-pae")
      ${PRINTOK};;To this:> case "${CURRENTKERNEL}" in
     "2.6.35-22-generic"| "2.6.35-22-generic-pae" | "2.6.35-23-generic" | "2.6.35-23-generic-pae" |"[COLOR="Red"]2.6.38-8[/COLOR]-generic" | "2.6.35-24-generic-pae")
      ${PRINTOK};;Proofread, save and close. Rerun the script and cross your fingers.

---

### Post by homemadev on 2011-07-31
I'm making some progress.. found this to edit so far.. pretty straightforward, but I'm bound to screw something up.. :)

```
case "${CURRENTKERNEL}" in
    "2.6.32-21-generic"|"2.6.38-8-generic"|"2.6.32-21-generic-pae"|"2.6.32-22-generic"|"2.6.32-22-generic-pae"|"2.6.32-23-generic"|"2.6.32-23-generic-pae"|"2.6.32-24-generic"|"2.6.32-24-generic-pae")
      ${PRINTOK};;
    *                                        )
      ${PRINTFAIL}
      handle_error "NOTSUPPORTKERNEL";;
esac
```

---

### Post by chili555 on 2011-07-31
> **homemadev said:**
> I'm making some progress.. found this to edit so far.. pretty straightforward, but I'm bound to screw something up.. :)

```
case "${CURRENTKERNEL}" in
    "2.6.32-21-generic"|"2.6.38-8-generic"|"2.6.32-21-generic-pae"|"2.6.32-22-generic"|"2.6.32-22-generic-pae"|"2.6.32-23-generic"|"2.6.32-23-generic-pae"|"2.6.32-24-generic"|"2.6.32-24-generic-pae")
      ${PRINTOK};;
    *                                        )
      ${PRINTFAIL}
      handle_error "NOTSUPPORTKERNEL";;
esac
```See my post above. It may or may not work.

---

### Post by homemadev on 2011-07-31
hmm.. not completely sure which kernel to take.. what is "-pae" all about? My 1st guess is to take the most recent kernel, avoiding ones that say "pae" at the end...

options...

```
ubuntu@ubuntu:~/Downloads/BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey/drivers$ ls
2.6.32-21-generic      2.6.32-22-generic-pae  2.6.32-24-generic
2.6.32-21-generic-pae  2.6.32-23-generic      2.6.32-24-generic-pae
2.6.32-22-generic      2.6.32-23-generic-pae

```

---

### Post by homemadev on 2011-07-31
so far so good...

```
$ sudo ./Install_3DSPUSB.sh 
 * Checking user...                    [ Ok ]
 * Verifying kernel...                    [ Ok ]
 * Copying modules...                    [ Ok ]
 * Installing utilities...                [ Ok ]
 * Installing 3dsp-wifi-radar...            [ Ok ]
 * Creating init script...                [ Ok ]
```

---

### Post by homemadev on 2011-08-01
So I have tried this in Ubuntu 10.04 and 11.04. In both cases, I was a little out of spec-- my kernel for 10.04 is 2.6.32-33-generic, while the latest supported kernel is 2.6.32-24-generic.

In both cases, I can start up the 3DSP card program and the 3DSP Wifi Radar, but I get the message, "No valid wireless device!" (see attached screenshot).. so it seems like a non starter.

Is there something I may need to disable?

Otherwise, it seems like I should try to get the supported kernel. I'm not sure how to do that, but I'll start looking.

Any other ideas?

Thanks for your help!

---

### Post by chili555 on 2011-08-01
> my kernel for 10.04 is 2.6.32-33-generic, while the latest supported kernel is 2.6.32-24-generic.Can you go into Synaptic and search for and install -24? What does this tell us?```
modinfo 3dspusbbus | grep 0100
dmesg | grep 3dsp
```We are looking for your device usb.id:> ID 05e1:[COLOR="Red"]0100[/COLOR] Syntek Semiconductor Co., Ltd 

---

### Post by homemadev on 2011-08-01
ok, downloading image for kernel -24... anything interesting in what's below?

```
$ dmesg | grep 3dsp
[  782.686897] 3dspusbbus: disagrees about version of symbol module_layout
[  782.703256] 3dspusbwlanpriv: disagrees about version of symbol module_layout
[  782.716501] 3dspusbwlan: disagrees about version of symbol module_layout
[  782.737321] 3dspusbbtpriv: disagrees about version of symbol module_layout
[  782.754610] 3dspusbbt: disagrees about version of symbol module_layout

```

```

$ sudo modinfo 3dspusbbus | grep 0100
ERROR: modinfo: could not find module 3dspusbbus

```

---

### Post by chili555 on 2011-08-01
> 3dspusbbus: disagrees about version of symbol module_layoutIt tried to load and encountered an error, but now it claims to not have any such module! Wacky!> modinfo: could not find module 3dspusbbusI'd try to get the -24 kernel and install again...and pray...

---

### Post by chili555 on 2011-08-01
Here is some interesting news:```
$ modinfo Desktop/Forum/homemadev/BlueW-2310U_2.5.2_101229_Ubuntu10.10_withouthotkey/drivers/2.6.35-24-generic/3dspusbwlan.ko | grep 0100
alias:          usb:v[COLOR="Red"]05E1[/COLOR]p[COLOR="Red"]0100[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```So, evidently, the module we want to install is [COLOR="Red"]3dspusbwlan[/COLOR].ko.

---

### Post by homemadev on 2011-08-01
OK! After a couple reboots, it is working. Thanks chili555!

(Also, I sent a note to 3DSP asking for new drivers...)

---

### Post by homemadev on 2011-08-01
Now if only it would connect automatically when I boot up.. :)

In case you are interested, here's the new info:
```

$ lsmod | grep -i 3dsp
3dspusbbt              21577  2 
3dspusbbtpriv         570556  1 3dspusbbt
3dspusbwlan            30583  0 
3dspusbwlanpriv       301330  1 3dspusbwlan
3dspusbbus              9393  2 3dspusbbt,3dspusbwlan
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,3dspusbbt
$ modinfo 3dspusbwlan
ERROR: modinfo: could not find module 3dspusbwlan
$ modinfo 3dspusbwlanpriv
ERROR: modinfo: could not find module 3dspusbwlanpriv
$ dmesg | grep 3dsp
[   12.390646] 3dspusbwlanpriv: module license 'Proprietary' taints kernel.
[   12.457822] 3dsp usb wlan device found:) intf 0, alt configs 1, endpoints 5
[   12.457941] intf 1 is not 3dsp wlan interface
[   18.176793] 3D[T:WMAIN:00249]load 3dspcode.bin 
[   23.724723] 3D[T:WMAIN:00249]load 3dspcode.bin 

```

---

### Post by chili555 on 2011-08-01
Awesome! Would you care to use the thread tools at the top and Mark Solved?

---

### Post by chili555 on 2011-08-01
> **homemadev said:**
> Now if only it would connect automatically when I boot up.. :)

What do you have to do to get it started? We can probably automate it.

---

### Post by homemadev on 2011-08-01
Well, it seems to get going with my defaults just find as follows (at bottom), so I'm adding that line following these instructions (immediately below). If that all makes sense to you, I'll mark this one SOLVED. :)

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

```
$ sudo 3dsp-wifi-radar 
read file: /etc/wifi-radar/wifi-radar.conf
Initialzers: domian is  US
starting dhcp thread...

starting scanning thread...

  key_mgmt=NONE
    auth_alg=OPEN

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/twifiu0/00:21:c5:16:20:b1
Sending on   LPF/twifiu0/00:21:c5:16:20:b1
Sending on   Socket/fallback
DHCPDISCOVER on twifiu0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on twifiu0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on twifiu0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on twifiu0 to 255.255.255.255 port 67 interval 10
DHCPOFFER of 192.168.1.83 from 192.168.1.254
DHCPREQUEST of 192.168.1.83 on twifiu0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.83 from 192.168.1.254
bound to 192.168.1.83 -- renewal in 39725 seconds.

```

---

### Post by chili555 on 2011-08-01
Post back if that doesn't work as expected. Thanks.

---

### Post by homemadev on 2011-08-01
Yeah.. that didn't work.. not sure if it may be a problem with privileges, since the command has to be run as root. help? How would you do it?

---

### Post by homemadev on 2011-08-01
ok, I found something that works..

[http://ubuntuforums.org/showthread.php?t=1721841](http://ubuntuforums.org/showthread.php?t=1721841)

all done, thanks again!

---

### Post by chili555 on 2011-08-01
Glad it's working!

---

