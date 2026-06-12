---
title: "Bigfoot K1 Linux Driver installation"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by Castle_Romeo on 2011-02-14
I have a Killer K1 NIC Card made by Bigfoot and I am thinking of putting it in my linux box.

Linux drivers are available for this card;_** I need to know how to INSTALL the drivers.**_ The drivers are not .tar.gz or .tgz , they are .ZIP format.

Thanks in advance.

---

### Post by cascade9 on 2011-02-14
I wouldnt be suprised if it ran 'out of the box'. The K1 has been around for a long time. It would be pretty ironic if it didnt, seeing how the K1 has a linux based OS running on the card....

If it doesnt, you'll have to hope it works with newer linux distros, muddle though the makefile process, and curse that bigfoot didnt give you any directions

If you arent using windows on the same system, I would just sell the K1 and use the onboard NIC, or an addon PCI or PCIe NIC. Any advatnages you get from the K1 will not be there with linux- 

>  Killer™ 2100 replaces the Window's network stack with a low latency Network Processing Unit specifically designed for online gaming. 

[http://www.bigfootnetworks.com/support-faq/#Q21](http://www.bigfootnetworks.com/support-faq/#Q21)

AFAIK the K1 did the same trick.

---

### Post by Nyrobie on 2011-05-13
I also need help with this can anyone help with the process? 

This is what I got when I tried to use the make command. 

root@halo-two:/home/soren/Downloads/linux_drv_v1.2_20080801# make
make -C /lib/modules/2.6.38-8-generic/build M=/home/soren/Downloads/linux_drv_v1.2_20080801
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/soren/Downloads/linux_drv_v1.2_20080801/built-in.o
  CC [M]  /home/soren/Downloads/linux_drv_v1.2_20080801/killer.o
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c: In function &#8216;killer_alloc_rx_pool&#8217;:
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:379:9: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:99:1: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;__le32&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:379:9: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
include/asm-generic/pci-dma-compat.h:99:1: note: declared here
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:401:17: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:99:1: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;u32&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:401:17: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
include/asm-generic/pci-dma-compat.h:99:1: note: declared here
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c: In function &#8216;killer_open&#8217;:
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:523:9: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:99:1: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;u32&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:523:9: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
include/asm-generic/pci-dma-compat.h:99:1: note: declared here
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:547:9: warning: passing argument 1 of &#8216;pci_dma_mapping_error&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:99:1: note: expected &#8216;struct pci_dev *&#8217; but argument is of type &#8216;u32&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:547:9: error: too few arguments to function &#8216;pci_dma_mapping_error&#8217;
include/asm-generic/pci-dma-compat.h:99:1: note: declared here
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c: In function &#8216;probe&#8217;:
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:736:15: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:737:15: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:738:15: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:739:15: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:740:15: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/home/soren/Downloads/linux_drv_v1.2_20080801/killer.c:741:15: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
make[2]: *** [/home/soren/Downloads/linux_drv_v1.2_20080801/killer.o] Error 1
make[1]: *** [_module_/home/soren/Downloads/linux_drv_v1.2_20080801] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

Also this is 11.04 fresh install. I have the linux headers and the build-essentials pack

---

### Post by Nyrobie on 2011-05-14
Do I need to make my own thread to get help?

---

### Post by chili555 on 2011-05-14
> **Nyrobie said:**
> Do I need to make my own thread to get help?Nope.> linux_drv_v1.2_[COLOR="Red"]2008[/COLOR]0801It is unlikely that a driver made in 2008 is going to compile in 2.6.38. Please post:```
lspci -nn
```We can probably find a better driver.

---

### Post by Nyrobie on 2011-05-14
> **chili555 said:**
> Nope.It is unlikely that a driver made in 2008 is going to compile in 2.6.38. Please post:```
lspci -nn
```We can probably find a better driver.

```

soren@halo-two:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:03.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1) [1022:960b]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GTX] [10de:0612] (rev a2)
02:00.0 Audio device [0403]: Creative Labs X-Fi Titanium series [EMU20k2] [1102:000b] (rev 03)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
04:06.0 Power PC [0b20]: Freescale Semiconductor Inc MPC8343E [1957:0086] (rev 30)

```

---

### Post by chili555 on 2011-05-15
> Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)I assume this is your Bigfoot. It is claimed by the module *atl1e* which is built in to the Natty kernel. Let's load it and see what happens:```
sudo modprobe atl1e
ifconfig
dmesg | grep atl
```Thanks.

---

### Post by Nyrobie on 2011-05-15
nope that is the built in motherboard card. I have been using that but I am dual booting this computer with windows so in windows I use the big foot card so at the moment I have 2 cables going into my pc and I would like to make it just 1. 

So since that's the only card it saw it doesn't even see the big foot NIC??

---

### Post by chili555 on 2011-05-15
> So since that's the only card it saw it doesn't even see the big foot NIC??Evidently not. It's not a USB device, is it?```
lsusb
```Are you quite sure it's not defective?

---

### Post by Nyrobie on 2011-05-15
Its not USB and no it works perfectly under windows 7. Its PCI not PCI-e like the new ones.

---

### Post by Nyrobie on 2011-05-15
I did some digging for you the Killer NIC is 

04:06.0 Power PC [0b20]: Freescale Semiconductor Inc MPC8343E [1957:0086] (rev 30)

---

### Post by chili555 on 2011-05-15
It looks like way more than a NIC; it looks like a whole system!

[http://www.chipcatalog.com/Motorola/MPC8343E.htm](http://www.chipcatalog.com/Motorola/MPC8343E.htm)

I'm not sure I have any ideas/talent/mojo to help here. I'm studying...

---

### Post by Nyrobie on 2011-05-15
Thanks for trying. Guess ill just have to keep 2 NICs plugged in or get rid of Ubuntu. =/

---

### Post by TechZilla on 2011-07-17
check this thread out! At the bare minimum, i believe this might set you in the right direction.

[size=1][http://www.bigfootnetworks.com/KillerForums/showthread.php?2703-Help-needed-with-Linux-driver-installation](http://www.bigfootnetworks.com/KillerForums/showthread.php?2703-Help-needed-with-Linux-driver-installation)[/size]

Now this is from '09, but it just might work, or work with more changes.
Post back if anyone gets this working, post the files/patches if possible.

BTW, many of the Bigfoot NIC cards (possibly all?) are SOC embedded Linux systems.  They really should open up the whole firmware so people can create mods/forks/distros

---

