---
title: "D-Link DWA-125 Wireless 150 USB Adapter"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by flbiggs on 2009-10-12
My kid has an HP computer that connects to the family's wireless gateway with a D-Link DWA-125 Wireless 150 USB Adapter.  The wireless adapter performed flawlessly under Vista, but I got tired of having to maintain Vista.  So, I installed Ubuntu on the HP, keeping Vista on a dual-boot partition in case he has to run Vista for school for some reason.  Ubuntu did not recognize the D-Link DWA-125 out of the box.

In case it saves others a few hours of time, here is how I got the wireless adapter working:

1.  Being lazy, I started with ndiswrapper.  But, it would not run the windows driver provided by D-Link (giving an error related to MmGetSystemRoutineAddress).  I compiled ndiswrapper using the most recent version... same error.  Looks like a bug or an unsupported call in the driver.

2.  The DWA-125 has a Ralink RT3070 chipset.  I tried the latest Ralink windows xp driver for the chipset.  Same problem.

3.  Fortunately, Ralink provides source code for linux kernel drivers.  So, I downloaded the latest linux driver for the RT3070USB from [www.ralinktech.com](www.ralinktech.com).  I extracted to my local directory.  Prior to compilation, I changed several options in the [ROOT_OF_DRIVER_SOURCE/]os/linux/config.mk file (more specifically, I changed 2 wpa_supplicant lines to 'y' instead of 'n').  In the root of the driver's source directory, I ran 'sudo make', and then 'sudo make install".  [EDIT:  NOTE THAT YOU NEED TO INSTALL THE 'BUILD-ESSENTIAL' PACKAGE FIRST]

3.  In Ubuntu 9.10 Karmic, the new kernel drivers for other Ralink cards really seem to muck things up, and I was not able to get them to work for this chipset (hopefully that is only a minor glitch).  To fix (9.10 only):

[INDENT]   a.  I blacklisted the newly built in Ralink drivers by adding the following end of the /etc/modprobe.d/blacklist.conf file:

      blacklist rt2x00usb
      blacklist rt2x00lib
      blacklist rt2800usb[/INDENT]

[INDENT]   b.  The kernel was still not loading my Ralink driver. I found that the kernel staging directory still had the old version of the driver in it. So, I moved that to a local directory (in case I need it later) by typing -- "sudo mv /lib/modules/2.6.31-15-generic/kernel/drivers/staging/rt3070/rt3070sta.ko [DESTINATION OF LOCAL DIRECTORY]."  UNFORTUNATELY, THIS NEEDS TO BE DONE AFTER EVERY KERNEL UPDATE.  UGH.  CAN SOMEONE ADVISE AS TO WORKAROUND? [/INDENT]

[INDENT][NOTE: My kernel at the time was 2.6.31-15-generic. If your's is different then the directories will change accordingly.][/INDENT]

[INDENT]   c.  Just in case, I run "sudo depmod"[/INDENT]

4.  I then installed the driver into the kernal by typing 'sudo modprobe rt3070sta'.  Plug in device and watch kernel log (or run dmesg) to make sure kernel identified USB device, loaded correct module and did not throw errors.

[INDENT]Some people report that dmesg/kernel log throws the following error when they plug in the device at this point:  "Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!".  That is a problem, and I believe it comes from a bug in the source code.  Fix by creating a sybolic link to the directory "/etc/Wireless/RT3070STA" called /etc/Wireless/RT2870STA".[/INDENT]
 
[INDENT]Note:  I as able to connect to the (temporarily unencrypted) network using iwconfig and ifconfig.  However, on reboot, the new rt3070sta kernel module was not loading automatically.  I found that the Wireless adapter was still causing ndiswrapper to load in place of the new rt3070sta kernel module.  I found that this was caused by 'alias' commands in the file '/etc/modprobe.d/ndiswrapper' interfering with things.  Since I did not need ndiswrapper any longer, I uninstalled it and deleted '/etc/modprobe.d/ndiswrapper'.  After that, the driver loaded flawlessly and automatically after reboot and/or re-plugging the usb device.[/INDENT]

5.  To get network-manager to work, change [ifupdown] managed=false to true in /etc/NetworkManager/nm-system-settings.conf. Then, reboot or run the following:

   sudo /etc/init.d/networking restart
   sudo restart network-manager

I hope this helps.

---

### Post by b2d on 2009-12-02
Sorry I'm all new to installing wifi from console, as you said default gnome managlment doesn't help out.
Please write all you 
iwconfig iwspy commands,
also please say if we need smth for WPA2 auth.
;)

---

### Post by flbiggs on 2009-12-08
[NOTE, I EDITED INITIAL POST TO INCLUDE WHAT I REPORTED IN THIS REPLY -- THAT IS, WORK AROUND FOR 9.10 KARMIC AND GETTING NETWORK-MANAGER UP AND RUNNING]

This driver stopped working after I upgraded to Ubuntu 9.10 - Karmic.  I downloaded the newest version of the driver's source code from Ralink, and compiled it using the instructions set forth above.  The wireless device would not work as it had with previous versions of Ubuntu.  The problem generally seemed to come from the newlyincluded kernel drivers for some Ralink chips -- rt2x00.  

Unfortunately, I was not able to make these drivers work for this RT3070 device (although I did not spend a huge amount of time on it).

After installing most current Ralink driver from source, here is what I did to restore perfect functionality to the device:

I blacklisted the newly built in Ralink drivers by adding the following end of the /etc/modprobe.d/blacklist.conf file:

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

2.  The kernel was still not loading my Ralink driver.  I found that the kernel staging directory still had the old version of the driver in it.  [EDIT:  NO HARD LINK IS NEEDED]  So, deleted /lib/modules/2.6.31-15-generic/kernel/drivers/staging/rt3070/rt3070sta.ko."

[NOTE: My kernel no is 2.6.31-15-generic.  If your's is different then the directories will change accordingly.]
[REQUEST:  I am not sure that it is technically correct to manipulate the staging directory this way.  Can someone explain a better/proper way?]

3.  run "sudo depmod" to update module dependencies.

4.  run lsmod to make sure none of the old rt*** drivers are loaded.  If any appear, then run sudo -r [NAME] to remove them.

5.  install the new module into the kernel by typing "sudo modprobe -i rt3070sta".

6.  Plug in device and watch kernel log (or run dmesg) to make sure kernel identified USB device, loaded correct module and did not throw errors.

7.  To get network-manager to work, change [ifupdown] managed=false to true in /etc/NetworkManager/nm-system-settings.conf.  Then, reboot or run the following:

  sudo /etc/init.d/networking restart
  sudo restart network-manager


I hope this helps someone.  If anyone knows other ways to accomplish this, then please advise. I can generally solve these kind of problems, but don't pretend to know the "right way".  

Thanks

---

### Post by b2d on 2009-12-09
Thanks for the hint!! 
right now I have 9.04 Jaunty. I have downloaded rt3070 chip driver
and installed it. Got rt3070sta module. When I load it I have ra0 interface.
I try wlist scan..
No results for ra0, also I noticed that HWaddr is 00:00:00:00:00:00 - thats 100% strange.
So I can't get DWA-125 adapter working. I'm I donig smth wrong?
Please Help me out

---

### Post by flbiggs on 2009-12-09
I think its a good sign that ifconfig shows ra0.  Can you please post in output from:
 
  sudo ifconfig

  sudo lshw -C network

  cat /etc/network/interfaces | grep "ra0"

  cat /etc/modprobe.d/blacklist.conf | grep "rt"

  dmesg [to keep it simple, unplug usb and show only new dmesg output that results from plugging it in.  log file viewer may help with this.]

  cat /etc/NetworkManager/nm-system-settings.conf | grep "managed"

---

### Post by IgPoGo on 2009-12-09
[SIZE=2]Hi flbiggs and b2b:

I'm followed this post for some days, and figuring out how to do working my usb wifi device. So I did everything flbiggs has made, but my ubuntu is 9.10, and I didn't find your olds problems.

I made the new operations and have the same result as b2b. I have ra0

I did the series of commands you said, and these are the results:


ubuntu@ubuntu:~$ [COLOR=#4169e1]sudo[/COLOR] [COLOR=RoyalBlue]ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ca:67:b9  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feca:67b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5593528 (5.5 MB)  TX bytes:934232 (934.2 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ubuntu@ubuntu:~$ [COLOR=#4169e1]sudo lshw -C network[/COLOR]
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ca:67:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.1.2.0 multicast=yes wireless=RT2870 Wireless

ubuntu@ubuntu:~$ [COLOR=#4169e1]cat /etc/network/interfaces | grep "ra0"[/COLOR]
ubuntu@ubuntu:~$ [COLOR=#4169e1]cat /etc/network/interfaces[/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

ubuntu@ubuntu:~$ grep "ra0"   [COLOR=#ff0000]it isn't in this list!!![/COLOR]

ubuntu@ubuntu:~$ [COLOR=#4169e1]cat /etc/modprobe.d/blacklist.conf | grep "rt"[/COLOR]
[COLOR=#c0c0c0]# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hangs at desktop session start (Ubuntu: #246969)
# EDAC driver for amd76x clashes with the agp driver preventing the aperture[/COLOR]
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb


[COLOR=#ff0000]Now [/COLOR][COLOR=#4169e1]dmesg[/COLOR][COLOR=#ff0000], when I remove and put it[/COLOR]

[  355.990250] -->RTUSBVenderReset
[  355.990376] <--RTUSBVenderReset
[  356.445033] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  356.445042] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" [COLOR=#000000]failed![/COLOR][COLOR=#ff0000] why do it try to open this files????[/COLOR]
[  356.445049] 1. Phy Mode = 0
[  356.445053] ERROR!!! NICReadRegParameters failed, Status[=0x00000001]
[  356.451461] ---> RTMPFreeTxRxRingMemory
[  356.451513] <--- RTMPFreeTxRxRingMemory
[  356.451518] !!! rt28xx Initialized fail !!! [COLOR=#ff0000]OF COURSE[/COLOR]
[  800.891729] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  800.891734] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  800.891738] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 1091.742873] usb 1-2: USB disconnect, address 2
[ 1091.743078] rtusb_disconnect: unregister usbnet usb-0000:00:13.2-2
[ 1091.743086] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[ 1091.996136]  RTUSB disconnect successfully
[ 1241.952077] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 1242.101977] usb 1-2: configuration #1 chosen from 1 choice
[ 1242.110496] 
[ 1242.110499] 
[ 1242.110501] === pAd = fa5ce000, size = 471516 ===
[ 1242.110504] 
[ 1242.110510] <-- RTMPAllocAdapterBlock, Status=0


ubuntu@ubuntu:~$ [COLOR=#4169e1]cat /etc/NetworkManager/nm-system-settings.conf | grep "managed" [/COLOR]
managed=false
ubuntu@ubuntu:~$ 
[/SIZE]

 

 [SIZE=2]and one more[/SIZE]
 

 [SIZE=2]ubuntu@ubuntu:~$ [COLOR=#800000][COLOR=Teal]s[/COLOR][COLOR=Teal]udo ifconfig ra0 up[/COLOR][/COLOR][/SIZE]
 [SIZE=2]SIOCSIFFLAGS: Operation not permitted
--------------------------------------------

If I find out how to work the correct driver I'll post it.

I forgot the 5 step, but after do it the result is the same, now

ubuntu@ubuntu:~$ [COLOR=RoyalBlue]cat /etc/NetworkManager/nm-system-settings.conf | grep "managed" [/COLOR]
managed=true


but I have the same result for ifconfig and iwconfig 


[/SIZE]

---

### Post by flbiggs on 2009-12-09
NOTE:  I UPDATED INITIAL POST TO ADDRESS THIS WORK-AROUND

IgPoGo, The message, "Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!" looks like the problem.  

Do you have a directory called "/etc/Wireless/RT3070STA"?  If so, try renaming that directory "RT2870STA". [EDIT: BETTER YET, CREATE A SYMBOLIC LINK "ln -s" COMMAND.  MAKE SURE THE LINK TO THE DIRECTORY IS NAMED 'RT2870STA'].

Then, check to see whether the file in that directory is named "RT3070STA.dat."  If so, change the name to "RT2870STA.dat".

Let me know how that changes the dmesg output when you plug in the USB device. 

Ugh, this fix is getting kind of messy.  I think the code has a bug that needs correcting, but let's get you working before diving into the source code.

---

### Post by IgPoGo on 2009-12-09
Hi flbiggs, thanks a l lot, now the led on the usb is blinking!!!!

I changed name of folder RT3070STA as you indicated before, but inside this folder I already found the RT2870STA.dat, may be this was the reason for the mess inside the kernel.

[COLOR=Navy]IgPoGo, The message, "Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!" looks like the problem.  

Do you have a directory called "/etc/Wireless/RT3070STA"? If so, try renaming that directory "RT2870STA". [EDIT: BETTER YET, CREATE A SYMBOLIC LINK "ln -s" COMMAND. MAKE SURE THE LINK TO THE DIRECTORY IS NAMED 'RT2870STA'].

Then, check to see whether the file in that directory is named "RT3070STA.dat."  If so, change the name to "RT2870STA.dat".[/COLOR]  

This the result of [COLOR=Blue]dmesg[/COLOR], when I diconnected and connected again

[  753.316050] usb 1-2: USB disconnect, address 2
[  753.316144] rtusb_disconnect: unregister usbnet usb-0000:00:13.2-2
[COLOR=Red][  753.316150] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[  753.572184]  RTUSB disconnect successfully[/COLOR]
[COLOR=SeaGreen][  758.212079] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  758.361498] usb 1-2: configuration #1 chosen from 1 choice[/COLOR]
[  758.370105] 
[  758.370108] 
[  758.370110] === pAd = fa5b4000, size = 471516 ===
[  758.370113] 
[  758.370119] <-- RTMPAllocAdapterBlock, Status=0

There the sequence of checkings

ubuntu@ubuntu:~$ [COLOR=Blue]ifconfig ra0[/COLOR]
ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ [COLOR=Blue]iwconfig ra0[/COLOR]
ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ [COLOR=Blue]sudo ifconfig ra0 up[/COLOR]
WORKS and the led became alive

Now I have to use iwconfig to setup the connection to my wireless router, the Wicd Network Manager doesn't get the new device I need to do more work on it.

Thanks a lot again, I'll report the new step, I hope tomorrow.

---

### Post by b2d on 2009-12-10
> **flbiggs said:**
> NOTE:  I UPDATED INITIAL POST TO ADDRESS THIS WORK-AROUND

IgPoGo, The message, "Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!" looks like the problem.  

Do you have a directory called "/etc/Wireless/RT3070STA"?  If so, try renaming that directory "RT2870STA". [EDIT: BETTER YET, CREATE A SYMBOLIC LINK "ln -s" COMMAND.  MAKE SURE THE LINK TO THE DIRECTORY IS NAMED 'RT2870STA'].

Then, check to see whether the file in that directory is named "RT3070STA.dat."  If so, change the name to "RT2870STA.dat".

Let me know how that changes the dmesg output when you plug in the USB device. 

Ugh, this fix is getting kind of messy.  I think the code has a bug that needs correcting, but let's get you working before diving into the source code.

That made it up! I have WiFi NOW! best Thanks guys!
Upgrading to 9.10 )) will see what's next)

---

### Post by IgPoGo on 2009-12-10
SOLVED

I have to wake up with the comand [COLOR=Blue]sudo ifconfig ra0 up[/COLOR], but is working the [COLOR=SeaGreen]Wicd Network Manager[/COLOR] works with it.

This is the process I did after boot the computer

ubuntu@ubuntu:~$ [COLOR=Blue]iwconfig[/COLOR]
[COLOR=Silver]lo        no wireless extensions.

eth0      no wireless extensions.
[/COLOR]
ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$[COLOR=Blue] sudo ifconfig ra0 up[/COLOR]
ubuntu@ubuntu:~$ [COLOR=Blue]iwconfig[/COLOR]
[COLOR=Silver]lo        no wireless extensions.

eth0      no wireless extensions.
[/COLOR]
ra0       RT2870 Wireless  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

After searched my wireless router and connect whit it by[COLOR=SeaGreen] Wicd Network Manager[/COLOR]

ubuntu@ubuntu:~$ [COLOR=Blue]iwconfig[/COLOR]
[COLOR=Silver]lo        no wireless extensions.

eth0      no wireless extensions.[/COLOR]

ra0       RT2870 Wireless  ESSID:"gecho"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:24:B2:77:2F:8A   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-17 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now it's working great, thanks a lot flbiggs and b2b, I hope this post solved the similar problem to other users.

And now I can changed the old Win XP without the curse of the cable.


__________________________________________________

The USB worked simply writting ra0 on Wicd's settings, I had wlan0.

Then refresh, cllick on buttom, and select your router.

---

### Post by b2d on 2009-12-16
All seems fine guys. This manual works, BUT time after time my system loses WiFi and asks password, but when I enter it - it tries to connect permanentlty, but always fails and ask pass again, besides that it doesn't see any other wifis. The most common way of solvng this is to unplug DWA-125 adapter and to plugin again, after that all seems ok. Sorry maybe for my non-profession atitude, just ask if I'm the only one with this trouble.
More info:
dmesg
[90423.822740] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90438.823849] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90453.824784] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90468.825879] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90483.826381] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90498.827472] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90513.828284] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90528.829343] IOCTL::unknown IOCTL's cmd = 0x000089f0
[90540.110475] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 608

---

### Post by martinzollinger on 2009-12-31
Great thread, however is there a guide for dummies?
In all seriousness, I cannot figure my way around the first post to even try these steps.
Thanks in advance,
Martin

---

### Post by neoncyber on 2010-01-16
Hi, when i do sudo make the next errors comes up:
 
[SIZE=2]Sergio:/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0# ls
chips iwpriv_usage.txt README_STA_usb sta
common Makefile RT2870STACard.dat sta_ate_iwpriv_usage.txt
include os RT2870STA.dat tools
Sergio:/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0# make
make -C tools
make[1]: se ingresa al directorio `/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: se sale del directorio `/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make -C /lib/modules/2.6.26-1-686/build SUBDIRS=/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make: *** /lib/modules/2.6.26-1-686/build: No existe el fichero o el directorio. Alto.
make: *** [LINUX] Error 2
Sergio:/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0# make install
make -C /home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
make[1]: se ingresa al directorio `/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make[1]: AtenciÃ³n: El archivo `Makefile.6' tiene una hora de modificaciÃ³n 1,1e+07 en el futuro
mkdir: no se puede crear el directorio Â«/etc/WirelessÂ»: El fichero ya existe
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.26-1-686/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.26-1-686/kernel/drivers/net/wireless/
install: no se puede efectuar `stat' sobre Â«rt3070sta.koÂ»: No existe el fichero o el directorio
make[1]: *** [install] Error 1
make[1]: se sale del directorio `/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make: *** [install] Error 2
Sergio:/home/neoncyber/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0# 
 
I think it's because in the readme file the model is 2870 but it's on the 3070 file.
[/SIZE]

---

### Post by mjrduran on 2010-01-19
Hi,

I have followed flbiggs instructions, WICD Network Manager recognized my D-Link DWA-125 but I had the message "Bad password" when trying to use a WPA-PSK connection.

I have followed the steps below and Ubuntu NetworkManager recognized my D-Link DWQ-125 and it is working now. The instructions below I found in the file "README_STA_usb" that comes with the driver files. I have modified the RT2870STA.dat according to the instructions provided.

Please see below:
================

# Modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
# Use "vi RT2870STA.dat" to modify settings according to your need.
#
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

- In my case:
NetworkType=Infra.

=================

# 2.) set Channel to "0" for auto-select on Infrastructure mode

- WICD Network Manager shows the channel for the connection. 
- In my case:
Channel=1

================

# 3.) set SSID for connecting to your Accss-point.

- Put the name of the connection you are trying to use. WICD Network Manager also shows the available connections.
- In my case: 
SSID=MyHomeConnection

================

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

- In my case:

AuthMode=WPAPSK

=================

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

- In my case:
EncrypType=TKIP

==================

After you insert the changes, please reboot your system so that the drive module can read the new configuration. Then, click the network manager icon and check if the available connections are listed. I hope it helps someone...

---

### Post by Kalifa on 2010-01-23
Hi guys!!! I was trying to set up my D-Link 125 USB but I got some problems. I pretty new using Linux and if you could help me out.

I got an Acer Aspire and install Ubunto 9.10 - Karmic Koala. My guess is for some reason, when send the sudo lshw -C network command, the vendor showed is nVidia!!! What does not make any sense for me as this is the vendor of the video card.

Follow bellow are some information about the commands:

ronaldo@HTPC:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:2a:47:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ronaldo@HTPC:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:fb:a6:2a:47:4c
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f


Tks!!!

---

### Post by Mr. Matt on 2010-01-24
Just needed to say a big thanks for this! Bought this adapted today.  Steps 3 & 4 were all I needed to get it working.

---

### Post by pc0020 on 2010-02-02
Hi,
 
My adapter works fine in ubuntu but when reboot to win7, it prompts the WPS setup panel and ask for pressing the WPS button within 120 sec, no matter on clicking "Exit" or kill the process in task manager, it prompts again and again until I unplug and re-plug the adapter, it works fine and driver installation is not required, how to fix it? Thanks.

---

### Post by fdlsys on 2010-02-10
Genius man! Got it. Automatically starts on reboot, connects on WPA2-PSK  - perfection! Forgot to mention - my Linux knowledge is at the level that I had too Google for every single instruction that you did not specifically provide as ready-made command line :oops:. So, if I managed to get it working, the method is foolproof, period! :KS

Thank you, thank you, thank you.

---

### Post by abitwise on 2010-02-13
Hello!

Thank you for your guideline, i also managed to get D-Link DWA-125 working under Ubuntu 9.10! I bought it for my wife's computer and driver was not implemented into ubuntu. For my computer i bought D-Link DWA-510 (PCI old style wifi card) and it works flawlessly. There is of course a small problem. We have many so called crackers around in the building, this morning someone tried to crack my Wifi, i think he saved my handshake. Looked like someone forcefully disconnected my computers 3 times. (If you want, you can read from here, how the cracking process works: [http://docs.alkaloid.net/index.php/Cracking_WEP_and_WPA_Wireless_Networks](http://docs.alkaloid.net/index.php/Cracking_WEP_and_WPA_Wireless_Networks)).

So my problem was, that AES didn't work, but TKIP works. AES is much more secure than TKIP.

---

### Post by JoZ3 on 2010-03-04
Hi, today update my kernel to 2.6.31-20 version, sice that i have the dwa-125 I have always followed the tutorial to install my device and have not had any problem (two times), but this time i cant install, when i run "sudo make install" i have this: 
```
make -C /home/jozemanuel/Escritorio/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux -f Makefile.6 install
mkdir: no se puede crear el directorio «/etc/Wireless»: El archivo ya existe
make[1]: se ingresa al directorio `/home/jozemanuel/Escritorio/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/jozemanuel/Escritorio/RT3070_LinuxSTA_V2.3.0.1_20100208/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: no se puede efectuar `stat' sobre «/home/jozemanuel/Escritorio/RT3070_LinuxSTA_V2.3.0.1_20100208/RT3070STA.dat»: No existe el fichero ó directorio
make[1]: *** [install] Error 1
make[1]: se sale del directorio `/home/jozemanuel/Escritorio/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux'
make: *** [install] Error 2

```

appear that the file RT3070STA no exist.

i try with this "cp RT2870STA.dat RT3070STA.dat"

and work fine. But when i run "sudo modprobe rt3070sta" have error:

```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf line 71: ignoring bad line starting with 'option'
FATAL: Error inserting rt3070sta (/lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg
```
[ 1381.040350] rt3070sta: Unknown symbol usb_alloc_urb
[ 1381.040627] rt3070sta: Unknown symbol usb_free_urb
[ 1381.041291] rt3070sta: Unknown symbol usb_register_driver
[ 1381.041909] rt3070sta: Unknown symbol usb_put_dev
[ 1381.042132] rt3070sta: Unknown symbol usb_get_dev
[ 1381.042559] rt3070sta: Unknown symbol usb_submit_urb
[ 1381.043529] rt3070sta: Unknown symbol usb_control_msg
[ 1381.044168] rt3070sta: Unknown symbol usb_deregister
[ 1381.045142] rt3070sta: Unknown symbol usb_kill_urb
[ 1381.045356] rt3070sta: Unknown symbol usb_buffer_free
[ 1381.046201] rt3070sta: Unknown symbol usb_buffer_alloc

```

any can help me??

tnx

---

### Post by JoZ3 on 2010-03-04
Problem solved -> [http://ubuntuforums.org/showpost.php?p=8916939&postcount=17]("http://ubuntuforums.org/showpost.php?p=8916939&postcount=17")

---

### Post by chili555 on 2010-03-04
Please see: [http://ubuntuforums.org/showpost.php?p=8917443&postcount=19](http://ubuntuforums.org/showpost.php?p=8917443&postcount=19)

---

### Post by JoZ3 on 2010-03-04
thanks for your post, it me was of big help, I solved the problem completely. many thank you very much again

---

### Post by chili555 on 2010-03-04
Very glad it's working for you. Enjoy!

---

### Post by bjbishop on 2010-07-06
Help! I've done everything listed with no error messages, but when I watch the kernal log my DWA-125 shows up as uhci_hcd. 

here's the actual log print out:
```
Jul  6 20:01:09 freegeek kernel: [ 3598.481362] usb 2-2.3: new full speed USB device using uhci_hcd and address 10
Jul  6 20:01:09 freegeek kernel: [ 3598.691543] usb 2-2.3: configuration #1 chosen from 4 choices
```

---

### Post by bjbishop on 2010-07-06
nevermind! all figured out!

---

### Post by manson105 on 2010-08-17
You guys are gods...
Thank you so much for this thread

---

### Post by spacegravity4me on 2010-08-23
i don't know what i'm doing wrong. I dl'd your file, I extracted it to the desktop. I ran all the commands and I still get nothing. When I run iwconfig at the end all i get is 

lo no wireless extensions

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
      MODE: Managed  Access Point: Not-Associated Tx-power=13 dBm
      Retry long limit:7 RTS thr:off Fragment thr:off
      Encryption key:off
      Power management:on

It's been four days working on this thing. Someone help!!!!

---

### Post by bkratz on 2010-08-23
> **spacegravity4me said:**
> i don't know what i'm doing wrong. I dl'd your file, I extracted it to the desktop. I ran all the commands and I still get nothing. When I run iwconfig at the end all i get is 

lo no wireless extensions

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
      MODE: Managed  Access Point: Not-Associated Tx-power=13 dBm
      Retry long limit:7 RTS thr:off Fragment thr:off
      Encryption key:off
      Power management:on

It's been four days working on this thing. Someone help!!!!

Well it looks like you have a working interface.  You might post the following outputs

```
sudo iwlist scan
rfkill list

```

---

### Post by spacegravity4me on 2010-08-23
I get 

lo interface doesn't support scanning

eth0 interface doesn't support scanning.

wlan0 No scan results


then

2:phy2: wireless LAN
   soft blocked: no
   Hard blocked: no

---

### Post by bkratz on 2010-08-23
Look around post 15 or so here, looks kinda familiar.

[http://art.ubuntuforums.org/showthread.php?t=1425564&page=2](http://art.ubuntuforums.org/showthread.php?t=1425564&page=2)

still looking

---

### Post by spacegravity4me on 2010-08-23
> **bkratz said:**
> Look around post 15 or so here, looks kinda familiar.

[http://art.ubuntuforums.org/showthread.php?t=1425564&page=2](http://art.ubuntuforums.org/showthread.php?t=1425564&page=2)

still looking

I've seen that before but I really don't know what to make of it. I tried a lot of it before. At this point I'm afraid of messing everything up again. I don't know where to go from here.

---

### Post by spacegravity4me on 2010-08-24
any more ideas?

---

### Post by spacegravity4me on 2010-08-25
i followed these instructions and manged to get the led on the adapter to start blinking but it's still not detecting any networks. 

----
When I have an issue with a device, I google the lsusb device id: 07d1:3c0d
This is the first hit on Google, so here is how to get the device working on Lucid 10.04:

1. Download the "RT3070USB(RT307x)"-driver from [http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)
Direct link: [http://www.ralink.com.tw/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEwTHpFMUwyUnZkMjVzYjJGa09Ea3pOREU1TnpBeE9TNWllakk5UFQxRVVFOWZVbFF6TURjd1gweHBiblY0VTFSQlgxWXlMak11TUM0eVh6SXdNVEF3TkRFeUM%3D](http://www.ralink.com.tw/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEwTHpFMUwyUnZkMjVzYjJGa09Ea3pOREU1TnpBeE9TNWllakk5UFQxRVVFOWZVbFF6TURjd1gweHBiblY0VTFSQlgxWXlMak11TUM0eVh6SXdNVEF3TkRFeUM%3D)

2. Extract the file, open a terminal and cd into it
tar -xvf DPO_RT3070_LinuxSTA_V2.3.0.2_20100412.bz2
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412

3. Change a file according to instructions here: [http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html](http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html)
Under "Here is what you need to do:"
...until the instructions tells you to recompile the driver.

4. Compile and install the driver:
make
sudo make install

5. Add a missing symlink:
ln -s /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

6. Load the driver
sudo modprobe rt3070sta

This worked for me. Lucid 10.04 with all updates installed as of today.

----

I got to step 5 and I didn't understand how to do what he said. I did however go to that location in the file system and there was nothing there so it appears I do need to add it. When I run the sudo modprobe rt3070sta command it says that it can't load the driver cause it doesn't exist. So it seems that it isn't installed or something. I think I'm installing it properly. Still need help. Anyone? Thanks.

---

### Post by bkratz on 2010-08-25
I'm afraid you are way beyond my comfort zone. I just spent an hour looking up to ls (link) command to try and understand what is going on. Just curious, did you ever get to post 37 of the earlier link.  It supposedly gives you step by step methodology for you particular usb device number
quote
Caution, this is for those devices with usb.id of 07d1:3c0d only! Here is the link again

[http://art.ubuntuforums.org/showthread.php?t=1425564&page=4](http://art.ubuntuforums.org/showthread.php?t=1425564&page=4)
Sorry, I'm not more help.

---

### Post by ario on 2010-10-02
Just because ubuntuforums.org boys said that their forum is getting larger and larger (!) I decided to not bother in this topic, But I created another one about installing and preparing wireless connection in 10.04, Please Click the link below and answer me:
*Is Ubuntu 10.04 continue support wireless? (At end I describe the installation problems I faced with the rt3070sta driver)*
[http://ubuntuforums.org/showpost.php?p=9919355&postcount=11](http://ubuntuforums.org/showpost.php?p=9919355&postcount=11)
Any response will be appreciated there!:D

---

### Post by aneganov on 2010-10-25
Doesn't work with Network Manager on 10.04 
Details: [http://ubuntuforums.org/showpost.php?p=10026350&postcount=25](http://ubuntuforums.org/showpost.php?p=10026350&postcount=25)

---

### Post by khaj_vah on 2011-03-27
ppl on ubuntu 10.10 after a ¨make¨ command i get this at the end 

/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2

Anyone PLS help me I really need this...

---

### Post by khaj_vah on 2011-03-27
I have tried this with other drivers but i get the same error

---

### Post by MooPi on 2011-03-27
Have you installed "build-essential"  ? It is generally needed for this type of operation.
Start fresh and lets try this 
```
sudo apt-get install build-essential
```
Then in order while in terminal navigate to the driver folder....
```
sudo make
sudo make install
```

---

### Post by kaustavdm on 2011-10-27
For Ubuntu 11.10, I found that I needed to use rt5370sta instead of rt3070sta. I've added detailed instructions in my blog post on how to [install Dlink DWA-125 on Ubuntu 11.10]("http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html") along with instructions given by flbiggs.

---

### Post by Asgerisme on 2011-12-06
This worked perfectly:P, but I only had to download the RT3070 Linux driver and write "sudo /etc/init.d/networking restart" in the Terminal :guitar: I uses Ubuntu 11.10 :) THNX for this tut :P

---

