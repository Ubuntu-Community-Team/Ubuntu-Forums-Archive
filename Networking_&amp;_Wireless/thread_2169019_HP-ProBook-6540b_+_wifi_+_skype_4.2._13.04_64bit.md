---
title: "HP-ProBook-6540b + wifi + skype 4.2. 13.04 64bit"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by Laz77 on 2013-08-20
For the longest time I've had this extremely annoying issue with my wireless  if (and ONLY if) skype is running.

Basically the scenario is that I have one or more terminal sessions open and suddenly they freeze and I get the "Write failed: Broken pipe". This is very risky behavior because I often loose my ssh session in the middle of doing something (potentially risky) on the remote server.

I'm not sure what info to supply but here's a bit.

{code}
ln@ln-HP-ProBook-6540b:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4350/4550]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
44:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
44:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
44:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
45:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
46:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
{/code}

If anyone is willing to helpo me trouble shoot I will be very grateful.

---

### Post by chili555 on 2013-08-20
I suggest you try this: [http://ubuntuforums.org/showthread.php?t=2168188](http://ubuntuforums.org/showthread.php?t=2168188)

---

### Post by Laz77 on 2013-08-20
Thanks a lot for your suggestion however it did not make a difference. I also tried rebooting but still no luck.

I was tailing some output in my ssh session and then I made a test call.... Write failed: broken pipe shortly after :mad:

---

### Post by chili555 on 2013-08-20
You may as well remove the unhelpful entry:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Remove the line you added:```
options iwlwifi 11n_disable=1
```Leave the remainder unchanged. Proofread, save and close gedit.

Is this helpful? [http://ubuntuforums.org/showthread.php?t=2155094](http://ubuntuforums.org/showthread.php?t=2155094)> I restored the sshd_config file back to its original. Now when I try to login the broken pipe error is no longer coming up.


---

### Post by Laz77 on 2013-08-20
Thanks for bearing with me. I checked out that post but I have been digging into various ssh problems and i'm pretty sure that this isn't the cause of the issue. Since the problem only occurs when skype is running one should think that it has something to do with it - one way or another. I suppose it could also be a local network issue. I'm on a fiber modem which is connected to a cisco ASA for VPN purposes and to this I have connected my acces point which I then connect to.

There are a lot of possible reasons but what annoys me the most is that there seem to NO output in the syslogs when it occurs. I have been running a ' tail -f /var/log/* ' to see if anything was written but it's not the case. Pretty hard to trouble shoot in that case!


EDIT: I just power cycled my entire setup. So far no problems but it's no guarantee. It also never occured to me to test it on my windows machine. If the same problem exists there then It must be a local network conf issue and I regret to have wasted your time. We shall see.

---

### Post by chili555 on 2013-08-20
No worries at all. I enjoy new, different problems; at least different to me. A pleasant break from the 'my Broadcom wireless doesn't work and I don't know how to Google.'

---

### Post by Laz77 on 2013-08-22
:D 

Just an an update I have now verified it to be a problem of skype and my cisco firewall. Good thing though is that I've found a work-around which is to start up software VPN client... yeah software vpn through a hardware vpn :-s
I know jack about this stuff but it works now so who cares!

Thanks again

---

