---
title: "D-Link DWA-125 Wireless-N USB Adapter Problem"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Jordan531 on 2010-08-29
[SIZE=2]Ok, so I've been following some other threads about this, as well as another site. [/SIZE]

These are the main things I've been doing/done.

[http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37)

[http://art.ubuntuforums.org/showthread.php?t=1434630](http://art.ubuntuforums.org/showthread.php?t=1434630)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653/comments/8)

I've  got my wireless adapter working, but under Wireless Networks in the  network manager thing in the top right it says disconnected. 

iwconfig gives me this

> 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I performed the steps in the links above after a clean install of Ubuntu 10.4. 

I'm  sorry if this is a problem that has already been addressed, I looked  around but I couldn't find this specific problem. And I'm a bit of a  newbie to linux, just as a forewarning.

Any help in regards to this issue would be greatly appreciated.

---

### Post by chili555 on 2010-08-29
> These are the main things I've been doing/done.

[http://www.uluga.ubuntuforums.org/sh...4&postcount=37](http://www.uluga.ubuntuforums.org/sh...4&postcount=37)

[http://art.ubuntuforums.org/showthread.php?t=1434630](http://art.ubuntuforums.org/showthread.php?t=1434630)

[https://bugs.launchpad.net/ubuntu/+s...653/comments/8](https://bugs.launchpad.net/ubuntu/+s...653/comments/8)
The problem is that these are conflicting methods. One is to compile a downloaded file and build your own driver and the other is to adapt an existing driver. You must select one or the other, not both.

Let's analyze what you have now. Please post:```
dmesg | grep -e rt2 -e rt3
cat /etc/udev/rules.d/network_drivers.rules
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Jordan531 on 2010-08-29
Ah, I would manage to do something to make it not work. =P

Ok, > [B]
dmesg | grep -e rt2 -e rt3[/B]

[   20.445411] usbcore: registered new interface driver rt2870


**cat /etc/udev/rules.d/network_drivers.rules**

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt3070sta"


**lsmod | grep -e rt2 -e rt3**

rt3070sta             599712  0 
Thanks for the help btw, I really appreciate it.

---

### Post by chili555 on 2010-08-29
It appears you have the compiled version loaded; it is present in lsmod and has created an interface. > in the network manager thing in the top right it says disconnected.Do you see any networks to select? Is there any activity if you click one and try to connect? What does this do for us?```
sudo iwconfig ra0 rate auto
sudo iwlist ra0 scan
sudo cat /var/log/syslog | grep rt3
```Thanks.

---

### Post by Jordan531 on 2010-08-29
Okay well now for some reason it says "device not ready" instead of "disconnected"   

But anyways

> jordan@Jordan-desktop:~$ sudo iwconfig ra0 rate auto
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device ra0 ; Network is down.
jordan@Jordan-desktop:~$ sudo iwlist ra0 scan
ra0       Interface doesn't support scanning : Network is down

jordan@Jordan-desktop:~$ sudo cat /var/log/syslog | grep rt3
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503066]  [<e097f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503094]  [<e097fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503122]  [<e096dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503168]  [<e097b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503203]  [<e097b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220374]  [<e097f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220392]  [<e097fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220412]  [<e096dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220445]  [<e097b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220471]  [<e097b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
I hadn't thought about it until now, but this time when I booted up the adapter wasn't in. Would that affect the fact that it says "device not ready"? Oh, and no I don't see any networks to select.

---

### Post by chili555 on 2010-08-29
Please run:```
lsusb
```Confirm you have an usb.id of 07d1:3c0d. If not, please post what it is.

Next, in a terminal, do:```
cd directory/you/downloaded/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412.bz2
sudo make uninstall
```Now, insert the device and reboot. Then run:```
iwconfig
sudo iwlist wlan0 scan
```Please post the result. Thanks.

---

### Post by Jordan531 on 2010-08-29
Okay, so I already knew this, but I ran **lsusb** again to confirm, my device ID is 07d1:3c16.

So I did the uninstall thing, then I inserted the device, rebooted, and ran these:
> jordan@Jordan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jordan@Jordan-desktop:~$ sudo iwlist wlan0 scan
[sudo] password for jordan: 
wlan0     Interface doesn't support scanning.

Now, however, when I click on the network icon in the top right, it doesn't even list the wireless network there at all.

---

### Post by chili555 on 2010-08-29
The rt3070sta module should work correctly:```
$ modinfo rt3070sta | grep 3C16
alias:          usb:v[COLOR="Blue"]07D1[/COLOR]p[COLOR="Blue"]3C16[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Please run and post:```
lsmod | grep rt3
dmesg | grep rt3
```Thanks.

---

### Post by Jordan531 on 2010-08-29
I ran both of those :
lsmod | grep rt3
dmesg | grep rt3
but neither gave me any results. =(

---

### Post by chili555 on 2010-08-29
Please try:```
sudo modprobe rt3070sta
dmesg | grep rt3
iwconfig
```Thanks.

---

### Post by Jordan531 on 2010-08-29
OK, heres the results.

> jordan@Jordan-desktop:~$ sudo modprobe rt3070sta
[sudo] password for jordan: 
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
jordan@Jordan-desktop:~$ dmesg | grep rt3
jordan@Jordan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-08-29
> $ locate rt3070sta
--- snip ---
/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.koIf you are running 10.04, don't you have this file? Please do:```
sudo updatedb
locate rt3070sta.ko
uname -r
```If you do not have the file matching your running kernel, we'll have to recompile it and do a couple of other steps.

*updatedb* will take a few moments, please be patient.

---

### Post by Jordan531 on 2010-08-29
Okay, heres the results

> jordan@Jordan-desktop:~$ sudo updatedb
jordan@Jordan-desktop:~$ locate rt3070sta.ko
/home/jordan/Desktop/thing/os/linux/.rt3070sta.ko.cmd
/home/jordan/Desktop/thing/os/linux/rt3070sta.ko
jordan@Jordan-desktop:~$ uname -r
2.6.32-24-generic
jordan@Jordan-desktop:~$ 



---

### Post by chili555 on 2010-08-29
Baffling...

Please do:```
cd Desktop/thing
make clean
make
sudo make install
sudo mv /etc/udev/rules.d/network_drivers.rules /etc/udev/rules.d/network_drivers.rules.bak
sudo mv /etc/modprobe.d/network_drivers.conf /etc/modprobe.d/network_drivers.conf.bak
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```You can simply copy and paste the commands. Reboot and let me have your good report. 

We'll get to the bottom of this if it rubs the letters off of my keyboard!

---

### Post by Jordan531 on 2010-08-29
Ok, so I did all that, rebooted, and ran iwconfig


jordan@Jordan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When I click the network icon in the top right bar it says 'disconnected' again under the wireless network.

I'm not sure if I was meant to, but I totally forgot to copy the results of this before I rebooted:

> cd Desktop/thing
make clean
make
sudo make install
sudo mv /etc/udev/rules.d/network_drivers.rules /etc/udev/rules.d/network_drivers.rules.bak
sudo mv /etc/modprobe.d/network_drivers.conf /etc/modprobe.d/network_drivers.conf.bak
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
:?

---

### Post by chili555 on 2010-08-29
We have the interface ra0 back and some progress. Let's see:```
sudo cat /var/log/syslog | grep -e rt2 -e rt3
ls /etc/Wireless
ls /etc/Wireless/RT3070STA
```We're getting closer.

---

### Post by Jordan531 on 2010-08-29
Okay here it is. 

> jordan@Jordan-desktop:~$ sudo cat /var/log/syslog | grep -e rt2 -e rt3
[sudo] password for jordan: 
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503066]  [<e097f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503094]  [<e097fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503122]  [<e096dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503168]  [<e097b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.503203]  [<e097b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3374.508214] !!! rt28xx Initialized fail !!!
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220374]  [<e097f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220392]  [<e097fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220412]  [<e096dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220445]  [<e097b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.220471]  [<e097b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
Aug 29 12:57:05 Jordan-desktop kernel: [ 3375.224319] !!! rt28xx Initialized fail !!!
Aug 29 14:05:55 Jordan-desktop kernel: [ 7505.007393] !!! rt28xx Initialized fail !!!
Aug 29 14:05:56 Jordan-desktop kernel: [ 7505.647979] !!! rt28xx Initialized fail !!!
Aug 29 16:53:31 Jordan-desktop kernel: [10019.277086] usbcore: registered new interface driver rt2870
Aug 29 16:53:32 Jordan-desktop kernel: [10020.225292]  [<e4e3f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.225308]  [<e4e3fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.225326]  [<e4e2dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.225358]  [<e4e3b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.225380]  [<e4e3b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.228046] !!! rt28xx Initialized fail !!!
Aug 29 16:53:32 Jordan-desktop kernel: [10020.675970]  [<e4e3f08a>] NICInitTransmit+0xca/0x920 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.675986]  [<e4e3fb60>] RTMPAllocTxRxRingMemory+0xd0/0x150 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.676006]  [<e4e2dffc>] rt28xx_init+0x9c/0x4e0 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.676046]  [<e4e3b3e0>] rt28xx_open+0x40/0xc0 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.676079]  [<e4e3b708>] MainVirtualIF_open+0xb8/0x140 [rt3070sta]
Aug 29 16:53:32 Jordan-desktop kernel: [10020.678904] !!! rt28xx Initialized fail !!!
Aug 29 16:54:53 Jordan-desktop kernel: [    8.856991] usbcore: registered new interface driver rt2870
Aug 29 16:54:54 Jordan-desktop kernel: [   12.964269] !!! rt28xx Initialized fail !!!
Aug 29 16:54:55 Jordan-desktop kernel: [   14.068198] !!! rt28xx Initialized fail !!!


> jordan@Jordan-desktop:~$ ls /etc/Wireless
RT3070STA
jordan@Jordan-desktop:~$ ls /etc/Wireless/RT3070STA
RT3070STA.dat
jordan@Jordan-desktop:~$ 


---

### Post by chili555 on 2010-08-29
Everything actually looks very good until we see:> Jordan-desktop kernel: [ 14.068198] !!! rt28xx Initialized fail !!! I am Googling and scratching my gray beard. Will be back later.

---

### Post by Jordan531 on 2010-08-29
Ok, thanks a lot man, I really appreciate it.

Would it help if i just did a fresh install of 10.4? Cause thats easy, it won't take long, I already did it once today anyways =P

---

### Post by chili555 on 2010-08-29
> Cause thats easy, it won't take long, I already did it once today anyways =PNope. We'll fix it in the morning. Are you in Western Canada; that is Pacific Time?

---

### Post by Jordan531 on 2010-08-29
Yep that's correct. I'll be up and available from at least 8 am PST on. Thanks again for the help. :)

---

### Post by chili555 on 2010-08-30
First, let's make sure that Network Manager is not interfering. Please see: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Especially see:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themIf you disconnect the ethernet cable, does the wireless begin to cooperate? 

If not, let's do some major surgery. You can copy and paste the commands from this post right into the terminal. Please do:```
cd Desktop/thing
sudo make uninstall
sudo gedit /etc/modules
```Change the line that reads rt3070sta to rt2870sta. Proofread, save and close gedit.```
sudo mv /etc/udev/rules.d/network_drivers.rules.bak /etc/udev/rules.d/network_drivers.rules
sudo mv /etc/modprobe.d/network_drivers.conf.bak /etc/modprobe.d/network_drivers.conf
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Change every instance of rt3070sta to rt2870sta. Proofread, save and close gedit. ```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Change every instance of rt3070sta to rt2870sta. Proofread, save and close gedit.

Now with the device inserted and the ethernet cable detached, reboot and give us all a good report...please!

---

### Post by Jordan531 on 2010-08-30
Aaaaaannnnddd IT WORKS!!! 

Beauty!

Thank you so much for your help! Hopefully I won't have any problems with it from here on out. 

Thanks again!

---

### Post by hodad on 2010-09-07
I've been trying to get the DWA-125 working also (for the last 10 hrs!).

I compiled the 2870 and 3070 drivers (as far as I can tell), but get nothing when I "grep" them as listed above.  The files seem to be there, but I don't think that they're getting to the proper locations in the filesystem (folders don't always match ones listed in the above instructions, though there are similar ones with the same files!?

At one point, I had the card lights flashing every ten seconds or so (looked like it was transmitting), but that was just a tease...   All day long I haven't been able to see any wireless entry on ifconfig.

Any idea on a strategy?  

Thanks!

---

### Post by chili555 on 2010-09-07
First, let's be sure your device is the same as referenced in the prior posts. Please run:```
lsusb
```Does your device have a usb.id of 07d1:3c0d? If not, please post it.> I compiled the 2870 and 3070 drivers The procedures above do *NOT* require compiling drivers! We may need to undo what's been done so far. Please post:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```We'll sort it out.

I am in the Eastern USA and so we may sort it out after a few hours sleep.

---

### Post by hodad on 2010-09-07
Thanks for your quick response!

Looks like I just got it working about 15 minutes ago using some more of your instructions, which I somehow missed earlier. My internet is running very slow (maybe I still have something wrong with the connection?), so couldn't reply quickly enough; sorry. 

Tomorrow, I'd like to go back thru all of this to see what I did, and perhaps summarize for others.  

Meanwhile, Thanks again, and have a good nap!

---

### Post by chili555 on 2010-09-08
Glad it's working. Please post back if you need more help.

---

### Post by hodad on 2010-09-08
I guess I got too cocky.

It's my kids pc, and I just loaded 10.04 on it, leading to this problem.  It was working great all day today, until I painstakingly reinstalled all of the hardware back into their room, with cables neatly routed and cable tied. Immediately, and for no apparent reason, it stopped working again@#$!

Symptom (from message log): no longer recognizing the driver, no wlan0 listing under iwconfig; in other words, back to square one!

One major hint though:
I realized that there was a spare drive hooked up inside the pc (two hard drives hooked up), so it may be that the relevent files are duplicated (I noticed that both drives have a full file system).  Perhaps the app is getting confused between duplicate file systems (?).  I unhooked the spare drive, and rebooted, now I'll start noodling again I guess.  Any suggestions appreciated , but I'll probably just try and "make" again.

---

### Post by chili555 on 2010-09-08
> **hodad said:**
> I guess I got too cocky.

It's my kids pc, and I just loaded 10.04 on it, leading to this problem.  It was working great all day today, until I painstakingly reinstalled all of the hardware back into their room, with cables neatly routed and cable tied. Immediately, and for no apparent reason, it stopped working again@#$!

Symptom (from message log): no longer recognizing the driver, no wlan0 listing under iwconfig; in other words, back to square one!

One major hint though:
I realized that there was a spare drive hooked up inside the pc (two hard drives hooked up), so it may be that the relevent files are duplicated (I noticed that both drives have a full file system).  Perhaps the app is getting confused between duplicate file systems (?).  I unhooked the spare drive, and rebooted, now I'll start noodling again I guess.  Any suggestions appreciated , but I'll probably just try and "make" again.Please post the details I requested in post #25. Thanks.

---

### Post by hodad on 2010-09-08
have to hand copy, since I'm sending this on my "main" pc.  Kids pc results of lsusb confirms 07d1:3c16

lsmod egrep "rt2" lists:
rt2870sta (with some trailing numbers)

lsmod egrep "rt3" lists:
(blank)

dmesg egrep "rt2" lists:
(numbers) RT2870sta: module is in the staging directory, quality unknown, ...warned.
(numbers) usbcore:registered new interface driver rt2870

dmesg egrep "rt3" lists:
(blank)

I'll be going to bed soon, will resume in AM

Thanks!

---

### Post by chili555 on 2010-09-09
It looks like, in *lsmod*, that the correct driver is loaded. *dmesg* doesn't report any errors or warnings. We're halfway home!

Next, please do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread twice, save and close gedit. Next, do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit.

Reboot and give us your report.

---

### Post by hodad on 2010-09-09
The adapter came on for a minute (it was blinking, and the networking icon was green), but then it dropped out again and now is offline.  I tried to ping the router, but I guess I was too late.


The wireless USB adapter came up on boot (I could tell because it was blinking), but Firefox was still "offline", and I couldn't get it online using Preferences-Network.

---

### Post by hodad on 2010-09-09
Status:
I rebooted, and adapter started blinking.  I ran Wicd network manager, and it seems to be trying to authenticate the pw with the router, but the router isn't responding. I checked the wireless security settings (WPA personal and the pw) - both good.   Wicd just posted: Connection failed- bad password, and the adapter stopped blinking.   
Will keep noodling...

---

### Post by hodad on 2010-09-09
Some more troubleshooting data:

I can restart the wireless by clicking on the network icon in the toolbar.  It tries to authenticate, but fails after a couple of minutes of trying.

I watched syslog scrolling by as the wireless adapter tried to authenticate with the router:

trying to associate with 00:1e:58:e8:f5:db SSID axmey (name I chose for router)
association request to driver failed.

I rechecked all of the security and PW settings, and they're good.

---

### Post by chili555 on 2010-09-09
Is your router set for WPA or WPA2? Some routers allow a mixed WPA *and* WPA2 mode which is very difficult for some drivers (or maybe wpa_supplicant) to associate with. If yours is so configured, pick one or the other, not both.

---

### Post by hodad on 2010-09-09
Only get one choice WPA or WPA2 Personal (if I recall correctly).

It's acedemic at the moment, as I decided to wipe the machine and start again...  I noticed that the two hard drives each had full ubuntu file systems, and that some of the application data I had been installing was mixed between the two drives.  Seemed like an unhealthy situation, so I have started to reload Edubuntu.  

Will check back after I get reinstalled.

Thanks for your help, and I'll return a little later...

---

### Post by chili555 on 2010-09-09
I'll be around. Looking forward to your report.

---

### Post by hodad on 2010-09-09
I'm back up with a clean 10.04 install.

adapter is still acting the same as before I wiped the drives and performed a complete reinstall; flashing, but won't authenticate.

iwconfig now reads:

wlan0  RTxx70   Wireless ESSID = "" Nickname "RT3070STA"
etc...

when I "lsmod |egrep "rt2" it finds rt2870sta

when I "lsmod |egrep "rt3" it finds nothing

iwlist wlan0 scan shows everything in order (as far as I can tell), lists proper ESSID for my router "axmey".  Does show "encryption key: on", I think for WPA and WPA2 Personal setting).

---

### Post by chili555 on 2010-09-09
That all sounds quite good! Can you click the Network Manager icon and connect?

---

### Post by hodad on 2010-09-09
System-Preferences Network Connections lists the wireless connection as SSID:axmey, everything else is fine. Checked ssid,pw, and WPA security settings on d-link router, and they are the same as entered on the pc. Still doesn't authenticate...

---

### Post by hodad on 2010-09-09
When I click on  the network icon (on sidebar, the one that's green), it shows a small padlock symbol on it that won't go away.

---

### Post by hodad on 2010-09-09
I plugged in an ethernet cable from the kids pc to the router, and am typing this from their pc, so the wired connection works fine.  I guess I'll unplug and see what happens.  Sorry about all of the short messages...

---

### Post by chili555 on 2010-09-09
Like the little padlock next to GBR1? That simply means the network is encrypted. If you click on the name of the network, you should be asked for the WPA password and connect.

---

### Post by hodad on 2010-09-09
Tried that about 20 times; it asks for the pw, i re-enter it, and nothing happens.  I did notice again that iwconfig shows the ESSID field "". Is that significant?

---

### Post by chili555 on 2010-09-09
The "" field simply means it's not yet associated with any network. Please post:```
sudo iwlist wlan0 scan
```I assume your wireless interface is wlan0; substitute if needed.

---

### Post by hodad on 2010-09-09
dave@kids-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:E8:F5:DB
                    Protocol:802.11b/g/n
                    ESSID:"axmey"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-27 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

dave@kids-desktop:~$

---

### Post by hodad on 2010-09-09
Got it working by turning off WPA security in both router and network manager!  I had checked all of the technical specs on both ends, and they were identical, so you were right about the WPa and WPA2 causing problems!

Now I just need to figure out how to re-enable security...

Maybe I'll try the WEP-128 key method.

---

### Post by hodad on 2010-09-09
Didn't work with WEP 128, so I went back to WPA and WPA2 with the same pw I used before.  

I found the command sudo iwlist wlan0 scan, which revealed the following:
The router had TKIP and AES, while the desktop had TKIP only under Group Cipher.  I changed the router to TKIP (only).  I also checked the protocol was the same 802.11 n, g, and b in both units (the router only had one checked, can't remember which).

Apparently, one or the other of the above worked! All told, it only took me four days to get the d-link card working with the dlink router!!! (I realize that's nothing to crow about).  Oh well, at least I learned a few commands!

Thanks for your help on this!  I am going to summarize my 20 pages of notes now. If I come up with anything readable, I'll post it.

---

### Post by chili555 on 2010-09-09
I'm glad it's (finally) working!

---

### Post by marvalis on 2010-09-30
My wireless DWA-125 connection was working until today (usb.id of 07d1:3c0d), changing rt3070sta to rt2870sta in all relevant files solved the problem.

I have no idea why it stopped working with rt3070, but thanks for the sollution.

FYI:[http://wiki.debian.org/rt2870sta#supported](http://wiki.debian.org/rt2870sta#supported)
> USB: 07D1:3C0D D-Link System DWA-125 Wireless N 150 Adapter(rev.A1) [Ralink RT2870]

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Guys , 

Could you please help me out on this driver problem ?

I'm using DWA-125 V.A2 (rt2870) .

By the way i'm using with Sheeva Plug which is on ARM processor  .

It seems that the OS has known the devices but it cannot start it . 

Let me post some of the result for you so that maybe you can help me out . 

When I run 

ifconfig wlan0 up

this is the result...

ifconfig wlan0 up
usb 1-1: firmware file rt3070.bin request failed (-2)
ERROR! NICLoadFirmware failed, Status[=0x00000001]
rt28xx Initialized fail!
SIOCSIFFLAGS: Operation not permitted


and 

dmesg | grep -e rt2 -e rt3

then

rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
usbcore: registered new interface driver rt2870
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!
usb 1-1: firmware file rt3070.bin request failed (-2)
rt28xx Initialized fail!


and

lsmod | grep -e rt2 -e rt3

then


rt2870sta             405245  0


I don't know what else should i do to try to make this device working with my sheevaplug.

By the way , kernel is 2.6.36.2

Would you guys please help advising on how to fix this ?

Thank you very much .

---

### Post by penny2524 on 2011-01-10
Really apologize for the duplicate post , 
I thought it didn't go through .

Sorry for the inconvenience .

---

### Post by chili555 on 2011-01-10
You could take this file and download it to your desktop. Right-click it and select 'Extract Here.' Open the terminal and do:```
cd Desktop
sudo cp rt3070.bin /lib/firmware
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```Now is it working?

---

### Post by penny2524 on 2011-01-10
> **chili555 said:**
> You could take this file and download it to your desktop. Right-click it and select 'Extract Here.' Open the terminal and do:```
cd Desktop
sudo cp rt3070.bin /lib/firmware
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```Now is it working?


Hi Chili555

Here is what I got from each command

rmmod -f rt2870sta

usbcore: deregistering interface driver rt2870
rtusb_disconnect: unregister usbnet usb-orion-ehci.0-1.3
RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
 RTUSB disconnect successfully
<--- rtusb exit


and 

modprobe rt2870sta


rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
rtusb init --->
=== pAd = e115a000, size = 472168 ===
<-- RTMPAllocAdapterBlock, Status=0
usbcore: registered new interface driver rt2870

#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
<-- ERROR in Alloc TX TxContext[3] struct rt_httx_buffer!
<-- RTMPAllocTxRxRingMemory, Status=3
ERROR! RTMPAllocDMAMemory failed, Status[=0x00000003]
rt28xx Initialized fail!

So It still doesn't work yet . 
Any other ideas ??

---

### Post by penny2524 on 2011-01-10
And modinfo command give me this 

modinfo rt2870sta


filename:       /lib/modules/2.6.36.2/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93E93E3E336F412601AF0FA
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.36.2 preempt mod_unload ARMv5 
parm:           mac:rt28xx: wireless mac addr (charp)

---

