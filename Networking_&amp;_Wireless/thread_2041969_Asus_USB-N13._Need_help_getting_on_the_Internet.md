---
title: "Asus USB-N13. Need help getting on the Internet"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by Placidia428 on 2012-08-13
I just got  Asus wireless dongle usb-N13 and I can't get it to reach the Internet. It can see the network, but is unable to authenticate and reach the Internet. I am using 12.04.

I read several related posts and thought, briefly, that I had success.

I tried:

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz") 
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src 
sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo dkms build -m rtl8192cu -v 3.3.23192 
sudo dkms install -m rtl8192cu -v 3.3.23192 
 
 
sudo gedit /etc/rc.local 
 
# Right above exit 0 add these two lines: 
 
 
modprobe rtl8192cu 
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id 



I rebooted and the dongle couldn't even see the network. I went into  System -> additional drivers and disabled the Realtek Wireless Lan  driver. I rebooted again, and Lo, I was on the Internet.

Not having wireless, I did all of this in the basement, next to the router. I unplugged everything, took the machine upstairs and could no longer get on the Internet. As before, I could get on the wireless network, but no further.

I tried:

placidia@Sandbox:~$ dmesg | grep 8192

and got:

[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88010fc00000 s83072 r8192 d23424 u524288

[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152

[   10.813630] Error: Driver 'rtl8192cu' is already registered, aborting...

[   10.871610] rtl8192cu: MAC address: c8:60:00:d3:8a:43

[   10.871614] rtl8192cu: Board Type 0

[   10.928246] usbcore: registered new interface driver rtl8192cu

[   11.947864] rtl8192cu: MAC auto ON okay!

[   11.980615] rtl8192cu: Tx queue select: 0x05

[   11.982125] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin

[  885.399818] Error: Driver 'rtl8192cu' is already registered, aborting...

So now what do I do? I hope someone can help.

---

### Post by Placidia428 on 2012-08-14
For some reason, it is now working again. Guess I'll mark this as "solved."

---

