---
title: "Wireless rt5390 help"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by pdxmusl on 2012-11-25
I just recently purchased a m4-1015 hp laptop and am having some issues with trying to get the wireless up and going. It uses the rt5390 ralink. 

I've installed 12.04 and I tried using the linux driver I found directly on the ralink site:
[http://www.ralinktech.com/en/04_support/license.php?sn=5001](http://www.ralinktech.com/en/04_support/license.php?sn=5001)
(the "RT539x PCIe" selection from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501))

But part of the instructions didn't seem to make sense. That could be part of the problem:
>  ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
           => #>cd wpa_supplicant-x.x
           => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d

The above is from the README_STA_pci file. It suggests I cd into a directory that doesn't appear to exist anywhere. I've unpacked the file I've downloaded from ralink again and rechecked. The directory and the config file it references above are nowhere that I can find.

After trying to follow the remainder of the setup instructions, I compiled anyway. I did a compile and install:
> sudo make
sudo make install

if I run:
sudo modprobe -v rt5390sta
> insmod /lib/modules/3.2.0-33-generic/kernel/drivers/net/wireless/rt5390sta.ko
But if I run the command again, I get nothing. I assume it crashed. But there is no output to suggest that. It just prints the above the first time. Prints nothing the second.

other commands:
ifconfig
> eth0      Link encap:Ethernet  HWaddr 84:34:97:6b:76:a3  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8634:97ff:fe6b:76a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:561823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:845825968 (845.8 MB)  TX bytes:20107785 (20.1 MB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110473 (110.4 KB)  TX bytes:110473 (110.4 KB)

lsmod | grep rt5390
> rt5390sta            1451749  0 

lspci
> 00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Ralink corp. Device 539b
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


---

### Post by chili555 on 2012-11-25
> But part of the instructions didn't seem to make sense. That could be part of the problem:
Quote:
** Build for being controlled by NetworkManager or wpa_supplicant wext functions
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
=> #>cd wpa_supplicant-x.x
=> #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
The above is from the README_STA_pci file. It suggests I cd into a directory that doesn't appear to exist anywhere. I've unpacked the file I've downloaded from ralink again and rechecked. The directory and the config file it references above are nowhere that I can find.
When instructions are nonsensical, it does little good to ignore them and plunge on; you are not likely to get a successful result. Stop and ask.

The answer is that you need only open the folder os > linux and open config.mk with a text editor. Then change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' if they are not already. Save and close the text editor. 

Since you've told the system that Network Manager will do all that messy wpa_supplicant stuff, *NOW *you may safely ignore the remainder.

Since you made changes in the file, recompile:```
cd Desktop/RT5390  [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo su
make clean
make
make install
modprobe -r rt5390sta
modprobe rt5390sta
exit
```> But if I run the command again, I get nothing. I assume it crashed.Nope. If it crashed, it would have told you the first time in undeniable terms. When a command returns nothing, it usually means, 'command executed as ordered and I have no errors or warnings to report.' When you issue the identical command again, silence means, 'already done; there are *still* no errors or warnings to report.'

After you recompile, detach the ethernet cable, reboot and let us have a new report.

---

### Post by pdxmusl on 2012-11-25
Since this is on a laptop, and I usually upgrade every may. I don't really need long term support. I decided to try ubuntu 12.10. I kinda forgot it was out as I don't think about the os again until may.....

In 12.10 this sort of seems to be working out of the box. By that I mean that it recognizes all my neighbors networks, but can't find mine. I can connect to it by "connecting to a hidden network". Which mines not hidden, but whatever. It connects.

Unfortunately, this does seem to mean I may have to connect manually each time, but this particular problem seems to be solved by upgrading to 12.10 which is fine for me for now. I can look more into it later or start a new thread for this problem.


However, chili555, thank you much for responding to my post so quickly. I apologize. If I thought about trying 12.10 earlier, I wouldn't have posted my question.

---

### Post by pdxmusl on 2012-11-25
Ok... So, the problem I mentioned in my previous post about it not recognizing my home network but everyone else....

This seems to be a proximity problem to the router. Moving the laptop just a few inches over and moving the router to the other side of the desk to give more distance between them seems to have resolved this problem. I've rebooted a few times now and it automatically connects just fine to my home network. All seems to be working just dandy. 

So, I guess we can mark this as solved by upgrading to 12.10. I'd be willing to explore the original problem if we think that would help the community.

---

### Post by chili555 on 2012-11-25
Glad it's working. I'll take a solved!

---

