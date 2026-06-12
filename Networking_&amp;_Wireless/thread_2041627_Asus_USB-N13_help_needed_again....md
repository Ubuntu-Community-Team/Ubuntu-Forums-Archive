---
title: "Asus USB-N13 help needed again..."
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by cbezerra on 2012-08-13
So I got help to get the adapter working, and it was doing great for 2 weeks. But last night after a forced restart from an update, it no longer worked.

thank you in advance for any help.

---

### Post by chili555 on 2012-08-13
What interesting messages do you see here?```
sudo modprobe 8192cu
dmesg | grep 8192
```Thanks.

---

### Post by Placidia428 on 2012-08-13
Hello all. I just got the same Asus dongle usb-N13 and had the same bad experience as noted in this forum. I read the related post of two weeks ago from cbezzera (Asus USB-N13 help needed) and pages linked therefrom. My dongle could see the wireless network but not reach the Internet.

Today, I tried:

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz) 
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src 
sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo dkms build -m rtl8192cu -v 3.3.23192 
sudo dkms install -m rtl8192cu -v 3.3.23192 
 
 
sudo gedit /etc/rc.local 
 
# Right above exit 0 add these two lines: 
 
 
modprobe rtl8192cu 
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id 

I got these lines of code from assorted relevant forum pages. Kudos to all.

I rebooted and the dongle couldn't even see the network. I went into System -> additional drivers and disabled the Realtek Wireless Lan driver. (I followed the point and click desktop icons. We're not in the Terminal here. Click on the icon with the gear and the wrench)

I rebooted and GOT WIRELESS. :popcorn:

By the way, I am running 12.04.

Anyway, I think the built-in free driver masks the new one, so you have to disable it. For now, it's working for me.

cbezzera - I seem to recall that you were running 10.10 (or 10.04?). If you just switched to 12.04, you would have got the built-in rtl8192 driver, which does not work.

---

### Post by cbezerra on 2012-08-13
chris@chris-laptop:~$ sudo modprobe 8192cu
[sudo] password for chris: 
FATAL: Error inserting 8192cu (/lib/modules/2.6.32-42-generic/updates/dkms/8192cu.ko): Invalid module format
chris@chris-laptop:~$ dmesg | grep 8192
[   16.006504] 8192cu: disagrees about version of symbol module_layout
[  286.329869] 8192cu: disagrees about version of symbol module_layout
[  319.647660] 8192cu: disagrees about version of symbol module_layout
[ 4855.542255] 8192cu: disagrees about version of symbol module_layout
[ 5030.015002] 8192cu: disagrees about version of symbol module_layout
[28712.023141] 8192cu: disagrees about version of symbol module_layout
[74758.708718] 8192cu: disagrees about version of symbol module_layout
chris@chris-laptop:~$

---

### Post by Placidia428 on 2012-08-13
OK. so now it's 3 hours later, and it's not working. :confused:

What changed? I got the computer working right next to the router - in the furnace room. Then moved the computer back upstairs and now, the dongle can see the network and connect to it, but it can't connect to the internet. I keep getting the password box.

I did this:

sudo modprobe 8192cu dmesg | grep 8192

And got:

placidia@Sandbox:~$ sudo modprobe 8192cu


[sudo] password for placidia: 

FATAL: Error inserting 8192cu (/lib/modules/3.2.0-23-generic/updates/dkms/8192cu.ko): Device or resource busy

placidia@Sandbox:~$ 

placidia@Sandbox:~$ dmesg | grep 8192


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
placidia@Sandbox:~$

---

### Post by cbezerra on 2012-08-13
Placidia, unfortunately I cannot help you. You should start a new thread, and copy/paste what you have posted here. That way more people will see what the issue is and can provide input. 

Just go to the main page, click 'networking & wireless', and click 'new thread'.

---

### Post by Placidia428 on 2012-08-13
OK. I'll do that.

---

### Post by cbezerra on 2012-08-15
Any ideas?

---

### Post by steeldriver on 2012-08-15
if the kernel got updated you *may* need to re-build the driver again against the new kernel headers

like you did here:
[http://ubuntuforums.org/showpost.php?p=12121392&postcount=16](http://ubuntuforums.org/showpost.php?p=12121392&postcount=16)

and possibly:
[http://ubuntuforums.org/showpost.php?p=12128927&postcount=24](http://ubuntuforums.org/showpost.php?p=12128927&postcount=24)

just an idea

---

### Post by cbezerra on 2012-08-16
Thank you. As far as ideas go, that one was great! ;)

---

