---
title: "Netgear GA311 help: '*-network:1 UNCLAIMED'"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by swm5126 on 2010-02-27
Hi,

I just recently installed a fresh copy of 9.10 server on an older machine I had laying around to use as a router and home server. Everything is setup and I'm on the net on it, except for some reason the Netgear GA311 I'm using for the internal network doesn't seem to be loading a driver.

I've tried modprobing 8139 (which it says isn't found) as well as 8139too, 8139 too goes through ok, but it doesn't make any change, with lshw still claiming that it is "unclaimed".

It seems that the Realtek chipset this card is based on is extremely compatible with Linux and I'm having trouble finding anyone with a similar issue with it. 

Any ideas?

---

### Post by chili555 on 2010-02-27
I think r8169 is the driver, actually. Let's find out. Please post:```
lspci -nn
```Thanks.

---

### Post by swm5126 on 2010-02-27
The computer I'm using actually has 3 NICs, one onboard, and two PCI cards. Both the built in card and the 100mbit PCI card are working fine, it's just the gigabit card that isn't working.

```
scott@ubuntu-server:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
01:07.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
01:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:0169] (rev 10)
01:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)

```

---

### Post by chili555 on 2010-02-27
> Realtek Semiconductor Co., Ltd. Device [[COLOR="Blue"]10ec:0169[/COLOR]] (rev 10)This is problematic. As far as I have been able to learn, there is no native Linux driver. Maybe we can find one and build it from Realtek's site: [http://www.realtek.com.tw/search/default.aspx?keyword=gigabit](http://www.realtek.com.tw/search/default.aspx?keyword=gigabit)

Let's see if we can find more detailed information about it. Please do:```
sudo lspci -vv
```Discard all the data relating to all other devices except our subject and post it here.

If one of my esteemed colleagues reads this and is aware of a viable driver for 10ec:0169, I am anxious to know.

---

### Post by swm5126 on 2010-02-28
Here goes

```
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Device 0169 (rev 10)
	Subsystem: Netgear Device 311a
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at e800 [disabled] [size=256]
	Region 1: Memory at 7ea00000 (32-bit, non-prefetchable) [disabled] [size=256]
	[virtual] Expansion ROM at 14000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

---

### Post by swm5126 on 2010-02-28
There is a driver listed on their site: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I downloaded it, I'm having a little trouble trying to compile it though.

```
scott@ubuntu-server:~/src/realtek/r8169-6.012.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/scott/src/realtek/r8169-6.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/scott/src/realtek/r8169-6.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/scott/src/realtek/r8169-6.012.00/src'
make -C /lib/modules/2.6.31-19-generic-pae/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic-pae'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/scott/src/realtek/r8169-6.012.00/src'
make: *** [modules] Error 2

```

---

### Post by chili555 on 2010-02-28
First, our verbose lspci doesn't really tell us much we didn't already know, unfortunately.

I downloaded and built, without error or warning, the file you referenced. It looks like you are missing the building tools:```
sudo apt-get install build-essential
```However, the built module doesn't alias your device.> root@LAPTOP40:/home/chili/r8169/r8169-6.012.00# modinfo r8169
filename:       /lib/modules/2.6.31-19-generic/kernel/drivers/net/r8169.ko
version:        6.012.00-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     EF4B27028AC0BF354ED4EF0
alias:          pci:v000010ECd0000[COLOR="Blue"]8169[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000010ECd0000[COLOR="Blue"]8167[/COLOR]sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31-19-generic SMP mod_unload modversions 586 
--- snip ---We are looking for 0169, and the built module aliases 8169 and 8167.

However, I have attempted a fix. Since I don't have the device, I have no way to try it. You will have to be our test pilot.

Since you have already tried unsuccessfully to build the module, after you install build-essential, cd to the correct directory and do:```
sudo make clean
sudo gedit src/r8169_n.c
```Go down to line 115 and change from this:> static struct pci_device_id rtl8169_pci_tbl[] = {
        	{ PCI_DEVICE(PCI_VENDOR_ID_REALTEK,	0x8167), 0, 0, RTL_CFG_0 },
	{ PCI_DEVICE(PCI_VENDOR_ID_REALTEK,	0x8169), 0, 0, RTL_CFG_0 },
	{0,},
};To this:> static struct pci_device_id rtl8169_pci_tbl[] = {
        { PCI_DEVICE(PCI_VENDOR_ID_REALTEK,     0x0169), 0, 0, RTL_CFG_0 },
	{ PCI_DEVICE(PCI_VENDOR_ID_REALTEK,	0x8167), 0, 0, RTL_CFG_0 },
	{ PCI_DEVICE(PCI_VENDOR_ID_REALTEK,	0x8169), 0, 0, RTL_CFG_0 },
	{0,},
};As you can see, we have just added your 0169 device. Proofread carefully, **making especially sure to match the indentation in the original file,** save and close gedit.

Now build the module according to the readme:> # make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# modprobe r8169Now run:```
ifconfig
```Did your card now appear as eth2, perhaps?

---

### Post by swm5126 on 2010-02-28
I'll give it a shot in a minute to see if that works. The strange thing is that I did have build-essential when I tried to build that. Not sure what I was doing wrong but I'll try again.

---

### Post by swm5126 on 2010-02-28
Tried it with your modification, but I still can't get it to build after cleaning it even. I did confirm that I have build-essential installed and it is up to date. I am getting the same errors while running 'sudo make clean modules' as before.

---

### Post by chili555 on 2010-02-28
Can you confirm that you have linux-headers installed matching your running kernel?```
ls /usr/src | grep `uname -r`
```If not, please install through Synaptic and try, try again.

---

### Post by swm5126 on 2010-02-28
Yeah, I just checked into that.

```
scott@ubuntu-server:~$ ls /usr/src | grep `uname -r`
linux-headers-2.6.31-19-generic-pae

```

Tried a few different things Googling symlinking some things, nothing has worked so far. I may just end up taking the adapter back. As much as I'd like to make this one work, it's really frustrating because apparently all of the other GA311s use the chipset which seems to be supported. :(

---

### Post by chili555 on 2010-02-28
WAIT!

Here is what I get with 'sudo make clean modules:'> $ sudo make clean modules
[sudo] password for chili: 
make -C src/ clean
make[1]: Entering directory `/home/chili/r8169/r8169-6.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/chili/r8169/r8169-6.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/chili/r8169/r8169-6.012.00/src'
make -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/chili/r8169/r8169-6.012.00/src'
make: *** [modules] Error 2
And here is what I get with:```
sudo su
make clean modules
```> # make clean modules
make -C src/ clean
make[1]: Entering directory `/home/chili/r8169/r8169-6.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/chili/r8169/r8169-6.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/chili/r8169/r8169-6.012.00/src'
make -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/home/chili/r8169/r8169-6.012.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/chili/r8169/r8169-6.012.00/src/r8169_n.o
  LD [M]  /home/chili/r8169/r8169-6.012.00/src/r8169.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/r8169/r8169-6.012.00/src/r8169.mod.o
  LD [M]  /home/chili/r8169/r8169-6.012.00/src/r8169.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
strip --strip-debug r8169.ko
make[1]: Leaving directory `/home/chili/r8169/r8169-6.012.00/src'No errors and no warnings. Why is 'sudo su' working and plain old 'sudo' not? I dunno, but it probably will get your device working.

---

### Post by swm5126 on 2010-02-28
Crap!

I had just left when you replied, I didn't even think of that. I was just able to compile it perfectly fine, but now I'll never know if it would have worked! Damn me for not waiting.

I ended up exchanging it for a Linksys card, which as the SAME exact Realtek chip on it as the Netgear card did, but it works perfectly fine! I'm sort of baffled.

---

### Post by chili555 on 2010-02-28
> I had just left when you replied,> WAIT!Hey, I yelled as loud as I could!

Here's the upside. Your wireless is working and you are a happy Ubuntu camper. As well, some searcher with an 0169 chipset is going to learn from our experience.

Glad it all worked out, no matter what it took.

---

### Post by swm5126 on 2010-02-28
Yeah I'm sure they will!

The only thing I could find when I was searching about the chipset was our own conversation on the forums here!

Thanks again though for all your help, nice to have people like you that are willing to provide help to people when sometimes it seems like there isn't always an answer.

---

### Post by wreckgar23 on 2012-10-13
Thought it would be good to confirm on this thread that (2.5 years later) I have a working network card thanks to the info on this thread - cheers!

---

### Post by wildmanne39 on 2012-10-13
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

