---
title: "Trouble getting DWA-125 USB Adapter, Rev. A2 to work.."
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by meiji1 on 2011-11-11
Hi there,

I know that driver issues with the DWA-125 wireless adapter rev. a2 on Ubuntu have been discussed many times here and elsewhere. 

I've looked over many of those threads carefully and I'm still not able to get very far. I compiled the rt2870sta driver from the sources as per chili555's (? I think that's his name..) instructions, and though that did result in an ra0 interface finally turning up in the iwconfig output, I wasn't able to get much further. In the device tab under Network Tools, the ra0 interface is an 'unknown device'..

I also installed ndiswrapper and ndisgtk from their debs, and none of the drivers on the packaged CD would load. One driver in particular keeps freezing my machine.

I'm thinking I need to post my own machine info to get anywhere on this, since I've exhausted every other avenue.

Thanks very much.

---

### Post by chili555 on 2011-11-11
Yep, that's my name. Please open a terminal and run and post:```
lsmod | grep rt2
dmesg | grep rt2
lsusb
uname -r
```Thanks.

---

### Post by meiji1 on 2011-11-11
Sure thing.

lsmod | grep rt2:
rt2870sta             619034 0

dmesg | grep rt2:
[    0.9812983] usbcore: registered new interface driver rt2870

lsusb:
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:1004 Hewlett-Packard DeskJet 970c/970cse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 002 Device 003: ID 07d1:3c16 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -r:
2.6.32-33-generic

---

### Post by chili555 on 2011-11-11
So far, so good. Now let's see:```
iwconfig
sudo iwlist ra0 scan
```I'll have to check in tomorrow. Good night.

---

### Post by meiji1 on 2011-11-11
iwconfig:
lo         no wireless extensions.

eth0       no wireless extensions.

ra0        Ralink STA
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sudo iwlist ra0 scan:
ra0       Interface doesn't support scanning.

Good night chili, thanks for your help.

---

### Post by meiji1 on 2011-11-12
Ok, I typed "ifconfig ra0 up" at the command line and the ra0 interface has been added to the ifconfig output. Also, the network adapter stick is now actively blinking. Not sure what to do now -- there's no change in Network Tools or in the Network Manager.

I type 'iwlist scan' and get back 
ra0                  No scan results

---

### Post by chili555 on 2011-11-12
When you compiled according to my instructions, are you quite sure you made the changes to config.mk outlined in the README? Can you give me a link to the outline you followed? I've written dozens.

---

### Post by meiji1 on 2011-11-12
I did not take the config.mk step, I'm certain of that. Still looking for the thread I followed. As you say, there's quite a few. :P

EDIT: I followed this one, although I'm sure I omitted some steps:

[http://ubuntuforums.org/showthread.php?t=1625657](http://ubuntuforums.org/showthread.php?t=1625657)

---

### Post by chili555 on 2011-11-12
> although I'm sure I omitted some stepsAnd then it didn't work perfectly; imagine that.

Please open the folder you extracted and navigate to the folder os then to linux and open the file config.mk with a text editor. Then set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor. Now we must recompile. Open a terminal and navigate to the location of the downloaded file; for example, if it's on your desktop:```
cd Desktop/2010_some_file
sudo su
make clean
make
make install
exit
```Reboot and tell us if things are improved.

---

### Post by meiji1 on 2011-11-12
Well, I can now attempt to connect to my wireless router with Network Manager, at least after configuring /etc/Wireless/RT2870STA/RT2870STA.DAT with my network information, but it won't connect. A panel will come up saying that I need to provide authentication, which I've done.

---

### Post by meiji1 on 2011-11-12
Well, I can now attempt to connect to my wireless router with Network Manager, at least after configuring /etc/Wireless/RT2870STA/RT2870STA.DAT with my network information, but it won't connect. A panel will come up saying that I need to provide authentication, which I've done.
 
EDIT: I'm now able to get to 'Connection established' on my network, but nothing loads in Firefox and there's some funky looking non class C IP address on the interface when I look at it in Network Tools.

---

### Post by chili555 on 2011-11-12
> after configuring /etc/Wireless/RT2870STA/RT2870STA.DAT with my network information,Including your encryption details as per the README?

---

### Post by meiji1 on 2011-11-12
Yes, the AuthMode, EncrypType, SSID and WPAPSK keys all reflect my router settings. Specifically,

AuthMode = WPA2PSK
EncrypType = AES

---

### Post by chili555 on 2011-11-12
Let's see what Network Mangler has to say about all this:```
sudo cat /var/log/syslog | grep -e etwork -e rt2 -e ra0 | tail -n25
```

---

### Post by meiji1 on 2011-11-12
OK, the result is

Nov 12 13:01:33 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 12 13:01:33 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Nov 12 13:01:33 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 12 13:01:33 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 12 13:01:33 mark-ubuntu-desktop NetworkManager: <info>  DHCP: device ra0 state changed (null) -> preinit
Nov 12 13:01:33 mark-ubuntu-desktop dhclient: Listening on LPF/ra0/34:08:04:9b:d3:45
Nov 12 13:01:33 mark-ubuntu-desktop dhclient: Sending on   LPF/ra0/34:08:04:9b:d3:45
Nov 12 13:01:33 mark-ubuntu-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Nov 12 13:01:39 mark-ubuntu-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
Nov 12 13:01:54 mark-ubuntu-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
Nov 12 13:02:14 mark-ubuntu-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  (ra0): DHCP transaction took too long, stopping it.
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  (ra0): canceled DHCP transaction, dhcp client pid 1822
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Timeout) started...
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0/wireless): could not get IP configuration for connection 'barclay'.
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  (ra0): device state change: 7 -> 6 (reason 0)
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets
Nov 12 13:02:19 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 9 (reason 7)
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) failed for access point (barclay)
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  Marking connection 'barclay' invalid.
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  Activation (ra0) failed.
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  (ra0): device state change: 9 -> 3 (reason 0)
Nov 12 13:09:54 mark-ubuntu-desktop NetworkManager: <info>  (ra0): deactivating device (reason: 0).

---

### Post by chili555 on 2011-11-12
Great; my favorite kind of problem. Everything looks fine except it just doesn't work! Is your router set to the dreaded and difficult mixed WPA and WPA2 mode or, hopefully, single-mode WPA2? You may need to consult the README and make sure if you change the router's settings, you might need to adjust the .dat file. If so, unload and reload the driver to get the new settings to take effect:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```

---

### Post by meiji1 on 2011-11-12
It's in "WPA2 Only" mode, as the router calls it. All the settings in the .dat match those of the router.

---

### Post by meiji1 on 2011-11-12
I think I'll try updating the router firmware (which I've never done) and playing around with the encryption settings. Wish me luck..

---

### Post by chili555 on 2011-11-13
Good luck. We can always try removing the compiled driver and tricking the built-in rt2870sta driver to grab your device; however, your readings suggest no issues with the driver you compiled.

---

### Post by meiji1 on 2011-11-13
I've upgraded the firmware and played with the encryption settings, and it has yielded nothing.

What's really bizarre is that I'm able to petition the DHCP server on the router if I connect to it with a wired connection, by

dhclient eth0

and it works flawlessly. But with 

dhclient ra0

it hangs and then fails a little while later. I've checked the logs on the router, and they say something like,

[date&time] UDHCPD: SIGUSR1 received

immediately following the dhclient ra0 attempt. 

So it seems that the router is acknowledging the DHCP request but unable to do anything with it when it's sent wirelessly. I don't know what to make of this. Could it be a driver issue?

---

### Post by chili555 on 2011-11-13
> [date&time] UDHCPD: SIGUSR1 receivedFrom *man udhcpd*:> SIGUSR1
              This  signal  causes udhcpc to renew the current lease or, if it does not have one, obtain a new lease.That suggests that dhclient, in your computer, asked for a DHCP lease. It's an entirely normal part of the process and, unfortunately, not informative.> Could it be a driver issue? It could be a driver issue, a wpa_supplicant issue or a Network Manager issue. The most usual suspect is, of course, an encryption key issue. I doubt that here because you've been quite detailed and diligent; I'm sure you've checked it a dozen or more times.

Are you sure ndiswrapper is not interfering?```
lsmod | grep ndis
```Are you ready to try removing the compiled driver and tricking the built-in rt2870sta driver to grab your device?

---

### Post by meiji1 on 2011-11-13
lsmod | grep ndis:
ndiswrapper           244800  0 

I thought I removed the ndiswrapper packages with apt-get, but apparently not. ndisgtk is still present at boot, also. I'd like to get rid of them, but I don't know how. I removed ndiswrapper and nothing has changed.

I am definitely ready to try removing the compiled driver and working with the built-in one.

---

### Post by praseodym on 2011-11-13
Remove ndiswrapper and its config via:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```

---

### Post by meiji1 on 2011-11-14
Thanks praseodym, I followed your instructions and they worked.

As for uninstalling the current rt2870sta driver, I went to the directory I built the source from and ran 'make uninstall'. Is that enough to do the job?

---

### Post by praseodym on 2011-11-15
Yes, thats enough

---

### Post by meiji1 on 2011-11-15
Based on hodad's experience in the earlier thread, I tried building the latest rt5370sta module from RAlink's website and it worked, sort of. All the usual wireless networks are now listed in the wicd GUI, and it reports the signal strength of my router at 94%. No wireless networks are reported in Network Manager, oddly enough.

The current problem is that I can't authenticate through to my network in wicd. I typed my PSK in and it comes back with bad password. I can post the wicd logs, if you'd like, or maybe it would be better to get Network Manager to work.

---

### Post by meiji1 on 2011-11-15
I'm now finding that Network Manager not only shows the wireless networks, but is now able to connect without any problems.

It's all working now, thanks for your help.

---

