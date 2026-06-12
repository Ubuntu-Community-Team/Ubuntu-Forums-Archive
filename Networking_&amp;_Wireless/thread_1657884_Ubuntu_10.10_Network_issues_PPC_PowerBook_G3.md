---
title: "Ubuntu 10.10 Network issues PPC PowerBook G3"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by JamesHayek on 2011-01-01
Hello again,
       
        I downloaded the iso and installed Ubuntu 10.10 on a very old PowerBook G3 (333MHz/ 512k Cache/ 64MB/40GB HD/ 8MB Video/ CD)

While running though the setup on the Alternate CD I ran into problems during the network set up. The automatic set up did not work, so I chose manual setup,entered the info needed and continued with the setup.

After installation I could not connect to the internet wirelessly, or even directly plugged in. However, after two reboots I magically was able to connect via the ethernet port. 

Even after the wonderful surprise of the ethernet now working, I still can not make use of the wireless card. The card is an old Apple Airport. (Airport ID 003065244925)

How can I test power to this device?  Do i need to use NDSWrapper for this project? Any direction will be greatly appreciated.

---

### Post by PatchesTheCaveman on 2011-01-01
Hi JamesHayek!  Please go to Applications > Accessories > Terminal and type in the following command and press Enter:
```
lspci -v
```

Copy/paste what appears into a reply to this thread.

---

### Post by JamesHayek on 2011-01-01
Hello Patches, thanks for the help!

Here is what was printed to screen from the above command:

```
 pbg3@ubuntu:~$ lspci -v
00:00.0 Host bridge: Motorola MPC106 [Grackle] (rev 40)
    Flags: bus master, fast devsel, latency 0

00:0e.0 USB Controller: Agere Systems USB (rev 12) (prog-if 10 [OHCI])
    Subsystem: Agere Systems USB
    Flags: bus master, medium devsel, latency 32, IRQ 28
    Memory at 80882000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:10.0 Unassigned class [ff00]: Apple Computer Inc. Paddington Mac I/O
    Flags: bus master, medium devsel, latency 32
    Memory at 80800000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

00:11.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc) (prog-if 00 [VGA controller])
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 24
    Memory at 81000000 (32-bit, non-prefetchable) [size=16M]
    I/O ports at 0c00 [size=256]
    Memory at 80881000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: atyfb

00:13.0 CardBus bridge: Texas Instruments PCI1211
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at 80880000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
    Memory window 0: 84000000-87fff000 (prefetchable)
    Memory window 1: 88000000-8bfff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001100-000011ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
 
```

---

### Post by PatchesTheCaveman on 2011-01-01
Run this and copy/paste:
```
lsusb
```

---

### Post by JamesHayek on 2011-01-01
The output is:

```

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

btw, the card is pcmicia

---

### Post by PatchesTheCaveman on 2011-01-01
Ah! Sorry, I haven't seen a PCMCIA card in quite some time.

Run this then:
```
sudo lspcmcia -vv
```
and copy/paste

---

### Post by JamesHayek on 2011-01-02
Sorry for the delayed response,work becond.

As for the command output, here is what I got.

```


pbg3@ubuntu:~$ sudo lspcmcia -vv
[sudo] password for pbg3: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:13.0)
    Configuration:    state: on    ready: yes
            Available IRQs: none
            Available ioports:    0x00000000 - 0x007fffff
            Available iomem:    0x80100000 - 0x807fffff
                        0x80900000 - 0x80ffffff
                        0x82000000 - 0x83ffffff
                        0x8c000000 - 0xfcffffff
pbg3@ubuntu:~$ 



```

I like those commands, they give me information on the input devices? So is it safe to assume we can ad "ls" to the beginning of any device to get back information on it?

---

### Post by PatchesTheCaveman on 2011-01-02
You can put *ls* in front of a lot of things to get information about them.  It's short for "list".  The *ls* command itself will list the files in the current directory.  If you want to see all the commands that start with "ls" on your machine, you can type ls and press TAB twice.  The first time you type TAB the shell will try to complete your command if there's only one that fits.  If not, the shell will list all the possible commands that start with what you've typed so far when you press TAB again.

Unfortunately the *lspcmcia* card apparently doesn't provide the information I need so run this one:
```
lshw -C network
```

---

### Post by JamesHayek on 2011-01-02
I used ls to list directories before but never knew it could list information on devices. Very cool. I will look into the command further.



```


sudo: timestamp too far in the future: Jan 1 00:00:00 1985
 *-network
      description: Ethernet interface
      physical id: 1
      logical name: eth0
      Serial: 00:50:e4:79:dd:70
      capabilities: ethernet physical
      Configuration: broadcast=yes driver=bmac ip:=192.168.1.8 link=yes multicast=yes



```

---

### Post by PatchesTheCaveman on 2011-01-02
Okay, it isn't recognizing your PCMCIA network card at all.  Do you have the manufacturer/model information?

---

### Post by JamesHayek on 2011-01-02
How are we able to determine that? What is the red flag in the sytax that I should of seen?

The info on the card is:

AirPort S/N PW239HMHLH8
AirPort I'd: 003065244925

On the bottom there is a row that reads: 825-5620 128 bits 017591/B

When I pulled the card out it was warm... Not sure if that helps.

---

### Post by JamesHayek on 2011-01-07
So I guess this card is good as crap? I am trying to avoid spending money on a card from a system that I am trying to fix just to give to someone. Especially since I just bought the HD.

Looks like I might have to just scrap Ubuntu on this laptop and just install its native OS X 10.2 on it.

---

