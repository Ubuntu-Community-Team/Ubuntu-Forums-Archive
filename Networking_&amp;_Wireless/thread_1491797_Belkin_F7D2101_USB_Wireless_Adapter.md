---
title: "Belkin F7D2101 USB Wireless Adapter"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by Anonymous Citizen on 2010-05-24
I'm a new user to Ubuntu and up to this point have been using my desktop connected by ethernet cable to my wireless router. I also have a laptop that connects wirelessly to my internet and thought I'd move it to another room without getting another huge cable. I went out to buy a wirless adapter and didn't think to look up compatibility to Ubuntu.   I searched google and pretty much got nothing. I followed the advice laid out here:

---

### Post by Anonymous Citizen on 2010-05-24
My reply keeps getting cut short. I tried to edit it but nothing happened. Is there some sort of limit for your first post? [Edit: I think NoScript on FireFox is the culprit.]

I followed these steps
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I tried all that. First try computer froze and then had to remove ndiswrapper in recovery mode. Then I compiled from source like the linked page said. I booted to XP on separate partition and used those drivers. Then I used pretty much every driver on my CD. I got it to install but iwconfig showed no wireless device. Running ndiswrapper returned no errors. When I ran dmesg

[ 1274.126422] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1274.270032] usb 1-10: reset high speed USB device using ehci_hcd and address 5
[ 1274.426770] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1274.426782] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
[ 1274.427771] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'

My computer is self built
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Motherboard: Biostar MCP6P M2+
Running
Ubuntu 9.10 (karmic)
Gnome 2.28.1 
Kernel 2.6.31-20-generic 

USB wireless adapter Belkin Surf and Share Part # F7D2101

I think I'm just out of luck but I was just maybe wondering if I'm missing anything.

---

### Post by Anonymous Citizen on 2010-05-24
So, nothing else? I guess I might have to look for another *working* usb adapter from one of the lists. By the way, the drivers I was trying from the manufacturer's CD said [Windows version]X64 so I'm not sure why they would come back as not being 64-bit.

---

### Post by eteq on 2010-08-24
This message is out-of-date, but I managed to get this adapter working under Ubuntu (lucid 64).  Pretty straightforward actually... I got most of this from [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815) , although it required a some slight changes. 

Run this command:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```

And add this line to the file (which may be empty) and save:

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Then run this command:
```
sudo gedit /etc/modprobe.d/network_drivers.conf 
```

And add this file (and save)
```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

and copy it to the directory ```
/lib/firmware/RTL8192SU/ 
```

To summarize, the first two commands tell linux to load the correct driver when that particular USB device is plugged in (which I figured out with the lsusb command), and the firmware is used to load the information the wireless chip needs to run.

---

### Post by Goldstar78 on 2010-09-27
ok, this works... for about 10 minutes or so. The connection got lost after a few minutes. Only a reboot or replugging the usbstick brings the connection back... for about 10 minutes or so.

I installed ubuntu-10.04.1-desktop-i386 an a very very old DELL. Everything but this is working well so far.

anyone an idea?

---

### Post by dforthman on 2010-10-28
I tried both the ndiswrapper and this little manual installation trick, but even though it is showing up in lsusb, iwconfig shows no wireless adapters.

Maybe I typo'd something - I'll try it again tonight just to be sure, but as of right now I still can't get my Ubuntu box online.

---

### Post by msbealo on 2011-04-07
The Method outlined by eteq worked for me on both my laptop and desktop.

I'm still running the connection through it's paces just to see if it's reliable but all good so far.

Thanks eteq.

Mark

EDIT: No, sorry. I take that back (except for the thanks). It worked for a while, it works on my laptop, it stopped working on my desktop. I reinstalled 10.10 on my desktop and it still doesn't work. It can see the networks but can't connect to them. I'm trying to find a solution but it's very frustrating.

---

### Post by bindaaz on 2011-06-23
See the post #69 & #70 in the following thread for the connect/disconnect problem.

---

### Post by bindaaz on 2011-06-23
And here is the link to the other post. [http://ubuntuforums.org/showthread.php?t=1522815&page=7](http://ubuntuforums.org/showthread.php?t=1522815&page=7)

---

