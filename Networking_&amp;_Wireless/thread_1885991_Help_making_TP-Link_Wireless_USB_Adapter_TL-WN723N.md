---
title: "Help making TP-Link Wireless USB Adapter TL-WN723N work consistently"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by SavvasKatseas on 2011-11-24
I've only recently made the jump to Ubuntu, using 11.10/64 as my only desktop OS. Everything seems to be working fine, except my USB Wireless adapter, TP-Link's TL-WN723N which is randomly connecting and disconnecting. The connection time appears to be random, too: I've experienced hours of connectivity and lots of connections/disconnections.

I've tried searching for a solution, but what I find doesn't concern this specific USB adapter. While searching for the adapter's drivers, I see that there are versions available for download at Realtek, but all of them are listed as  Kernel 2.6.37 (and earlier), which is why I haven't tried using them so far.

I've also recently switched to using a D-Link router as a wireless hub, which creates its own wireless/n network. Unfortunately this didn't solve my problems, as the new n network can be joined, but there's no connectivity to the internet. I am able to connecto the older router randomly but I'm getting really slow speed and lots of disconnects.

After searching around ubuntuforums.org, I've found a list of commands to output that should be useful in troubleshooting the problem. [The output is here]("http://paste.ubuntu.com/747321/"). Please let me know if there's any more info I can provide to make this a better question.

---

### Post by SavvasKatseas on 2011-11-24
Please note that the wireless adapter works in other operating systems without any loss of connectivity or speed, but I haven't tested it in this PC because I only want to keep Ubuntu installed on it. I've tried moving a laptop next to where the Ubuntu desktop is and using the adapter on it to make sure that this isnt' a wifi coverage problem, and indeed it isn't.

Another point worth noting is that the new n network can be joined by all of my other devices, such as an iPhone, another desktop and a netbook and has great connectivity. But I've noticed in the commands' output that Ubuntu sees the n network as a limited speed one:

iwlist scan
> wlan0     Scan completed :
          Cell 01 - Address: 34:08:04:B8:91:2E
                    ESSID:"psaroukla.the.killer"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

I'm not sure what gives.

---

### Post by praseodym on 2011-11-24
Hi,

tried pure WPA2-AES encryption instead of WEP?

Edit: Sorry didnt see the link

[COLOR="Red"]Edit[/COLOR] 2: You are trying to connect to a double network as shown by "sudo iwlist scan". Change the ESSID

---

### Post by SavvasKatseas on 2011-11-24
One of the networks has dots in its name, the other has hyphens -- so it's not a "double" network, unless there's something I don't understand. Just to be on the safe side, I've named the new n network "newn" and set it to WPA/WPA2, AES, PSK, n only. One of the many reasons I need to retire my old router is that I can't set proper security on it: it "forgets" the security rules a couple of minutes after they're set and its newest firmware doesn't change that problem.

It still can't connect to the new network. It scans for a couple of minutes, then asks for its password, accepts it, rescans and the loop goes on. Can I provide some info when that's happening?

I've also noticed that if I try to connect to newn, after the adapter fails to connect to it, it keeps failing to connect to the old network too. The only solution then is to either reboot or remove the USB adapter and place it back on, and the second solution doesn't always work.

---

### Post by SavvasKatseas on 2011-11-25
Any ideas? Should I abandon the adapter and try finding one that works with Ubuntu?

---

### Post by praseodym on 2011-11-25
Try installing this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip 
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/RTL8191SU_usb_linux_v2.6.6.0.20101111.zip
unzip -x RTL8191SU_usb_linux_v2.6.6.0.20101111.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver
tar xvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111
make
sudo make install 
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot. If there are errors with "sudo make install", copy the module by hand:
```
sudo cp 8712u.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a
sudo update-initramfs -u 
```

---

### Post by SavvasKatseas on 2011-11-25
Thanks for the suggestion. Is this a new version of the driver? If I follow the instructions will I be able to revert the changes?

Sorry if I'm nagging you, I'm just new at using Ubuntu and I'm not sure of how the driver system works.

---

### Post by praseodym on 2011-11-25
Yes, with

```
sudo make uninstall
```

or

```
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/wireless/8712u.ko 
```
and manually removing the line "blacklist r8712u" via
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
The original driver is still there.

---

### Post by SavvasKatseas on 2011-11-25
Make returns errors.

> make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.0.0-12-generic/build M=/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.o
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:23:0:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_ht.h:25:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:67,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function &#8216;get_da&#8217;:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:350:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:350:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:353:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:353:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:356:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:356:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:359:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:359:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:374:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:374:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:377:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:377:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:380:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:380:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:383:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:383:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:397:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:397:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:400:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:400:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:403:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:403:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:73:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h:434:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h:434:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:77:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_io.h: At top level:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2


---

### Post by praseodym on 2011-11-25
Try

```
make clean
sudo make
```
If it doesnt work, too, try it as "root":
```
sudo make clean
sudo su
make
make install
exit
```

---

### Post by SavvasKatseas on 2011-11-25
Nope, it still refuses...


> sino@margerita:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 

> sino@margerita:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111$ sudo su
root@margerita:/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.0.0-12-generic/build M=/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.o
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:23:0:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/osdep_service.h: In function ‘_init_timer’:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_ht.h:25:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:67,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function ‘get_da’:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:350:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:350:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:353:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:353:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:356:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:356:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:359:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:359:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function ‘get_sa’:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:374:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:374:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:377:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:377:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:380:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:380:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:383:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:383:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h: In function ‘get_hdr_bssid’:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:397:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:397:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:400:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:400:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:403:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/wifi.h:403:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:73:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h:434:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_recv.h:434:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/drv_types.h:77:0,
                 from /home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.c:24:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_io.h: At top level:
/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/include/rtl871x_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/sino/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2


---

### Post by praseodym on 2011-11-25
Seems that it doesnt work with kernel 3. You can try to install the Natty-Mainline-Kernel (here 2.6.38-8 ):

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/)

You need all three possible packages. Install them by double clicking, reboot into this kernel and try it again.

---

### Post by SavvasKatseas on 2011-11-25
Hi, thanks for the help so far.

Could you please clarify? Which are the three packages I need? I'm guessing that they'll probably be the two amd64 ones and the one marked as "all", but I may be wrong.

On the same page: what would changing the Kernel mean? If I'm correct I'd be downloading three different images, installing them and choosing which one Ubuntu will use during boot. Am I right? Will this affect my installation in any way, breaking anything?

---

### Post by SavvasKatseas on 2011-11-27
Turns out I'll be getting a new USB adapter, one that works out of the box. Thanks for all the help so far.

---

### Post by praseodym on 2011-11-27
For 32 bit: the files i386 and all.deb

For 64 bit: the files amd64 and all.deb

---

### Post by SavvasKatseas on 2011-11-27
Thanks, praseodym. I've answered my own above questions via a bit of searching around. I might turn this into a fun project whilst I'm waiting for the new adapter to arrive, just to see if I can make the old one working.

---

