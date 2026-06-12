---
title: "D-Link DWA-125 - Help Please"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by SolitaryMan1941 on 2010-06-21
Hello,

     I have been reading all of the threads on this issue and have tried a few solutions to no avail. I'm hoping that there is a solution to my problem, as a brand newbie I'm often flustered by this process. I cannot get the D-Link DWA-125 USB Adapter recognized or up and running. Here's a bit of info to get the thread started:

**iwconfig**
```
o        no wireless extensions.

eth0      no wireless extensions.
```[B]lsusb
[/B]```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5506 SanDisk Corp. 
Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**sudo modprobe rt2800usb**
```
blank
```[B]
lsmod | grep -e rt2 -e rt3
[/B]```
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
```[B]dmesg | grep -e rt2 -e rt3
[/B]```
[  776.764473] usbcore: registered new interface driver rt2800usb
```I also updated with
```
sudo gedit /etc/udev/rules.d/network_drivers.rules

Add one long line:
Code:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1",  ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe  -qba rt3070sta"

Proofread twice, save and close gedit.
Code:

sudo gedit /etc/modprobe.d/network_drivers.conf

Add one long single line:
Code:

install rt3070sta /sbin/modprobe --ignore-install rt3070sta  $CMDLINE_OPTS; /bin/echo "07d1 3c16" >  /sys/bus/usb/drivers/rt2870/new_id

Proofread twice, save and close gedit.
```Any ideas?

---

### Post by Bucky Ball on 2010-06-21
With a cable plugged in, plug in the wireless adapter then update with this:

```
sudo apt-get update
```

... in a terminal.

---

### Post by b k on 2010-06-21
> **SolitaryMan1941 said:**
> Hello,

     I have been reading all of the threads on this issue and have tried a few solutions to no avail. I'm hoping that there is a solution to my problem, as a brand newbie I'm often flustered by this process. I cannot get the D-Link DWA-125 USB Adapter recognized or up and running. Here's a bit of info to get the thread started:

**iwconfig**
```
o        no wireless extensions.

eth0      no wireless extensions.
```[B]lsusb
[/B]```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5506 SanDisk Corp. 
Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**sudo modprobe rt2800usb**
```
blank
```[B]
lsmod | grep -e rt2 -e rt3
[/B]```
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
```[B]dmesg | grep -e rt2 -e rt3
[/B]```
[  776.764473] usbcore: registered new interface driver rt2800usb
```I also updated with
```
sudo gedit /etc/udev/rules.d/network_drivers.rules

Add one long line:
Code:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1",  ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe  -qba [COLOR=Blue]rt3070sta[/COLOR]"

Proofread twice, save and close gedit.
Code:

sudo gedit /etc/modprobe.d/network_drivers.conf

Add one long single line:
Code:

install [COLOR=Blue]rt3070sta[/COLOR] /sbin/modprobe --ignore-install [COLOR=Blue]rt3070sta[/COLOR]  $CMDLINE_OPTS; /bin/echo "07d1 3c16" >  /sys/bus/usb/drivers/rt2870/new_id

Proofread twice, save and close gedit.
```Any ideas?

Hi there, you may wish to try this:

Change every instance of [COLOR=Blue]rt3070sta[/COLOR] to [COLOR=Red]rt2870sta[/COLOR] (remember to save).

Reboot

Post the output of **lsmod | grep -e rt2 -e rt3 **again

Hope the suggestion helps you.

---

### Post by SolitaryMan1941 on 2010-06-21
I have taken Bucky Ball's advice and updated via:
```
sudo apt-get update
```I have taken b k's advice and replaced very instance of [COLOR=Blue]rt3070sta[/COLOR] to [COLOR=Red]rt2870stae [COLOR=Black]in gedit, saved and rebooted. Here is the output from

[/COLOR][/COLOR][B]lsmod | grep -e rt2 -e rt3
[/B]```
rt2800usb              33496  0 
rt2x00usb              11260  1 rt2800usb
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb

```The USB adapter is still not working. Any more ideas?

---

### Post by b k on 2010-06-21
> **SolitaryMan1941 said:**
> I have taken Bucky Ball's advice and updated via:
```
sudo apt-get update
```I have taken b k's advice and replaced very instance of [COLOR=Blue]rt3070sta[/COLOR] to [COLOR=Red]rt2870stae [COLOR=Black]in gedit, saved and rebooted. Here is the output from

[/COLOR][/COLOR]The USB adapter is still not working. Any more ideas?

Hi there, I assume that [COLOR=Red]rt2870stae [COLOR=Black]is a typo error.

Please post output of :

[/COLOR][/COLOR]```
dmesg | tail -n15
```



```
sudo gedit /etc/modprobe.d/blacklist.conf
```

add this line at the end of the opened file:

blacklist rt2800usb

at the same time check if there is a line like *blacklist rt2870sta* - [COLOR=Red]if[/COLOR] there is put a [COLOR=Red]#[/COLOR] in front like this:

*[COLOR=Red]#[/COLOR]blacklist rt2870sta*

Remember to [COLOR=Blue]save[/COLOR] and close.

Reboot and see if there is any change.

Whatever is suggested above can be easily undone later on if not successful.

Suggest you try the above steps first.

There appears to be a working solution at post #8 here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653) but this solution involves much more work.
[COLOR=Blue]It is important[/COLOR] to 'undo' whatever you have done previously before attempting this solution.

Thanks and post back.

---

### Post by SolitaryMan1941 on 2010-06-23
b k here is the output from 
**dmesg | tail -n15**
```
[   21.521428] CPU1 attaching sched-domain:
[   21.521431]  domain 0: span 0-1 level MC
[   21.521435]   groups: 1 0
[   41.475241] eth0: link up.
[   41.475759] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   46.000047] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   46.232259] usb 2-1: configuration #1 chosen from 1 choice
[   46.307568] usbcore: registered new interface driver hiddev
[   46.314535] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.0/input/input4
[   46.314689] generic-usb 0003:1241:F767.0001: input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:04.0-1/input0
[   46.325741] input: HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.1/input/input5
[   46.325973] generic-usb 0003:1241:F767.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz Trackball Keyboard] on usb-0000:00:04.0-1/input1
[   46.326022] usbcore: registered new interface driver usbhid
[   46.326025] usbhid: v2.6:USB HID core driver
[   51.640018] eth0: no IPv6 routers present
```

---

### Post by SolitaryMan1941 on 2010-06-23
I have taken b k's advice and added 

blacklist rt2800usb via
     ```
sudo gedit /etc/modprobe.d/blacklist.conf 
``` there was no line *blacklist rt2870sta* to put a # in front of

I saved rebooted and still have no wireless connection.

---

### Post by SolitaryMan1941 on 2010-06-23
Here is the updated output from 

[B]dmesg | tail -n15
[/B]  ```
[   19.391477] nvidia 0000:00:10.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22
[   19.391490] nvidia 0000:00:10.0: setting latency timer to 64
[   19.391495] vgaarb: device changed decodes: PCI:0000:00:10.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.391724] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   21.890329] CPU0 attaching NULL sched-domain.
[   21.890337] CPU1 attaching NULL sched-domain.
[   21.935056] CPU0 attaching sched-domain:
[   21.935061]  domain 0: span 0-1 level MC
[   21.935064]   groups: 0 1
[   21.935071] CPU1 attaching sched-domain:
[   21.935073]  domain 0: span 0-1 level MC
[   21.935075]   groups: 1 0
[   27.310104] eth0: no IPv6 routers present
[  117.663432] eth0: link down.
[  145.163103] eth0: link up.
```

---

### Post by b k on 2010-06-24
> **b k said:**
> Hi there, I assume that [COLOR=red]rt2870stae [COLOR=black]is a typo error.[/COLOR]
 
[COLOR=red]Please post output of :[/COLOR]
 
[/COLOR]```
dmesg | tail -n15
```
 
 
 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
add this line at the end of the opened file:
 
blacklist rt2800usb
 
at the same time check if there is a line like *blacklist rt2870sta* - [COLOR=red]if[/COLOR] there is put a [COLOR=red]#[/COLOR] in front like this:
 
*[COLOR=red]#[/COLOR]blacklist rt2870sta*
 
Remember to [COLOR=blue]save[/COLOR] and close.
 
Reboot and see if there is any change.
 
Whatever is suggested above can be easily undone later on if not successful.
 
Suggest you try the above steps first.
 
There appears to be a working solution at post #8 here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653) but this solution involves much more work.
[COLOR=blue]It is important[/COLOR] to 'undo' whatever you have done previously before attempting this solution.
 
Thanks and post back.
 
_Edited :_ Link above is probably not appropiate as it is for device id 07d1:[COLOR=red]3c0d [/COLOR][COLOR=black]- sorry.[/COLOR]
This link [http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630) seems more appropriate although the procedure described applies to [COLOR=red]Ubuntu 9.10[/COLOR] and the suggested solution was by chili555 at some other thread - amended slightly for your device id.
 
 
Digging around on the internet and on this forum, it seems that your device id is not being claimed by the appropriate driver.
 
When you first started rt2800usb driver was loaded but the driver did not 'claim' your device id.
I guessed that it was the wrong driver for your device (again based on the scant info available from the internet).
 
It seemed like rt2870sta was the more likely (this is included in the Ubuntu 10.04 LTS) but again this driver did not 'claim' your device id. What was essentially done was trying to 'inject' your device id into the rt2870sta.
This seems to have failed - you can check with the *lsmod *command again to see if it is been loaded.
 
Your original code/commands also did not work because the rt3070sta has apparently being merged with the rt2870sta in Ubuntu 10.04 LTS.
 
If your device came with a driver installation CD (for windows) could you see whether there is any clue in the windows driver as to which of the above drivers is the correct one.
 
*ndiswrapper *is an additional program which can be installed in Ubuntu to use the Windows drivers (no guarantees though).
 
I am currently out of ideas so if there is anyone who can help [COLOR=#0000ff]SolitaryMan1941 [/COLOR][COLOR=black]you are most welcome to do so.[/COLOR]
 
Thanks
 
**_Update:_** Post #2 of this link is interesting [http://ubuntuforums.org/showthread.php?t=1518043](http://ubuntuforums.org/showthread.php?t=1518043) . There appears to be some success over there.
 
The code is different [COLOR=red]but[/COLOR] notice that the device ID is typed as 07[COLOR=red]D[/COLOR]1 3[COLOR=red]C[/COLOR]16
If you have not tried anything else, could you use capitals for [COLOR=red]D[/COLOR] and [COLOR=red]C [/COLOR][COLOR=black]in the code lines in post #3 in this thread again (still substituting [COLOR=#0000ff]rt3070sta[/COLOR] to [COLOR=red]rt2870sta[/COLOR] ) and see if it makes any difference.[/COLOR]
 
If it still does not work, 'undo' and try the codes in that link.
 
Good luck and post back.

---

### Post by David006 on 2010-07-25
(1.)

Your use of:

sudo apt-get update

should instead be:

sudo service udev reload  (or similar)


(2.)  I have resolved this (for me).

see:
[http://ubuntuforums.org/showpost.php?p=9632897&postcount=15](http://ubuntuforums.org/showpost.php?p=9632897&postcount=15)

---

### Post by mwangarch on 2010-08-10
Hate to pile on, but clearly the DWA-125 install is a problem for lots of us.  Have been trolling the flbiggs thread, this one and the /home/sasha.gerrand.id.au/ link, but still no joy.  
When I type in 
lusb |grep D-Link, I get the proper identification of the USB device:
Bus 001 Device 004: ID 07dl:3c0d D-Link System

However, when I type in:
dmesg |grep rt2, I get:
[   15.119435] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.180343] usbcore: registered new interface driver rt2870
[   15.812442] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
[   15.813408] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'

lsmod | grep -e rt2 -e rt3, gives the following:
rt2870sta             488820  0 

Any thoughts on getting the system to recognize & power up the device?  It works flawlessly under Windows.

Thanks.  Michael Wang

---

