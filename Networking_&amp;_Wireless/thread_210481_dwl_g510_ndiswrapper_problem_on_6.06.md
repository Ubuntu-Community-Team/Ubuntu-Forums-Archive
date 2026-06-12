---
title: "dwl g510 ndiswrapper problem on 6.06"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by desicrew on 2006-07-06
I am posting here because no one is responding at the kubuntu forums - below is the cut and paste of what i wrote there - anyone PLEASE help

so i cleaned out everything pertaining to ndiswrapper i.e.
Code:
sudo modprobe -r mrv8k
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

and did a re-install following the directions and NOW...i have this message "mrv8k51 driver present, hardware present" OH YEA!!!

except that for some reason now wlan0 is not showing up in iwconfig even after i modprobed ndiswrapper!!!


here is the output i get when I dmesg - anyone willing to help!!?!?

[4294696.536000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294696.583000] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[4294696.583000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 19 (level, low) -> IRQ 209
[4294696.584000] ndiswrapper: using irq 209
[4294696.592000] ndiswrapper (miniport_init:240): couldn't initialize device: C0000001
[4294696.592000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[4294696.592000] ndiswrapper (miniport_halt:271): device dfbc0260 is not initialized - not halting
[4294696.592000] ndiswrapper: device eth%d removed
[4294696.592000] unregister_netdevice: device eth%d/dfbc0000 never was registered
[4294696.592000] ACPI: PCI interrupt for device 0000:00:10.0 disabled
[4294696.592000] ndiswrapper: probe of 0000:00:10.0 failed with error -22

---

### Post by orb9220 on 2006-07-07
I don't understand why all the driver ndis wrapper stuff.

I have D-Link GWL-510 and when I installed dapper 6 days ago it just
worked except they are restriced mode driver and I change the default wireless applets from wlan0 to ath0 and it work.

the 510 is B1 version which I think uses a different chipset than the earlier
510.

Hope you find a cure.

---

### Post by desicrew on 2006-07-07
see mine is version a.....the marvel one...not the athros(sp?) version....it neither kubuntu or ubuntu picks it up automatically :(  so i need a cure thru ndiswrapper

---

### Post by desicrew on 2006-07-07
anyone know where i can get the package for ndiswrapper 0.9 for dapper drake 'cause that's the version the used to work wonderfully on mandriva with this driver....figure i can try that...as my next step in figuring this out

---

### Post by desicrew on 2006-07-07
so i decided to make ndiswrapper 0.9 from source because thats the version that used to work for me on mandriva w/ my cards win2k drivers....

here's where i am stuck when i do make install - any suggestions???

root@gm-desktop:~/ndis/ndiswrapper-0.9# make install
make -C driver install
make[1]: Entering directory `/home/gm/ndis/ndiswrapper-0.9/driver'
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/gm/ndis/ndiswrapper-0.9/driver DRV_VERSION="0.9" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/gm/ndis/ndiswrapper-0.9/driver/wrapper.o
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:253:36: error: macro "halt" passed 1 arguments, but takes just 0
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c: In function ‘call_halt’:
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:253: warning: statement with no effect
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c: In function ‘ndis_suspend’:
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:867: error: too many arguments to function ‘pci_save_state’
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c: In function ‘ndis_resume’:
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:897: error: too many arguments to function ‘pci_restore_state’
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c: In function ‘ndis_init_one’:
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:1294: error: too many arguments to function ‘pci_restore_state’
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c: In function ‘start_driver’:
/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.c:1448: warning: assignment from incompatible pointer type
make[3]: *** [/home/gm/ndis/ndiswrapper-0.9/driver/wrapper.o] Error 1
make[2]: *** [_module_/home/gm/ndis/ndiswrapper-0.9/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gm/ndis/ndiswrapper-0.9/driver'
make: *** [install] Error 2

---

### Post by tturrisi on 2006-07-07
look here for a drive for that DLink card:
[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)

---

### Post by desicrew on 2006-07-07
see that's the reason i need ndiswrapper...'cause my version of the card is the Marvell Chipset not the Atheros or the Realtek.....so ndiswrapper is my only solution...as far as what i have read online....

---

### Post by desicrew on 2006-07-10
anyone? I have actually gone ahead and ordered a 50ft cat 5 cable....so I dont have to rely on the wireless card....but that's just sad! I hate to have to resort to that!

---

### Post by orb9220 on 2006-07-11
My friend downstairs bought a trendnet card for $17 and he said worked great.

Cheaper than cat 5

---

### Post by desicrew on 2006-07-12
which trendnet card was it? Just out of curiosity - so if I do end up needing a wireless card one day? 'cause for now - I actually found the 50ft cat 5e cable for $5.99 =)

---

