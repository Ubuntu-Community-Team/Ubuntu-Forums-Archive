---
title: "Ethernet connection problem"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by afspecops510 on 2009-01-22
I recently installed intrepid after having some windows problems and my computer will not connect to the internet via ethernet.  I tried lspci and it didn't list an ethernet network controller.  If it matters, the lights on the ethernet port (its built into the motherboard) light up when a cable is plugged in.  I encounter the same problem using network manager or wicd.  Any solutions?

---

### Post by Iowan on 2009-01-22
What kind of controller is it (or, lacking that, what kind of motherboard)?

---

### Post by yoyoned on 2009-01-22
post the output of lspci and ifconfig

---

### Post by afspecops510 on 2009-01-22
> **yoyoned said:**
> post the output of lspci and ifconfig

Heres ifconfig.  The formatting is a little screwed up but all the info is there:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host         
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3184 (3.1 KB)  TX bytes:3184 (3.1 KB)


pan0      Link encap:Ethernet  HWaddr 5a:32:6f:64:68:53 
	  inet6 addr: fe80::5832:6fff:fe64:6853/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B)  TX bytes:6091 (6.0 KB)

---

### Post by afspecops510 on 2009-01-22
> **yoyoned said:**
> post the output of lspci and ifconfig

Heres the lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

---

### Post by afspecops510 on 2009-01-22
> **Iowan said:**
> What kind of controller is it (or, lacking that, what kind of motherboard)?

Don't know the kind of controller but i assume its an nvidia one because all the chipsets on the mobo are nvidia.  the motherboard model is Chaintech VNF4 (yes it is a crappy one).

---

### Post by afspecops510 on 2009-01-22
I know under the lspci i have a wireless controller (TI ACX111) listed but i've run into problems with it before and i am now.  I know how to fix it because i've done it before but i need the internet on that computer.

---

### Post by Loosewheel on 2009-01-23
> **afspecops510 said:**
> Don't know the kind of controller but i assume its an nvidia one because all the chipsets on the mobo are nvidia.  the motherboard model is Chaintech VNF4 (yes it is a crappy one).

I believe the controller is 'vitesse vsc8201rx'.
And on this Ubuntu-8.04 system, I found 'vitesse.ko' in 
'/lib/modules/'uname -r'/kernel/drivers/net/phy'.

If that is the module, then maybe 'sudo modprobe vitesse -v'
followed by, '/etc/init.d/networking restart' may bring it up.

---

### Post by afspecops510 on 2009-01-23
> **Loosewheel said:**
> I believe the controller is 'vitesse vsc8201rx'.
And on this Ubuntu-8.04 system, I found 'vitesse.ko' in 
'/lib/modules/'uname -r'/kernel/drivers/net/phy'.

If that is the module, then maybe 'sudo modprobe vitesse -v'
followed by, '/etc/init.d/networking restart' may bring it up.

I ran 'sudo modprobe vitesse -v' and then '/etc/init.d/networking restart' but I still am unable to connect.  Is it possible that it is another network controller built into the motherboard?

---

### Post by afspecops510 on 2009-01-23
Ok, correction, I just inspected the mothergboard and found that the network controller is indeed the Vitesse VSC8201RX.  Are there any other ways around it?

Otherwise, is there a way to get a USR5416 wireless card to work  without updating Ubuntu (I have no internet access on the computer)?  As far as I know, that card uses the ACX111 chipset and ACX111 doesn't run out of the box with Intrepid.  I got an ACX to work before but I had to connect to ethernet to update ubuntu and then ran modprobe acx.

---

### Post by entrope on 2009-01-23
Maybe try the Windows driver with ndiswrapper? Check the ndiswrapper website to see if your card is supported.

---

### Post by Loosewheel on 2009-01-24
This was interesting:
LAN2 (nVidia CK804 Gigabit)
    OK. Works fine with the FORCEDETH net driver. Gigabit speeds should work but not tested yet.

From here:
[http://www.melb.apana.org.au/wiki/GAK8NUltra9](http://www.melb.apana.org.au/wiki/GAK8NUltra9)

Same nVidia chip using 'forcedeth' driver. Probably won't work, but it wouldn't take long to 'sudo modprobe forcedeth'.
If it did happen to work, you could add it to '/etc/modules'

---

