---
title: "NIC 3c509b activaction"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by Lurkos on 2006-01-31
My Nic is a 3com EtherLink III 3c509b ISA.
I disable pnp of the nic using the dos utility and I set IRQ=3 and IO=0x300.
During the installation of Ubuntu 5.10 I manually load 3c509 module (sudo modprobe 3c509). So the installer recognised my NIC and configured it with DHCP.
After the installation, I add the line "3c509" in /etc/modules to load the module at boot time.
When I reboot the system 3c509 module is loaded, but my NIC isn't up.
I have to activate it using "sudo ifconfig eth0 up".
How can I activate my NIC during the boot?
It's very boring to type every time "sudo ifconfig eth0 up" ...

---

### Post by Lambert on 2006-01-31
In your /etc/network/interfaces file it should look something like this.

auto eth0

iface eth0 inet dhcp


This is for dhcp setup but notice the auto eth0 line. This should activate the nic during boot.

If this is there then there's something else happening where the nic isn't ready until after the networking script runs which is where the nic would be activated.

---

### Post by sup on 2006-01-31
> I disable pnp of the nic using the dos utility and I set IRQ=3 and IO=0x300.
Coul you please be more specific to how you do this? You mean BIOS by dos utility or what? Also, how did you find out you need set IRQ=3 and IO=0x300? I have been struggling with this card for some time with not much success all I get is this message in dmesg, but I have no idea what it means 
```
[  122.889116] pnp: Device 01:01.00 activated.
[  122.948486] eth1: 3c5x9 found at 0x220, BNC port, address  00 20 af c0 73 fbIRQ 5.
```
and I am ableto see the card with ifconfig -a :-/

---

### Post by az on 2006-01-31
The linux kernel does not play with PnP.  It cannot handle a ressource conflict.  Be sure that your card is not trying to steal an irq from another piece of hardware.  You can give priority to the isa bus for some irqs in your bios, usually.

---

### Post by Lurkos on 2006-02-01
[QUOTE=sup]Coul you please be more specific to how you do this? You mean BIOS by dos utility or what? Also, how did you find out you need set IRQ=3 and IO=0x300?
[/QUOTE]

I downloaded Etherdisk (floppy #1 and #2) from the 3com site.
You need the second disk to configure this NIC, and very often the file downloaded is damaged. :-/
(If you want I can email you theese files)
I tried lots of time and I wrote to 3com and so I obtain the image of the second disk of Etherdisk.
Then, under Windows 98, I unpacked it and I run preinstl.exe. This application says you which IRQs are free .
Then I run 3c5x9cfg.exe under DOS and I configured (F4) the IRQ and the IO (I check the addresses that aren't yet used by another hardware). There are others settings that you can change, e.g. full duplex / half duplex, enable / DISABLE pnp, setting the transceiver (normally 10baseT - RJ-45) ...
Then I run the NIC test to verify that everything is ok.
On GNU/Linux I add "3c509" on /etc/modules and "auto eth0
iface eth0 inet dhcp" on /etc/network/interfaces and the NIC works fine.

> 
I have been struggling with this card for some time


Me too :-)
I spent lots of hours to understand how can I set up this NIC.

> 
with not much success all I get is this message in dmesg, but I have no idea what it means 
```
[  122.889116] pnp: Device 01:01.00 activated.
[  122.948486] eth1: 3c5x9 found at 0x220, BNC port, address  00 20 af c0 73 fbIRQ 5.
```
and I am ableto see the card with ifconfig -a :-/

I'm not sure, anyway try to disable the PnP feature of the NIC.
You NIC is a 3c509 or a 3c509b?

---

### Post by Lurkos on 2006-02-01
[QUOTE=Lambert]
In your /etc/network/interfaces file it should look something like this.

auto eth0

iface eth0 inet dhcp

This is for dhcp setup but notice the auto eth0 line. This should activate the nic during boot.
[/QUOTE]

Thanks! It's works fine.
Now I am another problem ... :-/
During the boot Ubuntu tries to connect to ntp.ubuntulinux.org to update the system clock.
My NIC is connected with an ADSL modem and I don't want to enable the connection to the Internet during the boot.
So Ubuntu spends several minutes trying to connect to ntp.unbuntulinux.org and then reports and error.
Can I disable the clock syncronization?
Want file must I have to modify?
Thanks.

---

### Post by Lambert on 2006-02-01
sudo update-rc.d -f ntpdate remove

This removes the link in the rcX directory so it won't start at boot. In the future you can add it back if desired with the same command, different options. Read the man page for more info.

---

### Post by sup on 2006-02-06
> You NIC is a 3c509 or a 3c509b?
I actually have both. Yesterday I tried 3c509 and DSL (I am trying another dsitro on that computer, it is way too slow for Ubuntu) and it did not detect it at all, I had to modprobe the module and even then it worked bad (when IK tried to set up DHCP, it did not even tried). 3c509b is detected during bootup, but I cannot ping anywhere (DHCP is not working nor is static address). I ahve been playing with BIOS a lot, but with no success. I do not know why, could be a problem that I use non-crossed utp for connection to router (which has a crossover - it works flawl&#367;essly with another NIC)

Anyway, couold you please send me those files you spoke of to [email]tomashnyk@gmail.com[/email]

---

