---
title: "Setting up internet"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by anthony2k12 on 2009-12-31
Hiya,

Not sure if this is the exact place to put this since it is seemingly very simple, but it's proving to be more difficult then I though.

I have XBMC 9.11 installed (Uses Ubuntu 9.10 command line) and I'm trying to setup **wired** internet. I have it plugged in but it's not picking anything up. I've tested the cable and it works so it's not faulty.

I've added this to my /etc/network/interfaces file:
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```and run this command:

```
/etc/init.d/networking restart
```I'm met with this:
```
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
DHCPDISCOVER on eth0 to 255.255.255.255 prt 67 Interval x
No DHCPOFFERS received.
No working leases in persistent database - sleeping.                   
                                                        [OK] 
```Where X is the interval it tried.

I've also tried to ping Google and Gateway, neither worked. 
Anything you guys can suggest I'll try, thanks!

Also, as a side thing: My audio is also not working. Ubuntu LiveCD, audio did work so not sure what's wrong.
Here's what the output for **lspci** was:
```
00:00:0 Host bridge: Intel Corporation 82850 850 (Tehana) Chipset Host Bridge (MCH) (rev 04)
00:01:0 PCI bridge: Intel Corporation 82850 850 (Tehana) AGP Bridge (rev 04)
00:1e:0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f:0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04) 
00:1f:1 IDE interface: Intel Corporation 82801BA IDE V100 Controller (rev 04) 
00:1f:2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f:3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f:4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00:0 VGA compatible controller: nVidia Corporation NV43 (GeForce 6600GT) (rev a2)
02:04:0 USB Controller: NEC Corporation USB (rev 41)
02:04:1 USB Controller: NEC Corporation USB (rev 41)
02:04:2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:08:0 Ethernet Controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 SCSI Storage Controller: adapter AHA-2940U2/U2W
02:0b.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:0d.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.1a/b/g Wireless LAN Controller (rev 20)
```

---

### Post by Iowan on 2009-12-31
**ifconfig -a** will show all available interfaces. **sudo lshw -C network** will show results similar to **lspci**, but limited to network devices - and whether they have driver, alias, etc.

---

### Post by anthony2k12 on 2009-12-31
Before I do those commands, is it possible to somehow copy/paste what it spits out? The previous things I've put I hand typed and that's a bit of a task, heh.

I've also got this in my /etc/network/interfaces file now:
```
auto eth0
iface eth0 inet static
address 192.168.1.1
gateway 192.168.1.1
dns-nameservers 192.168.1.254
netmask 255.255.255.0
```

---

### Post by Iowan on 2009-12-31
Easy way is **ifconfig -a > ~/filename.txt** That'll copy results of **ifconfig -a ** into a file in your home directory named **filename.txt**. From there you can copy to a floppy/usb-stick to move to another machine, or you can open it with a text editor and use copy/past there. Another option is to click/drag to highlight the text, then in another window (or from browser), click center mouse button (or both left/right buttons simultaneously) to paste the highlighted text.

---

### Post by anthony2k12 on 2009-12-31
This is really weird, **ifconfig -a** did not return any results. I tried it with and without sudo and with and without -a, neither gave me any results. 

For **sudo lshw -C network** it said command not found.

[B]e:
[/B]Duh, when I outputted to the .txt it doesn't print any results. My bad.

**e2:**
Looks like I can't boot into the GUI for XBMC anymore so I can't figure out how to copy over the filename.txt. When I attempt to return I'm met ith a "could not connect to X server" error.

---

