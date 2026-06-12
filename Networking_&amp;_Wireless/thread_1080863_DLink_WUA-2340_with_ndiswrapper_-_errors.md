---
title: "DLink WUA-2340 with ndiswrapper - errors"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by vuroth on 2009-02-25
Following this guide:  [http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html)
I have installed ndiswrapper (latest version from sourceforge), and unzipped the driver from dlink.  Unfortunately, that gave me a setup executable, and ndiswrapper gives errors now.  Something like

> ndiswrapper version 1.54 loaded (blah)
ndis warapper (import:142): unkown symbol: ntoskrnl.exe: 'KeNumberProcessors'
ndisprawwper (load_sys_files:206) couldn't prepare driver neta5agu
ndiswrapper (load_wrap_driver:108) couldn't load driver neta5agu; check system log for messages from loadndisdriver

Is this something simple like I need to run the setup on a windows machine, then copy the files over to mythbuntu and retry the ndiswrapper install?

---

### Post by vuroth on 2009-02-25
Hmm installing on windows may not be the answer, as it installed a Win64 version.  I'm only running 32-bit mythbuntu :(

---

### Post by vuroth on 2009-02-25
Ok here's the solution.

Install on a 32 bit windows install.

Copy the Drivers directory to the linux machine
copy the .inf from the CD/install zip, from the WinXP/2K directory, to the same Drivers directory

sudo ndiswrapper -i netA5AGU.inf

Now I have a wlan0 entry in iwconfig.  :)

---

### Post by ApogeeSurfer on 2009-05-29
The dmesg error "ndiswrapper (import:242): unkown symbol: ntoskrnl.exe: 'KeNumberProcessors'" appears to also be caused by an incompatibility in the D-link WUA-2340 V1.5 Win-XP/2k driver and Ubuntu Jaunty (9.04).  
 
Regressing to the V1.4 WUA-2340 driver will allow the wlan0 device to be registered.  
 
Then the Admin>Administration>Network utility will show a Wireless Connection in it's Connection menu, where it can be edited with the proper encryption.  Only WEP (64bit) appears to be available as an encryption standard.  I found using WEP works with the router configured for 64-bit WEP.
 
A signal strength icon will appear in the upper right of the desktop.  Clicking it will bring down a menu from which the network's SSID's are listed.  You can create a connectin manually with apparently WPA2 if you select 'Create New Wireless Network' from the menu and then select 'WPA & WPA2 Personal' from the Wireless Security pull down menu.  I haven't tried this but other forum posts suggest that it will work.

---

