---
title: "No wireless internet after upgrading from DSL to FIOS."
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by leonard21117 on 2012-11-10
[SIZE=2]Hi,
I have Desktop PC Dell Inspiron 530,  Double boot with Windows Vista. Worked OK with DSL.
[/SIZE]
Verizon technician could set up wireless on Windows Vista but Could Not on Ubuntu 11.04.
[SIZE=2]Internet on Windows Vista[/SIZE] works OK.

I don't have internet on Ubuntu, cannot download any driver, unless there is a way around it.

Printed on the USB Adapter box:
USB wireless N-lite USB Adapter  is N220 by ZyXEL.
802.11n compliant and backward compatible with 802.11b/g 

Network connections Setting on Ubuntu filled out, but no connection.

What should I do to make it work?

---

### Post by ahallubuntu on 2012-11-10
So you have changed nothing in Ubuntu but you got rid of DSL and now have FIOS and a new wireless router?  Did you use wireless before to connect to DSL or did you connect directly with a cable?

Can you even see your new wireless network in the list of Wireless Networks?  What happens when you try to connect to it?

If you weren't using wireless internet before, maybe this card never worked with Ubuntu 11.04.

---

### Post by leonard21117 on 2012-11-10
> **ahallubuntu said:**
> So you have changed nothing in Ubuntu but you got rid of DSL and now have FIOS and a new wireless router?  Did you use wireless before to connect to DSL or did you connect directly with a cable?

Can you even see your new wireless network in the list of Wireless Networks?  What happens when you try to connect to it?

If you weren't using wireless internet before, maybe this card never worked with Ubuntu 11.04.
It was connected to DSL  directly with a cable. I see wireless network connection filed out with BSSID  and password. Status on it:  Never [connected]

---

### Post by ahallubuntu on 2012-11-10
I think I'm understanding what you did now: you originally had a DSL modem in your Dell to connect to DSL (phone line directly plugged into the back of the computer?).

Now you have FIOS, and the FIOS modem is not close enough to your Dell to connect to it with an ethernet (network) cable, so Verizon gave you that little wireless USB card to use instead?

Unfortunately, it may be that Ubuntu 11.04 doesn't support that card directly. I found a little about your card - it appears to use a chipset from Ralink that had some issues with Ubuntu 11.04 .  If you can follow, you might try this work-around to see if it works for you:

[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

FYI, support for Ubuntu 11.04 recently ended, so you won't be able to get new updates soon.  There's a good chance the newer versions of Ubuntu would automatically support your wireless card.  Ubuntu 12.04 LTS will be supported until 2017.

---

### Post by leonard21117 on 2012-11-10
You are correct on my connections.

Here is my setting, that might help:

lenny@lenny-Inspiron-530:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

enny@lenny-Inspiron-530:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 0586:343e ZyXEL Communications Corp. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 19ff:0218 Dynex 
Bus 001 Device 004: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lenny@lenny-Inspiron-530:~$ lspci -nn |grep -e 0280 -e 0200
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)


lenny@lenny-Inspiron-530:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1A:A0:8B:C7:00

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

--------------------------------------------------
lenny@lenny-Inspiron-530:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Dell Inspiron 530
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Inspiron 530
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ff00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
    Subsystem: Dell Inspiron 530
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at fe00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fd00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at fc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fb00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Inspiron 530
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at fa00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at f900 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at f800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Dell Inspiron 530
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Inspiron 530
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f700 [size=8]
    I/O ports at f600 [size=4]
    I/O ports at f500 [size=8]
    I/O ports at f400 [size=4]
    I/O ports at f300 [size=16]
    I/O ports at f200 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Dell Inspiron 530
    Flags: medium devsel, IRQ 11
    Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Inspiron 530
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f000 [size=8]
    I/O ports at ef00 [size=4]
    I/O ports at ee00 [size=8]
    I/O ports at ed00 [size=4]
    I/O ports at ec00 [size=16]
    I/O ports at eb00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Dimension 3000
    Flags: bus master, medium devsel, latency 0, IRQ 5
    Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at df00 [size=8]
    Capabilities: <access denied>


What else could be useful?


> **ahallubuntu said:**
> I think I'm understanding what you did now: you originally had a DSL modem in your Dell to connect to DSL (phone line directly plugged into the back of the computer?).

Now you have FIOS, and the FIOS modem is not close enough to your Dell to connect to it with an ethernet (network) cable, so Verizon gave you that little wireless USB card to use instead?

Unfortunately, it may be that Ubuntu 11.04 doesn't support that card directly. I found a little about your card - it appears to use a chipset from Ralink that had some issues with Ubuntu 11.04 .  If you can follow, you might try this work-around to see if it works for you:

[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

FYI, support for Ubuntu 11.04 recently ended, so you won't be able to get new updates soon.  There's a good chance the newer versions of Ubuntu would automatically support your wireless card.  Ubuntu 12.04 LTS will be supported until 2017.

---

### Post by leonard21117 on 2012-11-13
I made  it to the point that nm-tools show status as *connecting .* But it never got connected. After a while (1 min or so it) it said disconnected.

---

