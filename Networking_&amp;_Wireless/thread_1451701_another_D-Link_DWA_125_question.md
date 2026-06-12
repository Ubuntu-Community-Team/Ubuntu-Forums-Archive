---
title: "another D-Link DWA 125 question"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by scudderinc on 2010-04-10
I am an absolute novice when it comes to computers (and this is my first experience with Ubuntu).

I apologies for adding another thread on this topic, but the others were over my head.

Here's what I have:

Ubuntu 9.10
D-link DWA 125 Wireless 150 USB Adapter.

Any help to get the adapter to function would be greatly appreciated!!!

Thanks!

---

### Post by chili555 on 2010-04-10
Please go to Applications > Accessories > Terminal and do:```
lsusb
sudo modprobe rt3070sta
```Let us know the outcome of these two commands. In *lsusb*, you can skip all the 'root hub' listings and the parts about your mouse and other items that you are sure are not your wireless device.

---

### Post by scudderinc on 2010-04-10
Chili555 --  Thanks so much for coming to my rescue!

Results of lsusb:

> Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c0d D-link System
Bus 001 Device 001: ID 1d6b:0062 Linux Foundation 2.0 root hub

When I typed in **sudo modprobe rt3070sta** I was prompted to enter my password.  After I tried entering the password, the terminal reverted back to the default prompt.  When I tried that command again it reverted directly back to the default prompt.

---

### Post by chili555 on 2010-04-10
> After I entered the password the terminal reverted back to the default prompt. Good! That means the command was accepted with no errors or warnings. Your device is claimed by two conflicting drivers, so let's tweak one file. Please remove your device and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open with a big file in it. We will add a few lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, twice, save and close gedit. Now do:```
sudo rmmod rt2800usb
```Reinsert your device and reboot. Now does your wireless work? Can you click the Network Manager icon at the top right, select your network and connect?

---

### Post by scudderinc on 2010-04-10
I followed those steps and after reboot it did not recognize the adapter.  I then realized that I needed to actually install the driver (I'm such a novice).  

I popped in the CD and clicked on Autorun.exe.

This error message appeared:

> 
Archive:  /media/cdrom0/autorun.exe
[/media/cdrom0/autorun.exe]
End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will not be found on the last disk(s) of this archive.
note: /media/cdrom0/autorun.exe may be a plain executable, not an archive
zipinfo: cannot find zipfile directory in one of /media/cdrom0/autorun.exe or /media/cdrom0/autorun.exe.zip, and cannot find /media/cdrom0/autorun.exe.ZIP period.

I clicked on some of the other folders, and went into Settings --- Drivers.  It looks like the Adapter is only compatible with XP or Vista?

---

### Post by chili555 on 2010-04-10
When you did:```
sudo modprobe rt3070sta
```You did all you need to do. Please do:```
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```Now is it working?> It looks like the Adapter is only compatible with XP or Vista?Not true; the driver .exe is only compatible with Windows. The adapter is going to work if we have to wear out your keyboard!

---

### Post by scudderinc on 2010-04-10
ok.  i entered those 4 prompts, closed the terminal and went to the upper right hand corner to the networks icon.  i clicked on connect vpn, went to the wireless tab and it came up blank.

thanks again for your help and patience:)

---

### Post by chili555 on 2010-04-10
> i clicked on connect vpn, went to the wireless tab and it came up blank.VPN? Are you trying to set up a virtual private network? Do you see networks like the attached? (GBR1, Dynex, etc.)

What does this tell us?```
iwconfig
```Do you have a wireless interface, wlan0, perhaps?

---

### Post by scudderinc on 2010-04-10
> VPN? Are you trying to set up a virtual private network? Do you see  networks like the attached? (GBR1, Dynex, etc.)

I was just clicking to see if anything came up.  We have a network set up already with a D-link router, so with this computer it is simply about getting the adapter to get a signal so we have an internet connection.

I'm going to go try these steps.

---

### Post by scudderinc on 2010-04-10
ok.  here is what i got from [B]iwconfig

[/B]> lo                    no wireless extensions.
eth0              no wireless extensions.when I open the network preferences (i think that's what it is titled) box and click the wireless tab there is nothing coming up.

---

### Post by chili555 on 2010-04-11
Let's take a look at:```
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by scudderinc on 2010-04-11
alright...a new day as i resume my efforts!

results from

dmesg | grep -e rt2 -e rt3 
> 
[   16.498763] [COLOR=Red]rt3[COLOR=Black]070sta: module is from the stagin directory, the quality is unkown, you have been warned.
[   16.502017] usbcore: registered new interface driver [COLOR=Red]rt2[COLOR=Black]870[/COLOR][/COLOR][/COLOR][/COLOR]


---

### Post by chili555 on 2010-04-11
The module is loading but not creating the wireless interface. Let's see why:```
dmesg | grep -e 287 -e 307
```Thanks.

---

### Post by scudderinc on 2010-04-11
here's what came back:

>     [    0.333077] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
  [    0.706307] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21 
  [    1.928712] generic-usb 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:02.0-1/input1 
  [    1.928722] usbcore: registered new interface driver usbhid 
  [    1.928725] usbhid: v2.6:USB HID core driver 
  [   16.498763] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned. 
  [   16.502017] usbcore: registered new interface driver rt2870 
  

---

### Post by chili555 on 2010-04-11
Let's go deep in the system and find out more. Please do:```
dmesg > test.txt
lsmod >> test.txt
zip test.zip test.txt
```In your user directory, you will find a file called test.zip. Please attach it to your reply using that little paperclip.

---

### Post by scudderinc on 2010-04-11
alright.  i entered the prompts.  the only one that initiated a response was the last

   **zip test.zip test.txt **yielded this:

>   adding: test.txt (deflated 72%)    

---

### Post by chili555 on 2010-04-11
Let's turn the wrench tighter. Please do:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules

```
Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"
```

Proofread twice, save and close gedit.
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```

Add one long single line:

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id

```Reboot and let me know if the wireless is now working.

---

### Post by scudderinc on 2010-04-11
wow.  i don't know what you did, but it worked!!!

i can't thank you enough.  bless you!

---

### Post by chili555 on 2010-04-11
Great work! Glad it's working. Have fun and welcome to the Ubuntu party.

---

### Post by scudderinc on 2010-04-11
i do like the interface.  frankly, you can only go up from windows.

one final question...i want to block facebook from the computer (long story).

i've done that on a windows machine by simply adding [www.facebook.com](www.facebook.com) into the Hosts file.  is there something similar w/ ubuntu?

---

### Post by scudderinc on 2010-04-11
update: i found the host file.

thanks again for your help.

---

### Post by baoduy.duong0206 on 2010-06-02
[HTML]Let's turn the wrench tighter. Please do:
     Code:
     sudo gedit /etc/udev/rules.d/network_drivers.rules 
Add one long line:
     Code:
     ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta" 
Proofread twice, save and close gedit.
     Code:
     sudo gedit /etc/modprobe.d/network_drivers.conf 
Add one long single line:

     Code:
     install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id 
Reboot and let me know if the wireless is now working.     Let's turn the wrench tighter. Please do:
     Code:
     sudo gedit /etc/udev/rules.d/network_drivers.rules 
Add one long line:
     Code:
     ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta" 
Proofread twice, save and close gedit.
     Code:
     sudo gedit /etc/modprobe.d/network_drivers.conf 
Add one long single line:

     Code:
     install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id 
Reboot and let me know if the wireless is now working.     
[/HTML]------------
i try to do this but it don't work 
this is some thing, i have in dmesg 
ADDRCONF(NETDEV_UP): wlan0: link is not ready
rt2800usb 1-2:1.0: firmware: requesting rt2870.bin


[ 1681.784029] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 1681.932949] usb 1-2: configuration #1 chosen from 1 choice
[ 1681.963924] phy1: Selected rate control algorithm 'minstrel'
[ 1681.965399] Registered led device: rt2800usb-phy1::radio
[ 1681.965443] Registered led device: rt2800usb-phy1::assoc
[ 1681.965483] Registered led device: rt2800usb-phy1::quality
[ 1682.111000] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
[ 1682.358715] ADDRCONF(NETDEV_UP): wlan0: link is not ready


[    9.627928] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.641156] rtusb init --->
[    9.641258] usbcore: registered new interface driver rt2870
[    9.647414] intel_rng: FWH not detected
[    9.697049] lp: driver loaded but no devices found
[    9.700652] parport_pc 00:09: reported by Plug and Play ACPI
[    9.700699] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.704716] ses 4:0:0:2: Attached Enclosure device[IMG]http://www.qtl.co.il/img/copy.png[/IMG][IMG]http://www.qtl.co.il/img/url.png[/IMG][IMG]http://www.google.com/favicon.ico[/IMG][IMG]http://en.wikipedia.org/favicon.ico[/IMG][IMG]http://www.babylon.com/favicon.ico[/IMG][IMG]http://www.qtl.co.il/img/trans.png[/IMG]

---

### Post by chili555 on 2010-06-02
May I see:```
lsmod | grep rt2
```Thanks.

---

