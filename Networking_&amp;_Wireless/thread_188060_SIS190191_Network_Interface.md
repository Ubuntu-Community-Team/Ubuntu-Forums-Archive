---
title: "SIS190/191 Network Interface"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Gerbils on 2006-06-03
Hello,

I have just installed Ubuntu dapper drake. Unfortunatly I have problems getting my network interface working. I am using an Asus barebone model 	
T2-AE1 with a SIS190/191 Network Interface.

The download on sis.com is down. All I found was some very old driver for fedora core 3..

I have very little experience with linux/ubuntu.

Any advice?

---

### Post by Gerbils on 2006-06-04
I have send e-mails to asus and sis.

---

### Post by Paul Gibbons on 2007-03-27
I had a problem using any version of Linux with my system. 
I have since made a kernel change that seems to work for me.
I got the following output from the command dmesg:

[   43.613351] sis190 Gigabit Ethernet driver 1.2 loaded.
[   43.613412] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ
 23
[   43.613489] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   43.631843] 0000:00:04.0: Read MAC address from EEPROM
[   43.723849] 0000:00:04.0: Unknown PHY transceiver at address 0x

If you get the same then maybe my fix will help.

---

### Post by chennanbang on 2007-04-04
> **Paul Gibbons said:**
> I had a problem using any version of Linux with my system. 
I have since made a kernel change that seems to work for me.
I got the following output from the command dmesg:

[   43.613351] sis190 Gigabit Ethernet driver 1.2 loaded.
[   43.613412] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ
 23
[   43.613489] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   43.631843] 0000:00:04.0: Read MAC address from EEPROM
[   43.723849] 0000:00:04.0: Unknown PHY transceiver at address 0x

If you get the same then maybe my fix will help.

My ASUS T2-AE1 has the same problem.
How do you change the kernel, then install the ubuntu?
I can't wait to test your solution.:)

---

### Post by Paul Gibbons on 2007-04-05
Details of the change are given at:

[http://www.mail-archive.com/netdev@vger.kernel.org/msg34912.html]("http://www.mail-archive.com/netdev@vger.kernel.org/msg34912.html")

It simply involves adding a single line!

The change is for kernel version 2.6.20.

If you are able to build an install your own kernel then this should be enough. 
I am busy tonight but maybe tomorrow I can spend time checking out Ubuntu 2.6.17.

I hope this helps.


Paul

---

### Post by chennanbang on 2007-04-05
> **Gerbils said:**
> Hello,

I have just installed Ubuntu dapper drake. Unfortunatly I have problems getting my network interface working. I am using an Asus barebone model 	
T2-AE1 with a SIS190/191 Network Interface.

The download on sis.com is down. All I found was some very old driver for fedora core 3..

I have very little experience with linux/ubuntu.

Any advice?

I encounter the same situation.
My PC is ASUS T2-AE1, too.
One LiveCD made of ubuntu elements works on this machine. [https://answers.launchpad.net/ubuntu/+ticket/4635](https://answers.launchpad.net/ubuntu/+ticket/4635)
But I haven't make the ubuntu installation work.
Do you solve this problem?

---

### Post by chennanbang on 2007-04-05
> **Paul Gibbons said:**
> Details of the change are given at:

[http://www.mail-archive.com/netdev@vger.kernel.org/msg34912.html]("http://www.mail-archive.com/netdev@vger.kernel.org/msg34912.html")

It simply involves adding a single line!

The change is for kernel version 2.6.20.

If you are able to build an install your own kernel then this should be enough. 
I am busy tonight but maybe tomorrow I can spend time checking out Ubuntu 2.6.17.

I hope this helps.


Paul

Thanks, Paul,

It's nice to hear someone.
I know nothing about the kernel thing. I also ask my question here --> [https://answers.launchpad.net/ubuntu/+ticket/4635](https://answers.launchpad.net/ubuntu/+ticket/4635)
Please advise, thanks.

Regards.

---

### Post by Paul Gibbons on 2007-04-06
I have Ubuntu Edgy but the same instructions may work for Dapper.

OK you need to change the module called sis190.ko in the kernel.

sudo apt-get update 
sudo apt-get install build-essential

sudo apt-get install linux-source-2.6.17 ( this value depends on you version of Ubuntu)

cd /usr/src
sudo tar xvvf /usr/src/linux-source-2.6.17.tar.bz2  ( the exact name depends on the file downloaded above).
cd linux-source-2.6.17
sudo make menuconfig

select Exit and Yes to save configuration.

sudo gedit drivers/net/sis190.c
find the line
{ "Broadcom PHY BCM5461", { 0x0020, 0x60c0 }, LAN, F_PHY_BCM5461 }
and add the additional line
{ "Broadcom PHY AC131",   { 0x0143, 0xbc70 }, LAN, 0 },

so that the surrounding lines look like:

	{ "Broadcom PHY BCM5461", { 0x0020, 0x60c0 }, LAN, F_PHY_BCM5461 },
        { "Broadcom PHY AC131",   { 0x0143, 0xbc70 }, LAN, 0 },
	{ "Agere PHY ET1101B",    { 0x0282, 0xf010 }, LAN, 0 },

save the file and close the editor


sudo mkdir .tmp_versions
sudo make drivers/net/sis190.ko
sudo rmmod drivers/net/sis190.ko
sudo cp drivers/net/sis190.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo modprobe sis190

dmesg should now give output of the form:


[17184721.172000] sis190: version magic '2.6.17.14-ubuntu1 mod_unload K7 REGPARM gcc-4.1' should be '2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1'
[17184979.708000] sis190 Gigabit Ethernet driver 1.2 loaded.
[17184979.708000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 50
[17184979.708000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17184979.728000] 0000:00:04.0: Read MAC address from EEPROM
[17184979.860000] 0000:00:04.0: Broadcom PHY AC131 transceiver at address 1.
[17184980.372000] 0000:00:04.0: Using transceiver at address 1 as default.
[17184980.408000] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at f8a10000 (IRQ: 50), 0c:89:00:00:00:00
[17184980.408000] eth0: GMII mode.
[17184980.408000] eth0: Enabling Auto-negotiation.
[17184980.516000] ADDRCONF(NETDEV_UP): eth0: link is not ready


ifconfig should now show the device.
You need to change the settings using "networking" in the system settings somewhere.

Good luck

---

### Post by Paul Gibbons on 2007-04-06
If you still have the same problem I guess we need to add another line to sis190.c for your transceiver. To diagnose the problem add replace the line:

net_probe(tp, KERN_INFO "%s: %s transceiver at address %d.\n",
		  pci_name(tp->pci_dev),
		  (phy->type == UNKNOWN) ? "Unknown PHY" : p->name, phy_id);

with 
net_probe(tp, 
KERN_INFO "%s: %s trans at address 0x%x phy->id[0]= 0x%x phy->id[1]=0x%x.\n",
		  pci_name(tp->pci_dev),
		  (phy->type == UNKNOWN) ? "Unknown PHY" : p->name, phy_id, phy->id[0], phy->id[1]);


and repeat

sudo make drivers/net/sis190.ko
sudo rmmod drivers/net/sis190.ko
sudo cp drivers/net/sis190.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo modprobe sis190

This will identify the two hex values we need to identify the device. Note that the fouth digit of the second number must be set to 0 no matter what the above message states.
So for a  HP EX470 that uses a SIS966 southbridge with a sis196 PHY the output of the above is:
 Unknown PHY trans at address 0x0 phy->id[0]= 0x4d phy->id[1]=0xd016
and the solution is to add the line:
{ "Testing PHY",          { 0x4d, 0xd010 }, LAN, 0 },
to SiS191.c

---

### Post by chennanbang on 2007-04-08
Thanks, Paul!
Before testing your solution, I'd like to consult Gerbils about his installation on T2-AE1.
Because my installation on T2-AE1 failed after entering the desktop part.
So, I even can't use the Install icon on the desktop.
Gerbils, please advise.
Thanks.

---

### Post by Paul Gibbons on 2007-04-08
The instructions given are only suitable for situations where the OS installs and runs OK but for lack of network interface. In this case the command dmesg results in output of the form:

[ 43.613351] sis190 Gigabit Ethernet driver 1.2 loaded.
[ 43.613412] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ
23
[ 43.613489] PCI: Setting latency timer of device 0000:00:04.0 to 64
[ 43.631843] 0000:00:04.0: Read MAC address from EEPROM
[ 43.723849] 0000:00:04.0: Unknown PHY transceiver at address 0x

---

### Post by Muise on 2008-02-23
Thanks for the directions Paul, after making the changes, recompiling and doing a dmesg after loading the new version I got this info back: 
[I][B]
sis190 Gigabit Ethernet driver 1.2 loaded.
ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:04.0 to 64
0000:00:04.0: Read MAC address from EEPROM
0000:00:04.0: Unknown PHY trans at address 0x0 phy->id[0]= 0x4d phy->id[1]=0xd016.
0000:00:04.0: Using transceiver at address 1 as default.
0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at de812000 (IRQ: 17), 00:0a:e4:83:99:05
eth0: RGMII mode.
eth0: Enabling Auto-negotiation.[/B][/I]

---

### Post by Paul Gibbons on 2008-02-28
Hi Muise,
Given the output you have got so far I would suggest you try to add another line of the form:
{ "Broadcom PHY AC131", { 0x0143, 0xbc70 }, LAN, 0 },
to sis190.c that I added for my Sis190. From the values you have got the additional line should be 
{ "Anything", { 0x4d, 0xd010 }, LAN, 0 },
however you may need to change the 0 to 1,2 or 4.
Hope this helps
Paul

---

### Post by Muise on 2008-02-28
Thanks mate, I'll give that a try and let you know how it goes.

---

### Post by Muise on 2008-03-01
Tried it out, but unfortunately none of them (with 0, 1, 2, or 4 as the last parameter) changed the output dmesg was giving. It continues to say it's an unknown transceiver. I doesn't suppose you've got any other ideas that might help me out here?

---

### Post by Paul Gibbons on 2008-03-02
Sorry that has been unsuccessful.:( Please e-mail me your modified sis190.c to
paul (at) pkami (dot) e7even (dot) com.

---

### Post by Muise on 2008-03-06
Just an update on this, Paul and I have managed to get it up and running with the line

{ "SIS196 PHY", { 0x004d, 0xd010 }, LAN, 0 },

However we haven't gotten it to negotiate connections at gigabit speeds, so you may need to avoid bringing it online on a gigabit network for the time being.

---

