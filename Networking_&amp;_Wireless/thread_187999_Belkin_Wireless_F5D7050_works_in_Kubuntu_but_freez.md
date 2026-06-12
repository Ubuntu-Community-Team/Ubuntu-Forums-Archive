---
title: "Belkin Wireless F5D7050 works in Kubuntu but freezing the box in Ubuntu"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by guptan on 2006-06-03
I have a ***Belkin F5D7050*** USB wireless adapter which works fine on Kubuntu Desktop out of the box. It can very well search for available WiFi networks and get authenticated against WEP 128bit encryption and CONNECT to the network. But the very same card fails to work with Ubuntu Desktop, and it even freezes the system when I try to activate WiFi connection. I was thinking both Ubuntu and Kubuntu is having same hardware capabilities but  why my Wireless card is not working with Ubuntu when it can work very well in Kubuntu.

Please help me to sort out this issue. 

thanks in advance

Guptan.

---

### Post by guptan on 2006-06-04
Any takers?

---

### Post by jono.carnie on 2006-06-04
[QUOTE=guptan]Any takers?[/QUOTE]

Hi Guptan,

I got the F5D7050 to work under ubuntu with a little playing around using the ndiswrapper method and the rt73 driver.

Never used kubuntu, but you're right I wouldn't expect the change in interface to cause problems.

JC

---

### Post by ramcosca on 2006-06-06
[QUOTE=jono.carnie]Hi Guptan,

I got the F5D7050 to work under ubuntu with a little playing around using the ndiswrapper method and the rt73 driver.

Never used kubuntu, but you're right I wouldn't expect the change in interface to cause problems.

JC[/QUOTE]Now, explain this to a Linux n00b, please.

---

### Post by pelle.k on 2006-06-08
do "sudo nano /var/log/syslog" which should give you a log file with time stamps...
If you do this right after a freeze (and of course a reboot) find the time where it happened and copy/paste all relevant output in this thread.

---

### Post by tible on 2006-06-27
[QUOTE=guptan]I have a ***Belkin F5D7050*** USB wireless adapter which works fine on Kubuntu Desktop out of the box. It can very well search for available WiFi networks and get authenticated against WEP 128bit encryption and CONNECT to the network. But the very same card fails to work with Ubuntu Desktop, and it even freezes the system when I try to activate WiFi connection. I was thinking both Ubuntu and Kubuntu is having same hardware capabilities but  why my Wireless card is not working with Ubuntu when it can work very well in Kubuntu.

Please help me to sort out this issue. 

thanks in advance

Guptan.[/QUOTE]

Don't know if you sorted out, but I had exactly the same problem! My fingers were bleeding! 
Now my Belkin USB Network Adapter F5D7050 is WORKING on Ubuntu 6.06.
I used teh version of **Ndiswrapper** that comes with Ubuntu's CD. I copied the rt2500usb.inf, rt2500usb.sys and rt2500usb.cat (this one just to be sure... you know after ages under windoze ](*,) ) in my home directory from Belkin's installation directory under windoze. I unplugged everything from my USBs apart the wireless adapter (I've red somewhere that this could be one of the causes). 

Instaled the Windoze driver:
**tible@IrishLad:~$ sudo ndiswrapper -i rt2500usb.inf**

loaded the module instaled :
**tible@IrishLad:~$ sudo modprobe ndiswrapper**

checked if the module is loaded:
**tible@IrishLad:~$ ndiswrapper -l**
terminal answer:
[B]Installed ndis drivers:
rt2500usb               driver present, hardware present[/B]


I configured the wireless connection using the GUI window (iwconfig command from terminal is useless - hope to be wrong), actived and I get myself a freezed computer. Cursed windoze a lot ... :) ... and pressed the reset button. This happened several times till I start to read the ndiswrapper options and i noticed this:

[B]tible@IrishLad:~$ ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-[COLOR="Red"]d devid driver   Use installed 'driver' for 'devid'[/COLOR]
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


[COLOR="Red"]where 'devid' is either PCIID or USBID of the form XXXX:XXXX[/COLOR][/B]
This could be the secret.

I used this command:
**tible@IrishLad:~$ sudo ndiswrapper -d 050d:7050 rt2500usb**

and then I activated using the GUI networtk tool: The computer didnt freeze and the device green led start to blink! :mrgreen: 
I was HAPPY!

This is my story!
Good luck lads!
Tible the newbie.
(PS: My next goal is to recompile the kernel for my crap PC!)

---

### Post by neoTheCat on 2006-07-04
i tried everything as above, but when i load up the GUI, it just sits there and the cursor just spins.  this is what i get from dmesg:
```

[4296319.554000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4296319.562000] ndiswrapper: driver blkwgu (Belkin,11/10/2005,6.3.2.16) loaded
[4296322.200000] wlan0: vendor: 'Belkin Wireless G USB Network Adapter'
[4296322.200000] wlan0: ndiswrapper ethernet device 00:11:50:b1:51:f6 using driver blkwgu, 050D:705C.F.conf
[4296322.200000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4296322.202000] usbcore: registered new driver ndiswrapper
[4296325.321000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[4296325.321000]  printing eip:
[4296325.321000] 00000000
[4296325.321000] *pde = 00000000
[4296325.321000] Oops: 0000 [#1]
[4296325.321000] PREEMPT
[4296325.321000] Modules linked in: ndiswrapper isofs udf nls_cp437 ntfs rfcomm l2cap bluetooth ppdev radeon drm speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery i2c_acpi_ec ac ipv6 dm_mod md_mod af_packet lp joydev tsdev parport_pc parport psmouse serio_raw pcmcia snd_ali5451 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss pcspkr rtc snd_pcm snd_timer ati_agp agpgart shpchp pci_hotplug natsemi yenta_socket rsrc_nonstatic pcmcia_core snd soundcore snd_page_alloc i2c_ali1535 i2c_ali15x3 i2c_core evdev ext3 jbd ide_generic ohci_hcd usbcore ide_cd cdrom ide_disk generic alim15x3 thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4296325.321000] CPU:    0
[4296325.321000] EIP:    0060:[<00000000>]    Tainted: P      VLI
[4296325.321000] EFLAGS: 00010286   (2.6.15-23-386)
[4296325.321000] EIP is at _stext+0x3feffdc0/0x40
[4296325.321000] eax: c00000bb   ebx: d9316760   ecx: 0001010e   edx: ffff000d
[4296325.321000] esi: d83e4000   edi: 00000246   ebp: d83e5f4c   esp: d83e5f40
[4296325.321000] ds: 007b   es: 007b   ss: 0068
[4296325.321000] Process wrapper_wq (pid: 8459, threadinfo=d83e4000 task=d7c7d030)
[4296325.321000] Stack: d7560000 00000000 00000000 00000000 ecddfc81 d756ccd8 d7560000 ecdfe1e0
[4296325.321000]        ecdfe1e4 c012caca 00000000 d83e4000 eb588758 eb588748 eb588750 d83e4000
[4296325.321000]        ecddfbf0 d83e4000 00000001 00000000 d8ead6c0 00010000 00000000 00000000
[4296325.321000] Call Trace:
[4296325.321000]  [<ecddfc81>] wrap_work_item_worker+0x91/0xf0 [ndiswrapper]
[4296325.321000]  [<c012caca>] worker_thread+0x1ba/0x290
[4296325.321000]  [<ecddfbf0>] wrap_work_item_worker+0x0/0xf0 [ndiswrapper]
[4296325.321000]  [<c0118940>] default_wake_function+0x0/0x20
[4296325.321000]  [<c012c910>] worker_thread+0x0/0x290
[4296325.321000]  [<c0130d53>] kthread+0x93/0xa0
[4296325.321000]  [<c0130cc0>] kthread+0x0/0xa0
[4296325.321000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4296325.321000] Code:  Bad EIP value.
[4296325.321000]  <7>wlan0: no IPv6 routers present
[4296416.329000] ndiswrapper (iw_get_range:1415): getting bit rates failed: C0000001
[4296455.346000] ndiswrapper (iw_get_range:1415): getting bit rates failed: C0000001
[4296494.362000] ndiswrapper (iw_get_range:1415): getting bit rates failed: C0000001

```

but the drivers seemed to load up fine.  "ndiswrapper -l" gives me:
```

Installed ndis drivers:
blkwgu          driver present, hardware present

```

the only difference is i do not have the "rt2500*" files, but  BLKWGU.* files.  it's the F5D7050 version 4, if that makes a difference.

i never had this problem when i used my PCMCIA card, but since that flaked out, i have no choice other then USB.

thanks,
-=- neoTheCat

---

### Post by Arevos on 2006-08-29
Get the version 3 driver for the F5D7050. Dapper recognises that and runs it, whilst it seems to have problems with version 4. The downside is that there seems to be some manner of race condition with the driver that freezes up Linux on occassion. I'm still trying to find a solution to this.

---

### Post by bodycoach2 on 2006-08-29
I got it to work after three to four tries on a few machines. Others, it worked perfect, out-of-the-box. One thing: Make sure you only make one change at a time in Network manager. If it freezes, just try again. It will eventually work. So far, got it to work on all my Ubuntu/Xubuntu installations, even after a few frustrating freezes.

> **guptan said:**
> I have a ***Belkin F5D7050*** USB wireless adapter which works fine on Kubuntu Desktop out of the box. It can very well search for available WiFi networks and get authenticated against WEP 128bit encryption and CONNECT to the network. But the very same card fails to work with Ubuntu Desktop, and it even freezes the system when I try to activate WiFi connection. I was thinking both Ubuntu and Kubuntu is having same hardware capabilities but  why my Wireless card is not working with Ubuntu when it can work very well in Kubuntu.

Please help me to sort out this issue. 

thanks in advance

Guptan.

---

### Post by morbid88 on 2006-09-09
Thank you *so much*. I've been wracking my brains on this all week, and finally you've helped me out.

I'm using an MSI M660 laptop with a built-in WLAN based on the rt2571.

Apparently, nothing on the rt2x00 ([http://rt2x00.serialmonkey.com/]("http://rt2x00.serialmonkey.com")) project can help me get this thing to work without freezing, and much as I'd have loved to use the native drivers, I go with what I can get.

The manual for the laptop stated that it was an intel PRO 3945ABG, and I tried using those drivers for a few days and they wouldn't work. Then it occured to me to see which drivers windows installed, and look THAT up.

Damn manual was *wrong*. Hope someone else out there can make use of this information.

Now I'll be able to use Linux at home and at school! :-D 



> **tible said:**
> Don't know if you sorted out, but I had exactly the same problem! My fingers were bleeding! 
Now my Belkin USB Network Adapter F5D7050 is WORKING on Ubuntu 6.06.
I used teh version of **Ndiswrapper** that comes with Ubuntu's CD. I copied the rt2500usb.inf, rt2500usb.sys and rt2500usb.cat (this one just to be sure... you know after ages under windoze ](*,) ) in my home directory from Belkin's installation directory under windoze. I unplugged everything from my USBs apart the wireless adapter (I've red somewhere that this could be one of the causes). 


---

### Post by dom on 2006-09-21
Hi all,

I have also a Belkin F57050.

The device IC-ID is 3623A-F5D7050B
The device FCC-ID is K7S-F5D7050B

A sticker on the box notes "Version 3000uk".

Now, I've tried the rt73 drivers that come on the CD with the device.

I've gotten this to work fine with WPA and the ndiswrapper.

I cannot get it to work with wep however, though iwlist will show the networks, trying to connect with WEP doesn't work, it won't even associate. I've spent ages at this checking the key over and over, trying different iwconfig settings etc. No joy.

Yester eve I downloaded new drivers from belkins site, and I think I got the wrong ones as I ended up with the BLKWGU.* files and they didn't work at all. They seem to be for device 050D:705C where my device is 050D:705A.

If anybody has successfully gotten the device I have, as described above, to work with WEP i would like to hear how. 

What drivers are used and where on-line can they be found (or can you attach them here if not online)

With this device and rt73 driver I also see strange behaviour like hangs if i remove the device without doing ifdown or ifconfig down on it first, and even then there's no guarantee that it won't do something funny to the machine.

Anyway, hoping for help

---

### Post by asadler on 2006-09-23
Hi all,

I bought the F5D7050uk adpater, and there is a stiker on the box that says version 3000uk.  I am able to use the adapter with the rt73 drivers that come on the installation CD, but the connection does not stay up for more than a few hours before I get some kernel errors.....

 Badness in uhci_map_status at drivers/usb/host/uhci-hcd.c:726
t kernel:  [tcp_v4_err+773/1856] uhci_map_status+0x95/0xa0
t kernel:  [tcp_v4_err+1785/1856] uhci_result_control+0xf9/0x220
t kernel:  [tcp_v4_hnd_req+265/408] uhci_transfer_result+0x16d/0x180
t kernel:  [pg0+542083545/1069654016] timer_proc+0x69/0xa0 [ndiswrapper]
t kernel:  [tcp_v4_rcv+1405/1780] uhci_irq+0xe1/0x200
t kernel:  [tcp_setsockopt+546/1720] usb_hcd_irq+0x36/0x70
t kernel:  [save_v86_state+233/364] handle_IRQ_event+0x49/0x80
t kernel:  [do_sys_vm86+355/356] do_IRQ+0x8f/0x130
t kernel:  [show_registers+312/348] common_interrupt+0x18/0x20
t kernel: uhci_hcd 0000:00:1f.2: uhci_result_control: failed with status 800000
t kernel: [dfc2d270] link (1fc2d1e2) element (00000001)
t kernel:  Element != First TD
t kernel:   0: [c93a10c0] link (093a1100) e3 Length=7 MaxLen=7 DT0 EndPt=0 Dev=3
t kernel:   1: [c93a1100] link (093a1140) e3 SPD Length=3 MaxLen=3 DT1 EndPt=0 D
t kernel:   2: [c93a1140] link (00000001) e3 IOC Length=7ff MaxLen=7ff DT1 EndPt
t kernel: 


I tried upgrading to the "F5D7050_v4 Drivers" to no avail, then I noticed that the "F5D7050_v3 Drivers" page ([http://web.belkin.com/support/download/download.asp?download=F5D7050_v3&lang=1&mode=](http://web.belkin.com/support/download/download.asp?download=F5D7050_v3&lang=1&mode=)) contains the note "Only to use with a Version 3000 Adapter" so I am trying these now and will report back with any progress.

Andrew

---

### Post by pelle.k on 2006-09-24
Just to fill in:
'lsusb' tell me i have a "Bus 005 Device 004: ID 050d:705a Belkin Components".
I use the driver wich came on the driver cd. This is what I see in the first section of my inf file:
```
[ControlFlags]
;***********Belkin 802.11g board  ***********
;ExcludeFromSelect = USB\VID_050D&PID_705A

[Manufacturer]
%Belkin%        = Belkin

[Belkin]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
%050D7050.DeviceDesc%       = 050D7050.ndi,         USB\VID_050D&PID_705A
```
You see reference to your "id" all over the place. I suggest you do the same in those drivers you download from the internet...

I' have been running ndiswrapper on all kind of diffrent distros (using wep, so i don't know if it'll work with WPA) with succes on the first try.
It disconnects frequently on ndiswrapper versions older than the dapper one though...

---

### Post by Arevos on 2006-09-27
I found that the F5D7050 froze up my system after a few hours, perhaps as a result of the kernel errors asadler reported. I believe this is due to a bug in ndiswrapper, as the problems stopped when I installed the latest ndiswrapper from source (version 1.23). In the ndiswrapper changelog for version 1.18, there is mention of a bugfix for the freezing problems that plagued my system, so I suspect this bug affects all versions of ndiswrapper before 1.18, including version 1.8, which is included with Dapper.

Edgy currently has version 1.18, when last I checked, so the F5D7050 should work out of the box with 6.10. For those unwilling to try out Knot 3, the problem can also be easily solved by downloading ndiswrapper from source and installing it with "make install". I found that I had to install the drivers through the command line, as the GUI tool seemed to mess things up a bit (perhaps it only works with 1.8?).

This solved the problems for me, so it seems likely it will for everyone else, too.

---

### Post by homburg on 2006-09-27
[U]I have the belkin 802.11g usb adapter with fcc id k7sf5d7050A (I have no idea what version this translates to).
Linux says its version "1000" and uses the driver info.linux.driver = rtusb

My ap is set up with mac filtering as the only security, so I just need to choose the correct ssid. I use the usb nic on windows on the same machine without any problems.

I am currently using Dapper 6.06 (Had to install with the alternate cd because of my nvidia card, but thats a whole other story).

I have installed gnome-network-manager

I have three methods of activating the usb nic network interface ("rausb0"): 
1. Terminal: iwconfig
2. Ubuntu native network manager
3. gnome-network-manager

1. IWCONFIG
This method works! with no problems, that I can tell.
I open a terminal window and type

```
sudo iwconfig rausb0 essid ssidnameofmyap
sudo dhclient rausb0
```

and im connected to the net.

2. UBUNTU native network manager
Freezes, when I try to activate the interface.

3. gnome-network-manager
My ap shows up among others in the list of aps in the context menu of nm-applet.
But when I try to connect by clicking the "ssidnameofmyap" menu item, nm-applet goes to working mode and the usb key led starts blinking happily, but fails after af few seconds.

Since the native driver works without a problem, I would like to use this instead of ndiswrapper.

---

### Post by dom on 2006-10-10
cheers arevos, good to know, may get around to fixing with the newest ndiswrapper.

---

### Post by sheepsheds1 on 2007-02-18
I have currently tried to install my belkin network usb adaptor using the gui form of ndiswrapper. I says the drivers are installed and the hardware is present but when i use the command iwconfig then it does not say any networks are available. please help?

---

### Post by dom on 2007-02-26
> **sheepsheds1 said:**
> I have currently tried to install my belkin network usb adaptor using the gui form of ndiswrapper. I says the drivers are installed and the hardware is present but when i use the command iwconfig then it does not say any networks are available. please help?

Get WiFi Manager, if the adaptor is working, that should show you visible AP's and let you connect with the least amount of hassle. I no longer use the Belkin Adaptor I got, but I love wifi manager for managing wireless.

---

