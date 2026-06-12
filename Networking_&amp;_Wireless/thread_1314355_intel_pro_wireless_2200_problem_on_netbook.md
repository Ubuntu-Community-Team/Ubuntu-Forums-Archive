---
title: "intel pro wireless 2200 problem on netbook"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by nick.vasilakopoulos on 2009-11-04
I have a netbook and i can't figure out how to install the drivers for my wireless card.The model is intel pro wireless 2200 and i have installed ubuntu 9.10 netbook remix.Wired network works fine.I've already tried some guides i found from google but none of them seems to work for me.Please provide me a solution as soon as possible cause i am almost ready to throw it from the window!!!!!!!!!!:P

---

### Post by chili555 on 2009-11-04
Here is how you install the driver. Open a terminal and do:```
sudo modprobe iwp2200
```Check to see if an interface was created with:```
iwconfig
```If you have an interface, *eth1*, perhaps, click the Network Manager icon and connect.

---

### Post by nick.vasilakopoulos on 2009-11-05
thx for the moment.i will try and post the results

---

### Post by nick.vasilakopoulos on 2009-11-05
it says :'FATAL: Module iwp2200 not found.':mad:

---

### Post by chili555 on 2009-11-05
> **nick.vasilakopoulos said:**
> it says :'FATAL: Module iwp2200 not found.':mad:I wonder if that was eliminated to make the remix a bit slimmer. You can install it with:```
sudo apt-get install linux-backports-modules-karmic
```Then try again:```
sudo modprobe ipw2200
```

---

### Post by nick.vasilakopoulos on 2009-11-05
ok.sudo modprobe seems to work after that but then,with iwconfig it shows:
lo no wireless extensions.

eth0 no wireless extensions.

---

### Post by chili555 on 2009-11-05
Please do:```
sudo ifconfig eth1 up
iwconfig
```Do you have a wireless interface now? If not, please post:```
sudo lshw -C network
```Thanks.

---

### Post by nick.vasilakopoulos on 2009-11-05
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4c:50:6c:f4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:25 ioport:2000(size=256) memory0100000-d0100fff memory0000000-d000ffff(prefetchable) memory0020000-d003ffff(prefetchable)

---

### Post by chili555 on 2009-11-06
Is that all? There is no mention of an Intel IPW 2200 card, nor any other wireless card at all! What type of notebook is it? Let's look up its specifications. Also, please post:```
lspvi -vn
```Thanks.

---

### Post by nick.vasilakopoulos on 2009-11-08
with lspvi -vn it says:

No command 'lspvi' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lspvi: command not found


It's a netbook which a local shop here in greece sells.Below i paste a link of it.I also spoke with a person from the shop's technical support and tomorrow i am waiting a phone call from him in order to confrim the model of the wireless card.Just to mention that before i change to ubuntu from windows xp,the card worked fine.

[http://www.plaisio.gr/Laptop-Netbook-GPS/Notebook/Netbooks-Mini-Laptop/Turbo-X-MiniNote-Red-6-cell.htm](http://www.plaisio.gr/Laptop-Netbook-GPS/Notebook/Netbooks-Mini-Laptop/Turbo-X-MiniNote-Red-6-cell.htm)

---

### Post by chili555 on 2009-11-08
I apologize. I did, indeed, mean:```
lspci -vn
```I shall proofread more carefully. Can you please run that command and post it for us?

---

### Post by nick.vasilakopoulos on 2009-11-09
ok.no problem.here it is:
lspci -vn
00:00.0 0600: 8086:27ac (rev 03)
    Subsystem: 8086:1999
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 0300: 8086:27ae (rev 03)
    Subsystem: 8086:1999
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 0380: 8086:27a6 (rev 03)
    Subsystem: 8086:1999
    Flags: bus master, fast devsel, latency 0
    Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1991:5628
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d0540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 0604: 8086:27d0 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 0c03: 8086:27c8 (rev 02)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 0c03: 8086:27c9 (rev 02)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 0c03: 8086:27ca (rev 02)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 0c03: 8086:27cb (rev 02)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>

00:1f.0 0601: 8086:27b9 (rev 02)
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 0101: 8086:27df (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: 8086:1999
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: 8086:1999
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 18d0 [size=8]
    I/O ports at 18c4 [size=4]
    I/O ports at 18c8 [size=8]
    I/O ports at 18c0 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at d0544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 0c05: 8086:27da (rev 02)
    Subsystem: 8086:1999
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 0200: 10ec:8136 (rev 02)
    Subsystem: 1991:6030
    Flags: bus master, fast devsel, latency 0, IRQ 25
    I/O ports at 2000 [size=256]
    Memory at d0100000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by chili555 on 2009-11-09
I still see no sign of any wireless device. 

I did try to read the link you provided and I did see that a wireless device is referred to; however, I don't understand Greek.

Is it a built-in Mini-PCI device, or USB or PCMCIA or what? Is there an option to enable and disable the device in th computer's BIOS?

---

### Post by nick.vasilakopoulos on 2009-11-09
I am not sure about it's bios features but i will take a look.The first time i spoke with the shop's technical support they said tha it is an intel pro wireless card but they didn't mention the model,so i thought it was the 2200 cause it's dual mode[ntel® PRO/Wireless 2200BG Network Connection (Dual mode 802.11b/g].I am still waiting a call from them to tell me the exact model.

---

### Post by nick.vasilakopoulos on 2009-11-10
No...:mad:.There is no such option in the bios.

---

### Post by nick.vasilakopoulos on 2009-11-10
According to the shop's technical support it is a realtek card embed into the motherboard.He said that i cannot find the driver in the internet.I will search for the cd with the drivers they provided me when i bought it and see if we can figure something out.(I apologize if my English is poor.I try my best:).)

---

### Post by chili555 on 2009-11-10
Your *lspci* readout indicates that you do have a Realtek wired ethernet card. I still see no indication at all of any wireless device.

I suggest checking the computer's BIOS to see if there is a setting to enable/disable wireless. I'd also check to see if there is a switch on the case of the laptop that toggles the wireless on and off that may have been pushed to 'off.' 

Don't apologize for your English; it's just fine! Much better than my Greek!!!

---

### Post by nick.vasilakopoulos on 2009-11-10
:lolflag::lolflag::lolflag:ok!!No,in the bios there is nothing.I checked it twice.There is also no such switch[-X.Be right back with the cd i was telling you.

---

### Post by nick.vasilakopoulos on 2009-11-11
I found the cd but there is a small problem.It contains various drivers cause i think that they give it with many different netbooks and there is a setup manager that detects yous specific configuration and installs the necessary drivers.Maybe,there is a way to run this cd through a virtual windows simulator and see if it does something?I don't know:S...

---

### Post by nick.vasilakopoulos on 2009-11-22
OK.Problem solved!It was finally a usb dongle(Bluew-2310u)(WLAN and Bluetooth Wireless Card).I installed the right kernel(downloaded from ubuntu.com) and the usb dongle driver from here [http://www.3dsp.com.cn/web_html/download.html]("http://www.3dsp.com.cn/web_html/download.html.It") It works just fine.Thx again for your help.:-({|=

---

