---
title: "wi-fi usb sitecom n150 (device 0df6:006b) installation guide needed.."
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by meditya on 2013-05-04
Hi,


I am a newbie, who's trying to migrate from windows to ubuntu 13.04.
However, i cannot get my wireless usb stick ([sitecom n150]("http://www.sitecom.com/en/wi-fi-usb-adapter-n150/wla-1100/p/1561")) runs properly.

I have tried to follow the installation guide, and successfully installed the driver to my desktop (i check via the command "ndiswrapper -l" and get the response "net8192su: driver installed and device (0df6:006b) present".
However when i typed "iwconfig" the following response appears "eth0 no wireless extensions; lo no wireless extensions"

I tried also the command [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -e ndis -e wlan [/FONT][/COLOR]and there are about more than 20 lines indicate the "unknown symbol" error message, following the 
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) suggestion, i re-do the wireless installation file (net8192.inf) several times (using the file from different os folder (e.g. windowsxp64, windows764, windows2k).  Additional info, I use the producer's cd as the installation source file (inf) and I am installing ubuntu 13.04 64 bit on my desktop.

Is there anyone can help me with this problem? 


Thanks,
mdty

---

### Post by gordintoronto on 2013-05-04
Have you reviewed this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by meditya on 2013-05-05
hi ok i am trying tried to follow the guide ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) one by one..

i am on the step 2 now.. since i dont have internet connection on my ubuntu desktop (only wireless usb adapter, no internet's available in the house) i follow the guide number *"2.1.3. installing (ndisgtk) packages without internet access".  However the refered url *[https://help.ubuntu.com/starterguide/C/ch02.html](https://help.ubuntu.com/starterguide/C/ch02.html) is dead.  

Do how can i install the ndisgtk package to my desktop.  i am using pendrive to install the ubuntu btw.

---

### Post by gordintoronto on 2013-05-05
If you have the package, double-click on it to install it.

---

### Post by meditya on 2013-05-06
hi i've downloaded the NDISGTK package via [http://packages.ubuntu.com/raring/amd64/ndisgtk/download](http://packages.ubuntu.com/raring/amd64/ndisgtk/download) and installed the package into my desktop.

folowing the guide ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) i then stepped into the guide number 3.1, disable free drivers..
for this i've also followed the sugestion in the youtube video [https://www.youtube.com/watch?v=hBZa17yvl7o](https://www.youtube.com/watch?v=hBZa17yvl7o) and typed
"sudo gedit /etc/modprobe.d/blacklist"
then i blacklisted several devices:
"blacklist bcm43xx"
"blacklist bcm57xx" (i checked it via [COLOR=#333333][FONT=UbuntuMono]lspci -vvnn | grep 14e4)
[/FONT][/COLOR]"blacklist b43"
"blacklist 43legacy"
"blacklist ssb"
"blacklist rt2500usb"
then i restarted my machine

next i follow the guide number 3.3 (installing windows driver via command line), and so on..
and again when i reached step number 3.4 (load the new driver module) and typed "iwconfig", the screen said "eth0 - no wireless extensions and lo no wireless extensions).

any idea how can i solve this stuff..?

---

### Post by meditya on 2013-05-08
Is there anyone here who can really help me with the problem :confused:

---

### Post by chili555 on 2013-05-08
ndiswrapper always requires XP files. It also requires that the files match your architecture; either 32- or 64-bit. > I am installing ubuntu 13.04 [COLOR="#FF0000"]64 bit[/COLOR] on my desktop.
Here you are.

Next, we need to look at the error messages you are getting in dmesg. Can you please copy and paste from the terminal to a text file, transfer it on a USB stick and post it here:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by meditya on 2013-05-09
thanks much chili555.. 
now i find my high hope again.. :guitar:


As you suggested, i have unistalled the existing driver and reinstall the windows xp64 drivers,
then i typed "dmesg | grep ndis" the error messages (complete) looks like this..

____________________________________________________________________________________________________ m@ubuntU:~$ ndiswrapper -l
net8192su : driver installed
	device (0DF6:006B) present
[EMAIL="m@ubuntU:~$"]m@ubuntU:~$[/EMAIL] sudo ndiswrapper -r net8192su
[sudo] password for m: 
[EMAIL="m@ubuntU:~$"]m@ubuntU:~$[/EMAIL] ndiswrapper -l
[EMAIL="m@ubuntU:~$"]m@ubuntU:~$[/EMAIL] cd /home/m/Desktop/Drivers/WinX64
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] ndiswrapper -i net8192su.inf
couldn't create /etc/ndiswrapper/net8192su: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] sudo ndiswrapper -i net8192su.inf
installing net8192su ...
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] iwconfig
eth0      no wireless extensions.
lo        no wireless extensions.
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] sudo ndiswrapper -l
net8192su : driver installed
	device (0DF6:006B) present
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] sudo ndiswrapper -a net8192su.inf for 0Df6:006B
install/manage Windows drivers for ndiswrapper
usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information
where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] sudo modprobe ndiswrapper
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] dmesg| grep ndis
[   16.342345] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   17.333154] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   17.333163] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   17.333170] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   17.333175] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   17.333180] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   17.333185] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   17.333189] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   17.333194] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   17.333218] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   17.333222] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   17.333234] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   17.333238] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   17.333245] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   17.333254] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   17.333258] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   17.333263] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   17.333268] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   17.333276] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   17.333280] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   17.333285] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   17.333290] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   17.333294] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   17.333298] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   17.333301] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   17.333305] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   17.333307] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net8192su'
[   17.333388] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net8192su'
[   17.333450] usbcore: registered new interface driver ndiswrapper
[EMAIL="m@ubuntU:~/Desktop/Drivers/WinX64$"]m@ubuntU:~/Desktop/Drivers/WinX64$[/EMAIL] 
____________________________________________________________________________________________________

thanks once again :)

---

### Post by chili555 on 2013-05-09
I am not at all sure this is ever going to work in 64-bit. We have 64-bit inf and sys files and they are clearly marked for XP and include your device; here are some greps:> chili@Think410:~$ cat sitecom/drivers-and-utility-windows/88_91_92_SU_Driver/WinX64/net8192su.inf | grep XP
;; Windows 2000/[COLOR="#FF0000"]XP[/COLOR]
;; Windows 2000/[COLOR="#FF0000"]XP[/COLOR] parameters
chili@Think410:~$ cat sitecom/drivers-and-utility-windows/88_91_92_SU_Driver/WinX64/net8192su.inf | grep 006B
%WL-1100.DeviceDesc% = RTL8192su.ndi, USB\VID_0DF6&PID_006B
%WL-1100.DeviceDesc% = RTL8192su.ndi, USB\VID_[COLOR="#FF0000"]0DF6[/COLOR]&PID_[COLOR="#FF0000"]006B[/COLOR]
Just on a wild hunch, please try these after removing the older files:```
sudo ndiswrapper -e net8192su
sudo rm -rf /etc/ndiswrapper/*
```Then extract and install these as before and then give us the same diagnostics.

---

### Post by meditya on 2013-05-09
hi, thanks for the reply, 
i think we're getting somewhere, although...

as suggested, this is the terminal record
_____________________________________________________________________
[EMAIL="m@UbuntU:~$"]m@UbuntU:~$[/EMAIL] ndiswrapper -l
net8192su : driver installed
 
m@UbuntU:~$ sudo ndiswrapper -e net8192su
[sudo] password for m:
 
m@UbuntU:~$ ndiswrapper -l
 
m@UbuntU:~$ sudo rm -rf /etc/ndiswrapper/*
 
m@UbuntU:~$ lsusb
Bus 001 Device 003: ID 0df6:006b Sitecom Europe B.V.
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
m@UbuntU:~$ cd /home/m/Desktop/Drivers/WinX64
 
m@UbuntU:~/Desktop/Drivers/WinX64$ sudo ndiswrapper -i net8192su.inf
installing net8192su ...
 
m@UbuntU:~/Desktop/Drivers/WinX64$ sudo ndiswrapper -l
net8192su : driver installed
            device (0DF6:006B) present
 
m@UbuntU:~/Desktop/Drivers/WinX64$ dmesg|grep ndis
[  196.352588] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  196.391782] usbcore: registered new interface driver ndiswrapper
 
m@UbuntU:~/Desktop/Drivers/WinX64$ iwconfig
eth0      no wireless extensions.
lo        no wireless extensions.
_____________________________________________________________________

#... although the installation seemed successful, when i restart the desktop i cannot get in to ubuntu.  Black "error" screen was blocking me in.  The error message is like (the typing may be inaccurate):
[ 73.244972] BUG: unable to handle kernel pagisng request at ffffffffa03e56a8
[ 73.245014] IP: [<fffffa03d0f13>] object_signaled*0x53/0x90 [ndiswrapper]
and so on until
[ 73.258393] drm_kms_helper: panic occured, switching back to text console..

to get in, i have to unplug my wi-fi usb... 
if i plug the wi-fi usb in the middle of ubuntu session, the error message will appear again and will block everything.. 

any suggestion? thanks before..

---

### Post by praseodym on 2013-05-10
Hi,

this device works, if you add the ID to the driver:

[http://forum.ubuntuusers.de/post/5600242/](http://forum.ubuntuusers.de/post/5600242/)

To make it permanent, set up an udev-rule (bottom of that thread)

---

### Post by chili555 on 2013-05-10
> m@UbuntU:~/Desktop/Drivers/[COLOR="#FF0000"]WinX64[/COLOR]$ sudo ndiswrapper -l
net8192su : driver installed
device (0DF6:006B) presentIn my post above, I suggested you try and even attached WinXP drivers; i.e.32-bit, instead of WinX64. Please try again.

---

### Post by meditya on 2013-05-11
Hi All,


Great news, I'am now browsing via my Sitecom N150 WiFi Adapter..

to praseodym:  I followed your suggestion, and indeed the discussion at ([http://forum.ubuntuusers.de/post/5600242/](http://forum.ubuntuusers.de/post/5600242/)) discusses the same issue.  I followed the advises and now the issue is solved.  Thanks!!!
to chili555:  I tried also to install the 32 bit installer, but the 32bit driver had some kernel problem with the 64 bit ubuntu.  Nevertheless, thanks for your advises.
to gordintoronto:  Thanks for replying the issue at the beginning of this forum.

So I believe the installation for Sitecom N150 WiFi adapter in Ubuntu 13.04 is no longer an issue now, the discussion at [http://forum.ubuntuusers.de/post/5600242/](http://forum.ubuntuusers.de/post/5600242/) stands as a good reference.


Cheers,
:popcorn:

---

