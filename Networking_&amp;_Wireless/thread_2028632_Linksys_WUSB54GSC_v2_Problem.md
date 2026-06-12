---
title: "Linksys WUSB54GSC v2 Problem"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by Macle101 on 2012-07-18
I've been trying to install  this adapter for the past few days, but had no luck. I have the Original CD that came with it but dunno how to install it on Ubuntu. I tried to go [here]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB54GSv2") but I don't understand how to do those methods. Can someone walk me through them so I can possibly get the adapter to work?

Thank You.

---

### Post by chili555 on 2012-07-18
Depending on what Ubuntu version you've installed, the driver may be already installed. Please insert the device, open a terminal and run:```
lsusb
```Is the device ID 13b1:0014? If so, the driver rndis_wlan is already in Ubuntu 12.04. What version do you have?```
lsb_release -d
```For reference:> chili@LAPTOP60:~$ modinfo rndis_wlan
filename:       /lib/modules/3.2.0-26-generic-pae/updates/cw-3.3/rndis_wlan.ko
license:        GPL
description:    Driver for RNDIS based USB Wireless adapters
author:         Jussi Kivilinna
author:         Bjorge Dijkstra
srcversion:     56ECE439BA63D3D5EEE2D4B
alias:          usb:v*p*d*dc*dsc*dp*icEFisc01ip01*
alias:          usb:v*p*d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0411p004Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0BAFp0111d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v13B1p000Ed*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v1690p0715d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0A5CpD11Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0B05p1717d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v13B1p0026d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v[COLOR="Red"]13B1[/COLOR]p[COLOR="Red"]0014[/COLOR]d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v1799p011Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v050Dp011Bd*dc*dsc*dp*ic02isc02ipFF*
<snip>Once we have more information, we'll be in a better position to proceed.

---

### Post by Macle101 on 2012-07-18
I'm running Ubuntu 12.04 LTS

When I ran the first command this came up:

Bus 001 Device 016: ID 1737:0075 Linksys WUSB54GSC V2 802.11g Adapter

---

### Post by chili555 on 2012-07-18
We are going to have to use ndiswrapper as suggested in the link you gave. Do you have an internet connection on the computer now? Can you install niswrapper?```
sudo apt-get install ndisgtk
```We will also need to see what you have on the install CD. What are the files? Specifically, we are looking for the Windows XP .inf and .sys files appropriate to your architecture, either 32- or 64-bit. Find out with:```
arch
```i686 is 32-bit and x86_64 is 64-bit.

EDIT: I have them. Please download the attached to your desktop. Right-click and select *Extract Here*. Then, in a terminal, do:```
sudo ndisgtk
```When the box opens, point to Desktop > XP_2K > ndiswdm.inf. The system should install the driver automatically.

---

### Post by Macle101 on 2012-07-18
> **chili555 said:**
> We are going to have to use ndiswrapper as suggested in the link you gave. Do you have an internet connection on the computer now? Can you install niswrapper?```
sudo apt-get install ndisgtk
```We will also need to see what you have on the install CD. What are the files? Specifically, we are looking for the Windows XP .inf and .sys files appropriate to your architecture, either 32- or 64-bit. Find out with:```
arch
```i686 is 32-bit and x86_64 is 64-bit.

No I don't internet connection on the computer. I have the ndiswrapper file on my computer called ndiswrapper-1.58rc1.tar.gz   . I put it there with my USB Stick. 

I have 32-bit.

In the CD:

In the Driver File, there were two other files named, Xp_2k and Vista

Under XP_2k
[I]-bcm43xx.cat
-bcm43xx64.cat
-ndiswdm.inf
-ndiswdm.sys[/I]

and there was a *AUTORUN.INF* file

---

### Post by chili555 on 2012-07-18
Do you still have the Ubuntu install CD? The ndiswrapper .deb files are on it in /pool/main/n/ndiswrapper/. Drag and drop both to your desktop. Right-click them and select Install with Package Manager, or similar.

The problem with extracting and installing the tar.gz you have is that many complex prerequisites are needed. 

If you drag and drop the XP_2K folder from the Linksys CD, you can follow much the same process. ndisgtk is not on the Ubuntu CD, so do:```
sudo su
ndiswrapper -i Desktop/XP_2K/ndiswdm.inf
ndiswrapper -m
```Check to see if the install went well:```
ndiswrapper -l
```That's a lower-case L for 'list.' If everything is well, it ought to report the file is installed and the device is present. See if a wireless interface, ideally wlan0, is created:```
iwconfig
exit
```Click the Network Manager icon and connect!

---

### Post by Macle101 on 2012-07-18
The device is present and driver is installed.

But the last code wlan0 was not present. 

Only

lo

etho 

and both of them say no wireless extensions.

---

### Post by chili555 on 2012-07-18
Let's see what the logs say is going on behind the scenes:```
dmesg | grep ndis
```You can copy and paste the result from the terminal to a text document and transfer it on a USB key to post it here.

---

### Post by Macle101 on 2012-07-18
The terminal doesn't do anything when I type that in.

---

### Post by chili555 on 2012-07-18
Please try a slight variation:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Any errors or warnings are helpful, please post them if any.

---

### Post by Macle101 on 2012-07-18
Update: Just typed in the first code and it came up with:

FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2012-07-18
What were the hopefully two packages you copied off the CD to install? ndiswrapper-common and ndiswrapper-utils? You need both.

---

### Post by Macle101 on 2012-07-18
Yeah I installed both of them, and I just reinstalled them. It still comes up with it.

---

### Post by chili555 on 2012-07-18
Congratulations! You have an officially recognized Ubuntu bug, you lucky penguin! 

[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064)

Please download ndiswrapper-dkms and dkms here and install it. Then do:```
sudo modprobe ndiswrapper
```[http://packages.ubuntu.com/precise/ndiswrapper-dkms](http://packages.ubuntu.com/precise/ndiswrapper-dkms)

[http://packages.ubuntu.com/precise/dkms](http://packages.ubuntu.com/precise/dkms)

You should be all set.

---

### Post by Macle101 on 2012-07-18
Still not working for me. :\
No wireless interface when I type iwconfig

This is what shows up when I type in desmg  |  grep  ndis 
Open the Code Doc in attachment.

Anything I can do?

---

### Post by chili555 on 2012-07-19
> [70050.024859] Modules linked in: ndiswrapper(O+) [COLOR="Red"]ath5k ath mac80211 cfg80211[/COLOR] nls_utf8 isofsWhat?? Do you have another wireless device that's not working and competing for networking resources? Did you forget to tell me something? Shouldn't we troubleshoot the internal wireless and get it going?

---

### Post by Macle101 on 2012-07-19
> **chili555 said:**
> What?? Do you have another wireless device that's not working and competing for networking resources? Did you forget to tell me something? Shouldn't we troubleshoot the internal wireless and get it going?

I hooked up my ethernet cable with my laptop and I installed updates. But I think I might have installed the Vista Driver too. When I ask it to list a driver it shows two. How do I delete the vista one?

---

### Post by chili555 on 2012-07-19
*ath5k* is a native wireless driver that has nothing whatever to do with Vista or ndiswrapper. What is it doing there? What's going on?

---

### Post by wx5bix on 2013-05-25
I followed all the instructions on here and got the driver installed but when I check iwconfig it shows no wireless. Any ideas ?

---

### Post by chili555 on 2013-05-25
> **wx5bix said:**
> I followed all the instructions on here and got the driver installed but when I check iwconfig it shows no wireless. Any ideas ?What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by wx5bix on 2013-05-25
wx5bix@wx5bix:~$ ndiswrapper -l
ndiswdm : driver installed

wx5bix@wx5bix:~$ dmesg | grep ndis
[28236.989167] rndis_host 3-2:1.0: usb0: register 'rndis_host' at usb-0000:00:16.2-2, RNDIS device, b2:7d:49:f0:9d:af
[28236.989532] usbcore: registered new interface driver rndis_host
[28237.028697] usbcore: registered new interface driver rndis_wlan

---

### Post by wx5bix on 2013-05-25
wx5bix@wx5bix:~$ dmesg | grep ndis
[28236.989167] rndis_host 3-2:1.0: usb0: register 'rndis_host' at usb-0000:00:16.2-2, RNDIS device, b2:7d:49:f0:9d:af
[28236.989532] usbcore: registered new interface driver rndis_host
[28237.028697] usbcore: registered new interface driver rndis_wlan
[29020.062896] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[29020.127939] usbcore: registered new interface driver ndiswrapper
[29185.336347] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
[29185.755508] IP: [<f916b6fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[29185.755922] Modules linked in: ndiswrapper(O) rndis_wlan cfg80211 rndis_host cdc_ether usbnet cdc_acm usb_storage dm_crypt bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse serio_raw soundcore snd_page_alloc sp5100_tco i2c_piix4 k10temp mac_hid lp parport usbhid hid r8169 radeon pata_atiixp ttm drm_kms_helper drm wmi i2c_algo_bit
[29185.757440] EIP is at NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[29185.758753]  [<f9179652>] ? RtlFreeAnsiString+0x22/0x40 [ndiswrapper]
[29185.758753]  [<f916d398>] ? NdisReadNetworkAddress+0x1a8/0x1c0 [ndiswrapper]
[29185.758753]  [<f916d0f0>] ? read_setting+0x1f0/0x1f0 [ndiswrapper]
[29185.758753]  [<f917c788>] ? mp_init+0x68/0x220 [ndiswrapper]
[29185.758753]  [<f917d746>] ? NdisDispatchPnp+0xb6/0xdd0 [ndiswrapper]
[29185.758753]  [<f9174d6e>] ? IoInitializeIrp+0x2e/0x60 [ndiswrapper]
[29185.758753]  [<f9173e43>] ? get_current_nt_thread+0x63/0x70 [ndiswrapper]
[29185.758753]  [<f917605b>] ? IoBuildAsynchronousFsdRequest+0x2b/0x140 [ndiswrapper]
[29185.758753]  [<f9175732>] ? IofCallDriver+0x52/0xc0 [ndiswrapper]
[29185.758753]  [<f9176ce5>] ? IoSendIrpTopDev+0xe5/0x140 [ndiswrapper]
[29185.758753]  [<f9177082>] ? wrap_pnp_start_device+0x1b2/0x2c0 [ndiswrapper]
[29185.758753]  [<f917792e>] ? wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[29185.881415] EIP: [<f916b6fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper] SS:ESP 0068:f75eb95c

---

### Post by wx5bix on 2013-05-25
ndiswdm : driver installed
        device (1737:0075) present

---

### Post by wx5bix on 2013-05-25
I found that I had the ndiswrapper bug and got it corrected, however it still doesnt show any wireless capability when i look up iwconfig. Am i still missing something ?

---

### Post by chili555 on 2013-05-25
Now that you have it solved, please reboot and show me:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
iwconfig
```

---

### Post by wx5bix on 2013-05-25
When i run sudo modprobe ndiswrapper my sys freezes up and reboots?

wx5bix@wx5bix:~$ ndiswrapper -l
ndiswdm : driver installed
        device (1737:0075) present

wx5bix@wx5bix:~$ dmesg | grep ndis
[   80.165339] rndis_host 3-2:1.0: usb0: register 'rndis_host' at usb-0000:00:16.2-2, RNDIS device, b2:7d:49:f0:9d:af
[   80.165704] usbcore: registered new interface driver rndis_host
[   80.210283] usbcore: registered new interface driver rndis_wlan
[ 1560.673903] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 1561.014592] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
[ 1561.434150] IP: [<f911d6fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[ 1561.434572] Modules linked in: ndiswrapper(O+) nls_utf8 isofs binfmt_misc rndis_wlan cfg80211 rndis_host cdc_ether usbnet dm_crypt psmouse cdc_acm serio_raw snd_hda_codec_realtek k10temp snd_hda_codec_hdmi snd_hda_intel snd_seq_midi snd_hda_codec snd_hwdep snd_rawmidi snd_pcm sp5100_tco i2c_piix4 snd_seq_midi_event rfcomm bnep bluetooth parport_pc snd_seq ppdev snd_timer snd_seq_device snd soundcore snd_page_alloc mac_hid lp parport usb_storage usbhid hid r8169 radeon ttm pata_atiixp drm_kms_helper drm i2c_algo_bit wmi
[ 1561.436179] EIP is at NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[ 1561.437391]  [<f912b652>] ? RtlFreeAnsiString+0x22/0x40 [ndiswrapper]
[ 1561.437391]  [<f911f398>] ? NdisReadNetworkAddress+0x1a8/0x1c0 [ndiswrapper]
[ 1561.437391]  [<f911f0f0>] ? read_setting+0x1f0/0x1f0 [ndiswrapper]
[ 1561.437391]  [<f912e788>] ? mp_init+0x68/0x220 [ndiswrapper]
[ 1561.437391]  [<f912f746>] ? NdisDispatchPnp+0xb6/0xdd0 [ndiswrapper]
[ 1561.437391]  [<f9126d6e>] ? IoInitializeIrp+0x2e/0x60 [ndiswrapper]
[ 1561.437391]  [<f9125e43>] ? get_current_nt_thread+0x63/0x70 [ndiswrapper]
[ 1561.437391]  [<f912805b>] ? IoBuildAsynchronousFsdRequest+0x2b/0x140 [ndiswrapper]
[ 1561.437391]  [<f9127732>] ? IofCallDriver+0x52/0xc0 [ndiswrapper]
[ 1561.437391]  [<f9128ce5>] ? IoSendIrpTopDev+0xe5/0x140 [ndiswrapper]
[ 1561.437391]  [<f9129082>] ? wrap_pnp_start_device+0x1b2/0x2c0 [ndiswrapper]
[ 1561.437391]  [<f912992e>] ? wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[ 1561.437391]  [<f911c6dd>] ? loader_init+0x9d/0x130 [ndiswrapper]
[ 1561.437391]  [<f912af87>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[ 1561.437391]  [<f9130c71>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[ 1561.437391]  [<f91be077>] ? wrapper_init+0x77/0x1000 [ndiswrapper]
[ 1561.437391] EIP: [<f911d6fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper] SS:ESP 0068:f02fdae4

wx5bix@wx5bix:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2013-05-25
I don't think you fixed the bug, eh? What steps did you take to try to fix it? 

Where did you get the .inf and .sys files? Are they for XP? Is yours a 32- or 64-bit system?```
arch
lsusb
```

---

### Post by wx5bix on 2013-05-25
I followed these steps

""
 			 				[INDENT] 					Congratulations! You have an officially recognized Ubuntu bug, you lucky penguin! 

[http://askubuntu.com/questions/13289...pper-not-found]("http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found")

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/986064]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064")

Please download ndiswrapper-dkms and dkms here and install it. Then do: 	Code:
 	
sudo modprobe ndiswrapper 
[http://packages.ubuntu.com/precise/ndiswrapper-dkms](http://packages.ubuntu.com/precise/ndiswrapper-dkms)

[http://packages.ubuntu.com/precise/dkms](http://packages.ubuntu.com/precise/dkms)

You should be all set. 				[/INDENT] 			
  			   		
 			 				 			 			 				[INDENT]Registered Linux User #374501

Tarballs R Us.
[/INDENT]

---

### Post by chili555 on 2013-05-25
However, that bug is, roughly, "module ndiswrapper not found." What you have is a severe lock-up. Do you have a temporary wired ethernet connection? If so, please do:```
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-dkms
sudo modprobe ndiswrapper
```If this doesn't help, we'll get out the big tools!

---

### Post by wx5bix on 2013-05-25
I reinstalled everything and tried to run "sudo modprobe ndiswrapper" and it doesnt do anything.

DKMS: install completed.
wx5bix@wx5bix:~$ sudo modprobe ndiswrapper


No info, no asking for pswd. Nothin ?

---

### Post by wx5bix on 2013-05-25
So i restarted Konsole and tried to run "sudo modprobe ndiswrapper" again and asked for a pswd but no joy

---

### Post by wx5bix on 2013-05-25
Is there a way i can take a screen shot and post it on here?

---

### Post by wx5bix on 2013-05-25
I restarted. The. System and. Ran it again and it gave me a ton of info but then froze. I took a pic of it with my iPad but cannot link the pic on here from the iPad.

---

### Post by chili555 on 2013-05-25
If it froze, then we have the same problem and haven't fixed it yet. Where did you get the .inf and .sys files? Are they for Windows XP? Is yours a 32- or 64-bit system?
```
arch
lsusb

```

---

### Post by wx5bix on 2013-05-25
wx5bix@wx5bix:~$ arch
i686
wx5bix@wx5bix:~$ Carter12
Carter12: command not found
wx5bix@wx5bix:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 005 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 1737:0075 Linksys WUSB54GSC v2 802.11g Adapter

---

### Post by wx5bix on 2013-05-25
I copied the xp_2k file from the CD and moved to a folder on desktop. the installed from that folder.

---

### Post by wx5bix on 2013-05-25
I checked to see if everything was installed correctly and here is what i found...


wx5bix@wx5bix:~$ sudo su
[sudo] password for wx5bix: 
root@wx5bix:/home/wx5bix# ndiswrapper -i desktop/xp_2k/ndiswdm.inf
driver ndiswdm is already installed
root@wx5bix:/home/wx5bix# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper.conf ...
root@wx5bix:/home/wx5bix# ndiswrapper -l
ndiswdm : driver installed
        device (1737:0075) present
root@wx5bix:/home/wx5bix# iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.

root@wx5bix:/home/wx5bix# exit
exit
wx5bix@wx5bix:~$ dmesg | grep ndis
[   33.963447] rndis_host 1-2:1.0: usb0: register 'rndis_host' at usb-0000:00:12.2-2, RNDIS device, b2:7d:49:f0:9d:af
[   33.963690] usbcore: registered new interface driver rndis_host
[   34.011194] usbcore: registered new interface driver rndis_wlan
[  167.493455] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  167.833673] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
[  168.251557] IP: [<f91336fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[  168.251978] Modules linked in: ndiswrapper(O+) rndis_wlan cfg80211 rndis_host cdc_ether usbnet dm_crypt bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi cdc_acm snd_seq_midi_event sp5100_tco snd_seq snd_timer snd_seq_device psmouse serio_raw snd i2c_piix4 k10temp soundcore snd_page_alloc mac_hid binfmt_misc lp parport usbhid hid r8169 pata_atiixp radeon ttm wmi drm_kms_helper drm i2c_algo_bit usb_storage
[  168.253543] EIP is at NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper]
[  168.254804]  [<f9141652>] ? RtlFreeAnsiString+0x22/0x40 [ndiswrapper]
[  168.254804]  [<f9135398>] ? NdisReadNetworkAddress+0x1a8/0x1c0 [ndiswrapper]
[  168.254804]  [<f91350f0>] ? read_setting+0x1f0/0x1f0 [ndiswrapper]
[  168.254804]  [<f9144788>] ? mp_init+0x68/0x220 [ndiswrapper]
[  168.254804]  [<f9145746>] ? NdisDispatchPnp+0xb6/0xdd0 [ndiswrapper]
[  168.254804]  [<f913cd6e>] ? IoInitializeIrp+0x2e/0x60 [ndiswrapper]
[  168.254804]  [<f913be43>] ? get_current_nt_thread+0x63/0x70 [ndiswrapper]
[  168.254804]  [<f913e05b>] ? IoBuildAsynchronousFsdRequest+0x2b/0x140 [ndiswrapper]
[  168.254804]  [<f913d732>] ? IofCallDriver+0x52/0xc0 [ndiswrapper]
[  168.254804]  [<f913ece5>] ? IoSendIrpTopDev+0xe5/0x140 [ndiswrapper]
[  168.254804]  [<f913f082>] ? wrap_pnp_start_device+0x1b2/0x2c0 [ndiswrapper]
[  168.254804]  [<f913f92e>] ? wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
[  168.254804]  [<f91326dd>] ? loader_init+0x9d/0x130 [ndiswrapper]
[  168.254804]  [<f9140f87>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[  168.254804]  [<f9146c71>] ? wrapndis_init+0x41/0x50 [ndiswrapper]
[  168.254804]  [<f90ee077>] ? wrapper_init+0x77/0x1000 [ndiswrapper]
[  168.254804] EIP: [<f91336fd>] NdisMQueryAdapterResources+0x1d/0xb0 [ndiswrapper] SS:ESP 0068:f6895ae4
wx5bix@wx5bix:~$ iwconfig
lo        no wireless extensions.                                                                                                                                                               
                                                                                                                                                                                                
usb0      no wireless extensions.                                                                                                                                                               
                                                                                                                                                                                                
eth0      no wireless extensions.                                                                                                                                                               
                                                                                                                                                                                                
wx5bix@wx5bix:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 005 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 1737:0075 Linksys WUSB54GSC v2 802.11g Adapter

---

### Post by wx5bix on 2013-05-25
I unplugged the wireless card and plugged it back in and the system crashed after restarting i got this error
"the application KNetAttach has closed unexpectedly"
I think there is more going on than just the wireless install issues ?

---

### Post by wx5bix on 2013-05-25
Well I've tried everything I can think of, short of buying a new wireless adapter or moving my entire office. Guess ill keep searching for other options.
Thanks to everyone that has tried to help!

---

### Post by chili555 on 2013-05-25
You haven't yet tried compiling ndiswrapper-1.58 from source. Get a temporary wired ethernet coonection and do:```
sudo apt-get remove --purge ndiswrapper*
```Then follow these instructions to compile ndiswrapper-1.58: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981)

Then you'll probably need to reinstall the inf file:```
sudo ndiswrapper -i Desktop/xp_2k/ndiswdm.inf
```And load ndiswrapper:```
sudo modprobe ndiswrapper
```Check for errors or warnings:```
dmesg | grep ndis
```

---

### Post by wx5bix on 2013-05-25
i get all the way through "sudo make install" and enter "modprobe ndiswrapper" and still hangs...

---

### Post by wx5bix on 2013-05-25
I am reinstalling Ubuntu 12.04 from disk instead up the downloaded upgrades. See if that makes any difference.
I will try to reinstall the driver after the fresh install

---

### Post by wx5bix on 2013-05-25
O so I reinstalled Ubuntu 12.04 and tried to install ndiswrapper-1.58 as instructed but when I get to modprobe ndiswrapper the system still hangs and never progresses. Any other ideas ?

---

### Post by wx5bix on 2013-05-25
```
wx5bix@wx5bix:~$ sudo apt-get install linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev libtimedate-perl
  linux-headers-3.2.0-44-generic
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl linux-headers-3.2.0-44-generic
  linux-headers-generic
0 upgraded, 12 newly installed, 0 to remove and 542 not upgraded.
Need to get 10.1 MB of archives.
After this operation, 38.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.1 [180 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.1 [469 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main build-essential i386 11.5ubuntu2.1 [5,796 B]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-44-generic i386 3.2.0-44.69 [977 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic i386 3.2.0.44.53 [2,446 B]
Fetched 10.1 MB in 1min 36s (106 kB/s)                                         
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 168377 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7.1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-44-generic.
Unpacking linux-headers-3.2.0-44-generic (from .../linux-headers-3.2.0-44-generic_3.2.0-44.69_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.44.53_i386.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.1) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.1) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.2.0-44-generic (3.2.0-44.69) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-44-generic /boot/vmlinuz-3.2.0-44-generic
Setting up linux-headers-generic (3.2.0.44.53) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
wx5bix@wx5bix:~$ cd Desktop/ndiswrapper-1.58
wx5bix@wx5bix:~/Desktop/ndiswrapper-1.58$ make
make -C utils
make[1]: Entering directory `/home/wx5bix/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/wx5bix/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/home/wx5bix/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.2.0-44-generic-pae M=/home/wx5bix/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-44-generic-pae'
  LD      /home/wx5bix/Desktop/ndiswrapper-1.58/driver/built-in.o
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/crt_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/hal_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
  MKEXPORT /home/wx5bix/Desktop/ndiswrapper-1.58/driver/usb_exports.h
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/crt.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/hal.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/loader.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ndis.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/pe_linker.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/pnp.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/proc.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/rtl.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/wrapmem.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/wrapndis.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/wrapper.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/usb.o
  CC [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/divdi3.o
  LD [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
  LD [M]  /home/wx5bix/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-44-generic-pae'
make[1]: Leaving directory `/home/wx5bix/Desktop/ndiswrapper-1.58/driver'
wx5bix@wx5bix:~/Desktop/ndiswrapper-1.58$ sudo make install
make -C driver install
make[1]: Entering directory `/home/wx5bix/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.2.0-44-generic-pae/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.2.0-44-generic-pae/misc
/sbin/depmod -a 3.2.0-44-generic-pae
make[1]: Leaving directory `/home/wx5bix/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory `/home/wx5bix/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/wx5bix/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
wx5bix@wx5bix:~/Desktop/ndiswrapper-1.58$ modprobe ndiswrapper
                                                                    

```

---

### Post by wx5bix on 2013-05-26
correct me if im wrong, but it doesnt seem to me like ndiswrapper is installing ?

---

### Post by wx5bix on 2013-05-26
When I run modprobe ndiswrapper the terminal just hangs, if I try to close terminal it shows a process is running but never finishes. I'm about to pull my hair out. Been trying to install this driver for days now and really need to Internet on it.

---

### Post by wx5bix on 2013-05-26
I've gotten into ndisgtk to install the driver, however when I direct it to the .inf file it hangs and does not proceed after I click install

---

### Post by wx5bix on 2013-05-26
```
wx5bix@wx5bix:~$ sudo ndisgtk

(ndisgtk:6795): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
/usr/sbin/ndisgtk:127: GtkWarning: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.S2R0XW': No such file or directory
  gtk.main()
/usr/sbin/ndisgtk:127: GtkWarning: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
  gtk.main()
/usr/sbin/ndisgtk:127: GtkWarning: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.CYT0XW': No such file or directory
  gtk.main()
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf


```

---

### Post by wx5bix on 2013-05-26
How do I uninstall ndiswrapper? I think I need to start from the beginning and reinstall everything to see if maybe I missed something.

---

### Post by wx5bix on 2013-05-26
ok, I know whats hanging me up, how do i fix it ?

```
ndiswrapper:
Running module version sanity check.
Error! Module version 1.57 for ndiswrapper.ko
is not newer than what is already found in kernel 3.2.0-44-generic-pae (1.58).
You may override by specifying --force.


```

---

### Post by chili555 on 2013-05-27
> ndiswrapper:
Running module version sanity check.
Error! Module version 1.57 for ndiswrapper.ko
is not newer than what is already found in kernel 3.2.0-44-generic-pae (1.58).
You may override by specifying --force.This should not have happened if you did:```
sudo apt-get remove --purge ndiswrapper*
```Please try again and then reboot. Recompile:```
cd Desktop/ndisrapper-1.58[COLOR="#FF0000"] <--or wherever the folder is located, if not Desktop[/COLOR]
make clean
make
sudo make install
```Check your version:```
ndiswrapper -v
```Now remove the .inf:```
sudo ndiswrapper -e ndiswdm
sudo rm -rf /etc/ndiswrapper/*
```Now see if ndiswrapper loads without a lock-up:```
sudo modprobe ndiswrapper
```If it does, reload the inf:```
sudo ndiswrapper -i Desktop/xp_2k/ndiswdm.inf
```If there is still no lock-up, try:```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
iwconfig
```

---

### Post by wx5bix on 2013-05-27
I ran through and removed ndiswrapper, rebooted and reinstalled. modprobe ndiswrapper worked fine!!
Now im trying to install the ndiswdm.inf and here's what i get.

```
wx5bix@wx5bix:~$ sudo ndiswrapper -i Desktop/xp_2k/ndiswdm.inf
[sudo] password for wx5bix: 
couldn't open Desktop/xp_2k/ndiswdm.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.


```

I have the file on my Desktop and is the current version.

---

### Post by wx5bix on 2013-05-27
```
wx5bix@wx5bix:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.2.0-44-generic-pae/misc/ndiswrapper.ko
version:        1.58
vermagic:       3.2.0-44-generic-pae SMP mod_unload modversions 686 


```

---

### Post by wx5bix on 2013-05-27
```
wx5bix@wx5bix:~$ sudo ndiswrapper -e ndiswdm
[sudo] password for wx5bix: 
couldn't delete /etc/ndiswrapper/ndiswdm: No such file or directory
wx5bix@wx5bix:~$ sudo rm -rf /etc/ndiswrapper/*
wx5bix@wx5bix:~$ sudo modprobe ndiswrapper
wx5bix@wx5bix:~$ sudo ndiswrapper -i Desktop/xp_2k/ndiswdm.inf
couldn't open Desktop/xp_2k/ndiswdm.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.


```

---

### Post by chili555 on 2013-05-28
Let's see:```
ls Desktop
```Is the directory xp_2k listed there? If so, then let us see:```
ls Desktop/xp_2k
```Is ndiswdm.inf among other files listed? If so, let's go about this another way:```
cd Desktop/xp_2k
sudo ndiswrapper -i ndiswdm.inf
```How about now?

---

### Post by wx5bix on 2013-05-28
```
wx5bix@wx5bix:~$ ls Desktop
ndiswrapper-1.58  XP_2K
wx5bix@wx5bix:~$ ls Desktop/xp_2k
ls: cannot access Desktop/xp_2k: No such file or directory
wx5bix@wx5bix:~$ ls Desktop/xp_2k
bcm43xx64.cat  bcm43xx.cat  ndiswdm.inf  ndiswdm.sys
wx5bix@wx5bix:~$ cd Desktop/xp_2k
wx5bix@wx5bix:~/Desktop/xp_2k$ sudo ndiswrapper -i ndiswdm.inf
[sudo] password for wx5bix: 
installing ndiswdm ...
forcing parameter IBSSGMode from 0 to 2
wx5bix@wx5bix:~/Desktop/xp_2k$ 


```

---

### Post by chili555 on 2013-05-29
> wx5bix@wx5bix:~$ ls Desktop
ndiswrapper-1.58  **XP_2K**It appears that the name of the folder is XP_2K and not xp_2k. Linux is funny about that. The case counts. There is no 'almost' or 'I know what you meant' in Linux.

However, even so, you managed to get there!!!> wx5bix@wx5bix:~$ ls Desktop/xp_2k
bcm43xx64.cat  bcm43xx.cat  ndiswdm.inf  ndiswdm.sysHow you did that, I have no idea.  :confused:  And then:> wx5bix@wx5bix:~/Desktop/xp_2k$ sudo ndiswrapper -i ndiswdm.inf
[sudo] password for wx5bix: 
installing ndiswdm ...
forcing parameter IBSSGMode from 0 to 2So the inf file seemed to get installed with a bit of a hitch. Now what is the result of:```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

