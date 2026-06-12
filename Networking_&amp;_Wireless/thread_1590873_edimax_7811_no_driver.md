---
title: "edimax 7811 no driver"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by castle4dracula on 2010-10-08
Hi,  I'm going round in circles with this as I'm just not very good at using the command line in Ubuntu.  I've bought an Edimax EW-7811Un nano USB wifi adapter, and I'm really cheesed off at the moment because I can't get it to work on my laptop.  I've got Ubuntu 10.04 on it.  Any help you can give me will be appreciated veyr much, as I really want this tiny dongle to work with my computer. Ubuntu is much fats than Windows, and I use it all the time, but my current wifi donlge is an old big monstrosity!

---

### Post by chili555 on 2010-10-08
Please open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Please download the driver to your desktop here: [http://www.edimax.com/en/support_detail.php?pd_id=347&pl1_id=1&pl2_id=44](http://www.edimax.com/en/support_detail.php?pd_id=347&pl1_id=1&pl2_id=44)

Right-click and select 'Extract here.' A folder will be created named rtl8192CU... Open it and open the folder called 'driver.' There is a file in there called rtl8192CU... Right-click and select 'Extract here.' Now, back in the terminal, do:```
cd Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726
make
sudo make install
sudo modprobe 8192cu
```Does your Edimax spring to life? Post back and let us know.

---

### Post by castle4dracula on 2010-10-08
chili555,  you are the best!  Thank you so much for your help.  My edimax is now working like a dream. It took me a few goes before I realised that I needed to use upper and lower case where shown! Doh! Thanks again, your help is very much appreciated by this Linux newbie.

---

### Post by chili555 on 2010-10-08
Glad to have helped!

Whenever a new kernel or linux-image is installed, usually by the Update Manager, you will need to build the module again against the new kernel.```
cd Desktop/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe 8192cu
```Have fun!

---

### Post by milou on 2010-10-31
Hello,

Please, could you confirm that the solution works with Maverick kernels? In the driver package available on edimax website, it is noticed that this would be compatible with 2.6.32 kernels... "and maverick kernels is 2.6.35.

EDIT : latest drivers can be found directly on realteck website; this is an updated version of the above version, and is compatible with kernels up to 2.6.35.

[http://fichiers.touslesdrivers.com/realtek/RTL8192CU_v2.0.1126.zip](http://fichiers.touslesdrivers.com/realtek/RTL8192CU_v2.0.1126.zip)

---

### Post by chili555 on 2010-10-31
It compiled without warning or error on my 10.10 system just now. I don't have the device, so I can't test further.

Make sure you have *build-essential* and *linux-headers* installed.

---

### Post by milou on 2010-11-05
Ok. So I tried both driver versions on a Maverick 64 bits distribution. It compiles (though with a lot of warnings) in both cases. But each time I modprobe the module 8192cu, it freezes the 2 laptops I tried :confused: ... compiled on a standard Maverick Kernel 2.6.35-22 .

castle4dracula, could you tell here what is the system on which it worked "like a dream"? Distribution, flavor (32 or 64 bits), maybe laptop/computer on which you compiled the module?

---

### Post by milou on 2010-11-07
Some info about this wifi usb stick. I installed Maverick 32 bits and the realtek driver (I tried the 1126 version) works. That means this is a 32 bits version, which was not precised on the website.

For an unknown reason, the usb stick, though seen in gnome network manager, is greyed and showed as "disabled", though I can use it with wicd. Someone would know how to solve this problem?

---

### Post by steel-fender on 2011-01-23
Hey Chili555,
WOW!  It's been two frustrating days trying to get the Edimax EW-7811Un  adapter to work.  I am fairly new to the command line in ubuntu, and  nothing I was doing was working.  Either I got errors during make, or  missing files after unzipping, or nothing.  I tried your fix from the Oct. 8th post, and it did  not work.  Then I tried other suggestions, blacklisting, disabling,  etc.  Eventually the internal card on my netbook would only go up and  down in about 20 second intervals.  I wasn't sure what to do, but  instead of "Hulk SMASH!" I did the next best thing, wiped the drive and  reinstalled and updated the OS.  *deep breath, exhale, ....good*

I tried your fix on the fresh install and viola! Pure, gooey, awesomeness as the blue light started blinking.

I wasn't ready for this fight, everything on ubuntu has just worked for  me so far.  N'er a driver to install, but there sure are a lot of hits  in the forum for problems with wireless adapters.  I kept trying to find  a program that would pull up the usb ports, tell me what was plugged  in, and let me update the drivers, like a hardware manager.  No dice.

Can you suggest a good location for a beginner course on installing drivers?
AND...what was that about having to clean up after update manager loads a kernel or image file?
thanks for your help!

---

### Post by chili555 on 2011-01-23
I am very glad it's finally working and especially that we've avoided the Hulk-smash.

Wireless adapters are an especially difficult area. There are tens of manufacturers, each with dozens of models and new ones coming out just about daily. While the same is true of, say printers, we are quite willing to accept that a particular printer won't work in Linux no way no how. However, networking and the internet is so important that no one is willing to accept that some $12 USB dongle is so poorly made and that Linux drivers don't now and never will exist such that it won't ever work. I have seen more than a few posts where the question is, "I have read this device doesn't work|monitor|packet injection in Ubuntu. What's the work-around?" > Can you suggest a good location for a beginner course on installing drivers?Not really; however, installing drivers is no different than most other software in Linux. Either there is a native driver and it just works, or there is a (hopefully) fits-all tar.gz somewhere and you need the pre-requisites and compile just like we did here or there is no driver/software at all. Every new kernel version includes more common drivers, and other software and, I believe, drops really old obsolete things. For instance, I'd hate to try to get a SCSI printer running in kernel 2.6.36. > AND...what was that about having to clean up after update manager loads a kernel or image file?When you compiled the driver, you built it for your currently running kernel, known in Ubuntu-speak as linux-image. Some day soon, Update Manager will offer a newer linux-image, 2.6.35-25 perhaps. You will need to build a driver module for the newer kernel as I pointed out above.

Incidentally, there is suspicion that there is something fundamentally flawed with -24. I have removed it and suggest you avoid it.

---

### Post by steel-fender on 2011-01-28
Chili555,
skipped -24 and went straight to -25, guess what? 
you were right again, had to rebuild after the kernel update, your fix worked for that also.  

I remembered something else...after I got the ew-7811un to work I also installed the WICD network manager, which comes as a metapackage, to try it out.  After that, the network adapter would go up and down...so I uninstalled WICD...but it still went up, down, up, down!  Then I went to the Software Center and saw that eventhough I thought I had uninstalled it, the metapackage had left some remnant WICD programs still installed.  I removed them and the up and down stopped, and my network adapter performed normally.

I'm not sure whether it was the two network managers fighting, or WICD is just not awesome, or what, but without it everything is normal.  (yes I did try to prevent the ubuntu network manager from activating at startup, and rebooted, but still had the up down problem)

Thanks again

---

### Post by chili555 on 2011-01-28
> I'm not sure whether it was the two network managers fighting,I believe that's exactly the case. I also believe that had you removed Network Manager, Wicd would have performed normally. All's well that ends well!

---

### Post by monkeychef on 2011-02-18
Alright, so I used this method. It worked for about 5 minutes, and then I restarted. Now I can't tell if the wireless is coming from the crappy card (although I suspect it is) or if it is coming from the usb. I had to restart about 3 times because after the first and second restarts, I got a black screen before the login and it wouldn't move.

My question is, is there a way to tell if the usb is working or not, or if this is the card AND if it is running the card, how can I cleanly reinstall the driver again (I tried the method above, but it doesn't seem to work).

---

### Post by chili555 on 2011-02-19
> **monkeychef said:**
> Alright, so I used this method. It worked for about 5 minutes, and then I restarted. Now I can't tell if the wireless is coming from the crappy card (although I suspect it is) or if it is coming from the usb. I had to restart about 3 times because after the first and second restarts, I got a black screen before the login and it wouldn't move.

My question is, is there a way to tell if the usb is working or not, or if this is the card AND if it is running the card, how can I cleanly reinstall the driver again (I tried the method above, but it doesn't seem to work).I don't understand why you have two operating wireless cards, one of which is "the crappy card." I suggest you identify the drivers associated with "the crappy card" and blacklist them so it never starts. Please post:```
sudo lshw -C network
lsusb
```We'll figure out which is which and blacklist the baddie.

---

### Post by monkeychef on 2011-02-19
Alright, I'll do that as soon as I do a reinstall. For some reason or another, ubuntu won't start, and I have no clue what is going on because I'm a linux noob. 

The reason I had to wireless cards running was because I didn't know how to disable the internal on this laptop. It works about 20% of the time, but it is very slow. The wireless usb adapter I got to work 100% of the time (while I had the correct configuration for about 5 minutes before I restarted the computer and everything went to hell) and my internet speeds were much faster.

---

### Post by chili555 on 2011-02-19
> Alright, I'll do that as soon as I do a reinstall.Post back when you're ready and we'll get it sorted out.

---

### Post by monkeychef on 2011-02-19
walter@Walter-PC:~$ sudo lshw - network
[sudo] password for walter: 
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

walter@Walter-PC:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13fe:3800 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
walter@Walter-PC:~$

---

### Post by chili555 on 2011-02-19
> $ sudo lshw - networkPlease see above; my request was:> sudo lshw -**[COLOR="Red"]C[/COLOR]** network


---

### Post by monkeychef on 2011-02-19
My bad, it seems linux is very big on capitals and lowercase...


 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:07:26:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:29:3f:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:44400000-4440ffff

---

### Post by chili555 on 2011-02-19
Yes, indeed. > *-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
---snip---
configuration: broadcast=yes [COLOR="Red"]driver=ath5k[/COLOR]

Please do:```
sudo su
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```Upon reboot, the Atheros will not start; the Edimax will be your only working wireless device.

---

### Post by monkeychef on 2011-02-19
Thanks you so much, that was really great. One other question though. When I use the command sudo make install I get something that says

"cp: connot stat `/autoconf_rtl8192c_usb_linux.h`:no such file or directory"

Should this concern me?

---

### Post by chili555 on 2011-02-19
> Should this concern me?Yes, it should. Please do instead:```
sudo su
make clean
make
make install
exit
```Any errors this time?

---

### Post by monkeychef on 2011-02-19
None, it works amazing. I have restarted about 4 times now (this is going to my grandpa in FA so it has to work) and every time, wifi always works. I honestly love you (in that not gay way). You have been a huge help, thank you so much.

---

### Post by chili555 on 2011-02-19
I was very happy to help and I'm glad it's working. Give grandpa my regards; we grandpas love positive vibes!

---

### Post by monkeychef on 2011-02-19
BTW, are there any easy to set up wifi boosters that you can recommend? I have a good signal up to a few feet from the router, but if I go upstairs it won't connect (and I'm hoping that in FA I will be able to find a router easily with a good signal).

---

### Post by chili555 on 2011-02-19
I've messed with range extenders a few times and never had good luck. I'd suggest starting a new thread with 'range extender' in the title and maybe a better source can help.

---

### Post by Nevyn2009 on 2011-02-25
Hi Guys,

Firstly, thanks for this thread. I'm new to Ubuntu (but old to Unix, having started with Apollo Domain, then lots of HP-UX, Solaris, some Mandriva and RHEL...)

I've followed the steps on page 1. Then repeated it all as root when I got a similar 'cannot stat' as monkeychef :O)

I now have the blue blinkenlitz

I've been into Network Tools and set up the SSID and key, told it to use DHCP, but nothing. Nada. Zilch.

lshw -C network has this to say:

[FONT=monospace]*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1f:1f:bf:3a:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=unassociated[/FONT]

Hmmm, "[FONT=monospace]wireless=unassociated". There's obviously something I've missed. Any clues please?
[/FONT]

---

### Post by chili555 on 2011-02-25
> Hmmm, "wireless=unassociated". There's obviously something I've missed. Any clues please?It's not associated because it probably doesn't like the ssid and/or key. I'd delete those details and simply click the Network Manager icon at the top right and see if it sees your network. Click it and see if it asks for your key. Try to connect and post back.

---

### Post by Nevyn2009 on 2011-02-26
Reply via my new wireless connection...

I think I see my problem right there, too used to having to do things the hard way :o)

Cheers Chili

---

### Post by chili555 on 2011-02-26
> **Nevyn2009 said:**
> Reply via my new wireless connection...

I think I see my problem right there, too used to having to do things the hard way :o)

Cheers ChiliAwesome! Glad it's working. Have fun!

---

### Post by mikewhatever on 2011-03-07
Does anyone know if this particular device plays nicely with suspending to RAM? Does it wake up properly? Can someone please check.

---

### Post by Locke_99GS on 2011-03-30
The 2.6.39 kernel has merged the 8192cu driver, finally. As a module it will compile as rtl8192cu, of rtlwifi. My nvidia drivers will currently not compile against 2.6.39-rc1 though, so I'm not bothering with that kernel too much right now. Perhaps in a few weeks the kernel will be patched to support the nvidia driver, or nvidia will release a driver that supports the kernel. I may then have better luck and actually run it properly.

I'll be sure to post back if all goes well with it.

@mikewhatever I have this wifi dongle in my daughter's computer, and she just recently discovered the instant-on-awesomeness of "suspend". :) With the 1324 driver (off the top of my head) from Realtek compiled against 2.6.35 and 2.6.38, it suspends and wakes just fine.

---

### Post by Locke_99GS on 2011-04-01
Precompiled 39 kernel from Ubuntu mainline kernel ppa isn't configured for any of the new stuff in 39 :| So, as of now at least, you must compile your own kernel being sure to enable CONFIG_RTL8192CU (which then depends on CONFIG_MAC80211, CONFIG_USB, and CONFIG_EXPERIMENTAL.

39 finally does away with the BKL, which is why the nvidia driver didn't compile against it. Simply comment out the include directive for smp_lock.h in the nvidia sources and it will compile and function properly against the 39 kernel.

---

### Post by mikewhatever on 2011-04-03
Thanks, Locke_99GS, really appreciate your feedback.

---

### Post by Rootbrian on 2011-04-30
I haven't posted here in so long, my issue is with the 8192cu driver. Currently using ubuntu 11.04 on a diskless laptop (everything is booted via USB) and the driver used to work with 10.04 LTS, it doesn't with natty. It refuses to even compile.

Current kernel: 2.6.38-8-generic

Posting what I got in the terminal after endless tries to make:

```
user@user-seagate:~/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.38-8-generic/build M=/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_cmd.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_security.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_debug.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_io.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_query.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_set.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/ieee80211.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme_ext.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_wlan_util.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_pwrctrl.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_rf.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_recv.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_sta_mgt.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_xmit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/efuse/rtl8712_efuse.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/led/rtl8192c_led.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o
/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c: In function &#8216;_rtw_mutex_init&#8217;:
/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:305:2: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2
user@user-seagate:~/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126$ 

```

Also note, i'm using the latest version of the driver provided by realtek. Older drivers do the exact same thing. I cannot use the wireless device I bought, I really want to use it.

---

### Post by chili555 on 2011-04-30
> os_dep/osdep_service.c:305:2: error: implicit declaration of function ‘init_MUTEX’
For kernels newer than Maverick, every instance of init_MUTEX should be changed to sema_init. Please amend os_dep/osdep_service.c with a text editor and change line 305 and any other instances and then try again:```
make clean
make
sudo make install
etc.
```

---

### Post by Rootbrian on 2011-04-30
> **chili555 said:**
> For kernels newer than Maverick, every instance of init_MUTEX should be changed to sema_init. Please amend os_dep/osdep_service.c with a text editor and change line 305 and any other instances and then try again:```
make clean
make
sudo make install
etc.
```

Did that, made the change, make cleaned and here is the result after making again:

user@user-seagate:~/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.38-8-generic/build M=/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_cmd.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_security.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_debug.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_io.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_query.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_ioctl_set.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/ieee80211.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_mlme_ext.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_wlan_util.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_pwrctrl.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_rf.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_recv.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_sta_mgt.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/rtw_xmit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/efuse/rtl8712_efuse.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/core/led/rtl8192c_led.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/hal_init.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c_d_hal_init.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o
/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c: In function &#8216;_rtw_mutex_init&#8217;:
/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:305:2: error: too few arguments to function &#8216;sema_init&#8217;
include/linux/semaphore.h:32:20: note: declared here
make[2]: *** [/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/user/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2
user@user-seagate:~/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126$ 

That's the output. It's not working :S

---

### Post by chili555 on 2011-04-30
I suggest you email the developer; his name and email address is probably in the README. Be sure to tell him your kernel version:```
uname -a
```

---

### Post by Rootbrian on 2011-04-30
> **chili555 said:**
> I suggest you email the developer; his name and email address is probably in the README. Be sure to tell him your kernel version:```
uname -a
```

I sent them an e-mail, there wasnt anything in the readme file, I found it on their website after googling the driver name. Just waiting on a reply.

---

### Post by chili555 on 2011-04-30
Please let us know the answer. Since Natty was released, I'm sure there will be others with the same issue.

---

### Post by blueshreyansh on 2011-05-01
Hello Chili555!
I have just started using Ubuntu and the Ubuntu that I installed first time on my pc was Ubuntu 10.10.I have got a Wifi modem at my home and so I am using an Edimax Wireless IEEE802.11b/g/n nano USB Adapter.After installing Ubuntu I searched a lot on the net on 'How to install Edimax drivers for my device on Ubuntu' and the after 3 days of intense searching I found your post.Luckily things went fine and I was able to install the drivers and get the device started.Now after the launch of Ubuntu 11.04 I updated my PC but now when I try installing the Linux drivers for my device by your method then I can't as it says that '8192cu' invalid format but it was working just fine.So I would the really grateful to you if you could help me with this problem.

And though I am a newbie but I think it's because of the updated Linux kernel in Ubuntu 11.04.:):popcorn:

---

### Post by chili555 on 2011-05-01
> I think it's because of the updated Linux kernel in Ubuntu 11.04Quite correct. The driver won't compile against the new kernel or perhaps the newer gcc version. In several threads, I've advised posters to email the developer. In the meantime, I suggest sticking with 10.10.

---

### Post by blueshreyansh on 2011-05-01
I did mailed the developer and he sent me a file in .pdf format containing instructions on how to install the driver but the thing was not working but still if you want to see the instructions which he sent me then i can mail you the file.and one more thing he also sent me a folder containing th driver and interestingly this folder contained different files then the one available at the edimax site.And as you said that i should stick with 10.10 would that mean that i would never be able to get my wifi adapter work in natty?

---

### Post by chili555 on 2011-05-01
Please do; I'd like to try it. I'll send you a private message with my email address.

I only suggest you stick with 10.10 as long as it takes to work out how to compile 8912cu against the Natty kernel.

---

### Post by Nyxielle on 2011-05-03
I'm having the same problem here. when I type lsusb it's definately recognising that it's plugged in but I've tried everything here, both the first driver and the driver on the realtek website [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

but when I do what's been explained here, extracting the file in the driver folder, cd'ing to the directory.
make, make install, modprobe 8192cu...nothing happens. it basically just goes to "elle@elleinnad:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402$" so i can type another command. no lights on the usb, nothing recognised in the network manager *shrug*

I've got this and the netgear wnda 3200. So I've tried both adapters and neither are connecting me to the internet =/

im running ubuntu 10.10 64-bit, 2.6.35-22-generic.

---

### Post by MrHemlock on 2011-05-06
I'm running Ubuntu 11.04 64-bit and I fought with this for a few days. I think I have the driver working now. Here are the steps I followed:

1. download the driver from realtek, I got v2.0.1502, if you end up with a newer version then all bets are off. Link:[RealTek drivers]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

2. Extract the .zip file you downloaded
3. Extract the .tar.gz in the driver directory of the extracted download

4. Apply these changes to the driver directory you just extracted

```
diff -ru original/hal/rtl8192c/usb/rtl8192c_cmd.c modified/hal/rtl8192c/usb/rtl8192c_cmd.c
--- original/hal/rtl8192c/usb/rtl8192c_cmd.c	2011-04-02 06:45:13.000000000 -0400
+++ modified/hal/rtl8192c/usb/rtl8192c_cmd.c	2011-05-04 17:33:19.781543375 -0400
@@ -2102,7 +2102,7 @@
 
 	if(bDLOK)
 	{
-		DBG_871X("Set RSVD page location to Fw Len(%d).\n",sizeof(RsvdPageLoc));		
+		DBG_871X("Set RSVD page location to Fw Len(%lu).\n",sizeof(RsvdPageLoc));		
 		FillH2CCmd(Adapter, RSVD_PAGE_EID, sizeof(RsvdPageLoc), (u8 *)&RsvdPageLoc);
 	}
 
@@ -2181,7 +2181,7 @@
 	}
 
 	JoinBssRptParm.OpMode = mstatus;
-	printk("%s H2C len(%d)\n",__FUNCTION__,sizeof(JoinBssRptParm));
+	printk("%s H2C len(%lu)\n",__FUNCTION__,sizeof(JoinBssRptParm));
 	FillH2CCmd(padapter, JOINBSS_RPT_EID, sizeof(JoinBssRptParm), (u8 *)&JoinBssRptParm);
 	
 _func_exit_;
diff -ru original/os_dep/linux/usb_intf.c modified/os_dep/linux/usb_intf.c
--- original/os_dep/linux/usb_intf.c	2011-04-02 06:45:13.000000000 -0400
+++ modified/os_dep/linux/usb_intf.c	2011-05-06 09:09:35.939842904 -0400
@@ -1035,7 +1035,8 @@
 	if( padapter->registrypriv.power_mgnt != PS_MODE_ACTIVE )
 	{
 		if(padapter->registrypriv.usbss_enable ){ 	/* autosuspend (2s delay) */
-			pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time		 	
+			//pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time		 	
+			pm_runtime_set_autosuspend_delay(&pdvobjpriv->pusbdev->dev, 0 * HZ);
 
 			#if (LINUX_VERSION_CODE>=KERNEL_VERSION(2,6,35))
 			usb_enable_autosuspend(padapter->dvobjpriv.pusbdev);
```


5. build and install from inside the driver directory you extracted (rtl8192CU_linux_v2.0.1502.20110402 or something). You should get 1 warning after the make.

```
make clean
make
sudo make install
sudo modprobe 8192cu

```
5. Enjoy

---

### Post by liefra on 2011-05-08
[COLOR=Black]Thanks to MrHemlock's explaination, the compilation works now fine for me too on Ubuntu 11.04 64 Bit and Fedora 15 Beta 64 Bit.

But I still have problems to establish a WPA-PSK/WPA2-PSK Wifi connection. I have tried both the NetworkManager and wpa_cli, without success. The problem is that the 4-Way handshake is never successful, so my correct password ist never accepted.

Connecting with WEP works fine though.

Did anybody already got a  WPA-PSK/WPA2-PSK connection to work?

Cheers, Frank[/COLOR]

---

### Post by MrHemlock on 2011-05-10
> **liefra said:**
> [COLOR=Black]...But I still have problems to establish a WPA-PSK/WPA2-PSK Wifi connection...
Did anybody already got a  WPA-PSK/WPA2-PSK connection to work?[/COLOR]

Frank,

I'm using WPA2-PSK. It connects ok and sometimes will even re-connect when the signal is lost. Other times it completely locks my computer; I had to turn off wireless for the time being :(

---

### Post by liefra on 2011-05-11
Thanks for your reply.

I guess, I 'll wait for the next kernel version 2.6.39, which is said to include the 8192cu and 8192cus driver.

Cheers, Frank

---

### Post by Nyxielle on 2011-05-12
I don't think I quite understand :/
I extracted the zip, extracted the tar.gz in the driver folder. opened terminal and typed:

diff -ru original/hal/rtl8192c/usb/rtl8192c_cmd.c modified/hal/rtl8192c/usb/rtl8192x_cmd.c

and it came back saying: diff: original/hal/rtl8192c/usb/rtl8192c_cmd.c: No such file or directory
diff: modified/hal/rtl8192c/usb/rtl8192x_cmd.c: No such file or directory

I then cd'd to the directory and tried again: 

cd /home/elle/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402
elle@elleinnad:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402$ diff -ru original/hal/rtl8192c/usb/rtl8192c_cmd.c modified/hal/rtl8192c/usb/rtl8192c_cmd.c
diff: original/hal/rtl8192c/usb/rtl8192c_cmd.c: No such file or directory
diff: modified/hal/rtl8192c/usb/rtl8192c_cmd.c: No such file or directory

I'm not entirely sure what I'm doing wrong tbh

---

### Post by MrHemlock on 2011-05-13
Nyxielle,

Yeah, that isn't a good diff. I had two directories, modified and original. Those don't exist in the tar they were created while I was playing around trying to fix the compile errors. 

Your directory starts with rtl8192. There aren't that many changes and I'm not sure how to provide them in a way that doesn't require making the changes by hand. You only really need the last change, the others just fix warnings, so:
 
1. cd into the rtl8192... directory.
2. Open usb_intf.c by typing "gedit os_dep/linux/usb_intf.c &"
3. Go to line ~1035:

pdvobjpriv->pusbdev->autosuspend_delay = 0 * HZ;//15 * HZ; idle-delay time

and replace it with

pm_runtime_set_autosuspend_delay(&pdvobjpriv->pusbdev->dev, 0 * HZ);

now you can do:
make clean
make
sudo make install
sudo modprobe 8192cu

The make will generate ~3 warnings.

---

### Post by MrHemlock on 2011-05-13
BTW, I tried the compat-wireless driver with the same results. My machine locks if the signal gets dropped.

[http://wireless.kernel.org/en/users/Drivers]("http://wireless.kernel.org/en/users/Drivers")

---

### Post by TimC340 on 2011-06-24
> **chili555 said:**
> 
> Thanks you so much, that was really great. One other question though.  When I use the command sudo make install I get something that says

"cp: connot stat `/autoconf_rtl8192c_usb_linux.h`:no such file or directory"

Should this concern me?Yes, it should. Please do instead:```
sudo su
make clean
make
make install
exit
```Any errors this time?

I had the same. Tried the fix, but it seemed unable to find the target. I'd show the Terminal code, but the driver installation caused instability with a random but fairly rapid black screen lockup with flashing Caps Lock light. The laptop is an HP Pavilion ZE4120s - pretty old but serviceable - and it was rock solid under Maverick until I attemped the Edimax installation. It was working well apart from the instability, so it's doubly frustrating! Is there a way round this, or should I try a different wireless dongle? Is there anything else nearly as small that will actually work?

---

### Post by chili555 on 2011-06-24
> Is there a way round this, or should I try a different wireless dongle? Is there anything else nearly as small that will actually work?I would try a different device. Looking at several posts above plus yours does not give me much optimism. Will the computer boot stably without the Edimax inserted?

---

### Post by TimC340 on 2011-06-25
To be honest, I haven't tried. As it was a relatively new installation, I've reinstalled 10.10 and left out the Edimax. It's a pain having to use a wired connection, but it'll do for now! And it's back to being stable - I'd tried changing RAM chips, installing AMD Catalyst and even deleting the latest kernel in the attempts to stabilise it, but it seems that the Edimax or its driver are the culprit. I'll have a search for an alternative wireless dongle - I assume there are usable and stable ones out there?!

---

### Post by chili555 on 2011-06-25
> it seems that the Edimax or its driver are the culprit.Call me radical, but I'd put it right under the real wheel of my car as I drove to the pub.> I assume there are usable and stable ones out there?! Yes, many.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

There are posts here frequently asking for the best out-of-the box USB device and many replies.

---

### Post by Locke_99GS on 2011-06-27
Another option would be to build kernel 2.6.39 (or higher) and enable rtl8192cu, rtl8291c_common, rtlwifi, mac80211, and cfg80211 when configuring the kernel. Support is built in now, just turn it on. (no, kernels from the ubuntu mainline ppa won't work as they share a .config with .38 for natty and .35 for maverick - these didn't support rtl8192cu, therefore newer kernels sharing their .config don't get it enabled)

---

### Post by Nevyn2009 on 2011-07-06
> **chili555 said:**
> For kernels newer than Maverick, every instance of init_MUTEX should be changed to sema_init. Please amend os_dep/osdep_service.c with a text editor and change line 305 and any other instances and then try again:```
make clean
make
sudo make install
etc.
```

Thought I'd let the dust settle before going to 11.04, did an online update but ran into the exact same problem. Ho Hum.

The above edit didn't work for me either, but the link to supported cards you posted last week suggests replacing init_MUTEX(prwlock) with sema_init(prwlock**,1**)

Just to say that works. Make completes with no errors and everything's good.

(Edimax driver v2.0.939.20100726 - 11.04 - 2.6.38 )

---

### Post by pheisel on 2011-07-20
Mr Hemlocks method worked for me. I was having the "no 8192cu.ko" problem when using the drivers off of the edimax site. I then downloaded realtek's (link in Mr Hemlocks post). I applied his method to one of the c files (mentioned in his posts above) and it all worked. Thanks Mr Hemlock!
I'm on a 11.04 Natty install. Good Luck

---

### Post by tfbielawski on 2011-08-02
I tried this and got a FATAL: Module 8192cu not found. Any ideas?

Thanks,

Tom

---

### Post by tfbielawski on 2011-08-02
Forgot....Ubuntu 11.04 64bit, don't know if that matters....

Tom

---

### Post by `Kyle on 2011-08-03
> **liefra said:**
> [COLOR=Black]Thanks to MrHemlock's explaination, the compilation works now fine for me too on Ubuntu 11.04 64 Bit and Fedora 15 Beta 64 Bit.

But I still have problems to establish a WPA-PSK/WPA2-PSK Wifi connection. I have tried both the NetworkManager and wpa_cli, without success. The problem is that the 4-Way handshake is never successful, so my correct password ist never accepted.

Connecting with WEP works fine though.

Did anybody already got a  WPA-PSK/WPA2-PSK connection to work?

Cheers, Frank[/COLOR]

I have this same problem. I can get the wireless card to connect to WEP, but it doesn't connect to my WPA2 network.  I guess it's back to Windows, meh.

---

### Post by cliverlong on 2011-09-24
> **Nevyn2009 said:**
> Thought I'd let the dust settle before going to 11.04, did an online update but ran into the exact same problem. Ho Hum.

The above edit didn't work for me either, but the link to supported cards you posted last week suggests replacing init_MUTEX(prwlock) with sema_init(prwlock**,1**)

Just to say that works. Make completes with no errors and everything's good.

(Edimax driver v2.0.939.20100726 - 11.04 - 2.6.38 )

Hi

I'm a ubuntu newbie and am running it as a file server. Like many the size of the edimax nano usb wireless adapter appealed. I ran into the same problems as others described in this thread trying to install.

I think the change you described above has fixed the "make" problem - log below - but I'm not quite sure what to do next to get this device usable as a networking device. Can someone help?

Thanks

Clive

uname -a
Linux AMD64-xbmc 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 athlon i386 GNU/Linux


  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/os_intfs.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/usb_intf.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/ioctl_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/xmit_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/mlme_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/recv_linux.o
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.mod.o
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
root@AMD64-xbmc:/home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.38-11-generic/build M=/home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_security.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_debug.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_io.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_ioctl_query.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_ioctl_set.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/ieee80211.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_mlme.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_mlme_ext.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_wlan_util.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_pwrctrl.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_rf.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_recv.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_sta_mgt.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_xmit.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/efuse/rtl8712_efuse.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/led/rtl8192c_led.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/hal_init.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c_d_hal_init.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/os_intfs.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/usb_intf.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/ioctl_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/xmit_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/mlme_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/recv_linux.o
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.mod.o
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
root@AMD64-xbmc:/home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/osdep_service.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/os_intfs.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/usb_intf.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/ioctl_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/xmit_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/mlme_linux.o
  CC [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/os_dep/linux/recv_linux.o
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
root@AMD64-xbmc:/home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726# make install
install -p -m 644 8192cu.ko  /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-11-generic
root@AMD64-xbmc:/home/clive/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726#

---

### Post by chili555 on 2011-09-24
You've done 'make install.' I think the only thing left is to do:```
sudo modprobe 8192cu
```If you are running a file server, do you have a desktop manager, Gnome, Unity, KDE, etc.? Or do you need to configure with a terminal prompt only?

---

### Post by cliverlong on 2011-09-25
> **chili555 said:**
> You've done 'make install.' I think the only thing left is to do:```
sudo modprobe 8192cu
```If you are running a file server, do you have a desktop manager, Gnome, Unity, KDE, etc.? Or do you need to configure with a terminal prompt only?

Thanks for your response.

I found the ubuntu package wicd(?) which allowed me to enter the wifi (WPA2-PSK?) key and after some fiddling my network was found and a connection was made. I then found in top right hand corner of the desktop (mythbutnu uses XFCE(?) I believe) another network management icon where I could configure the wifi usb device. I have found that the wifi connection to my router stays stable for between 10 seconds and 5 minutes. There seems to be no pattern to the disconnection. When I put the wifi usb into a windows laptop or use a different laptop with a built-in wifi receiver, the connection is stable. 

Maybe the driver is defective in some way? I would have thought that once the wifi connection between the device and the router was established it would stay up as long as the signal was strong enough.

Regards

---

### Post by chili555 on 2011-09-25
> I found the ubuntu package wicd(?) which allowed me to enter the wifi (WPA2-PSK?) key and after some fiddling my network was found and a connection was made. I then found in top right hand corner of the desktop (mythbutnu uses XFCE(?) I believe) another network management icon I wonder if you have dueling and conflicting network managers. You might check:```
ps aux | grep etwork
```If Network Manager is installed, I'd open Synaptic and remove it, marking for complete removal including configuration files. Reboot and tell us if the connection is stable.

Of course, you could also remove Wicd and rely on NM.

---

### Post by mikewhatever on 2011-10-15
So, has anyone been able to get this device to work on Oneiric? It's recognized out of the box, but won't connect to any networks, secure or open.

---

### Post by gdselzer on 2011-12-31
The driver provided in the distribution appears to be broken.  In order to get this to work, follow the instructions here:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

The most recent version of the driver no longer requires Step 3 of the instructions in the linked page.  I've got mine up and running.  However, I can't figure out how to get the bitrate above 72Mb/s.  Has anyone figured out how to get the full 150Mb/s?

---

### Post by trosn on 2012-12-22
ignore this until I figure out how to delete it >< sorry

---

