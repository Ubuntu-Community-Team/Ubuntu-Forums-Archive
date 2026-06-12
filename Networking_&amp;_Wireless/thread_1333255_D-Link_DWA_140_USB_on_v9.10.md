---
title: "D-Link DWA 140 USB on v9.10"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by markfrancis2008 on 2009-11-21
Hello, I have recently installed 9.10 and have a strange problem with my usb wireless connection. Im using a D-link DWA 140 ([http://www.dlink.com/products/?pid=652]("http://www.dlink.com/products/?pid=652")), **it recognises my home network but wont connect to it. **

In the wiki ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")) its listed as "Works out of the box on Jaunty Jackalope kernel 2.6.28-11. Module from staging at this time, with zero issue found yet." but I can't seem to find the problem.

Because its a usb and not an internal card, I didnt see much when i put in the segested commands in the sticky, but here is some infomation I could get, I dont know how useful it is.

```
Tu Virsion 9.10

mark@ubuntu:~$ uname -mr
2.6.31-14-generic i686

mark@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  Mode:Managed  Frequency:2.427 GHz  
          Access Point: Not-Associated   Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mark@ubuntu:~$ sudo lshw -C network
[sudo] password for mark: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:b5:96:e7
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:ee00(size=256) memory:fddff000-fddfffff memory:fde00000-fde1ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:f0:14:ab:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

mark@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                        [ OK ]

```

Any help would be great, thanks.

---

### Post by mthorn on 2009-11-21
I'm don't have the answer but I have exactly the same problem. I notice that no one has answered your question in 9 hours.

Every installation of Ubuntu that I have done I have had issues with wireless USB. When I installed 8.04 I had a linksys usb dongle and learned about ndiswrapper and finally got it working. Then I upgraded to 9.04 and wifi broke again. ndiswrapper was now dropped from the distribution so upon recommendation, I bought a Dlink DWA-140 usb wifi stick and was able to get it working. Now I upgrade to 9.1 and again problems.

This is ridiculous. If you google "wifi problems ubuntu" you see that the problems have been continual for many years. 

We would appreciate a solution to this problem.

Also, why is wifi so difficult a problem for Ubuntu? Microsoft and Mac OS X upgrades have handled this just fine for me.

---

### Post by ktuomain on 2009-11-22
> **markfrancis2008 said:**
> Hello, I have recently installed 9.10 and have a strange problem with my usb wireless connection. Im using a D-link DWA 140 ([http://www.dlink.com/products/?pid=652](http://www.dlink.com/products/?pid=652)), **it recognises my home network but wont connect to it. **


This is quite easy to fix. Add the following line to /etc/modprobe.d/blacklist.conf file and then reboot:

blacklist rt2800usb

This file is owned by root, but you can usually edit it using sudo program to run an editor as a root user:

sudo nano  /etc/modprobe.d/blacklist.conf

I hope this helps.

---

### Post by mthorn on 2009-11-22
THANK YOU!

This worked perfectly.

---

### Post by AFI420 on 2009-11-22
will this work for my wusb54gc?

---

### Post by ktuomain on 2009-11-22
> **AFI420 said:**
> will this work for my wusb54gc?

I think wusb54gc has different chipset. DWA-140 seems to be using RT2870 chipset (at least mine is using RT2870). This is what lsusb command shows on my DWA-140:

Bus 001 Device 002: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]

If wusb54gc has the same chipset, it is quite likely that the blacklisting above helps. But if it is not same chipset (I think it is not the same chipset as wusb54gc seems to be 802.11g instead of 802.11n), blacklisting might not help. But it still might be worth trying even if it is using different chipset. If it doesn't help, you should remove that line and reboot again. And please let as know if blacklisting helps with wusb54gc.

I think that the problem with RT2870 chipset is that the system loads or at least tries to load the wrong driver (rt2800usb) which messes up the system. And blacklisting prevents loading the wrong driver. The same problem could also be happening with wusb54gc even if it has different chipset, but I cannot be sure about that.

---

### Post by AFI420 on 2009-11-22
the windows driver for my adapter is a rt2870.conf file which i used before with ndiswrapper, but still couldnt get a stable connection to my router. but I remember seeing it say that it was using alternate driver for rt2800


maybe if I blacklist 2800 it will use 2870. do I have to load it using ndiswrapper or is it already on the system?

---

### Post by ktuomain on 2009-11-22
> **AFI420 said:**
> 
maybe if I blacklist 2800 it will use 2870. do I have to load it using ndiswrapper or is it already on the system?

I think that my DWA-140 is not using ndiswrapper. I think that the driver it is using is called rt2870sta.

After the upgrade to Ubuntu 9.10 I haven't selected any proprietary driver or done anything else than just that blacklisting, rebooting and then just connecting to my access point by using network manager. I cannot remember anymore if I had installed some proprietary driver before the upgrade.

If the following command doesn't report any errors, I think you already have the driver file on your computer:

sudo modprobe rt2870sta

---

### Post by mthorn on 2009-11-23
ktuomain - 

Do you know why Ubuntu distros have so many problems with wifi? The reason I chose the D-link DWA-140 was that it was "green" listed in the Ubuntu documentation as supported by the kernel for 9.04. For 9.04 I did not have to install any drivers. It seems that if an OS version works with a recommended piece of hardware then an upgrade should have been tested against previous compatible hardware. I know Ubuntu is free and probably relies on the contributions of volunteers (and I'm grateful for their efforts) but do they have a rigorous process for testing releases? Is there something I could be doing as a user that would make upgrades smoother?

This difficulty with upgrades and hardware makes it problematic for me to donate machines and recommend Ubuntu for people in need that are lower income and lacking expertise. The support problem will be overwhelming.

I would appreciate your comments. Also, thanks for the help - my system continues to be stable.

---

### Post by ktuomain on 2009-11-24
> **mthorn said:**
> 
Do you know why Ubuntu distros have so many problems with wifi?


I am sorry, but I am no expert on this subject and I can offer just educated guesses. In my opinion driver support for WLAN cards has been incomplete in Linux for some time, but I see some encouraging signs that it is slowly improving.

> 
but do they have a rigorous process for testing releases? Is there something I could be doing as a user that would make upgrades smoother?
I think downloading and testing beta releases and release candidates of new Ubuntu versions would be a good idea. It is easy to test a new version using live cd or usb stick without touching the old installation.

And if you notice any compatibility problems (especially new problems), you should report them. Then the problem may be fixed before releasing the new version or at least addressed in the release notes.

---

### Post by mthorn on 2009-11-24
Good suggestion about booting and testing from live cd or usb stick prior to upgrade. I have used boot from usb stick in the past. Thanks.

---

### Post by sonicb00m on 2009-12-06
My dwa-140 doesn't work with ubuntu either. I tried the blacklist ocmmand but still exhibits the same problem.

I know the adapter works in linux because my tvix 7000 player detects and uses it correctly.

---

### Post by Tonny Hooijer on 2009-12-15
Thanks! 
Also worked for me.

---

### Post by ktuomain on 2009-12-15
> **sonicb00m said:**
> My dwa-140 doesn't work with ubuntu either. I tried the blacklist ocmmand but still exhibits the same problem.


Could you run lsusb command and check if the device id is 07d1:3c09? For example my DWA-140 shows the following information when I run lsusb:

Bus 001 Device 002: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]

Sometimes device manufacturers use same model number even when they change the chipset that is used. That could explain why that blacklist trick doesn't work, but all of this is just speculation as I don't know whether you have the same chipset or not.

---

### Post by bkratz on 2009-12-15
I just looked at the D-Link website and there are two versions available;

The original DWA-140 uses the Ralink rt2870 drivers (has a Linux driver available) and the DWA-140 Rev B which doesn't use the Ralink driver and has only Windows drivers listed which would require ndiswrapper. The version is listed on the stick-on label. Unfortunately you can't see this when purchasing.

---

### Post by graabein on 2009-12-21
> **bkratz said:**
> I just looked at the D-Link website and there are two versions available;

The original DWA-140 uses the Ralink rt2870 drivers (has a Linux driver available) and the DWA-140 Rev B which doesn't use the Ralink driver and has only Windows drivers listed which would require ndiswrapper. The version is listed on the stick-on label. Unfortunately you can't see this when purchasing.

I have a clean install of Ubuntu 9.10 and **DWA-140 Rev.B2**. It works on Vista but won't show up on Ubuntu even after blacklisting **rt2800usb**. 

Guess I'll have to look into ndiswrapper. Has anyone with the same problem done this?

---

### Post by graabein on 2009-12-22
Installed ndiswrapper and ndisgtk from Karmic Koala package repository. Installed driver from included CD, DWA-140 ver 1.31(E). 

Upon launching ndisgtk I get an error message *"Unable to see if harware is present"*. Click OK. Then it says *"Currently installed Windows Drivers: drt2870 hardware present."*

**$ lsusb**
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 002: ID 07d1:3c0a D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1b1c:0b29  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**$ ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
drt2870 : driver installed
	device (07D1:3C0A) present (alternate driver: rt2800usb)

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.



rt2800usb is still blacklisted BTW.

---

### Post by bkratz on 2009-12-22
> **graabein said:**
> Installed ndiswrapper and ndisgtk from Karmic Koala package repository. Installed driver from included CD, DWA-140 ver 1.31(E). 

Upon launching ndisgtk I get an error message *"Unable to see if harware is present"*. Click OK. Then it says *"Currently installed Windows Drivers: drt2870 hardware present."*

**$ lsusb**
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 002: ID 07d1:3c0a D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1b1c:0b29  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**$ ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
drt2870 : driver installed
	device (07D1:3C0A) present (alternate driver: rt2800usb)

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.



rt2800usb is still blacklisted BTW.



Curious if it worked for you then?

---

### Post by graabein on 2009-12-22
Nope. Did not, as you can see from iwconfig. No lights in the wireless USP adapter.

---

### Post by intrepidx on 2009-12-23
Hello,

Another +1 on this.  I also own a D-Link DWA-140 B2, and even after searching the internet high and low there is nothing that will make this device work.  I can not even get the light to turn on.

Has anybody reading this had any success with the B2 variant at all?  If so, what was your approach?

Also - does anybody know which developer out there could get support for this integrated with Ubuntu 9.10?  Let me know their e-mail address, I will paypal them enough money for a beer if they get this thing operational. :P

Or if it's a case of D-link not supplying sufficient info/drivers, maybe all affected users should e-mail them, motivating them to better support the open source community?

Happy holidays everyone.

Dave.

---

### Post by graabein on 2009-12-23
Happy holiday Dave. I'll paypal them a beer as well. :wink:

I might move the wireless adapter to another pc (with Windows) and get an internal PCI-e wireless card for this one. Anyone have a suggestion for cards that actually work with (Ubuntu) GNU/Linux?

---

### Post by freds3251 on 2009-12-23
I have the D-Link DWA-140 and struggled for a while to get it to actually connect. Even though it was showing my network was there. I read a bunch of posts of people saying to black list in /etc/modprobe.d on the blacklist.conf page. It was always "blacklist rt2800usb". I went and tried this as well as trying to play with variants to get it to connect. Not a single connection at any time. Then I found the exact driver name that mine used. So I went and put in the following phrase "blacklist rt2870sta". No quotations. lol, anyway after putting this in. I had success, internet was cruising right along. The only problem is the internet likes to be a bit buggy and drop a bar or 2, sometimes just disconnect and reconnect. Doesn't happen all the time, but anyway that's how I got mine to work. Hope this helps!!

---

### Post by graabein on 2009-12-23
That's good news! Did you install a driver with ndiswrapper? What kind of GNU/Linux are you running?

---

### Post by freds3251 on 2009-12-23
I use ubuntu 9.10- The Karmic Koala, released in October of 09. No I did not use ndiswrapper. Just ran as root and blacklisted what i posted above.

---

### Post by graabein on 2009-12-23
I removed the driver I installed and uninstalled ndiswrapper but no lights yet. Even after restart. 

lsusb still says the same id for the connected wireless adapter.

How should I go about this for it to work?

---

### Post by freds3251 on 2009-12-23
You sure you got the phrase right in blacklist.conf.... Im not sure if this matters, but I was sure to leave a space when I inserted "blacklist rt2870sta" Actually pm me and send a screen capture of blacklist.conf if you don't mind.

---

### Post by graabein on 2009-12-24
Message sent, freds3251.


For the record my blacklist.conf is:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Trying to get D-Link DWA 140 USB dongle to work with clean install of Ubuntu 9.10
blacklist rt2870sta
```

And I get no light in the wireless USB adapter. How do I turn it on?

I e-mailed D-Link here in Norway and asked if they had (open) drivers for Linux by the way.

---

### Post by graabein on 2009-12-27
What if I bought a wireless bridge, placed it next to my computer and connected ethernet to that? How do I set it up? Which (GNU/Linux friendly) brand should I get?

---

### Post by oblio on 2009-12-29
> **graabein said:**
> Message sent, freds3251.


For the record my blacklist.conf is:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# Trying to get D-Link DWA 140 USB dongle to work with clean install of Ubuntu 9.10
blacklist rt2870sta
```

And I get no light in the wireless USB adapter. How do I turn it on?

I e-mailed D-Link here in Norway and asked if they had (open) drivers for Linux by the way.

I'm using Mepis, not Ubuntu, so names/places may be different (blacklisting, for example)

Upgrade your kernel in Ubuntu to 2.6.32.
Download the latest RT2870USB linux driver package version 2.3.0 from Ralinktech
(you'll find it here: [http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2) )
Unpack that source file.  Make 2 small changes (I'll add them later **).
Run make and make install (both as root). Alternatively use checkinstall as substitute for 'make install': You'll end up with a reusable .deb then.
Replace the existing rt2870sta.ko driver in kernel staging with the one created during make and make install.
Blacklist rt2800usb - and for good measure rt3070sta as well - in /etc/modprobe.d/blacklist.
Put 'rt2870sta' (no quotes) in /etc/modules to make sure that this driver is loaded at boottime. 
Modprobe rt2870sta   (make sure the new driver module gets loaded)
You probably have to reboot here to get rid of the rt2800usb driver in memory (rmmod won't work).
Run dhclient ra0 to bring up the ra0 interface used 
Edit /etc/Wireless/rt2870sta.dat as needed  (SSID, encryption, country, etc).
Use your networkmanager to manage wireless interface (wicd)

** Two changes: change n to y in in /os/linux/config.mk
#ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=**y**
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y**
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //



Ko

---

### Post by graabein on 2009-12-30
OK thanks, but I'm back from holiday and the computer with the DWA-140 card is in my home town, miles from where I'm living. 

I'll bookmark the post and try it out come easter!

By the way, I got a quick reply from D-Link Team Leader Norwegian Consumer Support saying they did not have drivers for Linux.

---

### Post by traxi on 2010-01-02
i had to use the 3070 driver from the ralink page to get my dwa 140 rev.b to work. give it a try :)
[_this_]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV4THpJd0wyUnZkMjVzYjJGa01EVTRNalU1TlRjek1DNWllakk5UFQweU1EQTVYekV4TVRCZlVsUXpNRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNHhMakl1TUM1MFlYST1D")

---

### Post by proctor-the-doctor on 2010-01-03
ubuntu.fr has an excellent how-to:

[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den)

---

### Post by ravedog on 2010-01-03
Hey guys!

Just tried the guide provided here: [http://translate.googleusercontent.com/translate_c?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den&rurl=translate.google.com&usg=ALkJrhil4Nmc5cJr--JG9D8w6zBiY1BX1Q#d-link_dwa-140_b2](http://translate.googleusercontent.com/translate_c?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den&rurl=translate.google.com&usg=ALkJrhil4Nmc5cJr--JG9D8w6zBiY1BX1Q#d-link_dwa-140_b2)

And i still cant get it to work :(

My syslog says this after pluging the adapter in:

```

Jan  3 18:01:38 ra-ws kernel: [  368.982578] usb 1-1: USB disconnect, address 6
Jan  3 18:01:38 ra-ws kernel: [  368.982696] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1
Jan  3 18:01:38 ra-ws kernel: [  368.982701] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
Jan  3 18:01:38 ra-ws NetworkManager: <info>  (ra0): now unmanaged
Jan  3 18:01:38 ra-ws NetworkManager: <info>  (ra0): device state change: 2 -> 1 (reason 36)
Jan  3 18:01:38 ra-ws NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/net/ra0, iface: ra0)
Jan  3 18:01:38 ra-ws kernel: [  369.050086]  RTUSB disconnect successfully
Jan  3 18:01:42 ra-ws kernel: [  373.030026] usb 1-1: new high speed USB device using ehci_hcd and address 7
Jan  3 18:01:43 ra-ws kernel: [  373.195531] usb 1-1: configuration #1 chosen from 1 choice
Jan  3 18:01:43 ra-ws kernel: [  373.196225] 
Jan  3 18:01:43 ra-ws kernel: [  373.196226] 
Jan  3 18:01:43 ra-ws kernel: [  373.196227] === pAd = ffffc900076fc000, size = 502624 ===
Jan  3 18:01:43 ra-ws kernel: [  373.196228] 
Jan  3 18:01:43 ra-ws kernel: [  373.196231] <-- RTMPAllocAdapterBlock, Status=0
Jan  3 18:01:43 ra-ws NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/net/ra0, iface: ra0)
Jan  3 18:01:43 ra-ws NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/net/ra0, iface: ra0): no ifupdown configuration found.
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): driver does not support SSID scans (scan_capa 0x00).
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): new 802.11 WiFi device (driver: 'usb')
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): exported as /org/freedesktop/NetworkManager/Devices/5
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): now managed
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): device state change: 1 -> 2 (reason 2)
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): bringing up device.
Jan  3 18:01:43 ra-ws kernel: [  373.210058] #
Jan  3 18:01:43 ra-ws kernel: [  373.230067] #
Jan  3 18:01:43 ra-ws kernel: [  373.250075] #
Jan  3 18:01:43 ra-ws kernel: [  373.260177] #
Jan  3 18:01:43 ra-ws kernel: [  373.270086] #
Jan  3 18:01:43 ra-ws kernel: [  373.280089] #
Jan  3 18:01:43 ra-ws kernel: [  373.290094] #
Jan  3 18:01:43 ra-ws kernel: [  373.310103] #
Jan  3 18:01:43 ra-ws kernel: [  373.320107] #
Jan  3 18:01:43 ra-ws kernel: [  373.330112] #
Jan  3 18:01:43 ra-ws kernel: [  373.340116] #
Jan  3 18:01:43 ra-ws kernel: [  373.350121] #
Jan  3 18:01:43 ra-ws kernel: [  373.360126] #
Jan  3 18:01:43 ra-ws kernel: [  373.410148] #
Jan  3 18:01:43 ra-ws kernel: [  373.430032] #
Jan  3 18:01:43 ra-ws kernel: [  373.450041] #
Jan  3 18:01:43 ra-ws kernel: [  373.470050] #
Jan  3 18:01:43 ra-ws kernel: [  373.490059] #
Jan  3 18:01:43 ra-ws kernel: [  373.500062] #
Jan  3 18:01:43 ra-ws kernel: [  373.510069] #
Jan  3 18:01:43 ra-ws kernel: [  373.520073] #
Jan  3 18:01:43 ra-ws kernel: [  373.530077] #
Jan  3 18:01:43 ra-ws kernel: [  373.540083] #
Jan  3 18:01:43 ra-ws kernel: [  373.550087] #
Jan  3 18:01:43 ra-ws kernel: [  373.560092] #
Jan  3 18:01:43 ra-ws kernel: [  373.570096] #
Jan  3 18:01:43 ra-ws kernel: [  373.580100] #
Jan  3 18:01:43 ra-ws kernel: [  373.590105] #
Jan  3 18:01:43 ra-ws kernel: [  373.600110] #
Jan  3 18:01:43 ra-ws kernel: [  373.610114] #
Jan  3 18:01:43 ra-ws kernel: [  373.628669] <-- RTMPAllocTxRxRingMemory, Status=0
Jan  3 18:01:43 ra-ws kernel: [  373.630124] #
Jan  3 18:01:43 ra-ws kernel: [  373.635375] -->RTUSBVenderReset
Jan  3 18:01:43 ra-ws kernel: [  373.635500] <--RTUSBVenderReset
Jan  3 18:01:43 ra-ws kernel: [  373.690026] #
Jan  3 18:01:43 ra-ws kernel: [  373.710035] #
Jan  3 18:01:43 ra-ws kernel: [  373.730044] #
Jan  3 18:01:43 ra-ws kernel: [  373.750052] #
Jan  3 18:01:43 ra-ws kernel: [  373.770062] #
Jan  3 18:01:43 ra-ws kernel: [  373.780066] #
Jan  3 18:01:43 ra-ws kernel: [  373.790072] #
Jan  3 18:01:43 ra-ws kernel: [  373.800076] #
Jan  3 18:01:43 ra-ws kernel: [  373.810081] #
Jan  3 18:01:43 ra-ws kernel: [  373.820085] #
Jan  3 18:01:43 ra-ws kernel: [  373.830089] #
Jan  3 18:01:43 ra-ws kernel: [  373.840094] #
Jan  3 18:01:43 ra-ws kernel: [  373.850098] #
Jan  3 18:01:43 ra-ws kernel: [  373.860103] #
Jan  3 18:01:43 ra-ws kernel: [  373.870108] #
Jan  3 18:01:43 ra-ws kernel: [  373.880112] #
Jan  3 18:01:43 ra-ws kernel: [  373.890117] #
Jan  3 18:01:43 ra-ws kernel: [  373.900121] #
Jan  3 18:01:43 ra-ws kernel: [  373.910126] #
Jan  3 18:01:43 ra-ws kernel: [  373.970028] #
Jan  3 18:01:43 ra-ws kernel: [  373.990037] #
Jan  3 18:01:43 ra-ws kernel: [  374.010046] #
Jan  3 18:01:43 ra-ws kernel: [  374.027940] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
Jan  3 18:01:43 ra-ws kernel: [  374.027943] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
Jan  3 18:01:43 ra-ws kernel: [  374.027946] 1. Phy Mode = 0
Jan  3 18:01:43 ra-ws kernel: [  374.027948] ERROR!!! NICReadRegParameters failed, Status[=0x00000001]
Jan  3 18:01:43 ra-ws NetworkManager: <info>  (ra0): deactivating device (reason: 2).
Jan  3 18:01:43 ra-ws kernel: [  374.034309] ---> RTMPFreeTxRxRingMemory
Jan  3 18:01:43 ra-ws kernel: [  374.034336] <--- RTMPFreeTxRxRingMemory
Jan  3 18:01:43 ra-ws kernel: [  374.034339] !!! rt28xx Initialized fail !!!
Jan  3 18:01:43 ra-ws kernel: [  374.040062] #
Jan  3 18:01:43 ra-ws kernel: [  374.050064] #
Jan  3 18:01:43 ra-ws kernel: [  374.060070] #
Jan  3 18:01:44 ra-ws kernel: [  374.070075] #
Jan  3 18:01:44 ra-ws kernel: [  374.191379] #
Jan  3 18:01:44 ra-ws kernel: [  374.240151] #
Jan  3 18:01:44 ra-ws kernel: [  374.260035] #
Jan  3 18:01:44 ra-ws kernel: [  374.280044] #
Jan  3 18:01:44 ra-ws kernel: [  374.310058] #
Jan  3 18:01:44 ra-ws kernel: [  374.330067] #
Jan  3 18:01:44 ra-ws kernel: [  374.340143] #
Jan  3 18:01:44 ra-ws kernel: [  374.350076] #
Jan  3 18:01:44 ra-ws kernel: [  374.360081] #
Jan  3 18:01:44 ra-ws kernel: [  374.376997] <-- RTMPAllocTxRxRingMemory, Status=0
Jan  3 18:01:44 ra-ws kernel: [  374.378588] -->RTUSBVenderReset
Jan  3 18:01:44 ra-ws kernel: [  374.378714] <--RTUSBVenderReset
Jan  3 18:01:44 ra-ws kernel: [  374.380218] #
Jan  3 18:01:44 ra-ws kernel: [  374.390094] #
Jan  3 18:01:44 ra-ws kernel: [  374.400100] #
Jan  3 18:01:44 ra-ws kernel: [  374.410104] #
Jan  3 18:01:44 ra-ws kernel: [  374.420108] #
Jan  3 18:01:44 ra-ws kernel: [  374.430112] #
Jan  3 18:01:44 ra-ws kernel: [  374.440117] #
Jan  3 18:01:44 ra-ws kernel: [  374.450121] #
Jan  3 18:01:44 ra-ws kernel: [  374.460126] #
Jan  3 18:01:44 ra-ws kernel: [  374.520028] #
Jan  3 18:01:44 ra-ws kernel: [  374.540037] #
Jan  3 18:01:44 ra-ws kernel: [  374.560047] #
Jan  3 18:01:44 ra-ws kernel: [  374.580056] #
Jan  3 18:01:44 ra-ws kernel: [  374.590062] #
Jan  3 18:01:44 ra-ws kernel: [  374.600065] #
Jan  3 18:01:44 ra-ws kernel: [  374.610070] #
Jan  3 18:01:44 ra-ws kernel: [  374.620074] #
Jan  3 18:01:44 ra-ws kernel: [  374.630078] #
Jan  3 18:01:44 ra-ws kernel: [  374.640083] #
Jan  3 18:01:44 ra-ws kernel: [  374.650110] #
Jan  3 18:01:44 ra-ws kernel: [  374.660108] #
Jan  3 18:01:44 ra-ws kernel: [  374.670097] #
Jan  3 18:01:44 ra-ws kernel: [  374.680109] #
Jan  3 18:01:44 ra-ws kernel: [  374.690106] #
Jan  3 18:01:44 ra-ws kernel: [  374.700112] #
Jan  3 18:01:44 ra-ws kernel: [  374.710114] #
Jan  3 18:01:44 ra-ws kernel: [  374.720121] #
Jan  3 18:01:44 ra-ws kernel: [  374.730124] #
Jan  3 18:01:44 ra-ws kernel: [  374.800030] #
Jan  3 18:01:44 ra-ws kernel: [  374.807045] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
Jan  3 18:01:44 ra-ws kernel: [  374.807048] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
Jan  3 18:01:44 ra-ws kernel: [  374.807051] 1. Phy Mode = 0
Jan  3 18:01:44 ra-ws kernel: [  374.807053] ERROR!!! NICReadRegParameters failed, Status[=0x00000001]
Jan  3 18:01:44 ra-ws wpa_supplicant[1115]: Could not set interface 'ra0' UP
Jan  3 18:01:44 ra-ws wpa_supplicant[1115]: Failed to initialize driver interface
Jan  3 18:01:44 ra-ws NetworkManager: <WARN>  nm_supplicant_interface_add_cb(): Unexpected supplicant error getting interface: wpa_supplicant couldn't grab this interface.
Jan  3 18:01:44 ra-ws kernel: [  374.813411] ---> RTMPFreeTxRxRingMemory
Jan  3 18:01:44 ra-ws kernel: [  374.813438] <--- RTMPFreeTxRxRingMemory
Jan  3 18:01:44 ra-ws kernel: [  374.813441] !!! rt28xx Initialized fail !!!

```

The networkmanager applet says that there is a wireless card but says "Device not ready" ofc.

Anyone that knows what could have happened?

I have a DWA-140 B2. Ubuntu 9.10 with kernel 2.6.31-14-generic

Thanks in advance.

/RD

---

### Post by ravedog on 2010-01-03
Im a newbe so please correct me if im wrong, but it shouldnt even try to load the rt2870sta driver like the syslog says, right?

Really dont know what went wrong here... a cut out from the blacklist file looks like this btw:

```

# Wifi issue
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00usb
blacklist rt2x00lib

```

all according to the the guide.

br,

RD

---

### Post by ravedog on 2010-01-03
Ok, so it was a quite simple error when all came around. :P
It tried to open "/etc/Wireless/RT2870STA/RT2870STA.dat", but the driver installation only created that file in a folder called 3070. So when moved, all worked.

However, i do find that the speed and the stabillity is really low on this wifi dongle. anyone else that feels the same or is it just my setup perhaps.

br,

RD

---

### Post by proctor-the-doctor on 2010-01-05
i found some speed and stability problems here but i overcame most of them when i removed windows from the mix.

i was using this as an smb file transfer conduit and found that
1/ windows slowed this thing down to ~2MB/s w/ frequent dropouts
2/ even w/out windows in the mix (running between 2 linux boxes only) the speed was ~3-4MB/s w/ frequent dropouts

i tested by running some file transfers over sftp and between the 2 linux machines my speed increased to ~10MB/s (this is with a t100 ethernet in the mix).  basically saturated the t100 line.

so i replaced samba with nfs and now it is able to maintain the 10MB/s speed over time, so basically i am happy.

not sure what windows' issues are.  won't be testing.

proctor

---

### Post by sonicb00m on 2010-01-17
I got mine working again with linux-backports-modules-2.6.31.

However, can't get it to connect at anything but 54g. So no N mode. Any ideas?

---

### Post by proctor-the-doctor on 2010-01-20
> **proctor-the-doctor said:**
> i found some speed and stability problems here but i overcame most of them when i removed windows from the mix.
the speed was ~3-4MB/s w/ frequent dropouts

i tested by running some file transfers over sftp and between the 2 linux machines my speed increased to ~10MB/s (this is with a t100 ethernet in the mix).  basically saturated the t100 line.

so i replaced samba with nfs and now it is able to maintain the 10MB/s speed over time, so basically i am happy.

not sure what windows' issues are.  won't be testing.

proctor

update:
i tried with a gigabit cable and was not able to get much faster than 13MB/s.  so not as fast as i had hoped.  not sure what the bottleneck is at this point.

proctor

---

### Post by Ginsly on 2010-01-21
> **ktuomain said:**
> Could you run lsusb command and check if the device id is 07d1:3c09? For example my DWA-140 shows the following information when I run lsusb:

Bus 001 Device 002: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]

Sometimes device manufacturers use same model number even when they change the chipset that is used. That could explain why that blacklist trick doesn't work, but all of this is just speculation as I don't know whether you have the same chipset or not.

> **bkratz said:**
> I just looked at the D-Link website and there are two versions available;

The original DWA-140 uses the Ralink rt2870 drivers (has a Linux driver available) and the DWA-140 Rev B which doesn't use the Ralink driver and has only Windows drivers listed which would require ndiswrapper. The version is listed on the stick-on label. Unfortunately you can't see this when purchasing.

> **graabein said:**
> Installed ndiswrapper and ndisgtk from Karmic Koala package repository. Installed driver from included CD, DWA-140 ver 1.31(E). 

Upon launching ndisgtk I get an error message *"Unable to see if harware is present"*. Click OK. Then it says *"Currently installed Windows Drivers: drt2870 hardware present."*

**$ lsusb**
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 002: ID 07d1:3c0a D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1b1c:0b29  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Hi. When I first tried this adapter with a Karmic live cd a few weeks ago, it didn't work for me either. It worked out of the box with Jaunty, so I didn't install. A little bit of investigation today and I managed to get it working with a live Karmic cd (I'm posting from it right now)

It's labeled H/W Ver.:B1 F/W Ver.:1.40 and lsusb shows it's Device ID as ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]

In Jaunty lsmod shows the kernel module rt2870sta is loaded and not rt2800usb. In Karmic, lsmod shows both rt2870sta & rt2800usb are loaded (as well as rt2x00usb and rt2x00lib)

Blacklisting just rt2800usb didn't work for me but blacklisting all three of these modules did, as explained in the blacklisting section of  ["]this]("http://ubuntuforums.org/showthread.php?t=1342593&highlight=ID+07d1%3A3c09+D-Link+System+DWA-140+802.11n+Adapter+[ralink+rt2870) tutorial....

It worked on two different machines, and all I did was boot the live cd **without** the adapter plugged in, edit (with sudo) /etc/modprobe.d/blacklist.conf to show 

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

then plugged in the adapter. Lights came on and it connected with internet access. On one machine I had to issue > sudo /etc/init.d/network-manager restart to get the nm-applet to connect...

If you've being trying with ndiswrapper you should also add...

blacklist ndiswrapper 

On a side note, to get the same adapter working in Debian on my laptop, I had to follow the same method as Oblio, building the rt2870sta module from the source tarball on the D-Link website, and swap it with the Debian kernel module, but try the blacklist method first...

I'm thinking I might install Karmic now. Will post back when it's finished....

---

### Post by Nimnio on 2010-01-21
I'm using a D-Link DWA-140 B1 wireless USB adapter with Ubuntu 9.10. I could see my wireless router and many others, but my password was being rejected.

Blacklisting rt2800usb and rebooting worked for me. Now, if you'll excuse me, I'm going to go perform a rain dance on the front lawn.

Thanks, ktuomain!

---

### Post by elysion on 2010-01-23
Hi!

I just bought a DWA-140 and noticed it was sadly the version B2. Luckily I got it working following these instructions: [http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den](http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den).

Seems that the RT3070 driver available from Ralinktech already includes support for the DWA-140, so no need to patch the source or anything. Everything seems to be working quite steady - got even the pulseaudio raop sink module to work with my airport express, which was super :)!

---

### Post by zerng07 on 2010-01-23
Does anyone file a bug about that? I try to file a bug few minutes ago, but it always redirect me to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs).


I really hope this bug can be resolved in 10.04!!


My experiment with dwa-140 is below:

I use D-Link DWA-140 wifi usb stick. It worked well in 9.04, but stopped working after I upgrade to 9.10.

I firstly install linux-backports-modules-2.6.31-14-generic_2.6.31-14.16_i386.deb and reboot. And, it started to work again.

And about last week I tried to upgrade to 10.04 alpha to see if there would be something wrong with my box, and still my DWA-140 dropped again.

At that time, I searched for backports-modules again, then found out there were no backports-modules for Lucid!

So I gave up and reinstalled 9.10 with ubuntu-9.10-desktop CD, and it failed in the last installation stage unexceptly for three times. I was depressed but gave alternate CD a try, and my ubuntu 9.10 was back again now!

However, this time I use the method mentioned in the first post(blacklist the modules that my box displayed with lsmod, rt2800usb and rt2x00usb), and it works too!

Em.... so I was wondering what had happened with the installation of backports-module to make my dwa-140 work?

---

### Post by sonicb00m on 2010-01-28
zerng07 - I'm glad you tested alpha 10.04 - saved me wasting my time testing the dwa-140 . haha.

I can't answer your question i am afraid but have you got the adapter running anything faster than 54g mode?

I'm really tired of the wireless just not working as it should.

---

### Post by sablar_ocksa on 2010-01-30
Hi!

I also have the DWA-140 Rev B2. The french-guide that you guys provided was great and my wireless now works. 

Problem is that it wont load automatically and I have to load the module after every reboot:
sudo insmod / lib / modules / `uname-r` / kernel/drivers/net/wireless/rt3070sta.ko 

and then restart networking and network manager.

I followed the french guide step by step.

Any suggestions?
Thanks

---

### Post by linghao on 2010-01-30
> **sablar_ocksa said:**
> Hi!

I also have the DWA-140 Rev B2. The french-guide that you guys provided was great and my wireless now works. 

Problem is that it wont load automatically and I have to load the module after every reboot:
sudo insmod / lib / modules / `uname-r` / kernel/drivers/net/wireless/rt3070sta.ko 

and then restart networking and network manager.

I followed the french guide step by step.

Any suggestions?
Thanks

Hi Sablar, I also made it following the French guide. 
If you want it to load automatically everytime you start system, you can just simply add following line to /etc/modules

rt3070sta

so this module will be loaded automatically.

---

### Post by sablar_ocksa on 2010-02-06
> If you want it to load automatically everytime you start system, you can just simply add following line to /etc/modules

rt3070sta


I added rt3070sta to /etc/modules but it doen't work. As i emntioned earlier it worked when i loaded it manually as described above. 

And if i try to load it manually now this is what happens:

[FONT="Courier New"]johannes@JohannesLinux:~$ sudo insmod /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt3070sta.ko 
insmod: error inserting '/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt3070sta.ko': -1 File exists
[/FONT]

This means that the module has been loaded at boot, right? So i don't understand why it won't work. Now wireless isn't working at all. Any ideas or more info i can provide? Would really like for this to work...

Thanks

Updated 1/3 2010. Anyone?

---

### Post by Klvngam on 2010-03-01
> **ktuomain said:**
> This is quite easy to fix. Add the following line to /etc/modprobe.d/blacklist.conf file and then reboot:
 
blacklist rt2800usb
 
This file is owned by root, but you can usually edit it using sudo program to run an editor as a root user:
 
sudo nano /etc/modprobe.d/blacklist.conf
 
I hope this helps.
 
 
Worked great, thank you ^^ :D

---

### Post by georgevaccaro on 2010-03-23
Hmm, I'm another frustrated "relatively" long time ubuntu user (2+ years).  The irony is that I bought this adapter specifically because it was green lighted.  I was compensating for my VT6566 built into my zotac gf3900g-e that never worked well - sheesh.

Anyway, I downloaded the latest 3070 driver (2.3.0.1) from ralink since I have the DLINK DWA-140 B2 version, but when I open the tar.gz it it's still referencing the 2870.  The dat files are RT2870* vs. what I would expect: RT3070*.  Also the french guide talks about checking the os/linux/usb_main_dev.c for a reference to my device ID: 07d1:3c0a , but that is nowhere to be found.

I think ralink might have just posted an incorrect driver version accidentally, which all leads to my ultimate request:

Does anyone have the tar.gz file for the version referenced in the french guide (2.1.2.0 or any version prior to the 2.3.0.1 for that matter) that they might be able to post here or email to me?  I'd love to have this driver hell behind me finally.  Seems like if it's not one thing it's another.

My email is my username here @yahoo.com.

Thanks very much in advance.
g

---

### Post by georgevaccaro on 2010-03-23
> **georgevaccaro said:**
> Hmm, I'm another frustrated "relatively" long time ubuntu user (2+ years).  The irony is that I bought this adapter specifically because it was green lighted.  I was compensating for my VT6566 built into my zotac gf3900g-e that never worked well - sheesh.

Anyway, I downloaded the latest 3070 driver (2.3.0.1) from ralink since I have the DLINK DWA-140 B2 version, but when I open the tar.gz it it's still referencing the 2870.  The dat files are RT2870* vs. what I would expect: RT3070*.  Also the french guide talks about checking the os/linux/usb_main_dev.c for a reference to my device ID: 07d1:3c0a , but that is nowhere to be found.

I think ralink might have just posted an incorrect driver version accidentally, which all leads to my ultimate request:

Does anyone have the tar.gz file for the version referenced in the french guide (2.1.2.0 or any version prior to the 2.3.0.1 for that matter) that they might be able to post here or email to me?  I'd love to have this driver hell behind me finally.  Seems like if it's not one thing it's another.

My email is my username here @yahoo.com.

Thanks very much in advance.
g

OK, got it working thanks to finding an older driver attached to a forum here: [http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html](http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html)

It appears that one of my two hints that there was something wrong with the latest 3070 driver from ralink was incorrect as this version too had the root dat files names starting with "RT2870", but the usb_main_dev.c did have a reference to my model in this earlier version.  I'm not sure why the newer one doesn't but I'm up and running.  Hopefully this weird find will help the next in line.

Good luck!
g

---

### Post by drubdrub on 2010-04-03
> **georgevaccaro said:**
> OK, got it working thanks to finding an older driver attached to a forum here: [http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html](http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html)

It appears that one of my two hints that there was something wrong with the latest 3070 driver from ralink was incorrect as this version too had the root dat files names starting with "RT2870", but the usb_main_dev.c did have a reference to my model in this earlier version.  I'm not sure why the newer one doesn't but I'm up and running.  Hopefully this weird find will help the next in line.

Good luck!
g

That was my experience too.  Much looks like the RT2870 driver.  Quite confusing at the first glance.
Notes:
[LIST]
[*]File names in the top directory contain "2870"
[*]The Makefil has "CHIPSET = 3070".  A good sign.
[*]Many files in os/linux reference "3070".  Another good sign.
[*]File names in os/linux contain "3070" in the names.  Woohoo!
[*]The README_STA_usb file has errors.  Like the insmod() commands listed there.
[/LIST]

Looks like the rt2870 files were used as a template for the rt3070 driver and attention to detail was lacking.

*Still* not getting this futhermucker working.  Problem:
```

/sbin/insmod rt3070sta.ko
insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module

```

Attempted on a 9.10 system.
Any thoughts on how to get around this problem?  Many, many thanks!!

---

