---
title: "Wireless not receiving data"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by tathedj on 2010-12-31
Hi All, and Happy New Year.

I'm relatively new to Ubuntu but have had it running on a desktop for the last couple of months, on a Lenovo ThinkCentre and running really well.

Unfortunately I have logged on this morning and it doesn't seem to want to connect to the internet and retrieve my emails.

I says it's connected to my router but is not receiving data packets?

Can anyone provide suggestions on how to trouble shoot?

Thanks in advance.

Cheers

Todd

---

### Post by PatchesTheCaveman on 2010-12-31
Hi tathedj!  Sorry you're having trouble with your wireless connection.

To try and see what's going on, we need to collect some information.  Go to Applications > Accessories > Terminal on your top panel, type the following in the black box that appears, and press Enter:
```
lspci -v
```

Then, copy what appears and paste it into a reply to this thread.

Next, type this and press Enter:
```
ifconfig -a
```
and copy/paste that too.

Then, type in this command and press Enter:
```
sudo iwconfig
```
It will ask you for your password.  Type it in, press Enter, and then copy what appears and paste in your reply.

Finally, type this and press Enter:
```
uname -r
```
and copy/paste the one line that outputs.

With all that, we should be able to figure out what's going on.

---

### Post by tathedj on 2010-12-31
Hi PatchesTheCaveman,

Here are the responses, [Note-the last instruction didn't seem to work!]

todd@Todd-Home-Desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at d0000000 (32-bit, non-prefetchable) [size=1M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 30e0 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d0404000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0500000-d06fffff
    Prefetchable memory behind bridge: 00000000d0700000-00000000d08fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 00000000d0900000-00000000d0afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 3020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 3040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 3060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d0404400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo Device 100d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 30b0 [size=16]
    I/O ports at 30a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: medium devsel, IRQ 9
    Memory at d0404800 (32-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at 3080 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Lenovo Device 100d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at 3410 [size=8]
    I/O ports at 3404 [size=4]
    I/O ports at 3408 [size=8]
    I/O ports at 3400 [size=4]
    I/O ports at 30d0 [size=16]
    I/O ports at 30c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Lenovo Device 100d
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d0100000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

todd@Todd-Home-Desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:61:5e:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3487 (3.4 KB)  TX bytes:3487 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:b0:0f:6c:3b  
          inet6 addr: fe80::222:b0ff:fe0f:6c3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46701 (46.7 KB)  TX bytes:105459 (105.4 KB)

todd@Todd-Home-Desktop:~$ [code]sudo iwconfig[/sudo]
[code]sudo: command not found

Hope this helps.

Cheers, Todd

---

### Post by tathedj on 2010-12-31
Hi there, just saw your updated post, details below:


todd@Todd-Home-Desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TXXXXXX"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:XX:XX:XX:XX:XX   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

todd@Todd-Home-Desktop:~$ uname -r
2.6.32-27-generic

---

### Post by PatchesTheCaveman on 2010-12-31
Try running this:
```
sudo iwconfig wlan0 rate 54M
```
and see if that improves your situation.

---

### Post by tathedj on 2010-12-31
> **PatchesTheCaveman said:**
> Try running this:
```
sudo iwconfig wlan0 rate 54M
```and see if that improves your situation.

Hi Patches, unfortunately this doesn't seemed to have helped. The wireless is connected to my router and I can get online with my laptop running windows, but unfortunately, no joy with Ubuntu?

---

### Post by tathedj on 2010-12-31
Patches, I have also just rebooted and logged in with Vista that I also have on the desktop and the wi-fi works perfectly, thus eliminating a hardware fault.

Hoping you might have another suggested fix.

Cheers,

Todd

---

### Post by PatchesTheCaveman on 2010-12-31
You can try installing updated drivers for your system.  To do so, first run this command on the terminal:
```
sudo apt-get update
```

From the information you provided earlier, it looks like you're running Ubuntu 10.04 Lucid Lynx (LTS).  If that's correct run this next:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

If you're running Ubuntu 10.10 Maverick Meerkat, run this command instead:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

When you have run those commands, you will need to reboot to let the new drivers take effect.

---

### Post by tathedj on 2010-12-31
Hi Patches,

Thanks for the advice, I appreciate the time you have given to my problem. I will attempt what you have suggested and post the results.

Cheers,

---

### Post by bkratz on 2010-12-31
@patches

I believe his/her problem is shown below in red


wlan0 IEEE 802.11bg ESSID:"TXXXXXX" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:XX:XX:XX:XX:XX 
Bit Rate=24 Mb/s Tx-Power=19 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Encryption keyoff
[COLOR="Red"]Power Managementon[/COLOR]
Link Quality=48/70 Signal level=-62 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Dual booted Windows systems like to use power management and ubuntu can't turn it back off.  I have seen several threads recently that gave the command to correct this, but I will have to find one--I don't remember the command--maybe you do!?  I will look though just in case.

---

### Post by tathedj on 2010-12-31
Hi Patches,

I have just rebooted my desktop and all seems to be working!!! Not sure why the error, but internet access is available and I am receiving emails.

Thanks for taking the time to help with my problem.

Cheers,

Todd

---

### Post by bkratz on 2010-12-31
N/A

Congratulations

---

