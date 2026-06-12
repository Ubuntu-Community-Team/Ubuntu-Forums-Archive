---
title: "Netgear WNA3100 driver trouble on Ubuntu 12.04 32bit"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by ThaWade on 2012-09-08
First of all I'd like to say I know there are a few posts already with this topic. I've been through many of them with no luck except I'm more confused than ever. Due to 32bit and 64 bit being used in the same thread.   I'm new to Ubuntu as of 1 or 2 days. Other than the occassional live cd playing.  So if you help me please remember I'm a newbie and need things explained to no end.  

I decided to post all this information(may be overkill) since I saw in previous threads that Chili555 asked then regularly.  Hopefully it's clean enough to read.  Couldn't get it to not keep going past the window. so as not to have to scroll over to read but.. i'm noob when it comes to fourm postings.
EDIT: got this far from post 1695036 (this one really had me confuseand and no sort of luck except to install and uninstall drivers) and 1923143 (got it to detect my device in ndiswrapper -l)   ~I'll be looking through the others i found while i wait on a reply~
Ubuntu 12.04 32bit . Netgear wna3100 usb wireless adapter.  

```
thawade@thawade-desktop:~$ arch 
i686
``````
thawade@thawade-desktop:~$ lsusb 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. Cruzer 
Bus 002 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse 
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business 
Bus 001 Device 015: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
``````
thawade@thawade-desktop:~$ iwconfig 

lo        no wireless extensions. 
 
eth0      no wireless extensions.
``````
thawade@thawade-desktop:~$ ndiswrapper -l 

bcmwlhigh5 : driver installed 
    device (0846:9020) present 
``````
thawade@thawade-desktop:~$ sudo tail -f /var/log/syslog 

Sep  8 14:38:18 thawade-desktop kernel: [ 5954.151901] CPU0: Core temperature/speed normal 
Sep  8 14:39:05 thawade-desktop kernel: [ 6001.028014] [Hardware Error]: Machine check events logged 
Sep  8 14:44:09 thawade-desktop kernel: [ 6304.687501] CPU0: Core temperature above threshold, cpu clock throttled (total events = 30262) 
Sep  8 14:44:09 thawade-desktop kernel: [ 6304.689050] CPU0: Core temperature/speed normal 
Sep  8 14:47:50 thawade-desktop kernel: [ 6526.000021] [Hardware Error]: Machine check events logged 
Sep  8 14:49:14 thawade-desktop kernel: [ 6610.017049] CPU0: Core temperature above threshold, cpu clock throttled (total events = 30753) 
Sep  8 14:49:14 thawade-desktop kernel: [ 6610.018969] CPU0: Core temperature/speed normal 
Sep  8 14:54:17 thawade-desktop kernel: [ 6912.726419] CPU0: Core temperature above threshold, cpu clock throttled (total events = 32259) 
Sep  8 14:54:17 thawade-desktop kernel: [ 6912.728203] CPU0: Core temperature/speed normal 
Sep  8 14:59:21 thawade-desktop kernel: [ 7216.536021] CPU0: Core temperature/speed normal 
``````
thawade@thawade-desktop:~$ sudo modprobe ndiswrapper 
``````
thawade@thawade-desktop:~$ dmesg | grep ndis 

[   15.388705] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
[   15.778325] ndiswrapper (wrap_pnp_start_usb_device:647): reset failed: -19 
[   15.822669] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded 
[   15.822830] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 
[   15.822837] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) 
[   15.822846] ndiswrapper (mp_halt:254): device f4b09480 is not initialized - not halting 
[   15.822850] ndiswrapper: device eth%d removed 
[   15.822928] ndiswrapper: probe of 1-3:1.0 failed with error -22 
[   15.822985] usbcore: registered new interface driver ndiswrapper 
[  694.870378] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded 
[ 1982.437715] usbcore: deregistering interface driver ndiswrapper 
[ 1982.440316] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 
[ 1982.440331] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) 
[ 1982.440342] ndiswrapper (mp_halt:254): device f4ab5480 is not initialized - not halting 
[ 1982.440347] ndiswrapper: device eth%d removed 
[ 1982.440439] ndiswrapper: probe of 1-3:1.0 failed with error -22 
[ 3254.273999] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
[ 3254.339705] usbcore: registered new interface driver ndiswrapper 
[ 3856.360155] usbcore: deregistering interface driver ndiswrapper 
[ 4172.130678] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
[ 4172.236674] usbcore: registered new interface driver ndiswrapper 
[ 4401.168487] usbcore: deregistering interface driver ndiswrapper 
[ 4683.772806] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
[ 4683.799017] usbcore: registered new interface driver ndiswrapper 
``````
thawade@thawade-desktop:~$ sudo cat /var/log/syslog | grep -i ndis | tail -n20 

Sep  8 12:59:20 thawade-desktop kernel: [   15.822837] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) 
Sep  8 12:59:20 thawade-desktop kernel: [   15.822846] ndiswrapper (mp_halt:254): device f4b09480 is not initialized - not halting 
Sep  8 12:59:20 thawade-desktop kernel: [   15.822850] ndiswrapper: device eth%d removed 
Sep  8 12:59:20 thawade-desktop kernel: [   15.822928] ndiswrapper: probe of 1-3:1.0 failed with error -22 
Sep  8 12:59:20 thawade-desktop kernel: [   15.822985] usbcore: registered new interface driver ndiswrapper 
Sep  8 13:10:39 thawade-desktop kernel: [  694.870378] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.437715] usbcore: deregistering interface driver ndiswrapper 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.440316] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.440331] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001) 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.440342] ndiswrapper (mp_halt:254): device f4ab5480 is not initialized - not halting 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.440347] ndiswrapper: device eth%d removed 
Sep  8 13:32:07 thawade-desktop kernel: [ 1982.440439] ndiswrapper: probe of 1-3:1.0 failed with error -22 
Sep  8 13:53:18 thawade-desktop kernel: [ 3254.273999] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
Sep  8 13:53:19 thawade-desktop kernel: [ 3254.339705] usbcore: registered new interface driver ndiswrapper 
Sep  8 14:03:21 thawade-desktop kernel: [ 3856.360155] usbcore: deregistering interface driver ndiswrapper 
Sep  8 14:08:36 thawade-desktop kernel: [ 4172.130678] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
Sep  8 14:08:36 thawade-desktop kernel: [ 4172.236674] usbcore: registered new interface driver ndiswrapper 
Sep  8 14:12:25 thawade-desktop kernel: [ 4401.168487] usbcore: deregistering interface driver ndiswrapper 
Sep  8 14:17:08 thawade-desktop kernel: [ 4683.772806] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
Sep  8 14:17:08 thawade-desktop kernel: [ 4683.799017] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2012-09-08
> [COLOR="Red"]bcmwlhigh5 [/COLOR]: driver installed 
    device (0846:9020) presentWhere did you get your bcmwlhigh5.inf file? From one of my posts? Or...? I am concerned about this:> ndiswrapper (wrap_pnp_start_usb_device:647): reset failed: -19 
[   15.822669] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded 
[   15.822830] ndiswrapper (mp_init:211): couldn't initialize device: C0000001 
[   15.822837] ndiswrapper (pnp_start_device:395): [COLOR="Red"]Windows driver couldn't initialize the device[/COLOR] (C0000001) 
[   15.822846] ndiswrapper (mp_halt:254): device f4b09480 is not initialized - not halting I wonder if you have the wrong .inf file.

---

### Post by ThaWade on 2012-09-08
> **chili555 said:**
> Where did you get your bcmwlhigh5.inf file? From one of my posts? Or...? I am concerned about this:I wonder if you have the wrong .inf file.
 
bcmwlhigh5.inf i did get from one of your posts. The second thread i listed I believe.
 
I'm concerned as well. I was thinking I may need a reinstall after I saw all the errors.
 
EDIT: subscribed to this thread so I will respond faster hopefully. I wasn't really expecting a reply so soon. Thank You!

---

### Post by ThaWade on 2012-09-08
Ok came back to this ubuntu machine after a break it was froze/locked up on a blackish screen.  Rebooted and my wireless card started working? Very weird since I rebooted before I made this thread(or atleast I"m 75% sure I did).  But I did not have my ethernet cable plugged in this time. I know for a fact I did the other times. 

So my questions now are:
1: Does the wired ethernet interfere with a wireless connection? i.e. installing drivers etc. I disconnected wired 1  to let wireless1 connect after i saw 
bcmwlhigh5 : driver installed
 device (0846:9020) present
2: When and how often should you reboot while running different commands in the Terminal?
3: Is there a Thread for Terminal do's and don'ts?
4. Do you need to reboot after every install/uninstall in the terminal
Now I have these

t```
hawade@thawade-desktop:~$ iwconfig
```lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin.d8e"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 08:86:3B:2F:FD:8E   
          Bit Rate=270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```
thawade@thawade-desktop:~$ ndiswrapper -l
```bcmwlhigh5 : driver installed
    device (0846:9020) present

```
thawade@thawade-desktop:~$ dmesg |grep ndis
```[   16.521588] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   17.077150] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   17.783514] usbcore: registered new interface driver ndiswrapper
[  220.996658] ndiswrapper: device wlan0 removed
[  228.074620] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded

```
thawade@thawade-desktop:~$ sudo cat /var/log/syslog | grep -i ndis | tail -n20
```Sep  8 18:50:46 thawade-desktop kernel: [   16.521588] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Sep  8 18:50:46 thawade-desktop kernel: [   17.077150] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
Sep  8 18:50:46 thawade-desktop kernel: [   17.777129] wlan0: ethernet device 30:46:9a:29:ba:99 using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
Sep  8 18:50:46 thawade-desktop kernel: [   17.783514] usbcore: registered new interface driver ndiswrapper
Sep  8 18:50:54 thawade-desktop NetworkManager[767]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Sep  8 18:54:08 thawade-desktop kernel: [  220.996658] ndiswrapper: device wlan0 removed
Sep  8 18:54:15 thawade-desktop kernel: [  228.074620] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
Sep  8 18:54:16 thawade-desktop kernel: [  228.666719] wlan0: ethernet device 30:46:9a:29:ba:99 using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
Sep  8 18:54:16 thawade-desktop NetworkManager[767]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 4)

Link to thread i used [http://ubuntuforums.org/showthread.php?t=1923143](http://ubuntuforums.org/showthread.php?t=1923143) used the driver files in post #5. Gonna move the machine back to the other room. we'll see if it keeps working.
I think my post may be too much. But I wanted a thorough post. Not one like Post 1: this doesn't work. Post 2: It works/still doesn't work.  You know?

---

### Post by chili555 on 2012-09-08
Your readings in your last post look just fine. I wouldn't fight momentum; if it works, it works.

Only rarely should one have to reboot to get a new driver working. It is often the easiest way to *change* a driver rather than unloading the old driver, reloading the new driver, restarting networking, restarting Network Manager and probably a few other things I can't recall! A reboot stops everything and restarts everything.

Having wired running definitely interferes with wireless because Network Manager will disallow wireless if wired, usually faster and more secure, is available.

Here is a good resource about command-line, aka terminal, technique. [http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

I'm glad it's working by whatever means.

---

### Post by ThaWade on 2012-09-08
> **chili555 said:**
> I'm glad it's working by whatever means.

Thank you chili555, I will marked this as solved since its working. And Just want to say I'm sorry to the entire Ubuntu forums community for wasting so much forum space on something that fixed itself.

---

### Post by chili555 on 2012-09-08
> And Just want to say I'm sorry to the entire Ubuntu forums community for wasting so much forum space on something that fixed itself.Don't even think about it. No one wants anything except to get you and others running properly. Sometimes we get lucky and the stars align and things fix themselves. I actually pray for that every night but seldom get one. Thanks for the bone!

I'll take your Solved!

---

