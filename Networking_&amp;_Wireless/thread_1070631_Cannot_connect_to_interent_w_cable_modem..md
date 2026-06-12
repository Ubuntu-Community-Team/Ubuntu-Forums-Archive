---
title: "Cannot connect to interent w/ cable modem."
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Lopezadl2ian on 2009-02-15
Hello,

I am having problems connection to the internet with my cable modem. My cable modem is currently connected to a Netgear router which then connects to my computer with an Ethernet cable. I ran the following command: [COLOR="Blue"]dmesg | grep eth[/COLOR] After typing that command I got the following output.

First line: [COLOR="Red"][ 5.002180] Driver 'sd' needs updating [COLOR="Red"][/COLOR]- please use bus_type methods[/COLOR]

Second line: [COLOR="Red"][ 6.737344] Driver 'sr' needs updating - please use bus_type methods[/COLOR]

What does it mean by driver 'sd' and driver 'sr' as well as bus_type methods?and how can i fix this? Thanks.

---

### Post by chili555 on 2009-02-15
It has nothing to do with your ethernet. I have it in dmesg and I suspect most here do. It can safely be ignored. You got it because you asked for occurences of the pattern 'eth' and grep reported:> [ 5.002180] Driver 'sd' needs updating - please use bus_type m[COLOR="Red"]eth[/COLOR]odsLet's troubleshoot your wired connection with the output from:```
ifconfig
sudo lshw -C network
```Thanks.

---

### Post by Lopezadl2ian on 2009-02-15
Thanks for info. When i ran the ifconfig command I got the following output:

[COLOR="Red"]lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       UP LOOPBACK RUNNING  MTU: 16436  METRIC:1
       RX packets:864 errors:0 dropped:0 overruns:0 frame:0
       TX packets:864 errors:0 dropped:0 overruns:0 frame:0
       collision:0 txqueuelen:0
       RX Bytes:53568  (53.5 KB) TX bytes:53568 (53.5 KB)[/COLOR]

And when I enter the sudo lshw -C network command i get the following output:

[COLOR="Red"]*network DISABLED
     description:Ethernet interface
     physical id: 1
     logical name: pan0
     serial: 7a:be:98:a3:49:cf
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3
                    firmware=N/A link=yes mlticast=yes[/COLOR]

---

### Post by chili555 on 2009-02-15
Hmmmm...

That's as little information as I have ever seen! Let's try another command:```
lspci | grep -i ether
```I am wondering why, what is apparently your ethernet card, is shown as 'DISABLED.'

---

### Post by Lopezadl2ian on 2009-02-15
Ya I was thinking the same thing. When i typed the lspci | grep -i ether command it just returned with a blank command line.

---

### Post by chili555 on 2009-02-16
This just gets weirder and weirder! May we please see the entire result of:```
lspci
```What can you tell me about your ethernet interface? Is it built in to a desktop machine or a laptop or is it an add-in card? What is the make and model of your computer and, if applicable, your ethernet card.

---

### Post by Lopezadl2ian on 2009-02-17
> **chili555 said:**
> This just gets weirder and weirder! May we please see the entire result of:```
lspci
```What can you tell me about your ethernet interface? Is it built in to a desktop machine or a laptop or is it an add-in card? What is the make and model of your computer and, if applicable, your ethernet card.

It is built into the desktop. I just put the computer together about 1.5months ago. Motherboard: Gigabyte GA-EX58-UD4P with i7 Intel processor. Internet was working with previous XP/Vista install.

When I type the command [COLOR="Red"]lspci[/COLOR] i get the following output:
```
ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation QuickPath Architecture I/O Hub to ESI Port (rev 12) 
00:01.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 1 (rev 12) 
00:03.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 3 (rev 12) 
00:05.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 5 (rev 12) 
00:07.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 7 (rev 12) 
00:09.0 PCI bridge: Intel Corporation QuickPath Architecture I/O Hub PCI Express Root Port 9 (rev 12) 
00:10.0 PIC: Intel Corporation QuickPath Interconnect Physical and Link Layer Registers Port 0 (rev 12) 
00:10.1 PIC: Intel Corporation QuickPath Interconnect Routing and Protocol Layer Registers Port 0 (rev 12) 
00:11.0 PIC: Intel Corporation QuickPath Interconnect Physical and Link Layer Registers Port 1 (rev 12) 
00:11.1 PIC: Intel Corporation QuickPath Interconnect Routing and Protocol Layer Registers Port 1 (rev 12) 
00:13.0 PIC: Intel Corporation QuickPath Architecture I/O Hub I/OxAPIC Interrupt Controller (rev 12) 
00:14.0 PIC: Intel Corporation QuickPath Architecture I/O Hub System Management Registers (rev 12) 
00:14.1 PIC: Intel Corporation QuickPath Architecture I/O Hub GPIO and Scratch Pad Registers (rev 12) 
00:14.2 PIC: Intel Corporation QuickPath Architecture I/O Hub Control Status and RAS Registers (rev 12) 
00:15.0 PIC: Intel Corporation Trusted Execution Technology Registers (rev 12) 
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) 
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller 
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller 
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2) 
04:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2) 
07:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
07:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
09:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
ubuntu@ubuntu:~$ 

```

---

### Post by chili555 on 2009-02-17
That's very weird! Your *lspci* looks like you have _no_ ethernet at all. Please do:```
dmesg > dmesg.txt
```That will create a text file of your boot messages in your user directory. Post a reply with *dmesg.txt *as an attachment. Let us scan through the messages to see what's going on.

It will be fairly long, so let's not copy and paste it, thereby flooding the forum.

I wonder if we have an IRQ conflict or if the AHCI controller is being naughty.

---

### Post by Lopezadl2ian on 2009-02-17
> **chili555 said:**
> That's very weird! Your *lspci* looks like you have _no_ ethernet at all. Please do:```
dmesg > dmesg.txt
```That will create a text file of your boot messages in your user directory. Post a reply with *dmesg.txt *as an attachment. Let us scan through the messages to see what's going on.

It will be fairly long, so let's not copy and paste it, thereby flooding the forum.

I wonder if we have an IRQ conflict or if the AHCI controller is being naughty.

When I try to attach the file it says that the file exceeds the Kb limit. Is there another way I can send you this txt file.

---

### Post by chili555 on 2009-02-17
Where you see it in your user directory, right-click it and select 'Create Archive.' Drop down the menu to .zip and click 'Create.' Then you can attach dmesg.txt.zip.

Even if it doesn't compress it very much, the forum's limit for .zip is much greater than .txt, inexplicably.

---

### Post by cariboo on 2009-02-17
HAve you got your ethernet controller turn off in the BIOS by any chance.?

Jim

---

### Post by Lopezadl2ian on 2009-02-17
> **cariboo907 said:**
> HAve you got your ethernet controller turn off in the BIOS by any chance.?

Jim

Will check when I get home tonight. I was pretty sure it was enabled but I will check again. thanks.

---

### Post by Lopezadl2ian on 2009-02-17
> **chili555 said:**
> Where you see it in your user directory, right-click it and select 'Create Archive.' Drop down the menu to .zip and click 'Create.' Then you can attach dmesg.txt.zip.

Even if it doesn't compress it very much, the forum's limit for .zip is much greater than .txt, inexplicably.

Zip file attached.Thanks!

---

### Post by chili555 on 2009-02-17
I will be away until Sunday afternoon US EST. I hope some other ethernet freaks will jump in here. See you when I get back.

---

### Post by Lopezadl2ian on 2009-02-17
Im going to try plugging in a NIC card I have laying around and see if I can establish a connection. Thanks for support.

---

### Post by Lopezadl2ian on 2009-02-18
> **cariboo907 said:**
> HAve you got your ethernet controller turn off in the BIOS by any chance.?

Jim

Yes, my Ethernet controller is enabled in BIOS.

---

### Post by Lopezadl2ian on 2009-02-21
Problem is fixed. I decided to install Fedora 10. When I actually installed the OS I still had the same problem. When I typed the command [COLOR="Red"]lspci[/COLOR] I now saw that there was something in the code that said "Gigabit Ethernet controller" finally. I typed the command [COLOR="Red"]sudo ifconfig eth0 up[/COLOR]. After that, went to network configurations and noticed that it said Auto eth0 in the wired tab. Now I have a connection to the internet. Thanks all for the help!!

---

### Post by Lopezadl2ian on 2009-03-20
Ubunutu failed to auto-configure my Ethernet card. I have attached a zip file containing various commands that I entered to obtain data about the Ethernet card that is integrated to my mother board. All the commands are in bold. Thanks!!

---

### Post by chili555 on 2009-03-21
This is crazy! In all the data you have submitted, there is no sign of your ethernet interface!!!

May I assume it is built in to the motherboard? What is the brand and model of the motherboard?> Im going to try plugging in a NIC card I have laying around and see if I can establish a connection.Did that work out?

---

### Post by Lopezadl2ian on 2009-03-21
> **chili555 said:**
> This is crazy! In all the data you have submitted, there is no sign of your ethernet interface!!!

May I assume it is built in to the motherboard? What is the brand and model of the motherboard?Did that work out?

Yes the card is integrated into the motherboard. Mother board type is: [http://tinyurl.com/dee6qh](http://tinyurl.com/dee6qh). I could not find my old NIC card. I wanted to by a new NIC card but I notice all the NIC cards that are for sale in stores say they only have driver support for the Windows OS. Could I still use an off the shelf NIC card? Thanks.

---

### Post by chili555 on 2009-03-22
I have Googled your motherboard quite a bit relative to Linux and having the ethernet interface not detected seems to be a common issue. I have yet to find a solution!

Let's check a thing or two. Please check the BIOS and verify that Onboard H/W LAN is Enabled, Green LAN is Disabled, and that the computer is hooked to a working ethernet connection. Then check the BIOS settings for SMART LAN to determine that the BIOS reports 'Link Detected' and no cabling errors. When you finish booting, is your NIC detected in *lspci*?

I did see this mysterious message in your *dmesg.txt*:> aer 0000:00:01.0:pcie01: AER service couldn't init device: no _OSC supportI think this has something to do with ACPI, however ACPI seems to be loading without complaints.> Could I still use an off the shelf NIC card?Certainly. Any old Linksys will work. I wouldn't trust the obvious store brands; Dynex, for example.

According to the motherboard manual, if you attach an add-on NIC, you will need to disable the built-in in the BIOS at Onboard H/W LAN.

[http://www.linuxquestions.org/hcl/index.php/cat/10](http://www.linuxquestions.org/hcl/index.php/cat/10)

---

### Post by Lopezadl2ian on 2009-03-23
I checked and I did have the ethernet controller actived in the BIOS. I picked up NIC card today and installed it as well. Afer I instaleld I I re-booted my computer and ubuntu deteded the NIC card and auto configured it. I can now make a connection to the internet. Sweet! I guess the Ethernet controller that is on in my motherboard is not compatible with Linux? Thanks Chilli!! Your awesome! *bows*

---

