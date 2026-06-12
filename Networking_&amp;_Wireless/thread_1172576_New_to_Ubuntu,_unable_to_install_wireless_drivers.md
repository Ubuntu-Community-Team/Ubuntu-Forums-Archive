---
title: "New to Ubuntu, unable to install wireless drivers"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Mark_32 on 2009-05-28
Having loaded Ubuntu to my PC, I am unable to access the internet as Ubuntu does not recognise my USB wireless connection.
I have a Winbond USB pen for wireless connection.
I have downloaded some supposed drivers for this and have followed the instructions which were supplied through the Terminal but it just errors all the time.
I was wondering whether someone would be able to help and whether I have saved the files to the correct place, etc.
If anyone could help I'd be greatful, and please could you explain simply as this is my first time using Ubuntu.
Thanks:D

---

### Post by pytheas22 on 2009-05-28
Please open a terminal, run the following commands and post the output here:
```

uname -rm
lsusb
lshw -C Network
```

With that information, I'll know exactly which wireless card you have (knowing just the name is not enough) and can hopefully write you simple instructions for making it work.

---

### Post by Mark_32 on 2009-05-31
Thanks for your reply, I have gone to the terminal and typed the code you stated, the following was what was given:
mark@mark-laptop:~$ uname-rm
bash: uname-rm: command not found
mark@mark-laptop:~$ uname -rm
2.6.28-11-generic i686
mark@mark-laptop:~$ lsusb
Bus 001 Device 003: ID 18e8:6201 Qcom 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mark@mark-laptop:~$ lshw -C Cnetwork
WARNING: you should run this program as super-user.
mark@mark-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: 00:16:ec:a2:7a:ee
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
*-network:0 DISABLED
description: Ethernet interface
physical id: 1
logical name: vboxnet0
serial: 00:76:62:6e:65:74
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: f6:f2:92:ac:ff:90
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 
There seems to be no mention of the my USB wireless connection at all there. Hope that this helps
Thanks

---

### Post by pytheas22 on 2009-05-31
Thanks for the information.  I looked up your wireless card and there seems to be a native Linux driver for it named w35und, but it's very new and I'm not sure how well it would work.  So I think that the best route now will be to use ndiswrapper, which will allow you to drive your card using the Windows driver.

To give you instructions for configuring ndiswrapper, however, I need access to the Windows driver for your device, which I couldn't find.  Could you please provide a link to the driver that you use to make your card work in Windows, or, if the driver came on a CD, please upload the .exe (or .zip or whatever) file here?

It would also be helpful to know the exact model of your Winbond card.

---

### Post by Mark_32 on 2009-06-01
Thanks for getting back to me.
 
I have included the ZIP file to this thread, I hope that its attached OK.
 
There is no name of the device on the USB wifi, its just green with no model numbers or anything on it.

---

### Post by pytheas22 on 2009-06-01
Thanks for that file.  Please save it to your desktop on Ubuntu (under the name WLAN.zip), then run these commands to get it installed (if possible, you should plug into the Internet using an ethernet cable for these steps; if you don't have ethernet available, let me know and we can work around it):
```

sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd ~/Desktop
unzip WLAN.zip
cd WLAN
sudo ndiswrapper -i NETW35G.INF
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot your computer.  If all goes well, your wireless should work.  If not, please post the output of these commands so I can try to figure out what went wrong:
```

ndiswrapper -l
lsmod | grep ndis
dmesg | grep -e ndis -e wlan
sudo iwlist scan
lshw -C Network
```

---

### Post by Mark_32 on 2009-06-02
Hi,
Currently I don't have my laptop connected to the internet via the ethernet cable due to the port being broken. So have windows and ubuntu loaded, and use windows to connect to the internet via my wireless connection to access these posts.
Is there any other way to download the apps so that I can access dniswrapper.
I have tried downloading other apps through windows then sending them to the hard-drive so that I can access them, but have had issues with "permissions" and allowing me to access them.
Please could you advise another way for me to access dniswrapper.
I am very grateful for you help so far. Thanks

---

### Post by pytheas22 on 2009-06-02
Sure, you can install ndiswrapper without an ethernet connection; it just takes a few extra steps.

First, download [this file]("http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb") and [this file]("http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb"), and save them both to your desktop in Ubuntu.  This should leave you with two icons on your desktop with names beginning with 'ndiswrapper-common' and ndiswrapper-utils-1.9'.  Double-click the ndiswrapper-common package to install it.  When that's done, double-click ndiswrapper-utils-1.9 and install it as well.

With that finished, run these commands (you will still need the 'WLAN.zip' package on your desktop):
```

sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd ~/Desktop
unzip WLAN.zip
cd WLAN
sudo ndiswrapper -i NETW35G.INF
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot your computer. If all goes well, your wireless should work. If not, please post the output of these commands so I can try to figure out what went wrong:

```
ndiswrapper -l
lsmod | grep ndis
dmesg | grep -e ndis -e wlan
sudo iwlist scan
lshw -C Network
```

---

### Post by Mark_32 on 2009-06-03
Hi
I have done as you suggested, but the device still not working. Have inputted the code following rebooting and the following information came up:
 
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] ndiswrapper -l
netw35g : driver installed
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] lsmod | grep ndis
ndiswrapper           193436  0 
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] lsmod | grep ndis
ndiswrapper           193436  0 
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] dmesg | grep -e ndis -e wlan
[   11.627052] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.056419] ndiswrapper: driver netw35g (Winbond Electronics Corp.,08/26/2005,1.0.43.3) loaded
[   12.159446] Modules linked in: joydev snd soundcore snd_page_alloc ndiswrapper(+) usbhid sis900 mii fbcon tileblit font bitblit softcursor
[   12.159446]  [<dea0ddbf>] ? IoReuseIrp+0x2f/0x50 [ndiswrapper]
[   12.159446]  [<dea0ed51>] ? IofCompleteRequest+0x151/0x1a0 [ndiswrapper]
[   12.159446]  [<dea18694>] ? wrap_urb_complete_worker+0xd4/0x210 [ndiswrapper]
[   12.159446]  [<dea185c0>] ? wrap_urb_complete_worker+0x0/0x210 [ndiswrapper]
[   13.353032] wlan0: ethernet device 00:0d:f0:27:9c:a3 using NDIS driver: netw35g, version: 0x1004303, NDIS version: 0x500, vendor: 'Winbond W89C35 USB20 802.11bg Wireless LAN Adapter Driver', 18E8:6201.F.conf
[   13.353056] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.353129] usbcore: registered new interface driver ndiswrapper
[   13.468445] Modules linked in: snd_intel8x0(+) snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq sis_agp snd_timer snd_seq_device psmouse i2c_sis96x shpchp agpgart serio_raw pcspkr joydev snd soundcore snd_page_alloc ndiswrapper usbhid sis900 mii fbcon tileblit font bitblit softcursor
[   13.468534]  [<dea06ef2>] ? NdisFreeBufferPool+0x42/0x70 [ndiswrapper]
[   13.468570]  [<dea05aad>] ? NdisFreePacket+0x6d/0xa0 [ndiswrapper]
[   13.468589]  [<dea06ef2>] ? NdisFreeBufferPool+0x42/0x70 [ndiswrapper]
[   13.468608]  [<dea059fb>] ? NdisInterlockedDecrement+0xb/0x10 [ndiswrapper]
[   13.468630]  [<dea144dc>] ? mp_halt+0x5c/0x190 [ndiswrapper]
[   13.468652]  [<dea14864>] ? ndis_remove_device+0xd4/0x1e0 [ndiswrapper]
[   13.468670]  [<dea176ea>] ? NdisDispatchPnp+0xda/0x130 [ndiswrapper]
[   13.468689]  [<dea0e954>] ? IoQueueThreadIrp+0x14/0x160 [ndiswrapper]
[   13.468710]  [<dea0e22d>] ? IofCallDriver+0x4d/0xb0 [ndiswrapper]
[   13.468729]  [<dea0fbe6>] ? IoSendIrpTopDev+0xb6/0x110 [ndiswrapper]
[   13.468749]  [<dea0ff45>] ? pnp_remove_device+0x55/0x180 [ndiswrapper]
[   13.468778]  [<dea19f01>] ? wrap_pnp_remove_usb_device+0x25/0x27 [ndiswrapper]
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
vboxnet0  Interface doesn't support scanning.
pan0      Interface doesn't support scanning.
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: [EMAIL="pci@0000:00:04.0"]pci@0000:00:04.0[/EMAIL]
       logical name: eth0
       version: 91
       serial: 00:16:ec:a2:7a:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:16:23:7d:17:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] 

 
I hope the above information is of some help
 
Regards
Mark

---

### Post by pytheas22 on 2009-06-03
Thanks for that information.  ndiswrapper seems to be doing some strange things, but it may be possible to fix them.  Please try running this command once:
```

sudo ndiswrapper -a 18E8:6201 netw35g
```

Then reboot, then post the output of:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

If this doesn't help, we may need to ditch ndiswrapper and try the native Linux driver.

---

### Post by Mark_32 on 2009-06-03
hi have completed the above mentioned.
Have also put my keyboard via a different port, rather than USB.
The wifi adaptor now appears to have power to it but not connecting to the internet.
 
Code is below:
 
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] dmesg | grep -e ndis -e wlan
[   13.858430] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.276071] ndiswrapper: driver netw35g (Winbond Electronics Corp.,08/26/2005,1.0.43.3) loaded
[   15.572912] wlan0: ethernet device 00:0d:f0:27:9c:a3 using NDIS driver: netw35g, version: 0x1004303, NDIS version: 0x500, vendor: 'Winbond W89C35 USB20 802.11bg Wireless LAN Adapter Driver', 18E8:6201.F.conf
[   15.572934] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.572991] usbcore: registered new interface driver ndiswrapper
[   15.880085] ndiswrapper: device wlan0 removed
[   16.916385] ndiswrapper: driver netw35g (Winbond Electronics Corp.,08/26/2005,1.0.43.3) loaded
[   17.224987] Modules linked in: lp parport joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event sis_agp snd_seq snd_timer snd_seq_device psmouse ndiswrapper shpchp agpgart serio_raw snd soundcore snd_page_alloc i2c_sis96x pcspkr sis900 mii fbcon tileblit font bitblit softcursor
[   17.225070]  [<dea6ddbf>] ? IoReuseIrp+0x2f/0x50 [ndiswrapper]
[   17.225111]  [<dea6ed51>] ? IofCompleteRequest+0x151/0x1a0 [ndiswrapper]
[   17.225131]  [<dea78694>] ? wrap_urb_complete_worker+0xd4/0x210 [ndiswrapper]
[   17.225162]  [<dea785c0>] ? wrap_urb_complete_worker+0x0/0x210 [ndiswrapper]
[   18.411923] wlan0: ethernet device 00:0d:f0:27:9c:a3 using NDIS driver: netw35g, version: 0x1004303, NDIS version: 0x500, vendor: 'Winbond W89C35 USB20 802.11bg Wireless LAN Adapter Driver', 18E8:6201.F.conf
[   18.411953] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   26.931773] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw35g : driver installed
 device (18E8:6201) present
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL]

---

### Post by pytheas22 on 2009-06-03
hmmm, it looks somewhat better now.  Could you please also post the output of:
```

sudo iwlist scan
lshw -C Network
```

Sorry for not asking for those in my last post.

---

### Post by Mark_32 on 2009-06-03
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results
vboxnet0  Interface doesn't support scanning.
pan0      Interface doesn't support scanning.
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL] lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: [EMAIL="pci@0000:00:04.0"]pci@0000:00:04.0[/EMAIL]
       logical name: eth0
       version: 91
       serial: 00:16:ec:a2:7a:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:f0:27:9c:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw35g driverversion=1.53+Winbond Electronics Corp.,0 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: b6:1e:59:31:81:88
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[EMAIL="mark@mark-laptop:~$"]mark@mark-laptop:~$[/EMAIL]

---

### Post by pytheas22 on 2009-06-03
hmmm, everything now looks like it's working as expected, but your wireless card isn't seeing any networks.  One possible reason is that the network is operating in a different mode than your card.  Your wireless card is on 11g mode; do you know if your network is on 11b or 11n?  You can check this by opening a web browser on a computer that's connected to the Internet and entering '192.168.1.1' in the address bar (if that returns a server-not-found error, try 192.168.0.1 or 10.0.0.1 instead).  This should open your wireless router's configuration utility.

It's also possible that the card is just not working properly, even though it looks like it should be.  Are there usually multiple networks visible from your location?  If so, and Ubuntu's not seeing any of them, then it's likely there's a problem with the wireless driver (since it's unlikely that none of the networks near your house would be in 11g mode, which is the most common).

---

### Post by Mark_32 on 2009-06-04
Hi
Would it be worth me reinstalling ubuntu again to see whether it was something I may have done trying to sort the problem myself at an earlier point?

---

### Post by pytheas22 on 2009-06-04
> **Mark_32 said:**
> Hi
Would it be worth me reinstalling ubuntu again to see whether it was something I may have done trying to sort the problem myself at an earlier point?

Reinstalling never hurts if you can spare an hour for the reinstallation.  But have you been able to check which mode your router is operating in?  If it's in 11g mode but the wireless card is still not seeing it, then I suspect there's a problem with ndiswrapper (which already has been behaving a bit strangely on your machine, according to the output you posted over the last few days), and the only way to make the card work will probably be to try the native Linux driver.

On the other hand, if you haven't yet checked which mode your router is on, I'd recommend doing that before trying to reinstall Ubuntu.

---

### Post by richard.e.morton on 2010-05-02
Hi,

I know this is an old post but hopefully you're still subscribed for notifications ;-) I am running 10.04 and have a Winbond W89C35 device.

Bus 001 Device 008: ID 0416:0035 Winbond Electronics Corp. W89C35 802.11bg WLAN Adapter

Is the native driver you mentioned correct for this card (and how did you look this up). Secondly what is the state of the native driver; a year later is ready for use?

thanks

R

---

### Post by Gary00 on 2010-05-02
its not working for me.

---

### Post by pytheas22 on 2010-05-03
I'm not sure what the status of the w35und driver is at this time, but it's included on my Ubuntu 9.10 netbook by default, which is encouraging (strangely, it doesn't seem to exist on my new Ubuntu 10.04 desktop).  You can try loading it by typing:
```

sudo modprobe w35und
```

and see if it brings up your wireless interface.  Please let me know how this goes and we can take it from there.

---

