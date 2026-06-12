---
title: "how to configure broadband connection"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by cool3019 on 2010-04-23
hi all
i m new to linux world , i really want to learn linux 
so i decided to start with ubuntu
but the problem is that i have broadband connection at home so want to use it but dnt know how to exactly configure this in ubuntu 9.10 desktop 
can any one help me
pls
thanks in advance
:)

---

### Post by dannyboy79 on 2010-04-23
most recent systems will "just work".
 did you install ubuntu yet?
did you click on firefox? 
what is your setup? do you have a firewall/router or just a modem directly to your computer?

answer the above questions in a response and then go to apps, then accessories, then choose Terminal. once in there, enter this command and post back the results from entering the command. it should spit out a lot of text.
```
sudo lspci
```
it should report your ethernet chipset so we know what module (driver in windows speak) to ensure is installed properly in our system.
you could also try this:
```
dmesg | grep eth0
```

DONT FORGET, YOU WANT HELP, THEN PLEASE PROVIDE ALL THE INFO THAT I HAVE REQUESTED. OTHERS WILL WANT TO KNOW THE SAME THINGS IF THEY TRY TO HELP.

---

### Post by Iowan on 2010-04-23
There are a few threads mentioning BSNL - if that happens to be your provider. I'm a bit spoiled, since my DSL modem acts like a router - all I need to do is configure the machine for DHCP. I can find a few links if your [Search]("http://ubuntuforums.org/search.php") doesn't turn up anything.

---

### Post by cool3019 on 2010-04-24
sorry i forgot to add one thing more
i have installed microsoft virtual pc and then installed ubbuntu 
but   i think it is not making ny diffrence since ICS is workig well through ethernet card 
 
then i used ur first command said and output is 


00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 20)



then i used second command and output is as 



[   28.624887] eth0: Digital DS21140 Tulip rev 32 at Port 0xec00, 00:03:ff:e9:31:d5, IRQ 11.
[   48.400752] eth0: Using EEPROM-set media 100baseTx-FDX.
[   60.864792] eth0: no IPv6 routers present


 so waiting for ur reply

---

### Post by dannyboy79 on 2010-04-24
awaiting answers to all my questions

---

### Post by cool3019 on 2010-04-26
i have installed ubuntu 9.10 on my dell inspiron 1525 laptop
i have modem directly connected to my computer
no there is no more microsoft virtual pc so now output of the first command is




00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)




and output of the second command is 



coolcool@coolcool-laptop:~$ dmesg | grep eth0
[    2.265700] sky2 eth0: addr 00:21:9b:e8:31:d5
[   14.577821] sky2 eth0: enabling interface
[   14.578015] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.044587] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   16.044776] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.112042] eth0: no IPv6 routers present


i think this is the information u were asking for 
thanks

---

### Post by cool3019 on 2010-04-26
last time i tried to configure adsl connection using pppoeconf command then next time i found my networking is disabled , i dnt know whether this problem was caused by ny misconfiguration of adsl
after that i could not get my networking enabled because i had no control on network connections 
and i had to reinstall ubuntu
can u tell me please why networking was disabled and what i should have done get that working again rather than reinstalling os again
please answer this i got stuck badly in this 
thanks in advance

---

### Post by dineshs on 2010-04-26
If```
ifconfig
```doesnt show a valid  IP address try to assign it manually
Right-click on the nm-applet and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 8.8.8.8 
then click apply 
Note :The IP addresses are examples.Substitute your values

If you are using NM do this
```
gksudo gedit /etc/network/interfaces
``` 
The file should contain only this 
```
auto lo 
iface lo inet loopback
``` 

Who is your ISP.What is the modem?

---

### Post by dannyboy79 on 2010-04-26
if you rely on on a dsl connection and need to enter ISP provided info to connect then I am not sure if you can use Network Manager. I found this here:
[http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem](http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem)
when you say that your networking was disabled can you please explain EXACTLY what you mean. provide log files etc etc.

---

### Post by cool3019 on 2010-05-02
thanks for replying 
when i said that my networking was disabled then it was like i could not edit my network connections 
whenever i put my cursor on networking applet then it showed me that my networking was disabled
then i tried to create new ethernet connection but that also not worked.....
i dnt know what was happened 
whenever i typed ifconfig then it shown me eth0 but its ipv4 infromation was not given
sorry i can provide u ny log file coz i have reinstalled os

---

