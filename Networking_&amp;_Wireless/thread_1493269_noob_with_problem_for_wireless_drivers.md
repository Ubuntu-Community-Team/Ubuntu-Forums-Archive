---
title: "noob with problem for wireless drivers"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by mexico90 on 2010-05-25
Hi i have a dell vostro 1510 and am having problems with getting my cards drivers in linux mint. I used this workaround 

[http://ubuntuforums.org/showthread.php?t=704088&highlight=1395+broadcom+success](http://ubuntuforums.org/showthread.php?t=704088&highlight=1395+broadcom+success)

however when I try to use the command to install the driver (  [FONT=&quot]sudo ndiswrapper -i bcmwl5.inf) I get in return "[/FONT]  couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219."  

Im assuming this is because I extracted the file "  [FONT=&quot]R174291" [FONT=Arial]in the wrong place. all I did was use the extract here. since i loaded the file unto a usb stick that means it was extracted unto the usb. I also tried extracting unto the desktop but is till get the same error. can anyone tell me what i'm doing wrong?

and im sorry im posting a mint problem in a ubuntu forum but its the place where i found that workaround. thanks in advance folks[/FONT] 
[/FONT]

---

### Post by chili555 on 2010-05-25
> I also tried extracting unto the desktopIn the terminal, do:```
cd Desktop
ls
```Do you see the .inf file? If so, please do:```
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by mexico90 on 2010-05-25
> **chili555 said:**
> In the terminal, do:```
cd Desktop
ls
```Do you see the .inf file? If so, please do:```
sudo ndiswrapper -i bcmwl5.inf
```

thanks. i didnt get any errors but for some reason it still isnt recognizing my wifi card. 
when i use the hardware thing in mint it shows me two drivers i need 

the first one is called
             "broadcom b43 wireless driver" when i click on "activate" i get this error: "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"
  when i do what it says in terminal I get this:"bash: /var/log/jockey.log: Permission denied"


ok?.. sooo... on to the other driver: 
    "broadcom sta wireless"
  click "activate" and get:"SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) Could not resolve 'archive.ubuntu.com'"


ugh... what now?

---

### Post by chili555 on 2010-05-26
> ugh... what now?In order to install the Hardware Drivers, your system must have access to the internet to download files. If you don't, that's why you get 'Failed to fetch...'

Since you seem most of the way installed with ndiswrapper, let's troubleshoot:```
ndiswrapper -l
```Does it say, driver installed and device present? Then try:```
iwconfig
```Do you have a wireless interface, wlan0, perhaps? Is the wireless switch activated on your laptop?

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by mexico90 on 2010-05-26
> **chili555 said:**
> In order to install the Hardware Drivers, your system must have access to the internet to download files. If you don't, that's why you get 'Failed to fetch...'

Since you seem most of the way installed with ndiswrapper, let's troubleshoot:```
ndiswrapper -l
```Does it say, driver installed and device present? Then try:```
iwconfig
```Do you have a wireless interface, wlan0, perhaps? Is the wireless switch activated on your laptop?

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

ok heres what happened when i tried the above codes
   *ndiswrapper -l*
    *WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.*
    *WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.*
    *WARNING: All config files need .conf: /etc/modprobe.d/blacklist.old, it will be ignored in a future release.*
    *bcmwl5 : driver installed*
    *                device (14E4:4315) present (alternate driver: ssb)*
  
   
  *iwconfig*
    *lo        no wireless extensions.*
    
  
  *eth0      no wireless extensions.*
    
  
  *wlan0     IEEE 802.11bg  ESSID:off/any  *
    *          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   *
    *          Retry  long limit:7   RTS thr:off   Fragment thr:off*
    *          Power Management:off*
    


ok so installed and stuff but still not working? I followed your link and tried this suggestion from it.
    *lshw -C Network*
  
  *WARNING: you should run this program as super-user.*
  
  *  *-network               *
  
  *       description: Network controller*
  
  *       product: BCM4312 802.11b/g*
  
  *       vendor: Broadcom Corporation*
  
  *       physical id: 0*
  
  *       bus info: pci@0000:06:00.0*
  
  *       version: 01*
  
  *       width: 64 bits*
  
  *       clock: 33MHz*
  
  *       capabilities: bus_master cap_list*
  
  *       configuration: driver=b43-pci-bridge latency=0*
  
  *       resources: irq:19 memory:f4000000-f4003fff*
  
  *  *-network*
  
  *       description: Ethernet interface*
  
  *       product: RTL8111/8168B PCI Express Gigabit Ethernet controller*
  
  *       vendor: Realtek Semiconductor Co., Ltd.*
  
  *       physical id: 0*
  
  *       bus info: pci@0000:07:00.0*
  
  *       logical name: eth0*
  
  *       version: 02*
  
  *       serial: 00:1c:23:59:9c:8f*
  
  *       width: 64 bits*
  
  *       clock: 33MHz*
  
  *       capabilities: bus_master cap_list rom ethernet physical*
  
  *       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes*
  
  *       resources: irq:29 ioport:5000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable)*
  
  *  *-network DISABLED*
  
  *       description: Wireless interface*
  
  *       physical id: 2*
  
  *       logical name: wlan0*
  
  *       serial: 00:1f:e1:82:fa:69*
  
  *       capabilities: ethernet physical wireless*
  
  *       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg*
  
  
so from what i can gather its all installed but for some reason is disabled. can you translate what it means?

---

### Post by chili555 on 2010-05-26
I repeat, is the wireless switch activated on your laptop? Let's see:```
rfkill list all
dmesg | grep -e b43 -e wlan
```Thanks.

---

### Post by mexico90 on 2010-05-27
> **chili555 said:**
> I repeat, is the wireless switch activated on your laptop? Let's see:```
rfkill list all
dmesg | grep -e b43 -e wlan
```Thanks.

yes the switch is on.

   *[FONT=&quot]xavier@xavier-laptop ~ $ rfkill list all[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]0: dell-wifi: Wireless LAN[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]            Soft blocked: no[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]            Hard blocked: no[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]1: phy0: Wireless LAN[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]            Soft blocked: no[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]            Hard blocked: no[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot]xavier@xavier-laptop ~ $ dmesg | grep -e b43 -e wlan[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][    0.958973] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][    0.958989] b43-pci-bridge 0000:06:00.0: setting latency timer to 64[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   14.175279] b43-phy0: Broadcom 4312 WLAN found (core revision 15)[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   14.277656] Registered led device: b43-phy0::tx[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   14.277677] Registered led device: b43-phy0::rx[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   14.277698] Registered led device: b43-phy0::radio[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   14.996271] b43 ssb0:0: firmware: requesting b43/ucode15.fw[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.027527] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.034006] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.034012] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.034015] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.145312] b43 ssb0:0: firmware: requesting b43/ucode15.fw[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.147219] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.150438] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.150443] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found[/FONT]*
  *[FONT=&quot][/FONT]*
  *[FONT=&quot][   15.150447] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/FONT]*
  *[FONT=&quot][/FONT]*

---

### Post by v1ad on 2010-05-27
always after installing drivers through ndiswrapper do 

ifconfig wlan0 up

and also try to use the windows xp .inf file

---

### Post by chili555 on 2010-05-27
It look like the native driver b43 is loading. Before we fix that, let's see what ndiswrapper says. Please post:```
ndiswrapper -l
```Thanks.

---

### Post by mexico90 on 2010-05-27
> **chili555 said:**
> It look like the native driver b43 is loading. Before we fix that, let's see what ndiswrapper says. Please post:```
ndiswrapper -l
```Thanks.

   ndiswrapper -l
  
  WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
  
  WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
  
  WARNING: All config files need .conf: /etc/modprobe.d/blacklist.old, it will be ignored in a future release.
  
  WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'Reading'
  
  WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with 'Building'
  
  WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'Reading'
  
  WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'ndiswrapper-common'
  
  bcmwl5 : driver installed
  
                  device (14E4:4315) present (alternate driver: ssb)

---

### Post by chili555 on 2010-05-27
> WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'Reading'Looks like a good plan gone bad; let's try to fix it. Please do:```
ls /etc/modprobe.d | grep black 
```You may have both a blacklist and a blacklist.conf. If so, we'll need to consolidate. Please post:```
cat /etc/modprobe.d/blacklist
```Thanks.

---

### Post by mexico90 on 2010-05-27
> **chili555 said:**
> Looks like a good plan gone bad; let's try to fix it. Please do:```
ls /etc/modprobe.d | grep black 
```You may have both a blacklist and a blacklist.conf. If so, we'll need to consolidate. Please post:```
cat /etc/modprobe.d/blacklist
```Thanks.

   *[FONT=&quot]xavier@xavier-laptop ~ $ ls /etc/modprobe.d | grep black[/FONT]*
  
  *[FONT=&quot]blacklist[/FONT]*
  
  *[FONT=&quot]blacklist-ath_pci.conf[/FONT]*
  
  *[FONT=&quot]blacklist.conf[/FONT]*
  
  *[FONT=&quot]blacklist-firewire.conf[/FONT]*
  
  *[FONT=&quot]blacklist-framebuffer.conf[/FONT]*
  
  *[FONT=&quot]blacklist-modem.conf[/FONT]*
  
  *[FONT=&quot]blacklist.old[/FONT]*
  
  *[FONT=&quot]blacklist-oss.conf[/FONT]*
  
  *[FONT=&quot]blacklist-watchdog.conf[/FONT]*
  
  [I][FONT=&quot]
xavier@xavier-laptop ~ $ cat /etc/modprobe.d/blacklist[/FONT][/I]
  
  
  
  
  
  *[FONT=&quot]blacklist bcm43xx[/FONT]*
  
  *[FONT=&quot]Reading package lists...[/FONT]*
  
  *[FONT=&quot]Building dependency tree...[/FONT]*
  
  *[FONT=&quot]Reading state information...[/FONT]*
  
  *[FONT=&quot]ndiswrapper-common is already the newest version.[/FONT]*

---

### Post by chili555 on 2010-05-27
Let's repair and consolidate. Please run:```
sudo su
mv /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf
rm /etc/modprobe.d/blacklist
echo b43 >> /etc/modprobe.d/blacklist.conf
exit
reboot
```Now is your wireless working?

---

### Post by mexico90 on 2010-05-27
> **chili555 said:**
> Let's repair and consolidate. Please run:```
sudo su
mv /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf
rm /etc/modprobe.d/blacklist
echo b43 >> /etc/modprobe.d/blacklist.conf
exit
reboot
```Now is your wireless working?
    [FONT=&quot]no unfortunately it isn't[/FONT]
[I][FONT=&quot]
[/FONT][/I]
```
*[FONT=&quot]xavier@xavier-laptop ~ $ sudo su[/FONT]*
  
  *[FONT=&quot] _________________________________________[/FONT]*
  
  *[FONT=&quot]/ Q: How many existentialists does it     \[/FONT]*
  *[FONT=&quot]| take to screw in a light bulb? A: Two.  |[/FONT]*
  *[FONT=&quot]| One to screw it in andd one to observe   |[/FONT]*
  *[FONT=&quot]| how the light bulb                      |[/FONT]*
  *[FONT=&quot]| itself symbolizes a single incandescent |[/FONT]*
  *[FONT=&quot]| beacon of subjective    [/FONT]*
  *[FONT=&quot]| reality in a netherworld of endless     |[/FONT]*
  *[FONT=&quot]| absurdity reaching out toward a         |[/FONT]*
  *[FONT=&quot]\ maudlin cosmos of nothingness.          /[/FONT]*
  
  *[FONT=&quot] -----------------------------------------[/FONT]*
 * **[FONT=&quot]       ___  [/FONT]*
  
  *[FONT=&quot]     {~._.~}[/FONT]*
  
  *[FONT=&quot]      ( Y )[/FONT]*
  
  *[FONT=&quot]     ()~*~()   [/FONT]*
  
  *[FONT=&quot]     (_)-(_)   [/FONT]*
  
  *[FONT=&quot]xavier-laptop xavier # mv /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf[/FONT]*
  
  *[FONT=&quot]mv: cannot stat `/etc/modprobe.d/ndiswrapper': No such file or directory[/FONT]*
  
  *[FONT=&quot]xavier-laptop xavier # rm /etc/modprobe.d/blacklist[/FONT]*
  
  *[FONT=&quot]rm: cannot remove `/etc/modprobe.d/blacklist': No such file or directory[/FONT]*
  
  *[FONT=&quot]xavier-laptop xavier # echo b43 >> /etc/modprobe.d/blacklist.conf[/FONT]*
  
  *[FONT=&quot]xavier-laptop xavier # exit[/FONT]*
  
  *[FONT=&quot]exit[/FONT]*
  
  *[FONT=&quot]xavier@xavier-laptop ~ $ reboot [/FONT]*
```

---

### Post by chili555 on 2010-05-27
> rm: cannot remove `/etc/modprobe.d/blacklist': No such file or directoryI don't quite understand how that can be, because here it is:> xavier@xavier-laptop ~ $ ls /etc/modprobe.d | grep black

[COLOR="Red"]blacklist
[/COLOR]
blacklist-ath_pci.conf

blacklist.conf

blacklist-firewire.conf

blacklist-framebuffer.conf

blacklist-modem.conf

blacklist.old

blacklist-oss.conf

blacklist-watchdog.confMay I see:```
ls /etc/modprobe.d
```Thanks.

---

### Post by mexico90 on 2010-05-27
> **chili555 said:**
> I don't quite understand how that can be, because here it is:May I see:```
ls /etc/modprobe.d
```Thanks.

man this is getting ridiculous. thank you for your help so far!
heres what came up.

   [FONT=&quot]xavier@xavier-laptop ~ $ ls /etc/modprobe.d[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]alsa-base.conf           blacklist-framebuffer.conf  blacklist-watchdog.conf[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist-ath_pci.conf   blacklist-modem.conf        libpisock9.conf[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist.conf           blacklist.old               ndiswrapper.conf[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist-firewire.conf  blacklist-oss.conf[/FONT]
  [FONT=&quot][/FONT]
  
tried plugging into my friends internet direct with ethernet and no go on that either. wont even work in windows...

---

### Post by chili555 on 2010-05-27
It looks like we got the .conf business fixed. It was probably a miracle!

I would like to see if b43 is blacklisted. Please let me see:```
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

### Post by mexico90 on 2010-05-28
> **chili555 said:**
> It looks like we got the .conf business fixed. It was probably a miracle!

I would like to see if b43 is blacklisted. Please let me see:```
cat /etc/modprobe.d/blacklist.conf
```Thanks.

   [FONT=&quot] [/FONT]
  [FONT=&quot]xavier@xavier-laptop ~ $ cat /etc/modprobe.d/blacklist.conf[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# This file lists those modules which we don't want to be loaded by[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# alias expansion, usually so some other driver will be loaded for the[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# device instead.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# evbug is a debug tool that should be loaded explicitly[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist evbug[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# these drivers are very simple, the HID drivers are usually preferred[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist usbmouse[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist usbkbd[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# replaced by e100[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist eepro100[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# replaced by tulip[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist de4x5[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# causes no end of confusion by creating unexpected network interfaces[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist eth1394[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# hardware on its own (Ubuntu bug #2011, #6810)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist snd_intel8x0m[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Conflicts with dvb driver (which is better for handling this device)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist snd_aw2[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist i2c_i801[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# replaced by p54pci[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist prism54[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# replaced by b43 and ssb.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist bcm43xx[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# most apps now use garmin usb driver directly (Ubuntu: #114565)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist garmin_gps[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# replaced by asus-laptop (Ubuntu: #184721)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist asus_acpi[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# low-quality, just noise when being used for sound playback, causes[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# hangs at desktop session start (Ubuntu: #246969)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist snd_pcsp[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# ugly and loud noise, getting on everyone's nerves; this should be done by a[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# nice pulseaudio bing (Ubuntu: #77010)[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist pcspkr[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# EDAC driver for amd76x clashes with the agp driver preventing the aperture[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# from being initialised (Ubuntu: #297750). Blacklist so that the driver[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# continues to build and is installable for the few cases where its[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]# really needed.[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]blacklist amd76x_edac[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]b43[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]b43[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]b43[/FONT]
  
looks like its blacklisted 3 times! how do i get rid of that?

---

### Post by mexico90 on 2010-05-30
any other ideas?

---

### Post by chili555 on 2010-05-30
> looks like its blacklisted 3 times! how do i get rid of that?Let's do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change these lines:```
b43

b43

b43
```To read like this:```
blacklist b43
blacklist ssb
```Leave all the other lines untouched. Proofread carefully, save and close gedit. Now reboot and let us see:```
iwconfig
ndiswrapper -l
```Thanks.

---

### Post by mexico90 on 2010-05-30
> **chili555 said:**
> Let's do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change these lines:```
b43

b43

b43
```To read like this:```
blacklist b43
blacklist ssb
```Leave all the other lines untouched. Proofread carefully, save and close gedit. Now reboot and let us see:```
iwconfig
ndiswrapper -l
```Thanks.


do i just cut out the 3 b43's and paste that? or paste that in place for every b43 in the blacklist?

---

### Post by chili555 on 2010-05-31
> cut out the 3 b43's and paste that?Yes, exactly.

---

### Post by mexico90 on 2010-05-31
> **chili555 said:**
> Yes, exactly.

   xavier@xavier-laptop ~ $ iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  xavier@xavier-laptop ~ $ ndiswrapper -l
  
  WARNING: All config files need .conf: /etc/modprobe.d/blacklist.old, it will be ignored in a future release.
  
  bcmwl5 : driver installed
  
                  device (14E4:4315) present (alternate driver: ssb)

---

### Post by chili555 on 2010-05-31
Please try:```
sudo modprobe ndiswrapper
iwconfig
```Thanks.

---

