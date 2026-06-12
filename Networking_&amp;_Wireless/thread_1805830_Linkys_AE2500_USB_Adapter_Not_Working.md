---
title: "Linkys AE2500 USB Adapter Not Working"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by philipscott on 2011-07-16
Hi, I am a total Linux noob and I cannot get my Linkys AE2500 USB Adapter working. As far as I know, Linkys does not have drivers for Linux.
Whenever I used it with Windows XP, it worked (blue light turned on on the USB Adapter.)

Is there any way I can get it working with Ubuntu 11.04?

---

### Post by chili555 on 2011-07-16
Please open a terminal and run and post:```
lsusb
```That will give us some details about the device and we can proceed.

Here is a note to searchers: [http://www.wikidevi.com/wiki/Linksys_AE2500](http://www.wikidevi.com/wiki/Linksys_AE2500)

bcmwlhigh5.inf??

---

### Post by upgrdman on 2011-07-31
I just bought an AE2500 and it does not work for me either.

lsusb shows:
Bus 002 Device 003: ID 13b1:003a Linksys

dmesg shows just one relevant line:
[125747.902669] usb 2-2: new high speed USB device using ehci_hcd and address 3

After lots of Google'ing it seems the only possible option is Ndiswrapper. I'm going to return my AE2500 and try to find something with native Linux support.

-Farrell

---

### Post by CR4ZYC on 2011-08-05
I have the same model AE 2500. 
I get :   13b1:003a  during lsusb
I have tried [B]ndiswrapper [SIZE=1]with the different inf files provided with the windows driver cd.
But I had no success.[/SIZE]
Has any body had any luck?
[/B]

---

### Post by moffa on 2011-08-16
I got the Vista driver to install in ndiswrapper. It looks installed although I'm getting this error and it doesn't work.

from dmesg:```

ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  380.924770] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'

```

but ndiswrapper -l
```

bcmwlhigh6 : driver installed
	device (13B1:003A) present

```

---

### Post by chili555 on 2011-08-16
> I got the Vista driver to install in ndiswrapper. Here is what *man ndiswrapper-1.9* says:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install ***Windows XP***  drivers  and kernel module to load the Windows XP drivers. Both are called ndiswrapper.Would you please try the XP .inf and .sys files?

---

### Post by moffa on 2011-08-16
When trying to install the XP driver:
```
sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete

```
Only the Vista driver (Win7 driver has the same error as XP) installed.

I seem to have skipped some errors from dmesg

```

[  940.283723] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  940.283729] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[  940.283742] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  940.283745] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  940.283748] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  940.283751] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  940.283754] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  940.283757] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  940.283762] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  940.283765] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  940.283768] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[  940.283771] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  940.283776] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  940.283779] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  940.283783] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  940.283786] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  940.283789] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  940.283792] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  940.283795] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  940.283798] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  940.283802] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  940.283806] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  940.283809] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  940.283812] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  940.283815] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  940.283821] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  940.283829] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  940.283832] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  940.283836] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  940.283839] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  940.283840] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  940.284192] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'

```

---

### Post by chili555 on 2011-08-16
This might be fun...or not. May I see:```
uname -r
ndiswrapper -v
```Was the .sys file in the same directory when you installed the .inf?

---

### Post by moffa on 2011-08-16
uname -r
```
2.6.38-11-generic
```
ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.38-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.38-11-generic SMP mod_unload modversions 

```

Yes, the sys file was in the same directory as the inf

---

### Post by chili555 on 2011-08-16
Is this a compiled version of ndiswrapper? I thought the default version in Natty was 1.55. > couldn't find section "Linksys_AE1200.files.NT[COLOR="Red"]amd64[/COLOR]" -I wonder where this comes from; you don't have a 64-bit system. Did you inadvertantly grab the x64 .inf and .sys?

---

### Post by moffa on 2011-08-16
It's the repo version of ndiswrapper.  It installed when I installed ndisgtk.

I thought I was using the x64 version. uname -m shows x86_64

---

### Post by chili555 on 2011-08-16
Are you certain you removed the Vista .inf file?```
sudo ndiswrapper -e bcmwlhigh6
```And then install the XP with ndisgtk. In fact, I might remove the Vista version and reboot before you continue. Check /etc/ndiswrapper/ for any remnants and delete them if found:```
sudo rm -rf /etc/ndiswrapper/*
```Then install the XP .inf and .sys files and check dmesg again.

---

### Post by moffa on 2011-08-16
Removed the Vista inf file and rebooted.
ndisgtk fails, shell fails with the same error.

dmesg shows
```

[  219.420011] usb 2-5: new high speed USB device using ehci_hcd and address 5
[  219.700009] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  219.852147] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'

```

---

### Post by moffa on 2011-08-16
I'm tempted to go the BCM4323 (the chipset of the adapter) route and see if I have any luck.

---

### Post by chili555 on 2011-08-16
As far as I know, ndiswrapper is the only possibility. I haven't actually seen it working yet. You could be a pioneer!

---

### Post by Schnyd on 2011-08-21
I also just picked one of these cards up. Works great when I boot into windows but dead in the water in Ubuntu.

---

### Post by praseodym on 2011-08-21
Can you show the output of:

```
cat /var/log/syslog | grep loadndisdriver
```

There are problems with the ndiswrapper-version 1.56 with kernel 2.6.38, you may try the patched version. You need to uninstall the old version and the config first:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/3080287/ndiswrapper-1.56_patch_12.tar.gz
tar xvf ndiswrapper-1.56_patch_12.tar.gz
cd ndiswrapper-1.56_patch_12
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
```

Dont install ndisgtk, this will reinstall the old version of ndiswrapper again.

---

### Post by bd22 on 2011-08-31
Hello all,
this is what "worked" for me
I inserted the Disk that came with my AE2500 adapter.
Copied the files in setup/adapter/drver/ to my desktop then
run the following in terminal

```

$ sudo ndiswrapper -i Desktop/win7/bcmwlhigh6.inf

```

that installed it fine. 
Then i restarted my computer and THEN nothing is happening:confused: the blue light on the usb does not come on and i dont know what else i can try from terminal.

i tried the above instruction again and it said "driver bcmwlhigh6 is already installed ". i am not sure how i can make the driver run / or check if its running.

Here are my comp specs
Kernel Linux 2.6.38-8-generic(x86_64)
Distribution : Mint 11 - OEM

uname -r   :  
```
2.6.38-8-generic
```
ndiswrapper -v : 
```
utils Version : '1.9', utils version needed by module:'1.9'
filename: /lib/modules/2.6.38-8-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version : 1.56
vermagic: 2.6.38-8-generic SMP mo_unload modversions  
```

i had to type this since i am using my other computer - their might be some spelling mistakes.

If someone knows how i can start this driver please let me know. it should be simple i assume.

PS: you dont need to copy the files to your desktop from the cd. I did that because i was experimenting a lot and was easier to have it at desktop. you can give the path of the inf file from the disk. 

thanks for any help

---

### Post by bd22 on 2011-08-31
I am making progress.... i will post more as i know more.
I am getting the following error if you guys know how to solve it post here please. calling it a nigh for now
ndiswrapper (load_sys_file:206): couldn't prepare driver 'bcmwlhigh6'
ndiswrapper (load_wrap_driver:108): could't load driver bcmwlhigh6; check system log for messages from loadndisdriver

---

### Post by praseodym on 2011-08-31
cat /var/log/syslog | grep loadndisdriver

please. Did you try the XP or Vista driver? Maybe the Win7 ist just not working...

---

### Post by chili555 on 2011-08-31
> **praseodym said:**
> cat /var/log/syslog | grep loadndisdriver

please. Did you try the XP or Vista driver? Maybe the Win7 ist just not working...Neither the Vista nor the Windows 7 driver will ever work. Here is a snip from *man ndiswrapper*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install ***Windows XP***  drivers  and kernel module to load the ***Windows XP*** drivers. Both are called ndiswrapper.

---

### Post by bd22 on 2011-08-31
```
cat /var/log/syslog | grep loadndisdriver
 
 please. Did you try the XP or Vista driver? Maybe the Win7 ist just not working... 	
```

Hello,
When i tried the XP inf file it said driver was not installed right away.
The vista/win7 inf installed fine without problem.
I am at school now but i will try the terminal command when i get home.

```
Neither the Vista nor the Windows 7 driver will ever work. Here is a snip from *man ndiswrapper*: 	Quote:
 	 	 		 			 				DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install ***Windows XP***  drivers  and kernel module to load the ***Windows XP*** drivers. Both are called ndiswrapper. 			 		
```

when you dont have options u try anything :P  - but thanks for pointing this out.
But it this just means we are stuck because the Xp driver does not install at all using ndiswrapper. :(

---

### Post by praseodym on 2011-08-31
Before trying another driver the module has to be unloaded and the config-files of the other driver removed:

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
sudo depmod -a
```
After that try the others, just to be sure.

---

### Post by Rian428 on 2011-09-04
I just got the windows xp driver on the disc to work using ndiswrapper. I installed the bcmwlhigh5.inf,  then folloing the directions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). I'm a total linux noob I installed ubuntu today so I have no idea what I did. Just thought I should let you know it is possible.

---

### Post by Rian428 on 2011-09-04
Ok So I got the adapter to work but is there any way that I can load the drivers automatically. Every time I restart I have to run these commands.
 
    sudo depmod -a 
    sudo modprobe ndiswrapper

Do I just Have to live with it or is there some way to make them automatic?:confused:

---

### Post by nm_geo on 2011-09-04
> **Rian428 said:**
> Ok So I got the adapter to work but is there any way that I can load the drivers automatically. Every time I restart I have to run these commands.
 
    sudo depmod -a 
    sudo modprobe ndiswrapper

Do I just Have to live with it or is there some way to make them automatic?:confused:

Please do this:  "rc.local runs during boot up"

```
sudo gedit /etc/rc.local
```

Add these lines without sudo before the Exit 0

```
depmod -a
modprobe ndiswrapper
```

reboot

---

### Post by lastchance167 on 2011-09-05
Hey everyone having trouble, i just downloaded the ndiswrapper, using the ubuntu software center, clicked both addons too, and used the UI which it gives you, under system> administrations. its called windows wireless drivers, anyways, i clicked install browsed to the cd, and found the .inf under the xp folder, it was named bcmwlhigh5.inf, and it installed, now the wireless poped up fine after that, and works on open connects but wont work on my router, which is using a WPA2-PSK security, i typed the password in and it trys to connect forever, still working on that but, have confirmed it working with OPEN networks. 

anyways hope this helps some people. ill put an update out there if i get it working on mine as well.

---

### Post by chaosmage1030 on 2011-09-30
If anyone is still having issues with this, I fixed the issue by using the 32bit Ubuntu, rather than the 64bit.  It installed right away and didnt cause any issues using the xp driver from the cd.

Hope this helps!

---

### Post by moffa on 2011-10-05
Did anyone get it working in the 64-bit version of Ubuntu?

---

### Post by supernix on 2011-10-07
> **moffa said:**
> Did anyone get it working in the 64-bit version of Ubuntu?

I am running Linux Mint 11 using the CD 32bit version.
I used their ndiswrapper tool to install the WinXP drivers.
After the drivers were installed I plugged the adapter in.
After that the network sought the DHCP and setup the connection automatically.
This is what I did and how it worked for me.
Hope this helps.

---

### Post by amac777 on 2011-10-08
> **lastchance167 said:**
> Hey everyone having trouble, i just downloaded the ndiswrapper, using the ubuntu software center, clicked both addons too, and used the UI which it gives you, under system> administrations. its called windows wireless drivers, anyways, i clicked install browsed to the cd, and found the .inf under the xp folder, it was named bcmwlhigh5.inf, and it installed, now the wireless poped up fine after that, and works on open connects but wont work on my router, which is using a WPA2-PSK security, i typed the password in and it trys to connect forever, still working on that but, have confirmed it working with OPEN networks. 

anyways hope this helps some people. ill put an update out there if i get it working on mine as well.

Did you ever figure out how to get it working with WPA2-PSK? Mine works with no security and WEP, but doesn't seem to work well wth WPA (although a couple times it worked but was not repeatable)

---

### Post by sifterr on 2011-10-09
Hello,

This is my first post regarding Linux, but I would like to confirm that the **AE2500 adapter works flawlessly on Ubuntu 11.04 (server only tested) and with WPA2**. I can not speak for the 64 bit processors but suspect it might work as I will explain in the steps I took below.

1. Used the drivers from the CD and the winXP version. You need to copy all the files not just the .inf in the XP folder. However, only copy over the ones WITHOUT '64' in them (or just64 have not tested 64 bit). Exclude any 'AE1200xp.sys' if present since we are only talking about the 2500.

2. Assuming ndiswrapper is installed run command:  sudo ndiswrapper -i bcmwlhigh5.inf   (or whichever is the inf file). YOU MAY GET AN ERROR about the AE1200 just ignore it.

3. Go to the forum below and start at step3
         -supplement the alternative mentioned in the forum with                   **cfg80211**
[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)


At this point the adapter should work with iwconfig etc. assuming no encryption is used.

Now to get it to work with WPA2 I found this forum by kevdog. It explains how to use and apply wpa_supplicant which will be needed.
                             [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

1. Command:  sudo apt-get install wpasupplicant 
2. Create a config file named wpa_supplicant.conf and place it directly in the    /etc/   directory
3. The contents of the config file are as followed with your modifications for essid and passphrase:

ctrl_interface=/var/run/wpa_supplicant  network={         ssid="ESSID_IN_QUOTES"         psk="place here ASCII PSK Password in Quotes"         key_mgmt=WPA-PSK         proto=RSN WPA         pairwise=CCMP TKIP         group=CCMP TKIP }


(I am using AES encryption but I did not change the TKIP.)

4. After placing the config file in the /etc directory run the following commands:
       Assumes your interface wlan0 and driver is wext (see wpa_supplicant -l).
       
      
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 

(open a new terminal alt+F2)
sudo dhclient wlan0

EVERYTHING SHOULD WORK FROM HERE
(you may return to termianl1 alt+F1 and use cntrl + d or cntrl +z to kill the sudo wpa_supplicant to avoid restart errors)


edit: after each restart the command: sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf    (as show above) will have to be ran again followed by     sudo dhclient wlan0   
If any one has a solution to this please post.
        
 5. That is what did it for me. I am not sure what it all meant but I hope it helps anyone else trying to get this working. Also thanks for the support in this thread and all the others. It really helps

---

### Post by themacoz on 2011-10-16
Followed the instructions on the Ubuntu site and it couldn't have been simpler. Dumb luck!? ...

Only clues I could suggest is use the ndiswrapper package they propose in the instructions, delete any version of the driver you've installed and install it with these instructions.

BTW I am on Ubuntu 11.04

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper)

---

### Post by alexpigment on 2011-10-20
For those that got it working, could you get it to connect 5ghz signals? My linksys e4200 router only supports the 40mhz width (necessary for 300mbps) on the 5ghz channel.  When I installed with sifterr's instructions I was only able to see 2.4ghz ssid's, so I ended up going back to my ae1000 adapter.  Just wanted to make sure others were seeing the same. If not, I may have another go at it.

---

### Post by RogerPBrown on 2011-10-22
I have Ubuntu 11.10 (lubuntu, actually) and this is how I got my Linksys AE2500 working...

1) Install ndisgtk (graphical frontend for ndiswrapper).
2) Go to Start > "System Tools" > "Windows Wireless Drivers".
3) Click "Install New Driver"
4) Insert the provided CD-ROM and browse to /media/Setup/adapter/driver/xp/bcmwlhigh5.inf
5) Click Install

A few moments later, I could use the NetworkManager applet (nm-applet) in the system tray to select my SSID and all was well.

---

### Post by vansloot on 2011-10-23
> **RogerPBrown said:**
> I have Ubuntu 11.10 (lubuntu, actually) and this is how I got my Linksys AE2500 working...

1) Install ndisgtk (graphical frontend for ndiswrapper).
2) Go to Start > "System Tools" > "Windows Wireless Drivers".
3) Click "Install New Driver"
4) Insert the provided CD-ROM and browse to /media/Setup/adapter/driver/xp/bcmwlhigh5.inf
5) Click Install

A few moments later, I could use the NetworkManager applet (nm-applet) in the system tray to select my SSID and all was well.

Were you running the 32-bit or 64-bit version of Ubuntu? There seems to be a pattern emerging where the drivers work on 32-bit but not 64-bit. That's not really an option for me since I have 8GB of RAM.

Thanks!
Hans

Here's a log with my driver install details:

```

/media/Setup/adapter/driver/xp$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
/media/Setup/adapter/driver/xp$ uname -a
Linux hvs-linux 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
/media/Setup/adapter/driver/xp$ ls -alp
total 4605
dr-x------ 1 hvs hvs    2048 2011-05-06 12:38 ./
dr-x------ 1 hvs hvs    2048 2011-05-06 12:38 ../
-r-------- 1 hvs hvs 1176064 2011-03-30 01:22 AE1200xp64.sys
-r-------- 1 hvs hvs 1034240 2011-03-30 01:22 AE1200xp.sys
-r-------- 1 hvs hvs 1176064 2011-03-30 01:22 AE2500xp64.sys
-r-------- 1 hvs hvs 1034240 2011-03-30 01:22 AE2500xp.sys
-r-------- 1 hvs hvs    7179 2011-04-27 23:47 bcmh43xx64.cat
-r-------- 1 hvs hvs    7993 2011-04-27 23:47 bcmh43xx.cat
-r-------- 1 hvs hvs   95544 2011-03-30 02:14 bcmwlcoi64.dll
-r-------- 1 hvs hvs   91448 2011-03-30 02:14 bcmwlcoi.dll
-r-------- 1 hvs hvs   87164 2011-04-27 06:46 bcmwlhigh5.inf
/media/Setup/adapter/driver/xp$ ndiswrapper -l
/media/Setup/adapter/driver/xp$ ls /etc/ndiswrapper/
/media/Setup/adapter/driver/xp$ ls -lap /etc/ndiswrapper/
total 16
drwxr-xr-x   2 root root  4096 2011-10-23 00:28 ./
drwxr-xr-x 132 root root 12288 2011-10-23 00:04 ../
/media/Setup/adapter/driver/xp$ sudo depmod -a
/media/Setup/adapter/driver/xp$ sudo ndiswrapper -i bcmwlhigh5.inf 
installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete
/media/Setup/adapter/driver/xp$ sudo depmod -a
/media/Setup/adapter/driver/xp$ sudo modprobe ndiswrapper
/media/Setup/adapter/driver/xp$ cat /var/log/syslog | grep ndis
Oct 23 11:13:20 hvs-linux kernel: [   92.605310] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Oct 23 11:13:20 hvs-linux loadndisdriver: loadndisdriver: load_driver(337): coudln't find valid drivers files for driver bcmwlhigh5
Oct 23 11:13:20 hvs-linux adndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Oct 23 11:13:20 hvs-linux loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Oct 23 11:13:20 hvs-linux kernel: [   92.887475] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
Oct 23 11:13:20 hvs-linux kernel: [   92.887504] usbcore: registered new interface driver ndiswrapper
/media/Setup/adapter/driver/xp$ 

```

---

### Post by sifterr on 2011-10-23
Sorry alexpigment I have not tested the instruction with 5ghz signals. But have you tried adding your ssid to the wpa_suplicant file? If you are not using server perhaps try the install with ndisgtk per the instructions above, although I do not know what encryption they have found success with.

Also vansloot, can you try a variation of only including the 64 files (move the 32 and AE1200s to another directory) when doing an install and if not try with only the 32 files.

---

### Post by cthom06 on 2011-11-25
For people still having trouble on 64-bit:

The bmwlhigh5.inf is missing info for the 64-bit install, I modified it to contain the appropriate sections and it installed the xp64 driver without any apparent problems; however, now ```
modprobe ndiswrapper
``` stalls the cpu and freezes the entire system.

I'm looking into it more to see if I can figure out why.

---

### Post by FlyWheel on 2011-12-16
Recently upgraded to ubuntu 11.10 64 bit. Using the graphical system tool, if I try to install the win7 or xp driver, it says invalid driver. The vista driver complains that it can't find the hardware, but then it says hardware detected: yes. But there is no joy. No wireless options appear.  I had an older Belkin usb wifi, It had a loose usb connection, but otherwise worked fine.  I hope we can find a resolution to this soon.

---

### Post by Fat-n00b on 2012-01-23
Ok... So I had the same problem as everyone else here... but I fixed it and I am an ultra n00b with Linyx/ubuntu.  Actually in Xubuntu 11.10 32bit (I would assume the steps would be the same for 64bit other than choosing the XP 64 bit drivers) I used the XP Driver and NDISWrapper GUI.

Here is the quick and dirty of what I did:

#1. Make sure you have removed all previous installs attempts. I opened the NDISWrapper GUI and removed all drivers there.  I then double checked in terminal to make sure by

```
  ndiswrapper -l 
```#2. Make sure you "Blacklist" but the directions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) are a little hazy at  best > For Versions 9.04 and Later, the Filename has changed to blacklist.conf  so what you want to do for 11.10 is this:

```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```#3. I then Copied the XP driver (.inf) and sys (.sys) files into a folder on my computer you want to make sure the correct .sys file is in the same folder as the .inf file.  So you want for the 32bit version the following 2 files saved to folder that you can find (remember GUI is your friend here at least mine):

AE2500xp.sys
bcmwlhigh5.inf

#4. I then used NDISWrapper GUI to install the copied driver clear simple follow on screen commands.

#5. I then doubled checked that the driver loaded correctly by (look at the direction 3.4.2.1. in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for expected output)

```
 ndiswrapper -l 
```[SIZE=2]_At this point I think many think they have finished but they have a couple more steps..._
[/SIZE]
#6. Next I loaded the driver into memory by running the following lines in terminal

```
sudo depmod -a 
  sudo modprobe ndiswrapper
```#7. I check to see if my wireless was now working in terminal by using ip addr 
```
 ip addr 
```You are looking for a wlan0 line like:

```
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP>
```_[SIZE=3]THIS NEXT IS THE STEP THAT MOST n00bs FORGET[/SIZE]_

#8. You must get the NDISWrapper drivers to load at start up.  I could not follow the directions on [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to completion not sure if it was just me or if they need to updated but what I did was

#8.a. get/install 'gedit' from the software center (search results have the name as 'Text Editor')

Finally I used nm_geo's directions on page 3 of this topic to complete the install

#8.b. edit the rc.local file to include the load driver to memory commands (again thanks nm_geo )
#8.b.1 in terminal 
```
 sudo gedit /etc/rc.local
```#8.b.2. add 'depmod -a' and 'modprobe ndiswrapper' before the exit 0

```

depmod -a
modprobe ndiswrapper

exit 0
```I hope this helps someone.  And thanks to all of you for your help even though I am not the OP this did help me.

---

### Post by chili555 on 2012-01-24
> THIS NEXT IS THE STEP THAT MOST n00bs FORGET

#8. You must get the NDISWrapper drivers to load at start up. I could not follow the directions on [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) to completion not sure if it was just me or if they need to updated but what I did was

#8.a. get/install 'gedit' from the software center (search results have the name as 'Text Editor')

Finally I used nm_geo's directions on page 3 of this topic to complete the install

#8.b. edit the rc.local file to include the load driver to memory commands (again thanks nm_geo )
#8.b.1 in terminal
Code:

 sudo gedit /etc/rc.local

#8.b.2. add 'depmod -a' and 'modprobe ndiswrapper' before the exit 0

Code:

depmod -a
modprobe ndiswrapper

exit 0

That's an effective method, however, the usual method is easier:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Also, in your step that blacklists the module ssb, please be aware that this module is also used with the Broadcom ethernet driver b44. Blacklisting it may disable ethernet. There are other ways to disable b43, the wireless driver, but not b44 the ethernet driver.

---

### Post by Fat-n00b on 2012-02-03
> **chili555 said:**
> That's an effective method, however, the usual method is easier:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

I sometimes have to disconnect and reconnect my wireless nic before xubuntu will admit there is a wireless device connected... It is USB based do think your solution will help that or is it a problem with USB controller?

---

### Post by chili555 on 2012-02-03
> **Fat-n00b said:**
> I sometimes have to disconnect and reconnect my wireless nic before xubuntu will admit there is a wireless device connected... It is USB based do think your solution will help that or is it a problem with USB controller?Is its driver ndiswrapper? If so, then yes. If not, we'll need to find out what the driver is and load it instead.

---

### Post by kronoxx on 2012-02-10
XP driver don't work on x64 systems.

So waiting for latest patch for brcmfmac driver. It will support usb cards based on BCM43236.

[http://www.spinics.net/lists/linux-wireless/msg84419.html](http://www.spinics.net/lists/linux-wireless/msg84419.html)
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)

---

### Post by brpylko on 2012-02-10
or running jockey-gtk could work.

---

### Post by praseodym on 2012-02-11
Did you try the latest stable ndiswrapper version 1.57? See here:

[http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113](http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113)

---

### Post by kronoxx on 2012-02-14
> **praseodym said:**
> Did you try the latest stable ndiswrapper version 1.57? See here:

[http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113](http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113)

On x64 - same result with 1.57: 

installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete

ndiswrapper -l
bcmwlhigh5 : invalid driver!

---

### Post by hebetude on 2012-02-18
Confirmed not working on 64bit.

Ubuntu 11.10 x64

filename:       /lib/modules/3.0.0-16-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       3.0.0-16-generic SMP mod_unload modversions

---

### Post by praseodym on 2012-02-19
Try

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```
Check after that:

```
cat /etc/modprobe.d/ndiswrapper.conf
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by heavyt on 2012-02-19
> **chili555 said:**
> Is its driver ndiswrapper? If so, then yes. If not, we'll need to find out what the driver is and load it instead.
Yes it is driver ndiswrapper. Is there a work around for  disconnect and reconnect my wireless usb?

---

### Post by chili555 on 2012-02-19
> **heavyt said:**
> Yes it is driver ndiswrapper. Is there a work around for  disconnect and reconnect my wireless usb?Tell us more. What are you trying to achieve?

---

### Post by heavyt on 2012-02-20
> **chili555 said:**
> Tell us more. What are you trying to achieve? 

Have a Linkys AE2500 USB with a driver ndiswrapper. it will not work after my desktop resume from suspend. I have to disconnect then reconnect the usb ae2500 for it to work, as reported by others.

Xubuntu, HP-Compaq-dc7800-Ultra-slim-Desktop

---

### Post by chili555 on 2012-02-20
> **heavyt said:**
> Have a Linkys AE2500 USB with a driver ndiswrapper. it will not work after my desktop resume from suspend. I have to disconnect then reconnect the usb ae2500 for it to work, as reported by others.

Xubuntu, HP-Compaq-dc7800-Ultra-slim-DesktopLet's write one file and see if it helps:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="ndiswrapper"
```Proofread, save and close gedit. Any improvement? It may take a reboot.

---

### Post by heavyt on 2012-02-23
> **chili555 said:**
> Let's write one file and see if it helps:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="ndiswrapper"
```Proofread, save and close gedit. Any improvement? It may take a reboot.

Thanks for your reply. Yes I found those codes (by you and wildmanne39) in the Ubuntu forums. Problem solved, thanks again.:p

Also found that iogear usb wireless-N (Model GWU625) is truly a plugin and works, linux friendly!

---

### Post by moffa on 2012-03-11
> **kronoxx said:**
> On x64 - same result with 1.57: 

installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete

ndiswrapper -l
bcmwlhigh5 : invalid driver!

I figured out the problem with the driver not installing.  The driver has a bug.

Adding "amd64" after "NT" on lines 76, 83, 87 and 94 allow you to install the driver on an X64 system. I had to reboot and then run "depmod -a" and "modprobe ndiswrapper" but I still cannot get the system to detect the card.

At least the driver is loading:

bcmwlhigh5 : driver installed
	device (13B1:003A) present

tail /var/log/messages shows:
... kernel: [  737.208361] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
kernel: [  737.305390] usb 1-1.2: reset high speed USB device number 3 using ehci_hcd
loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5 
kernel: [  737.402096] usbcore: registered new interface driver ndiswrapper

Any idea what to do next?

---

### Post by devguy299 on 2012-03-24
> **moffa said:**
> I figured out the problem with the driver not installing.  The driver has a bug.

Adding "amd64" after "NT" on lines 76, 83, 87 and 94 allow you to install the driver on an X64 system. I had to reboot and then run "depmod -a" and "modprobe ndiswrapper" but I still cannot get the system to detect the card.

At least the driver is loading:

bcmwlhigh5 : driver installed
    device (13B1:003A) present

tail /var/log/messages shows:
... kernel: [  737.208361] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
kernel: [  737.305390] usb 1-1.2: reset high speed USB device number 3 using ehci_hcd
loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5 
kernel: [  737.402096] usbcore: registered new interface driver ndiswrapper

Any idea what to do next?

I also had to modifiy the bcmwlhigh5.inf file. I added the two amd64 entries in bold below. I am not sure if you did this but I also had to changed the files for them to point at the 64bit version of the files for example: **AE1200xp64.sys,,,6 **.  Here is what I have.

;----------------------------------------------------------------- 
; filename for CopyFiles 
; 
; Flag = 2 is COPYFLG_NOSKIP (2) 
; Flag = 33 is COPYFLG_WARN_IF_SKIP (1) | COPYFLG_NO_VERSION_DIALOG (32) 
[Linksys_AE1200.files.NT] 
    AE1200xp.sys,,,6 
 
[Linksys_AE2500.files.NT] 
    AE2500xp.sys,,,6 
 
[Linksys_AE1200.sys.files] 
    AE1200xp.sys,,,6 
 
[Linksys_AE2500.sys.files] 
    AE2500xp.sys,,,6 
 
[B][Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6 [/B]
 
[LinksysIHV.files.NTamd64] 
    bcmihvsrv64.dll,,,6 
    bcmihvui64.dll,,,6 
 
[LinksysIHV.files.NTx86] 
    bcmihvsrv.dll,,,6 
    bcmihvui.dll,,,6

I notice if I did not change the sys files to point at the 64bit version of the files the driver still installed with no errors but the adaptor still would not work. After changing that the adaptor was picked up after reboot. The good news I can now select the adaptor and connect to my router. The bad news is, I cannot get it to use my 5ghz bandwidth on my router.The ssid does not appear in the list for selection and cannot be manually entered for the 5ghz side of my router. The adaptor only seems to be able to see the 2.46ghz signal. Running at 2.46ghz only connects at 100 or 144 mbps. If I could get to the 5ghz side it could run a 300mbps. The worst part is when I use the adaptor it connects at 2.46ghz  and works but will lock up and force me to restart the machine after sometime. FYI I am on Fedora 15 not Ubuntu on the machine I am trying it on.

Does anyone have suggestions on how to make it run more stable and maybe connect to the 5ghz side of my router.

---

### Post by chili555 on 2012-03-24
Great information, guys! Thanks.

Bookmarked.

---

### Post by devguy299 on 2012-03-24
> **devguy299 said:**
> I also had to modifiy the bcmwlhigh5.inf file. I added the two amd64 entries in bold below. I am not sure if you did this but I also had to changed the files for them to point at the 64bit version of the files for example: **AE1200xp64.sys,,,6 **.  Here is what I have.

;----------------------------------------------------------------- 
; filename for CopyFiles 
; 
; Flag = 2 is COPYFLG_NOSKIP (2) 
; Flag = 33 is COPYFLG_WARN_IF_SKIP (1) | COPYFLG_NO_VERSION_DIALOG (32) 
[Linksys_AE1200.files.NT] 
    AE1200xp.sys,,,6 
 
[Linksys_AE2500.files.NT] 
    AE2500xp.sys,,,6 
 
[Linksys_AE1200.sys.files] 
    AE1200xp.sys,,,6 
 
[Linksys_AE2500.sys.files] 
    AE2500xp.sys,,,6 
 
[B][Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6 [/B]
 
[LinksysIHV.files.NTamd64] 
    bcmihvsrv64.dll,,,6 
    bcmihvui64.dll,,,6 
 
[LinksysIHV.files.NTx86] 
    bcmihvsrv.dll,,,6 
    bcmihvui.dll,,,6

I notice if I did not change the sys files to point at the 64bit version of the files the driver still installed with no errors but the adaptor still would not work. After changing that the adaptor was picked up after reboot. The good news I can now select the adaptor and connect to my router. The bad news is, I cannot get it to use my 5ghz bandwidth on my router.The ssid does not appear in the list for selection and cannot be manually entered for the 5ghz side of my router. The adaptor only seems to be able to see the 2.46ghz signal. Running at 2.46ghz only connects at 100 or 144 mbps. If I could get to the 5ghz side it could run a 300mbps. The worst part is when I use the adaptor it connects at 2.46ghz  and works but will lock up and force me to restart the machine after sometime. FYI I am on Fedora 15 not Ubuntu on the machine I am trying it on.

Does anyone have suggestions on how to make it run more stable and maybe connect to the 5ghz side of my router.

This is more information on my setup incase anyone can help me. Like I said my problem is it tends to lockup on a heavy load of network traffic. Such as copying a big file. I can surf the net and in fact I am using it now. I just want to work out connecting to the 5ghz band on my router and the stability issue.

# dmesg |grep ndiswrapper
[   41.981775] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   42.148867] ndiswrapper: driver bcmwlhigh5 (Cisco Consumer Products LLC,03/28/2011, 5.100.68.46) loaded
[   42.526482] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013e98000, 16000, 4
[   42.526494] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013e9be80, 16000, 5
[   42.526499] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013e9fd00, 16000, 5
[   42.526504] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ea3b80, 16000, 5
[   42.526509] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ea7a00, 16000, 5
[   42.526514] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eab880, 16000, 5
[   42.526519] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eaf700, 16000, 5
[   42.526523] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eb3580, 16000, 5
[   42.526528] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eb7400, 16000, 5
[   42.526535] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ebb280, 16000, 5
[   42.526539] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ebf100, 16000, 4
[   42.526544] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ec2f80, 16000, 5
[   42.526549] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ec6e00, 16000, 5
[   42.526553] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ecac80, 16000, 5
[   42.526558] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eceb00, 16000, 5
[   42.526562] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ed2980, 16000, 5
[   42.526567] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ed6800, 16000, 5
[   42.526571] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eda680, 16000, 5
[   42.526577] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ede500, 16000, 5
[   42.526582] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ee2380, 16000, 5
[   42.526587] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ee6200, 16000, 5
[   42.526591] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eea080, 16000, 4
[   42.526596] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013eedf00, 16000, 5
[   42.526600] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ef1d80, 16000, 5
[   42.526605] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ef5c00, 16000, 5
[   42.526611] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013ef9a80, 16000, 5
[   42.526616] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013efd900, 16000, 5
[   42.526620] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f01780, 16000, 5
[   42.526625] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f05600, 16000, 5
[   42.526629] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f09480, 16000, 5
[   42.526634] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f0d300, 16000, 5
[   42.526639] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f11180, 16000, 4
[   42.526643] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f15000, 16000, 4
[   42.526648] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f18e80, 16000, 5
[   42.526652] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f1cd00, 16000, 5
[   42.526659] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f20b80, 16000, 5
[   42.526676] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f24a00, 16000, 5
[   42.526681] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f28880, 16000, 5
[   42.526686] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f2c700, 16000, 5
[   42.526690] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f30580, 16000, 5
[   42.526695] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f34400, 16000, 5
[   42.526702] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f38280, 16000, 5
[   42.526706] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f3c100, 16000, 4
[   42.526711] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f3ff80, 16000, 5
[   42.526715] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f43e00, 16000, 5
[   42.526720] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f47c80, 16000, 5
[   42.526724] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f4bb00, 16000, 5
[   42.526729] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f4f980, 16000, 5
[   42.526733] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f53800, 16000, 5
[   42.526738] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013f57680, 16000, 5
[   42.547305] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   42.842127] usbcore: registered new interface driver ndiswrapper
[   47.134108] NetworkManager[948]: <info> (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 4)

#tail /var/log/messages 
Mar 24 13:03:53 localhost NetworkManager[948]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 24 13:03:53 localhost NetworkManager[948]: <info> Policy set 'Auto happy' (wlan1) as default for IPv4 routing and DNS.
Mar 24 13:03:53 localhost NetworkManager[948]: <info> Activation (wlan1) successful, device activated.
Mar 24 13:03:53 localhost NetworkManager[948]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Mar 24 13:03:53 localhost dbus: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 24 13:03:53 localhost dbus: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 24 13:04:26 localhost dbus: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Mar 24 13:04:26 localhost dbus: [system] Successfully activated service 'org.freedesktop.PackageKit'
Mar 24 13:06:07 localhost dbus: [system] Activating service name='net.reactivated.Fprint' (using servicehelper)
Mar 24 13:06:07 localhost dbus: [system] Successfully activated service 'net.reactivated.Fprint' 

This is what is in my /etc/modprobe.d/ndiswrapper.conf______________________________

install usb:v13B1p0039d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
install usb:v13B1p003Ad*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper

___________________________________________________________________________

I ran 

 ndiswrapper -m
 ndiswrapper -mi and also tried ma parameters.

 Both helped to populate the file and get the adaptor up and running but I am not sure if either mi or ma are better to use?
 
I also have a feeling that both my stabiity issue and the not connecting to the 5ghz band has something to do with the defaults being set in the  bcmwlhigh5.ini. For example there is a section where it sets ups some choices to enumurate and then specifies a default such as...

    HKR,    Ndi\params\Intolerant, ParamDesc,    0,      %Intolerant% 
    HKR,    Ndi\params\Intolerant, type,         0,      "enum" 
    HKR,    Ndi\params\Intolerant\enum, "0",     0,      %Disabled% 
    HKR,    Ndi\params\Intolerant\enum, "1",     0,      %Enabled% 
    HKR,    Ndi\params\Intolerant,default,,"0"  --default is set to 0 -disabled

This is just an example and there are many setting most of which I am not farmilar with. I did try updating some of them and then reinstalling the driver but still nothing. There are to many settings to guess which ones need to be changed. I am hoping someone might be familar with it and might be able to help.

Also, is there a way to change these settings after the installation. A config file or something? Changing them and reloading the driver gets to be a pain.

Thanks.

---

### Post by makokitten on 2012-03-27
Hi, I am a new ubuntu linux guy and I don't know much about linux, but I have been learning fast from these forums. I am still having trouble with the linksys ae2500 wireless adapter and I did the configuration of the  bcmwlhigh5.inf file by adding the 2 lines that devguy299 told in the forums.

> [B]
Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6
[/B]

I rebooted my computer and I am still having problems with the driver to load. I installed the vista and xp drivers, but I'm not too sure how to uninstall the vista drivers. When I added the 2 lines I also did some previous editing that chili555 and praseodym had instructed. I am running a 64bit version of ubuntu and I followed all the directions on this forum. If anyone has any clues for what I could do to get it running that would be fantastic because I am at a total loss on what to do. If anymore information is required please tell me and please write the command to use so I can get you the proper information. Sorry if I'm asking alot, but I am new to linux and I want to learn a lot more.

Thank you for all of your help on this,
Dan

---

### Post by chili555 on 2012-03-27
> I installed the vista and xp drivers, but I'm not too sure how to uninstall the vista drivers. Which one is in /etc/ndiswrapper now?

---

### Post by makokitten on 2012-03-27
there are 2 directories in there, bcmwlhigh5 and bcmwlhigh6. do I remove one of them?

---

### Post by chili555 on 2012-03-27
Are the actual inf files in there, too? Can you read each one and see which one is for Vista?```
sudo less /etc/ndiswrapper/bcmwlhigh[COLOR="Red"]X[/COLOR]/bcmwlhigh[COLOR="Red"]X[/COLOR].inf
```...where X is 5 and then 6. Remove whichever is incorrect:```
sudo ndiswrapper -e bcmwlhigh[COLOR="Red"]X[/COLOR]
```Remove the Vista .inf. Then I'd do:```
sudo modprobe -r ndiswrapper
sudo modprobe ndisrwapper
ndiswrapper -l
dmesg | grep ndis
```Note any errors or warnings and report them here.

---

### Post by makokitten on 2012-03-27
Ok, I found the vista drivers and they are under the folder bcmwlhigh6. I did the command > sudo ndiswrapper -e bcmwlhigh[COLOR=Red]X[/COLOR]Where the X is I replaced with 6. From there I get the msg

> cannot remove path when cwd is /etc/ndiswrapper/bcmwlhigh6 for /etc/ndiswrapper/bcmwlhigh6:  at /usr/sbin/ndiswrapper-1.9 line 126
couldn't delete /etc/ndiswrapper/bcmwlhigh6: Inappropriate ioctl for device

And yes the sys and inf file is in the folder

---

### Post by chili555 on 2012-03-27
What does this tell us:```
ndiswrapper -l
```Does it tell us 5 or 6 is installed? Or...what?> cannot remove path when cwd is /etc/ndiswrapper/bcmwlhigh6 for /etc/ndiswrapper/bcmwlhigh6: at /usr/sbin/ndiswrapper-1.9 line 126
couldn't delete /etc/ndiswrapper/bcmwlhigh6: Inappropriate ioctl for device We can brute force it once we're a little bit clearer about what sup.

---

### Post by makokitten on 2012-03-27
When I did ndiswrapper -l it gave me these results:

bcmwlhigh5 : invalid driver!
bcmwlhigh6 : driver installed
    device (13B1:003A) present

---

### Post by chili555 on 2012-03-27
> **makokitten said:**
> When I did ndiswrapper -l it gave me these results:

bcmwlhigh5 : invalid driver!
bcmwlhigh6 : driver installed
    device (13B1:003A) presentAnd you are quite sure that 6 is Vista and that 5 is XP *AND* 64-bit? Can you show us relevant quotes from each? I only ask because you say:> Hi, I am a new ubuntu linux guy and I don't know much about linux,And I say:> Join Date: Aug 2005
Beans: 12,473 Let's just check signals before we commit.

---

### Post by makokitten on 2012-03-27
Ok, here are the files in the bcmwlhigh6 directory:

mako-kitten@Darkstalker:/etc/ndiswrapper/bcmwlhigh6$ ls
13B1:0039.F.conf  ae1200vista64.sys  bcmwlhigh6.inf
13B1:003A.F.conf  ae2500vista64.sys

Here are the files in the bcmwlhigh5 directory:

mako-kitten@Darkstalker:/etc/ndiswrapper/bcmwlhigh5$ ls
13B1:0039.F.conf  13B1:003A.F.conf  bcmwlhigh5.inf

I noticed that in the bcmwlhigh5 directory that there is no sys file. I have the xp drivers still loaded on my HD, should I copy the sys file into this directory?

---

### Post by chili555 on 2012-03-27
The missing .sys file is probably a part of the issue. We need to read the first several lines of the .inf files:```
sudo gedit /etc/ndiswrapper/bcmwlhigh6/bcmwlhigh6.inf
```Copy and paste the few lines that say Vista. Do the same for 5 and show us where it refers to XP and 64-bit. Afterwards, we'll get on our surgical masks.

---

### Post by makokitten on 2012-03-27
Ok now I'm gettin somewhere, I copied the sys files to the /etc/ndiswrapper/bcmwlhigh5 directory and I did a ndiswrapper -l command and it gave me this output:

bcmwlhigh5 : driver installed
    device (13B1:003A) present
bcmwlhigh6 : driver installed
    device (13B1:003A) present

It now recognizes the xp driver, but when I use the ndiswrapper gui program it doesn't give me an option to pick wireless networks. I'll give you the first couple of lines in the bcmwlhigh5 and 6 inf files. If you find something wrong then lets hope we can correct this ^^

bcmwlhigh5.inf info:
; x64 (AMD64, Intel EM64T) - WinXP 
; 
[Cisco.NTamd64] 
    %Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039 
    %Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A 
;----------------------------------------------------------------- 
; x86 - Win2K, WinXP 
; 
[Cisco] 
    %Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039 
    %Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A 
    
;----------------------------------------------------------------- 
; x64 (AMD64, Intel EM64T) WinXP 
; 
 
[Linksys_AE1200.NTamd64] 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter_H.brcm.reg, common.reg, common.prevista.reg, bgn.options.reg, gn40.options.reg, nbg20.channels.reg, nbg40.channels.reg 
    DelReg          = common.delreg 
    CopyFiles    = Linksys_AE1200.files.NTamd64 
 
[Linksys_AE1200.NTamd64.Services] 
    AddService     = Linksys_adapter_H, 2, Linksys_AE1200_H.Service.NTamd64, common.EventLog 
 
 
[Linksys_AE2500.NTamd64] 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter_H.brcm.reg, common.reg, common.prevista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg 
    DelReg          = common.delreg 
    CopyFiles    = Linksys_AE2500.files.NTamd64 
 
[Linksys_AE2500.NTamd64.Services] 
    AddService     = Linksys_adapter_H, 2, Linksys_AE2500_H.Service.NTamd64, common.EventLog 
 
;----------------------------------------------------------------- 
; x86 - Win2k, WinXP 
; 
 
[Linksys_AE1200.NT] 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter_H.brcm.reg, common.reg, common.prevista.reg, bgn.options.reg, gn40.options.reg, nbg20.channels.reg, nbg40.channels.reg 
    DelReg        = common.delreg 
    CopyFiles    = Linksys_AE1200.files.NT 
 
[Linksys_AE1200.NT.Services] 
    AddService     = Linksys_adapter_H, 2, Linksys_AE1200_H.Service.NT, common.EventLog 
 
 
[Linksys_AE2500.NT] 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter_H.brcm.reg, common.reg, common.prevista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg 
    DelReg        = common.delreg 
    CopyFiles    = Linksys_AE2500.files.NT 
 
[Linksys_AE2500.NT.Services] 
    AddService     = Linksys_adapter_H, 2, Linksys_AE2500_H.Service.NT, common.EventLog 
 
 
;----------------------------------------------------------------- 
; NT systems 
; 
 
[Linksys_adapter.reg] 
    ; Ndis Info 
    ; Interfaces 
    HKR,    Ndi\Interfaces,    UpperRange,    ,    "ndis5" 
    HKR,    Ndi\Interfaces,    LowerRange,    ,    "ethernet" 
 
[Linksys_adapter.brcm.reg] 
    HKR,    Ndi,    HelpText,        ,    %Linksys_adapter_HELP% 
    HKR,    Ndi,    Service,        0,    "Linksys_adapter" 
 
[Linksys_adapter_H.brcm.reg] 
    HKR,    Ndi,    HelpText,        ,    %Linksys_adapter_HELP% 
    HKR,    Ndi,    Service,        0,    "Linksys_adapter_H" 
 
    HKR,                                    ,"featureflag", 65537, "0x00000004" 
 
[common.EventLog] 
    AddReg = common.AddEventLog.reg 
 
[common.AddEventLog.reg] 
    HKR,    ,    EventMessageFile,    0x00020000,    "%%SystemRoot%%\System32\netevent.dll" 
    HKR,    ,    TypesSupported,        0x00010001,    7 
 
 
; WinXP and 2k -high 
[Linksys_AE1200_H.Service.NTamd64] 
    DisplayName    = %Linksys_adapter_H_Service_DispName% 
    ServiceType    = 1            ; %SERVICE_KERNEL_DRIVER% 
    StartType    = 3            ; %SERVICE_DEMAND_START% 
    ErrorControl    = 1            ; %SERVICE_ERROR_NORMAL% 
    ServiceBinary    = %12%\AE1200xp64.sys 
    LoadOrderGroup    = NDIS 
 
 
[Linksys_AE2500_H.Service.NTamd64] 
    DisplayName    = %Linksys_adapter_H_Service_DispName% 
    ServiceType    = 1            ; %SERVICE_KERNEL_DRIVER% 
    StartType    = 3            ; %SERVICE_DEMAND_START% 
    ErrorControl    = 1            ; %SERVICE_ERROR_NORMAL% 
    ServiceBinary    = %12%\AE2500xp64.sys 
    LoadOrderGroup    = NDIS 
 
; WinXP and 2k -high 
[Linksys_AE1200_H.Service.NT] 
    DisplayName    = %Linksys_adapter_H_Service_DispName% 
    ServiceType    = 1            ; %SERVICE_KERNEL_DRIVER% 
    StartType    = 3            ; %SERVICE_DEMAND_START% 
    ErrorControl    = 1            ; %SERVICE_ERROR_NORMAL% 
    ServiceBinary    = %12%\AE1200xp.sys 
    LoadOrderGroup    = NDIS 
 
; WinXP and 2k -high 
[Linksys_AE2500_H.Service.NT] 
    DisplayName    = %Linksys_adapter_H_Service_DispName% 
    ServiceType    = 1            ; %SERVICE_KERNEL_DRIVER% 
    StartType    = 3            ; %SERVICE_DEMAND_START% 
    ErrorControl    = 1            ; %SERVICE_ERROR_NORMAL% 
    ServiceBinary    = %12%\AE2500xp.sys 
    LoadOrderGroup    = NDIS

The bcmwlhigh6.inf file is a bit longer, I'll send that in another post

---

### Post by makokitten on 2012-03-27
This is the bcmwlhigh6.inf configuration:

; x64 (AMD64, Intel EM64T) - WinVista 
; 
[Cisco.NTamd64.6.0] 
    %Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039 
    %Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A 
 
 
;----------------------------------------------------------------- 
; x86 - WinVista 
; 
[Cisco.NTx86.6.0] 
    %Linksys_AE1200_DeviceDesc% = Linksys_AE1200, USB\VID_13B1&PID_0039 
    %Linksys_AE2500_DeviceDesc% = Linksys_AE2500, USB\VID_13B1&PID_003A 
 
 
 
; Bcm COI and WDF Co-installer 
 
 
[Linksys_adapter_wdfsect] 
    KmdfLibraryVersion = 1.5 
 
;----------------------------------------------------------------- 
; x64 (AMD64, Intel EM64T) - WinVista 
; 
 
[Linksys_AE1200.NTamd64] 
    *IfType        = 71    ; IF_TYPE_IEEE80211 
    *MediaType    = 16    ; NdisMediumNative802_11 
    *PhysicalMediaType = 9  ; NdisPhysicalMediumNative802_11 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter.cisco.reg, common.reg, common.vista.reg, bgn.options.reg, gn40.options.reg, nbg20.channels.reg, nbg40.channels.reg, Linksys_IHV.reg.NTamd64 
    DelReg          = common.delreg, common.vista.delreg 
    CopyFiles    = Linksys_AE1200.files.NTamd64, LinksysIHV.files.NTamd64 
    RegisterDlls    = LinksysIHVUI.regsrv.NTamd64 
 
[Linksys_AE2500.NTamd64] 
    *IfType        = 71    ; IF_TYPE_IEEE80211 
    *MediaType    = 16    ; NdisMediumNative802_11 
    *PhysicalMediaType = 9  ; NdisPhysicalMediumNative802_11 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter.cisco.reg, common.reg, common.vista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg, Linksys_IHV.reg.NTamd64 
    DelReg          = common.delreg, common.vista.delreg 
    CopyFiles    = Linksys_AE2500.files.NTamd64, LinksysIHV.files.NTamd64 
    RegisterDlls    = LinksysIHVUI.regsrv.NTamd64 
 
 
[Linksys_AE1200.NTamd64.Services] 
    AddService = Linksys_adapter, 2, Linksys_AE1200.Service.NTamd64, common.EventLog 
 
[Linksys_AE2500.NTamd64.Services] 
    AddService = Linksys_adapter, 2, Linksys_AE2500.Service.NTamd64, common.EventLog 
 
 
; Bcm COI and WDF Co-installer 
[Linksys_AE1200.NTamd64.CoInstallers] 
        CopyFiles       = CoInstall.CopyFiles.NTamd64, Linksys_adapter.CoInstaller.CopyFiles.NTamd64 
        AddReg          = Linksys_AE1200_CoInstaller_AddReg.NTamd64 
 
[Linksys_AE1200_CoInstaller_AddReg.NTamd64] 
    HKR,,CoInstallers32,0x00010000, "WdfCoInstaller01005.dll,WdfCoInstaller" 
 
[Linksys_AE1200.NTamd64.Wdf] 
    KmdfService = Linksys_adapter, Linksys_adapter_wdfsect 
 
 
[Linksys_AE2500.NTamd64.CoInstallers] 
        CopyFiles       = CoInstall.CopyFiles.NTamd64, Linksys_adapter.CoInstaller.CopyFiles.NTamd64 
        AddReg          = Linksys_2500_CoInstaller_AddReg.NTamd64 
 
[Linksys_2500_CoInstaller_AddReg.NTamd64] 
    HKR,,CoInstallers32,0x00010000, "WdfCoInstaller01005.dll,WdfCoInstaller" 
 
[Linksys_AE2500.NTamd64.Wdf] 
    KmdfService = Linksys_adapter, Linksys_adapter_wdfsect 
 
;Linksys_adapter_wdfsect is already set in 64bit section 
 
 
 
;----------------------------------------------------------------- 
; x86 - WinVista 
; 
 
[Linksys_AE1200.NTx86] 
    *IfType        = 71    ; IF_TYPE_IEEE80211 
    *MediaType    = 16    ; NdisMediumNative802_11 
    *PhysicalMediaType = 9  ; NdisPhysicalMediumNative802_11 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter.cisco.reg, common.reg, common.vista.reg, bgn.options.reg, gn40.options.reg, nbg20.channels.reg, nbg40.channels.reg, Linksys_IHV.reg.NTx86 
    DelReg          = common.delreg, common.vista.delreg 
    CopyFiles    = Linksys_AE1200.files.NTx86, LinksysIHV.files.NTx86 
    RegisterDlls    = LinksysIHVUI.regsrv.NTx86 
 
 
[Linksys_AE2500.NTx86] 
    *IfType        = 71    ; IF_TYPE_IEEE80211 
    *MediaType    = 16    ; NdisMediumNative802_11 
    *PhysicalMediaType = 9  ; NdisPhysicalMediumNative802_11 
    Characteristics    = 0x84    ; NCF_PHYSICAL | NCF_HAS_UI 
    BusType        = 15    ; PNP bus 
    AddReg        = Linksys_adapter.reg, Linksys_adapter.cisco.reg, common.reg, common.vista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg, Linksys_IHV.reg.NTx86 
    DelReg          = common.delreg, common.vista.delreg 
    CopyFiles    = Linksys_AE2500.files.NTx86, LinksysIHV.files.NTx86 
    RegisterDlls    = LinksysIHVUI.regsrv.NTx86 
 
     
[Linksys_AE1200.NTx86.Services] 
    AddService = Linksys_adapter, 2, Linksys_AE1200.Service.NTx86, common.EventLog 
     
[Linksys_AE2500.NTx86.Services] 
    AddService = Linksys_adapter, 2, Linksys_AE2500.Service.NTx86, common.EventLog 
 
;Co-installers for Vista x86 
;============================================================================= 
 
 
; Bcm COI and WDF Co-installer 
[Linksys_AE1200.NTx86.CoInstallers] 
        CopyFiles       = CoInstall.CopyFiles.NTx86, Linksys_adapter.CoInstaller.CopyFiles.NTx86 
        AddReg          = Linksys_AE1200_CoInstaller_AddReg.NTx86 
 
[Linksys_AE1200_CoInstaller_AddReg.NTx86] 
    HKR,,CoInstallers32,0x00010000, "WdfCoInstaller01005.dll,WdfCoInstaller" 
 
[Linksys_AE1200.NTx86.Wdf] 
    KmdfService = Linksys_adapter, Linksys_adapter_wdfsect 
 
[Linksys_AE2500.NTx86.CoInstallers] 
        CopyFiles       = CoInstall.CopyFiles.NTx86, Linksys_adapter.CoInstaller.CopyFiles.NTx86 
        AddReg          = Linksys_AE2500_CoInstaller_AddReg.NTx86 
 
[Linksys_AE2500_CoInstaller_AddReg.NTx86] 
    HKR,,CoInstallers32,0x00010000, "WdfCoInstaller01005.dll,WdfCoInstaller" 
 
[Linksys_AE2500.NTx86.Wdf] 
    KmdfService = Linksys_adapter, Linksys_adapter_wdfsect 
 
;Linksys_adapter_wdfsect is already set in NTamd64 section 

I hope this helps

---

### Post by chili555 on 2012-03-27
You were quite correct. We want 5 and not 6. Please do:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwlhigh6
```If that fails, then do:```
sudo rm -rf /etc/ndiswrapper/bcmwlhigh6/*
sudo rmdir /etc/ndiswrapper/bcmwlhigh6
```Now reload ndiswrapper:```
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by makokitten on 2012-03-27
ok I did these commands and had no errors

sudo modprobe -r ndiswrapper sudo ndiswrapper -e bcmwlhigh6
Then I tried this command and had no problems or errors

sudo modprobe ndiswrapper
Then I did a "ip addr" and it brought back this:

> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:19:66:e3:7f:4c brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::219:66ff:fee3:7f4c/64 scope link 
       valid_lft forever preferred_lft forever

The wireless adapter shows up in ndiswrapper gui and says it's installed, yet I get no options to discover my wireless network. Is there a specific command I need to use to detect my wireless network?

---

### Post by chili555 on 2012-03-27
Please reboot so we have a clean slate and then post:```
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by makokitten on 2012-03-27
Sorry for the late reply, but I had to visit my grandma and take a nap (been at this all day), anyway, here is the output from those commands:

> mako-kitten@Darkstalker:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (13B1:003A) present
mako-kitten@Darkstalker:~$ dmesg | grep ndis
[   52.897465] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   53.188903] usbcore: registered new interface driver ndiswrapper
[  108.744677] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  108.748311] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  108.751952] ndiswrapper: driver bcmwlhigh5 (Cisco Consumer Products LLC,03/28/2011, 5.100.68.46) loaded
[  108.754610] IP: [<ffffffffa00a6e39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  108.754649] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek bnep rfcomm bluetooth binfmt_misc nvidia(P) snd_seq_midi snd_rawmidi ppdev snd_seq_midi_event snd_seq snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_device snd_timer k10temp serio_raw edac_core edac_mce_amd parport_pc snd ndiswrapper soundcore snd_page_alloc i2c_nforce2 lp parport usbhid hid floppy pata_amd forcedeth sata_nv
[  108.754687] RIP: 0010:[<ffffffffa00a6e39>]  [<ffffffffa00a6e39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  108.754767]  [<ffffffffa008fc7a>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[  108.754785]  [<ffffffffa00a6e50>] ? USBD_InterfaceIsDeviceHighSpeed+0x20/0x20 [ndiswrapper]
[  108.754804]  [<ffffffffa00a6e80>] ? USBD_InterfaceReference+0x30/0x30 [ndiswrapper]
[  108.754826]  [<ffffffffa00a6df0>] ? USBD_GetUSBDIVersion+0x20/0x20 [ndiswrapper]
[  108.754842]  [<ffffffffa00a6eb0>] ? USBD_InterfaceDereference+0x30/0x30 [ndiswrapper]
[  108.754858]  [<ffffffffa00a6ee0>] ? USBD_InterfaceQueryBusTime+0x30/0x30 [ndiswrapper]
[  108.754874]  [<ffffffffa00a6f10>] ? USBD_InterfaceSubmitIsoOutUrb+0x30/0x30 [ndiswrapper]
[  108.754890]  [<ffffffffa00a6e30>] ? USBD_InterfaceGetUSBDIVersion+0x40/0x40 [ndiswrapper]
[  108.754911]  [<ffffffffa00a7067>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  108.754934]  [<ffffffffa00a2e02>] ? mp_init+0x72/0x210 [ndiswrapper]
[  108.754949]  [<ffffffffa009ceca>] ? pdoDispatchPnp+0x5a/0x190 [ndiswrapper]
[  108.754964]  [<ffffffffa009abb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  108.754984]  [<ffffffffa00a3fbb>] ? ndis_start_device+0x2b/0x870 [ndiswrapper]
[  108.755011]  [<ffffffffa009abb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  108.755027]  [<ffffffffa009af26>] ? IoSyncForwardIrp+0x96/0xe0 [ndiswrapper]
[  108.755048]  [<ffffffffa00a5073>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[  108.755066]  [<ffffffffa00a7067>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  108.755087]  [<ffffffffa009abb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  108.755106]  [<ffffffffa009abdc>] ? IofCallDriver+0x6c/0xc0 [ndiswrapper]
[  108.755129]  [<ffffffffa009abb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  108.755149]  [<ffffffffa009c8d7>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
[  108.755177]  [<ffffffffa009d1dc>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[  108.755196]  [<ffffffffa009d531>] ? wrap_pnp_start_device+0xd1/0x180 [ndiswrapper]
[  108.755212]  [<ffffffffa009d7bf>] ? wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
[  108.755391] RIP  [<ffffffffa00a6e39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]

btw, on top of loading after reboot I had troubles starting up ubuntu when the wireless card was plugged in so I unplugged it and restarted. I plugged it back in after it safely booted up

---

### Post by chili555 on 2012-03-28
> Sorry for the late reply, but I had to visit my grandma and take a napGrannies and Grampies love that! As it happens, I was Skyping with my grandchildren last evening!

Is the 32-bit or 64-bit .sys file in /etc/ndiwrapper/bcmwlhigh5 or both? Only the 64-bit should be there.

> Adding "amd64" after "NT" on lines 76, 83, 87 and 94> I also had to changed the files for them to point at the 64bit version of the files for example: AE1200xp64.sys,,,6 .Are you sure you did all these steps?

---

### Post by makokitten on 2012-03-28
I'm gonna try to give this one last try, I did alot of editing and it seems I'm not getting past a certain point. I'll try today to get it working, but if it don't happen I'll just sell this wireless adapter and buy one that is compatible. So lets try this again ;)

I edited the bcmlhigh5.inf file and added this information:

			 		> Adding "amd64" after "NT" on lines 76, 83, 87 and 94 

I made sure too that no other sys files that aren't 64bit are in /etc/ndiswrapper/bcmlhigh5

I might need to reinstall and start fresh or just get another wireless adapter :(

---

### Post by chili555 on 2012-03-28
> **makokitten said:**
> I'm gonna try to give this one last try, I did alot of editing and it seems I'm not getting past a certain point. I'll try today to get it working, but if it don't happen I'll just sell this wireless adapter and buy one that is compatible. So lets try this again ;)

I edited the bcmlhigh5.inf file and added this information:

			 		

I made sure too that no other sys files that aren't 64bit are in /etc/ndiswrapper/bcmlhigh5

I might need to reinstall and start fresh or just get another wireless adapter :(And after you do some double-checking and editting, if necessary, I'd reboot and check again:```
dmesg | grep ndis
```About 2/3rds of my business is bcmwlhigh5.inf and 64-bit; not very much of it successful. 

I doubt you'd need to reinstall. Just remove ndiswrapper, the entire /etc/ndiswrapper folder and you're good as new.

There are many threads here about working out of the box USB devices.

---

### Post by devguy299 on 2012-03-30
> **makokitten said:**
> I'm gonna try to give this one last try, I did alot of editing and it seems I'm not getting past a certain point. I'll try today to get it working, but if it don't happen I'll just sell this wireless adapter and buy one that is compatible. So lets try this again ;)

I edited the bcmlhigh5.inf file and added this information:

                     

I made sure too that no other sys files that aren't 64bit are in /etc/ndiswrapper/bcmlhigh5

I might need to reinstall and start fresh or just get another wireless adapter :(

I had edited the ini file and it installed the device but it ran terrible.  It would lockup and it did not see the 5ghz bandwidth on the router. The AE2500 seems to have trouble working under ndis wrapper on 64bit linux. I since decided to try the AE1000 and to my supprise it was up and running with no effort at all. I plugged it in to my machine and booted up to a fully functional device. Works in both 2 & 5ghz bandwidths, no lockups at 270mbps. FYI... I tested it on Fedora core 15 64bit.

---

### Post by Wojosama on 2012-04-01
I just want to say thank you to everyone who contributed to this discussion, the xp driver worked with no problems using ndiswrapper on 32bit, but when I switched to 64bit I entered a world of hurt. 

However, thankfully, I can confirm the Linksys AE1200 working on 64bit ubuntu 11.10 on 802.11g. The AE1200 and AE2500 share the same drivers, so both should work fine. I can't speak on 802.11N connectivity as I don't have an N router to test it with, sorry. A lot of this will be similar to Fat-n00b's info in post #40 but with all the stuff I had to do extra to make it work on 64bit. 

Before you start, I have not added/modified/deleted anything relating to networking or any other hardware drivers(modules) since I did the clean install of 11.10 x64.
These are the steps I took (pretty much all found here and pieced together):

**NOTE: THE FILES YOU DELETE IN STEP 3B ARE THE 32BIT DRIVERS. THESE INSTRUCTIONS ARE FOR 64BIT ONLY FOR THAT REASON.**
[B]NOTE 2: IF YOU HAVEN'T DONE ANY WORK TO INSTALL THESE DRIVERS WITH NDISWRAPPER YOU CAN SKIP STEP 1.
[/B]
**1.** First remove all prior work with this (replace bcmwlhigh5 with bcmwlhigh6 if you tried installing vista or win7 drivers):

```

sudo ndiswrapper -e bcmwlhigh5
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -rf /etc/ndiswrapper/*
sudo depmod -a

```I would restart the computer now just to be safe.

**2.** Next, I had to build version 1.57 of ndiswrapper as the one in the ubuntu repositories didnt work, instructions for removing your current version and downloading/building/installing the new version can be found here: [HTML]http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113[/HTML]**3a.** After that is done, you must make sure you've got the right files in the folder with the winxp inf file.
Download the XP driver here if you need it (You MUST use the windows xp drivers): [HTML]http://homedownloads.cisco.com/downloads/driver/1224667593495/AE1200xp.zip[/HTML]**3b.** Extract those to an easy place to find them. After you extract them, **delete the following files** from the folder (probably unnecessary but do it just in case): AE1200xp.sys, AE2500xp.sys, bcmh43xx.cat, bcmwlcoi.dll

**4.** Now you need to add the following lines to bcmwlhigh5.inf:
Open in a text editor and put the cursor at the begining of line 178 and paste these lines:
```
 

[Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6 


```                            Adding "amd64" after "NT" on lines 76, 83, 87 and 94                      is NOT necessary, it would just try to make the inf use the 32bit versions of the .sys files which doesn't work (and I've had you delete those files just in case you did amend those lines).
[B]
5.[/B] Blacklist other bcm modules to keep them from loading
```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```[B]
6.[/B] Time to install! Finally, I know.
Here's the commands (**PLEASE READ THE NOTES BELOW FIRST**):
```

sudo ndiswrapper -i /home/adam/Desktop/XP/bcmwlhigh5.inf   **CHANGE TO YOUR LOCATION**
sudo ndiswrapper -m -ma -mi
sudo depmod -a
sudo modprobe ndiswrapper

```A few notes on the code you'll enter (or did enter if you didn't read ahead first :p); 
First you can either  direct ndiswrapper to your inf file (as i did), or you can cd to the  folder it's in and just do 'sudo ndiswrapper -i bcmwlhigh5.inf'  
Second is that I don't know if everything in the second command is  necessary but it DOES work, they are exactly what I used.
Lastly, and this is VERY important, the moment I typed in the 'sudo depmod -a' and hit enter, my computer completely froze and I had to hit the restart button on the tower, however when it rebooted, voila! I could see my wireless adapter for the first time since I installed 64bit, and I could connect to my wireless network!

Two final things about connecting to your router (which I had to do on 32bit and am guessing would've had to do on 64bit as well had i not already done it): 
1. If your router is set to NOT broadcast SSID you will probably not be able to connect to it. I had to set it to broadcast in the end as nothing i did worked, and i tried a LOT of stuff lol. 
2. If you are using WPA, in my case WPA2 - PSK, I had to change my password as for some reason it just would not connect, I ended up using one generated from here: [HTML]http://www.yellowpipe.com/yis/tools/WPA_key/generator.php[/HTML]After setting the new wpa password, I was able to connect without any problem. Keep in mind, I had 2 phones, and 3 other computers connected to it all using the old password but it just would not work with the ubuntu+ndiswrapper combo until I used the one I generated, so if using WPA, and you can't connect, try one from the generator before you give up on WPA.
MAC address filtering enabled on the router was obviously unaffected through all of this, so setting SSID to broadcast was the only layer of security I had to sacrifice.

Sorry for the MASSIVE post. I just can't thank everyone here enough, and if this keeps even one person from wasting their entire weekend like I just did, then making this post was well worth it. I know the last post is a couple days old but if I googled my here, someone else will as well. If there's somewhere else that it would be helpful for me to post this info I'd appreciate it if anyone would let me know. I've only used Ubuntu for a very, very short time, but I've been helped countless times by posters like you guys, so if i contribute back in any way, then I'd really like to.
(P.S. Longest first post ever? lol)

---

### Post by ChopstickNINJ4 on 2012-04-05
Hi all,

I tried following Wojosama's post and got to the point where I load the driver into memory using ```
sudo modprobe ndiswrapper
``` whatever program I used to run the command either through terminal using ndiswrapper 1.57, or later trying with ndisgtk and ndiswrapper 1.56 freeze.  About a minute or so later my whole system will crash even if I try to kill the processes.

After rebooting ```
user@ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (13B1:003A) present

``` shows an installed device, but it is not listed anywhere if I run ifconfig.

Thanks in advance for all your help!

---

### Post by Wojosama on 2012-04-05
Hey chopstick, sorry you're having trouble, I did have that exact same problem at some point during my endeavor. I see your device is 003A, so you're using the 2500 right? A few questions, that are probably basic and redundant, but better to ask than to assume the answers (I know they are stupid questions, but I'm just trying to cover all bases).

1. You're using 64bit ubuntu 11.10? (Told you they were stupid questions)
2. Did you completely remove all 3 of the old ndis apps (ndiswrapper-utils-1.9, ndiswrapper-common, and ndisgtk, must remove all 3) as per the instructions on the link for building the newer version before you built and installed 1.57? Every last instruction must be followed to the letter on the link i provided.
3. If you have a wired ethernet connection hooked up try removing it before you restart.
4. Possibly try everything again from step 1, and make sure you reboot after step 1 and also try restarting after step 5 as well.
5. If all else fails, maybe there is something different about the drivers between the 1200 and 2500, try all the steps and use the drivers from: [HTML]http://homedownloads.cisco.com/downloads/driver/AE2500xp_WHQL,0.zip[/HTML]I hope something in there helps you. Good luck man.

---

### Post by ChopstickNINJ4 on 2012-04-07
Hi Wojosama,

I did all the steps you did and in a moment of rash craziness went ahead and tried to figure out how to get the AE2500 up and running on Arch Linux (that was a huge learning experience XD) to see if having fewer packages would help reduce any of the issues.  Anyways I did that and got all the way down to [https://bbs.archlinux.org/viewtopic.php?id=137630]("https://bbs.archlinux.org/viewtopic.php?id=137630"), but for some reason I ended up with one discrepancy:

```
[  122.723060] wlan0: ethernet device c0:c1:c0:60:48:5f using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13B1:003A.F.conf
[  122.729393] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  127.745307] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I never got to the point where where my wireless adapter actually came up and connected.  Also I think modprobe crashes because something else was loaded as the driver for the AE2500 so I will unload that and take another crack at it.  I would much rather get this working on a nice prepacked linux distro instead of having to figure out every single thing to install and configure down to whether or not I want sound on startup by running daemons O.o

**EDIT**

So, I managed to get the driver working on 12.04 following this guide.  However Linux doesn't have the ability to manage it very well?  None of the iwconfig functions change power level or bit rate.  Anyways, long story short, it only works if I'm sitting REALLY close to the router, otherwise I have > 90% invalid misc packets.

Also when configuring ndiswrapper do:

```
ndiswrapper -mi
ndiswrapper -m
```

ndiswrapper -m -mi -ma isn't properly formatted?  When running ndiswrapper -mi or -ma add the same entries for the USB device ID, it overwrites the entire ndiswrapper.conf file and removes the alias for wlan0.  So ```
ndiswrapper -mi
``` FIRST and then ```
ndiswrapper -m
``` otherwise it doesn't register it as wlan0.

So my solution was to go out and buy a new wireless card :-D  Thanks for all the help everybody!

---

### Post by devinthenuke on 2012-05-01
I had the exact same problem tonight but I was able to get it up and running...Below you will find how I did this

1)  Go to [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) and download the ndiswrapper-1.57.tar.gz
2)  Download the AE2500 Driver for WINDOWS XP at [http://homesupport.cisco.com/en-us/support/adapters/AE2500](http://homesupport.cisco.com/en-us/support/adapters/AE2500)
3)  UNZIP the AE2500 Driver ZIP package from CISCO and then transfer the unzipped folder and ndiswrapper-1.57.tar.gz to a thumbdrive
4)  Mount said thumbdrive in your System, bring up terminal and find your thumbdrive (we will say it mounted as MYDRIVE)
                         *************************EXAMPLE**************************
                         *you@yourputer:/media/MYDRIVE$*********************
                         ***************END EXAMPLE****************************
5)  Extract your file ndiswrapper-1.57.tar.gz file
                         **********************************EXAMPLE************************************
                         *you@yourputer:/media/MYDRIVE$tar zxvf ndiswrapper-1.57.tar.gz*
                         *********************************END EXAMPLE*******************************
6)  Navigate to the new directory where ndiswrapper-1.57.tar.gz was unzipped to and run make uninstall followed by the make command, finally run the make install command
                         **********************************EXAMPLE************************************
                          *you@yourputer:/media/MYDRIVE$cd ndiswrapper-1.57  *************
                         *you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$make uninstall*
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$make **********
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *******BLAH, BLAH, BLAH, BLAH********************************************
                         *you@yourputer:/media/MYDRIVE/ndiswrapper-1.57$sudo make install**
                          *********************************END EXAMPLE*******************************
7)  After this gets done executing we are ALMOST ready to make the driver work on Ubuntu we need to find the folder where the .inf and .sys files are (for the WINDOWS XP drivers)...lets assume on the Thumb drive under a folder named XP...navigate to that folder.  Once there run the ndiswrapper -i driver.inf command.  Then run ndiswrapper -l command, you should see your driver
                         **********************************EXAMPLE************************************
                           *you@yourputer:/media/MYDRIVE$cd xp  *************
                         *you@yourputer:/media/MYDRIVE/xp$sudo ndiswrapper -i  bcmwlhigh5.inf*
                         *you@yourputer:/media/MYDRIVE/xp$ndiswrapper -l                         *
                           *********************************END EXAMPLE*******************************

8)  FINALLY you will complete this last step to load your driver.  Run the modprobe ndiswrapper command
                         **********************************EXAMPLE************************************
                            *you@yourputer:/media/MYDRIVE/xp$sudo modprobe ndiswrapper****
                            *********************************END EXAMPLE*******************************

After completing step 8 my USB Adapter started working and I had a list of networks to connect to, connected to my home network and immediately posted my solution here for you to see.  I hope this solution works for you, best of luck.

---

### Post by TB411 on 2012-05-13
Im using Ubuntu Studio 10.04 64-bit. Any of the commands listed above (as to installing ndiswrapper) gave me this error.
----------------------------------------------------------------

tb411@ubuntu:/media/MYDRIVE$ cd ndiswrapper-1.57
tb411@ubuntu:/media/MYDRIVE/ndiswrapper-1.57$ make uninstall
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/media/MYDRIVE/ndiswrapper-1.57/driver'
Makefile:36: *** Cannot find kernel version in /lib/modules/2.6.32-21-preempt/build, is it configured?.  Stop.
make[1]: Leaving directory `/media/MYDRIVE/ndiswrapper-1.57/driver'
make: *** [uninstall] Error 2
----------------------------------------------------------------

Please help with this error!

---

### Post by chili555 on 2012-05-13
Please see my PM. We need more information.

---

### Post by smartfreak17 on 2012-06-23
> **sifterr said:**
> Hello,

This is my first post regarding Linux, but I would like to confirm that the **AE2500 adapter works flawlessly on Ubuntu 11.04 (server only tested) and with WPA2**. I can not speak for the 64 bit processors but suspect it might work as I will explain in the steps I took below.

1. Used the drivers from the CD and the winXP version. You need to copy all the files not just the .inf in the XP folder. However, only copy over the ones WITHOUT '64' in them (or just64 have not tested 64 bit). Exclude any 'AE1200xp.sys' if present since we are only talking about the 2500.

2. Assuming ndiswrapper is installed run command:  sudo ndiswrapper -i bcmwlhigh5.inf   (or whichever is the inf file). YOU MAY GET AN ERROR about the AE1200 just ignore it.

3. Go to the forum below and start at step3
         -supplement the alternative mentioned in the forum with                   **cfg80211**
[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)


At this point the adapter should work with iwconfig etc. assuming no encryption is used.

Now to get it to work with WPA2 I found this forum by kevdog. It explains how to use and apply wpa_supplicant which will be needed.
                             [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

1. Command:  sudo apt-get install wpasupplicant 
2. Create a config file named wpa_supplicant.conf and place it directly in the    /etc/   directory
3. The contents of the config file are as followed with your modifications for essid and passphrase:

ctrl_interface=/var/run/wpa_supplicant  network={         ssid="ESSID_IN_QUOTES"         psk="place here ASCII PSK Password in Quotes"         key_mgmt=WPA-PSK         proto=RSN WPA         pairwise=CCMP TKIP         group=CCMP TKIP }


(I am using AES encryption but I did not change the TKIP.)

4. After placing the config file in the /etc directory run the following commands:
       Assumes your interface wlan0 and driver is wext (see wpa_supplicant -l).
       
      
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 

(open a new terminal alt+F2)
sudo dhclient wlan0

EVERYTHING SHOULD WORK FROM HERE
(you may return to termianl1 alt+F1 and use cntrl + d or cntrl +z to kill the sudo wpa_supplicant to avoid restart errors)


edit: after each restart the command: sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf    (as show above) will have to be ran again followed by     sudo dhclient wlan0   
If any one has a solution to this please post.
        
 5. That is what did it for me. I am not sure what it all meant but I hope it helps anyone else trying to get this working. Also thanks for the support in this thread and all the others. It really helps


Hi, i followed all the steps but ended up with the following error:

@ubuntu:~/Desktop/Driver$ sudo ndiswrapper -i bcmwlhigh6.inf 
installing bcmwlhigh6 ...
couldn't find models section "Cisco" -
installation may be incomplete


Can someone please help me out with this .....................

---

### Post by chili555 on 2012-06-23
> @ubuntu:~/Desktop/Driver$ sudo ndiswrapper -i bcmwlhigh6.inf
installing bcmwlhigh6 ...
couldn't find models section "Cisco" -
installation may be incompleteDid you use the files that came on the driver CD that came with your device...or...? Is yours a 64-bit system? Please run and post:```
arch
lsb_release -d
```

---

### Post by smartfreak17 on 2012-06-25
> **chili555 said:**
> Did you use the files that came on the driver CD that came with your device...or...? Is yours a 64-bit system? Please run and post:```
arch
lsb_release -d
```

$arch
x86_64
$lsb_release
No LSB modules are available

---

### Post by chili555 on 2012-06-25
> $lsb_release
No LSB modules are availableThat's not what I asked:```
lsb_release [COLOR="Red"]-d[/COLOR]
```Also, I asked:> Did you use the files that came on the driver CD that came with your device...or...?

---

### Post by smartfreak17 on 2012-06-25
> **chili555 said:**
> That's not what I asked:```
lsb_release [COLOR=Red]-d[/COLOR]
```Also, I asked:

yes I copied the files from the installation disc from the win7 folder   that had the .inf and .sys files. Actually i completely copied the win7   folder onto ubuntu desktop and named it Driver.

---

### Post by chili555 on 2012-06-25
ndiswrapper uses XP files, not Win 7. Please try again.

---

### Post by smartfreak17 on 2012-06-26
> **smartfreak17 said:**
> $arch
x86_64
$lsb_release
No LSB modules are available

$lsb_release -d
Description: Ubuntu12.04LTS

I tried copying the .inf and .sys files from the xp folder from the driver CD. When I do the following:

sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ....
could't find section:Linksys_AE1200.files.NTamd64" -
installation may be incomplete
could't find section:Linksys_AE2500.files.NTamd64" -
installation may be incomplete 
and when I do
$ndiswrapper -l
bcmwhigh4: invalid driver!

Is this got something to do with my processor ? as seen from the above message
"
Linksys_AE2500.files.NT_**amd64**_" - "

---

### Post by chili555 on 2012-06-26
> Is this got something to do with my processor ? as seen from the above message
"
Linksys_AE2500.files.NTamd64" - "You have a 64-bit install and need 64-bit .inf and .sys files. Were there several versions in the XP folder? What are they named? Did you erase the old incorrect installation?```
sudo ndiswrapper -e bcmwhigh4
```I'm a little confused because your earlier post referred to:> sudo ndiswrapper -i bcmwlhigh[COLOR="Red"]6[/COLOR].infIt's pretty important to be surgically precise here; it won't work otherwise.

---

### Post by smartfreak17 on 2012-06-26
> **chili555 said:**
> You have a 64-bit install and need 64-bit .inf and .sys files. Were there several versions in the XP folder? What are they named? Did you erase the old incorrect installation?```
sudo ndiswrapper -e bcmwhigh4
```I'm a little confused because your earlier post referred to:It's pretty important to be surgically precise here; it won't work otherwise.

sudo ndiswrapper -i bcmwlhigh[COLOR=Red]6[/COLOR].inf 			 		
The bcmwlhigh[COLOR=Red]6[/COLOR].inf 			 		 file I used here was from the Win7 Folder and NOT the XP one. Sorry about the confusion on this.

.sys files available in in the XP folder are:
AE2500xp.sys and AE2500xp64.sys

I copied all the files from the XP folder (except AE1200) but inspite of that it still did not work. AM I supposed to only copy the AE2500xp64.sys file, the bcmwlhigh5.inf and the .dll files ?

---

### Post by chili555 on 2012-06-26
> AM I supposed to only copy the AE2500xp64.sys file, the bcmwlhigh5.inf and the .dll files ?You probably don't want the .dlls. ndiswrapper sometimes works better if the 32-bit files are absent, so I'd copy over just the 64-bit parts. You might nuke the parts not working now:```
sudo rm -rf /etc/ndiswrapper/*
```Then install the 64-bit parts again.

Can you read the .inf file with a text editor? Does it mention amd64?

By the way, bcmwlhigh5.inf in 64-bit is hit and miss; many have tried and few have succeeded.

---

### Post by smartfreak17 on 2012-06-27
> **chili555 said:**
> You probably don't want the .dlls. ndiswrapper sometimes works better if the 32-bit files are absent, so I'd copy over just the 64-bit parts. You might nuke the parts not working now:```
sudo rm -rf /etc/ndiswrapper/*
```Then install the 64-bit parts again.

Can you read the .inf file with a text editor? Does it mention amd64?

By the way, bcmwlhigh5.inf in 64-bit is hit and miss; many have tried and few have succeeded.

Well, I nuked all the 32 bit ones and reinstalled the driver again but still get the following:

sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ....
could't find section:Linksys_AE1200.files.NTamd64" -
installation may be incomplete
could't find section:Linksys_AE2500.files.NTamd64" -
installation may be incomplete 

$ndiswrapper -l
bcmwhigh5: invalid driver!

I checked the .inf file in a text editor it has  "Linksys_AE2500.files.NTamd64" in there, dont why its not working. The  files I copied from the Driver CD are:
1) AE2500xp64.sys
2) bcmwlhigh5.inf
3) bcmh43xx64.cat

---

### Post by chili555 on 2012-06-27
You might try this file. I have no idea if it will work as I don't have the device. It may be the same as yours. Also, just to be very careful, I'd probably also include the AE1200xp64.sys file in the folder as well, since it's referenced in the .inf file. 

bcmwlhigh5.inf on 64-bit is right up there with CSS and ffmpeg in terms of being a black art. I'd rather invent time travel!

---

### Post by smartfreak17 on 2012-06-28
> **chili555 said:**
> You might try this file. I have no idea if it will work as I don't have the device. It may be the same as yours. Also, just to be very careful, I'd probably also include the AE1200xp64.sys file in the folder as well, since it's referenced in the .inf file. 

bcmwlhigh5.inf on 64-bit is right up there with CSS and ffmpeg in terms of being a black art. I'd rather invent time travel!

Well I still get the same invalid driver error and installation may be incomplete. Looks like there is no way around this. I did include the AE1200xp64.sys file ........:(

---

### Post by chili555 on 2012-06-28
> Looks like there is no way around this.A 32-bit install or a fully supported out-of-the-box adapter, perhaps?

---

### Post by Ankersman on 2012-07-19
This link helped a lot:

[http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/](http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/)

follow it to the letter and you should get it going.

---

### Post by Jwpe on 2012-08-01
Just wanted to say thanks to those in this thread who have provided such helpful and comprehensive suggestions for getting Linksys USB adapters up and running. 

I am now able to connect to my network using my Linksys AE1200 on Ubuntu 11.10 64-bit.

I successfully modified the .inf file to use the x64 .sys files and used ndiswrapper 1.57 in order to get the hardware to be recognised. 

Unfortunately the connection, while established, doesn't seem to want to carry traffic. I can't visit any pages in-browser and ping google produces "unknown host". Not sure if there is an effective way of improving connection quality. Does anyone have any suggestions? Are there any configuration settings I could change to improve connection quality?

Thanks very much!

---

### Post by chili555 on 2012-08-01
>  Does anyone have any suggestions? Are there any configuration settings I could change to improve connection quality?Please start a new thread and post:```
iwconfig
ifconfig
ping -c3 74.125.131.99
ping -c3 192.168.1.1  [COLOR="Red"]<--or whatever your router/gateway address is[/COLOR]
```Send me a private message with the link. Thanks.

---

### Post by ccb147 on 2012-11-25
hi all,

running 12.04 (32-bit)

trying to install linksys ae2500 and read through some posts but not sure what to start with...should I try installing ndiswrapper?

---

### Post by chili555 on 2012-11-25
> **ccb147 said:**
> hi all,

running 12.04 (32-bit)

trying to install linksys ae2500 and read through some posts but not sure what to start with...should I try installing ndiswrapper?Yes and post back with:```
lsusb
```Thanks.

---

### Post by ccb147 on 2012-11-26
lsusb produces:

13b1:003a

---

### Post by chili555 on 2012-11-26
On your 32-bit system, I think this is all you need. As you can see by the length of this thread, it's all a bit experimental, so we may get a correctable error the first time through. Please download this file to your desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo ndiswrapper -i Desktop/xp32/bcmwlhigh5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```If it is not working, post:```
dmesg | grep ndis
```

---

### Post by ccb147 on 2012-11-26
ndiswrapper: command not found
FATAL: Module ndiswrapper not found



EDIT: also, I typed dmesg | grep ndis and got nothing as far as a response. Do I need to blacklist anything before I install?

---

### Post by chili555 on 2012-11-26
> **ccb147 said:**
> ndiswrapper: command not found
FATAL: Module ndiswrapper not found



EDIT: also, I typed dmesg | grep ndis and got nothing as far as a response. Do I need to blacklist anything before I install?Did you install ndiswrapper? Any errors?```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
sudo modprobe ndiswrapper
```

---

### Post by ccb147 on 2012-11-26
okay,  I did the sudo reinstall followed by the commands you gave me with the .zip file, below is the terminal output:


patricia@Patricia:~$ sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot
The following NEW packages will be installed:
  dkms fakeroot ndiswrapper-dkms
0 upgraded, 3 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 364 kB of archives.
After this operation, 1,434 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
patricia@Patricia:~$ sudo ndiswrapper -i Desktop/xp32/bcmwlhigh5.inf
installing bcmwlhigh5 ...
couldn't find "AE1200xp.sys" in "Desktop/xp32"; make sure all driver files, including .inf, .sys (and any firmware files) are in "Desktop/xp32" -
installation may be incomplete
patricia@Patricia:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper.conf ...
patricia@Patricia:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2012-11-26
> After this operation, 1,434 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
[COLOR="Red"]Abort[/COLOR].So it didn't, for whatever reason, actually install anything! Let's try a different approach.```
sudo apt-get install -y dkms fakeroot ndiswrapper-dkms
```Now, let's refine our driver package:```
sudo ndiswrapper -e bcmwlhigh5
```Remove the xp32 folder and zip from your desktop and try this one using the same process as above.

[https://dl.dropbox.com/u/58267392/xp32.zip](https://dl.dropbox.com/u/58267392/xp32.zip)

I uploaded to Dropbox because the size, after adding AE1200xp.sys, exceeds the size that can be uploaded directly through the forum.

---

### Post by ccb147 on 2012-11-27
Okay, so I followed  your instructions and as terminal finished executing a window popped up and asked me for the wireless password.  I typed the password in and waited, and waited, and waited.  Then it asked me again for the password--ad infinitum.

---

### Post by chili555 on 2012-11-27
Well, we're getting closer! Let's see what the logs say:```
cat /var/log/syslog | grep -e ndis -e etwork | tail -n20
```Please be sure the ethernet is disconnected as you try to connect.

---

### Post by ccb147 on 2012-11-28
wpa_supplicant[2059]: Trying to associate with 11:11:11:11:11:11 (SSID='zzzzz' freq=2437 MHz)
NetworkManager[762]: <warn> Activation (wlan0) failed for access point (zzzzz)


The 11:11:11:11:11:11 is not the correct output, I used x's initially but that gave me a bunch of smiley faces

---

### Post by chili555 on 2012-11-28
Did you type or copy and paste the command exactly as requested, including the pipe symbols | ??

As an example, on my systsem, it shows:> Nov 28 16:06:59 LAPTOP410 NetworkManager[999]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 16:06:59 LAPTOP410 NetworkManager[999]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 16:07:00 LAPTOP410 NetworkManager[999]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 16:07:00 LAPTOP410 NetworkManager[999]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Nov 28 16:07:00 LAPTOP410 NetworkManager[999]: <info> Policy set 'GBR1' (wlan0) as default for IPv4 routing and DNS.
Nov 28 16:07:00 LAPTOP410 NetworkManager[999]: <info> Activation (wlan0) successful, device activated.
Nov 28 16:07:00 LAPTOP410 N[COLOR="Red"]etwork[/COLOR]Manager[999]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
<snip>

---

### Post by ccb147 on 2012-11-28
[B]note: I changed your code from *etwork to *network in your previous post

[/B]here was the output after a reboot:

                                  patricia@Patricia:~$ cat /var/log/syslog | grep -e ndis -e network | tail -n20  
 Nov 28 16:41:44 Patricia kernel: [   16.598242] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95ae280, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598244] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95b2100, 16000, 4  
 Nov 28 16:41:44 Patricia kernel: [   16.598246] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95b5f80, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598249] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95b9e00, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598251] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95bdc80, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598253] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95c1b00, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598255] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95c5980, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598257] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95c9800, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.598259] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f95cd680, 16000, 5  
 Nov 28 16:41:44 Patricia kernel: [   16.614912] ndiswrapper (ndis_encode_setting:383): unknown type: 3  
 Nov 28 16:41:44 Patricia kernel: [   16.906674] usbcore: registered new interface driver ndiswrapper  
 Nov 28 16:41:44 Patricia NetworkManager[799]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)  
 Nov 28 16:41:50 Patricia NetworkManager[799]: <info> Config: added 'ssid' value 'zzzzz'  
 Nov 28 16:41:55 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)  
 Nov 28 16:42:11 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)  
 Nov 28 16:42:27 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)  
 Nov 28 16:42:42 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)  
 Nov 28 16:43:20 Patricia NetworkManager[799]: <info> Config: added 'ssid' value 'zzzzz'  
 Nov 28 16:43:25 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)  
 Nov 28 16:43:41 Patricia wpa_supplicant[1144]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)








Here is the output after a reboot with ethernet wired in:


patricia@Patricia:~$ cat /var/log/syslog | grep -e ndis -e network | tail -n20
Nov 28 16:50:42 Patricia kernel: [   16.645169] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94dbe00, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.645171] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94dfc80, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.645173] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94e3b00, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.645175] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94e7980, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.645177] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94eb800, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.645180] ndiswrapper (MmBuildMdlForNonPagedPool:1864): f94ef680, 16000, 5
Nov 28 16:50:42 Patricia kernel: [   16.661722] ndiswrapper (ndis_encode_setting:383): unknown type: 3
Nov 28 16:50:42 Patricia kernel: [   16.940701] usbcore: registered new interface driver ndiswrapper
Nov 28 16:50:42 Patricia NetworkManager[789]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Nov 28 16:50:48 Patricia NetworkManager[789]: <info> Config: added 'ssid' value 'zzzzz'
Nov 28 16:50:53 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:51:09 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:51:22 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:51:38 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:51:54 Patricia NetworkManager[789]: <info> Config: added 'ssid' value 'zzzzz'
Nov 28 16:51:59 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:52:14 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:52:30 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:52:46 Patricia wpa_supplicant[1018]: Trying to associate with 00:1e:e5:56:6a:84 (SSID='zzzzz' freq=2437 MHz)
Nov 28 16:54:54 Patricia NetworkManager[789]: <warn> Activation (wlan0) failed for access point (zzzzz)

---

### Post by ccb147 on 2012-11-30
bump

---

### Post by ccb147 on 2012-12-12
can anybody help?  Chili has almost made it work...just need to make the machine actually connect to the router instead of continuously searching for it!!

---

### Post by Dravenm4 on 2012-12-24
I have been successful in connecting to my router but only at 2.4Ghz and only in Wirless G also unable to config the wireless access for any encryption other then WEP

---

### Post by Dravenm4 on 2012-12-24
dravenm4@Draven-Alpha:~$ cat /var/log/syslog | grep -e ndis -e network | tail -n20
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073446] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124c6e80, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073448] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124cad00, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073450] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124ceb80, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073452] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124d2a00, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073453] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124d6880, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073455] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124da700, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073457] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124de580, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073458] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124e2400, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073460] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124e6280, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073461] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124ea100, 16000, 4
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073463] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124edf80, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073465] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124f1e00, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073466] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124f5c80, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073468] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124f9b00, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073470] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900124fd980, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073472] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012501800, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.073474] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012505680, 16000, 5
Dec 24 01:01:11 Draven-Alpha kernel: [   14.091411] ndiswrapper (ndis_encode_setting:383): unknown type: 3
Dec 24 01:01:11 Draven-Alpha kernel: [   14.370583] usbcore: registered new interface driver ndiswrapper
Dec 24 01:01:11 Draven-Alpha NetworkManager[874]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)



Just my 2 cents

---

### Post by chili555 on 2012-12-24
I'm fairly confident that the result of this error:> ndiswrapper (ndis_encode_setting:383): unknown type: 3...is this symptom:> unable to config the wireless access for any encryption other then WEP You may wish to try compiling ndiswrapper's latest version and then, if that doesn't help, try to find and install a later, better (??) Windows XP .inf and .sys file package. 

Would you like additional assistance with these steps?

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

---

### Post by Dravenm4 on 2012-12-24
Well I did recompile Ndiswrapper to the latest package availible 1.58rc1. But what did you mean by the latest xp .ini? I used the one off the disk and the one off the site I modified the .ini file to reflect the extra lines


[Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6

I am interested in any help you will throw at me..


And Happy Holidays

---

### Post by Dravenm4 on 2012-12-24
dravenm4@Draven-Alpha:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.2.0-35-generic/misc/ndiswrapper.ko
version:        1.58rc1
vermagic:       3.2.0-35-generic SMP mod_unload modversions 
dravenm4@Draven-Alpha:~$

---

### Post by chili555 on 2012-12-24
>  But what did you mean by the latest xp .ini? I used the one off the disk and the one off the site I modified the .ini file to reflect the extra linesWere there various versions on the disk? XP, Vista, 7, et al? You need XP. As well, you need the version matching your architecture; i.e. x86 or x86_64.

64-bit is often a bit tricky.

---

### Post by Dravenm4 on 2012-12-24
> **chili555 said:**
> Were there various versions on the disk? XP, Vista, 7, et al? You need XP. As well, you need the version matching your architecture; i.e. x86 or x86_64.

64-bit is often a bit tricky.

Yeah the disk had xp, vista, and win7... I only use XP cause thats what NDISWrapper works with. And I am 64 bit Ubuntu I removed the none 64bit files from the folder when installing.

---

### Post by Dravenm4 on 2013-01-08
Is there no further info?

---

### Post by praseodym on 2013-01-08
Please check:

```
impriv wlan0
```
You may need to change the router mode to b+g only instead of n

---

### Post by vedasenko on 2013-02-23
Massive thanks to Wojosama (post #79), I can confirm that following those steps, Ubuntu 12.04, 64bit I was able to get the AE2500 wifi adapter running. Has anyone been able to get it to connect to a N router (post #58)?

---

### Post by Sea Monkey on 2013-04-28
> **Wojosama said:**
> I just want to say thank you to everyone who contributed to this discussion, the xp driver worked with no problems using ndiswrapper on 32bit, but when I switched to 64bit I entered a world of hurt. 

However, thankfully, I can confirm the Linksys AE1200 working on 64bit ubuntu 11.10 on 802.11g. The AE1200 and AE2500 share the same drivers, so both should work fine. I can't speak on 802.11N connectivity as I don't have an N router to test it with, sorry. A lot of this will be similar to Fat-n00b's info in post #40 but with all the stuff I had to do extra to make it work on 64bit. 

Before you start, I have not added/modified/deleted anything relating to networking or any other hardware drivers(modules) since I did the clean install of 11.10 x64.
These are the steps I took (pretty much all found here and pieced together):

**NOTE: THE FILES YOU DELETE IN STEP 3B ARE THE 32BIT DRIVERS. THESE INSTRUCTIONS ARE FOR 64BIT ONLY FOR THAT REASON.**
[B]NOTE 2: IF YOU HAVEN'T DONE ANY WORK TO INSTALL THESE DRIVERS WITH NDISWRAPPER YOU CAN SKIP STEP 1.
[/B]
**1.** First remove all prior work with this (replace bcmwlhigh5 with bcmwlhigh6 if you tried installing vista or win7 drivers):

```

sudo ndiswrapper -e bcmwlhigh5
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -rf /etc/ndiswrapper/*
sudo depmod -a

```I would restart the computer now just to be safe.

**2.** Next, I had to build version 1.57 of ndiswrapper as the one in the ubuntu repositories didnt work, instructions for removing your current version and downloading/building/installing the new version can be found here: [HTML]http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113[/HTML]**3a.** After that is done, you must make sure you've got the right files in the folder with the winxp inf file.
Download the XP driver here if you need it (You MUST use the windows xp drivers): [HTML]http://homedownloads.cisco.com/downloads/driver/1224667593495/AE1200xp.zip[/HTML]**3b.** Extract those to an easy place to find them. After you extract them, **delete the following files** from the folder (probably unnecessary but do it just in case): AE1200xp.sys, AE2500xp.sys, bcmh43xx.cat, bcmwlcoi.dll

**4.** Now you need to add the following lines to bcmwlhigh5.inf:
Open in a text editor and put the cursor at the begining of line 178 and paste these lines:
```
 

[Linksys_AE1200.files.NTamd64] 
    AE1200xp64.sys,,,6 
 
[Linksys_AE2500.files.NTamd64] 
    AE2500xp64.sys,,,6 


```                            Adding "amd64" after "NT" on lines 76, 83, 87 and 94                      is NOT necessary, it would just try to make the inf use the 32bit versions of the .sys files which doesn't work (and I've had you delete those files just in case you did amend those lines).
[B]
5.[/B] Blacklist other bcm modules to keep them from loading
```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```[B]
6.[/B] Time to install! Finally, I know.
Here's the commands (**PLEASE READ THE NOTES BELOW FIRST**):
```

sudo ndiswrapper -i /home/adam/Desktop/XP/bcmwlhigh5.inf   **CHANGE TO YOUR LOCATION**
sudo ndiswrapper -m -ma -mi
sudo depmod -a
sudo modprobe ndiswrapper

```A few notes on the code you'll enter (or did enter if you didn't read ahead first :p); 
First you can either  direct ndiswrapper to your inf file (as i did), or you can cd to the  folder it's in and just do 'sudo ndiswrapper -i bcmwlhigh5.inf'  
Second is that I don't know if everything in the second command is  necessary but it DOES work, they are exactly what I used.
Lastly, and this is VERY important, the moment I typed in the 'sudo depmod -a' and hit enter, my computer completely froze and I had to hit the restart button on the tower, however when it rebooted, voila! I could see my wireless adapter for the first time since I installed 64bit, and I could connect to my wireless network!

Two final things about connecting to your router (which I had to do on 32bit and am guessing would've had to do on 64bit as well had i not already done it): 
1. If your router is set to NOT broadcast SSID you will probably not be able to connect to it. I had to set it to broadcast in the end as nothing i did worked, and i tried a LOT of stuff lol. 
2. If you are using WPA, in my case WPA2 - PSK, I had to change my password as for some reason it just would not connect, I ended up using one generated from here: [HTML]http://www.yellowpipe.com/yis/tools/WPA_key/generator.php[/HTML]After setting the new wpa password, I was able to connect without any problem. Keep in mind, I had 2 phones, and 3 other computers connected to it all using the old password but it just would not work with the ubuntu+ndiswrapper combo until I used the one I generated, so if using WPA, and you can't connect, try one from the generator before you give up on WPA.
MAC address filtering enabled on the router was obviously unaffected through all of this, so setting SSID to broadcast was the only layer of security I had to sacrifice.

Sorry for the MASSIVE post. I just can't thank everyone here enough, and if this keeps even one person from wasting their entire weekend like I just did, then making this post was well worth it. I know the last post is a couple days old but if I googled my here, someone else will as well. If there's somewhere else that it would be helpful for me to post this info I'd appreciate it if anyone would let me know. I've only used Ubuntu for a very, very short time, but I've been helped countless times by posters like you guys, so if i contribute back in any way, then I'd really like to.
(P.S. Longest first post ever? lol)

Thank you so much!  The only additional thing i had to do was to add ndiswrapper to /etc/modules so it runs on startup.

---

### Post by mjalberts13 on 2013-12-06
Thank you good sir!(Wojosama (post #79)) I followed those steps and I am currently posting this via wireless connection :D.

---

### Post by max30 on 2014-01-28
What does this line do? "[COLOR=#000000][FONT=Ubuntu Mono]echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]"
[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]and how would I undo it? I've tried a tutorial that is pretty much like yours, but still couldn't my AE2500 to show up in Network settings. So I bought a new PCI wireless card--still waiting for it to arrive--and I'm afraid that line could give me problems in installing the new wireless card. I don't really know if this helps, but I'm running Elementary OS Luna. I'm super new to Linux.

Thanks in advance

---

### Post by chili555 on 2014-01-28
> **max30 said:**
> What does this line do? "[COLOR=#000000][FONT=Ubuntu Mono]echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]"
[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]and how would I undo it? I've tried a tutorial that is pretty much like yours, but still couldn't my AE2500 to show up in Network settings. So I bought a new PCI wireless card--still waiting for it to arrive--and I'm afraid that line could give me problems in installing the new wireless card. I don't really know if this helps, but I'm running Elementary OS Luna. I'm super new to Linux.

Thanks in advanceIt blacklists a number of Broadcom drivers typically associated with laptop wireless cards. I doubt it will affect your PCI card, but if you think it will, merely do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines:```
blacklist bcmn43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```All the previous lines remain untouched. Save and close gedit and you are all set!

---

### Post by max30 on 2014-01-29
Thanks, Chili

---

### Post by goldentoa11 on 2014-03-12
Hi all,

I have the Linksys N600 USB adapter, which I believe is the same as the AE2500. When I run `lsusb`, I get

```
Bus 002 Device 006: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]
```

I've gotten ndiswrapper 1.59 to run the XP driver for 64bit and here are the steps I used.

1) Get the source to ndiswrapper (I used 1.59. [Download]("http://sourceforge.net/projects/ndiswrapper/"))
2) Compile and install ndisrapper
3) [Download]("http://downloads.linksys.com/downloads/driver/AE2500xp_WHQL,0.zip") the Windows XP driver for the AE2500
4) Extract the zip archive you just downloaded

*Note: Here is that part that you have to edit. The driver for 64x does not work by default, because the inf file omitted necessary configurations for the 64x files. Essentially, what happens is the INF file says to use files that are listed later, but then those files are never listed, so we need to add those files in to the INF.*

5) Open "bcmwlhigh5.inf" in gedit and add this line, around line 170:

```
[Linksys_AE2500.files.NTamd64]
  AE2500xp64.sys,,,6

```

6) Run this command: `ndiswrapper -i bcmwlhigh5.inf`

At this point, the driver should be installed successfully. `ndiswrapper -l` should return

```

bcmwlhigh5 : driver installed
    device (13B1:003A) present

```

7) Blacklist the default BCM42xx drivers by adding

```
#blacklist the bcm43xx drivers
blacklist bcm43xx
blacklist bcm43
blacklist bcm43legacy
blacklist ssb

```
to `/etc/modprobe.d/blacklist.conf`

8) run `depmod -a`

9) At this point, either use modprobe to load ndiswrapper into memory (didn't work for me; it just hung and did nothing) or restart your computer (after I restarted, I could see my wireless networks)

At this point, I am successfully using the WinXP 64x drivers in Ubuntu 13.04 x86_64. Kernel is 3.8 generic.

---

### Post by SEALBoy on 2014-07-17
> **goldentoa11 said:**
> Hi all,

I have the Linksys N600 USB adapter, which I believe is the same as the AE2500. When I run `lsusb`, I get

```
Bus 002 Device 006: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]
```

I've gotten ndiswrapper 1.59 to run the XP driver for 64bit and here are the steps I used.

1) Get the source to ndiswrapper (I used 1.59. [Download]("http://sourceforge.net/projects/ndiswrapper/"))
2) Compile and install ndisrapper
3) [Download]("http://downloads.linksys.com/downloads/driver/AE2500xp_WHQL,0.zip") the Windows XP driver for the AE2500
4) Extract the zip archive you just downloaded

*Note: Here is that part that you have to edit. The driver for 64x does not work by default, because the inf file omitted necessary configurations for the 64x files. Essentially, what happens is the INF file says to use files that are listed later, but then those files are never listed, so we need to add those files in to the INF.*

5) Open "bcmwlhigh5.inf" in gedit and add this line, around line 170:

```
[Linksys_AE2500.files.NTamd64]
  AE2500xp64.sys,,,6

```

6) Run this command: `ndiswrapper -i bcmwlhigh5.inf`

At this point, the driver should be installed successfully. `ndiswrapper -l` should return

```

bcmwlhigh5 : driver installed
    device (13B1:003A) present

```

7) Blacklist the default BCM42xx drivers by adding

```
#blacklist the bcm43xx drivers
blacklist bcm43xx
blacklist bcm43
blacklist bcm43legacy
blacklist ssb

```
to `/etc/modprobe.d/blacklist.conf`

8) run `depmod -a`

9) At this point, either use modprobe to load ndiswrapper into memory (didn't work for me; it just hung and did nothing) or restart your computer (after I restarted, I could see my wireless networks)

At this point, I am successfully using the WinXP 64x drivers in Ubuntu 13.04 x86_64. Kernel is 3.8 generic.

Ok I basically did what you said for my laptop but it isn't quite working yet. I have an onboard wifi adapter (Intel Corporation Centrino Wireless-N 1000). When I toggle it off using my hardware switch it will disable the AE2500 as well. Is there a way I can disable it in Ubuntu without disabling the AE2500. My AE2500 has the light on but is not seeing any networks.

Very new Ubuntu user so please be patient. Thank you.

---

### Post by chili555 on 2014-07-18
> **SEALBoy said:**
> Ok I basically did what you said for my laptop but it isn't quite working yet. I have an onboard wifi adapter (Intel Corporation Centrino Wireless-N 1000). When I toggle it off using my hardware switch it will disable the AE2500 as well. Is there a way I can disable it in Ubuntu without disabling the AE2500. My AE2500 has the light on but is not seeing any networks.

Very new Ubuntu user so please be patient. Thank you.Would you start a new thread and leave the link here. This is getting pretty old and long. Thanks.

---

### Post by oldos2er on 2014-07-18
Old thread closed.

---

