---
title: "fritz wlan usb installed but disabled"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by cholericfun on 2011-03-15
Hello,

i have just installed a Fritz Wlan USB stick on a practically fresh Maverick 32 Bit install with ndiswrapper.
(i used this guide [in german] [http://wiki.ubuntuusers.de/fritz!wlan_usb_stick](http://wiki.ubuntuusers.de/fritz!wlan_usb_stick))

so far so well, problem is, i cant enable the wireless. 
As far as i can see, this is no "on-button" issue. The build in wireless is either dead or never been there. 
It shows in the output below, but the "wifi-on/off" button doesnt do anything to the LED thats supposed to turn on and in an case... no connection.

I think basically what my problem is that i can't figure out how to enable the wireless (its greyed out in the network-manager)
i also installed the 32Bit version of the driver on a 32Bit Notebook.

below is some output of what i found on other threads to try:

```
lsusb
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 057c:6201 AVM GmbH AVM Fritz!WLAN v1.1 [Texas Instruments TNETW1450]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
 ndiswrapper -l
fwlan : driver installed
	device (057C:6201) present

```
```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:a4:4d:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:b8000000-b8000fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:b9:8a:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.178.30 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:18 ioport:3000(size=256) memory:b8001000-b80010ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:04:0e:c8:10:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+fwlan driverversion=1.56+AVM GmbH,12/28/2006,2.0.6.1 multicast=yes wireless=IEEE 802.11g
```
i know little about the above output apart from the right driver beeing loaded, but a little question here, why is the 3rd network not given a number like the 1st wireless and ethernet?

```
sudo iwlist wlan0 scan 
wlan0     Scan completed :
          Cell 01 - Address: 00:90:96:F8:32:B2
                    ESSID:"ALICE-WLAN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:26:4D:39:9F:0B
                    ESSID:"EasyBox-399F45"

....  //and so on

```

also the "Disabled" wireless sees some WiFi spots around me


But finally (see attachment) i dont get anything.

---

### Post by chili555 on 2011-03-15
> As far as i can see, this is no "on-button" issue. *The build in wireless is either dead or never been there.* I disagree. It looks healthy to me.> *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:a4:4d:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:b8000000-b8000fff
What does this tell us?```
rfkill list all
dmesg | grep ipw
```Thanks.

---

### Post by cholericfun on 2011-03-15
There..

```
rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

this tells whether theres an "on/off button" active, right?
i just tried pressing about all sorts of obvious and not-so obvious buttons and no changes, since the laptop was used with this external FritzWlan USB i guess that means theres something broken. 

also this doesn't do anything
```
rfkill unblock all
```

and rebooting whithout a lan-cable doesnt help either.

```
dmesg | grep ipw
[   18.967840] libipw: 802.11 data/management/control stack, git-1.1.13
[   18.967843] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.050638] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.050643] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.050775] ipw2200 0000:06:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.068768] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.855415] ipw2200: Radio Frequency Kill Switch is On:
[   19.891327] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   23.448164] ipw2200: Failed to send POWER_MODE: Command timed out.
sea@kaffee:~$ 


```

---

### Post by chili555 on 2011-03-15
What kind of laptop is it? A Dell, perhaps??

Please do:```
tail -f /var/log/messages
```Leave the terminal open and see if button presses, both a hardware wireless switch and also any Fn keys, are recognized by the kernel. Close the session with Ctrl+c.

---

### Post by cholericfun on 2011-03-15
cool, will do in a second,
just for hardware: sorry i forgot
Medion WIM 2090


i get hardly any response, especially not from the supposed wlan switch, the few that are responding here are all of the same form

```
Mar 16 01:39:56 kaffee kernel: [  255.140265] Skipping EDID probe due to cached edid

```

---

### Post by chili555 on 2011-03-15
Please check here; a Medion with an Intel 2200ABG card: [http://ubuntuforums.org/showthread.php?t=1428815&page=2](http://ubuntuforums.org/showthread.php?t=1428815&page=2)> Solved!
It had to change my wireless adapter to Last State in the BIOS.
I thought you had to do this if your system was dualbooting, so I didn't check that out earlier.
Haha Thanks, Chili555! There is another fix proposed in that thread, but please check your BIOS first.

---

### Post by cholericfun on 2011-03-15
well it was disabled in the BIOS, put it on "last state" but that doesnt change anything. More irritating, when i rebooted again, if was again disabled.
the other recommendations as far as i can tell didnt make any difference either. Although i have the feeling i might easily miss something.

---

### Post by chili555 on 2011-03-15
Are disabled and last state your only choices? Is always on an option?

Please try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 bt_coexist=1
sudo rfkill unblock all
rfkill list all
```

---

### Post by cholericfun on 2011-03-15
just tried setting BIOS to fail-safe defaults,
at least that succeeded in leaving the WLan capability in "Last State" mode as opposed to "Disabled".
Nonetheless, i am no closer to getting a wireless connection.
I guess this BIOS setting really only affects the internal wlan, 
which i presume to be somewhat disfunct anyway. In any case, this setting worked with the Fritz USB under windows until rather recently.

PS:yes, disable and last state are the only options

and:
```
sudo rmmod -f ipw2200
[sudo] password for sea: 
sea@kaffee:~$ sudo modprobe ipw2200 bt_coexist=1
sea@kaffee:~$ sudo rfkill unblock all
sea@kaffee:~$ rfkill list all
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

which i tried already, not sure why the hard block can stay on.
thanks so far btw!

---

### Post by chili555 on 2011-03-15
> I guess this BIOS setting really only affects the internal wlan, I'm not sure I agree. My wireless switch affects both internal and USB.

I am fresh out of ideas.

---

### Post by flash63 on 2011-03-16
Hallo,
most of the older Medion Laptops need Acer-Hotkeys to enable WLAN. To determine that, you need the Medion MD-Number like MD96500 for your PC. Take a look at the bottom, there must be a sticker with Medion numbers. 

By the way, ipw2200 don't work with **rfkill**.

Test it
```

sudo modprobe -rf ipw2200
sudo modprobe ipw2200 disable=0 led=1

```
(but i think it didn't work)

Unload the ipw2200 Module
```
sudo modprobe -rf ipw2200
```
The stick should now work.

You can use a new udev-rule for that
```

sudo gedit 10-wlan-stick.rules

```
Content
```

# UDEV-Rule for WLAN-Cards
# load/unload driver for int. wireless device

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

### ignore flash-memory 
SUBSYSTEM=="block", ATTR{idVendor}=="057c", ATTR{idProduct}=="62ff", ACTION=="add", OPTIONS+="ignore_device"

SUBSYSTEM=="usb", ATTR{idVendor}=="057c", ATTR{idProduct}=="5601", RUN+="/sbin/modprobe -rf ipw2200"
SUBSYSTEM=="usb", ATTR{idVendor}=="057c", ATTR{idProduct}=="6201", RUN+="/sbin/modprobe -rf ipw2200"
GOTO="wlan_rules_end"

LABEL="onboard_load"

#SUBSYSTEM=="usb", ATTR{idVendor}=="057c", ATTR{idProduct}=="5601", RUN+="/sbin/modprobe ipw2200"
#SUBSYSTEM=="usb", ATTR{idVendor}=="057c", ATTR{idProduct}=="6201", RUN+="/sbin/modprobe ipw2200"
KERNEL=="wlan*", RUN+="/sbin/modprobe ipw2200"

LABEL="wlan_rules_end"

```
Activate it
```
sudo service udev reload
```
unplug/plug in the stick and test it in each case (the stick needs ~30 seconds after powering on to switch to wlan-mode)
```
iwconfig
```

---

### Post by cholericfun on 2011-03-16
> **flash63 said:**
> Hallo,
most of the older Medion Laptops need Acer-Hotkeys to enable WLAN. To determine that, you need the Medion MD-Number like MD96500 for your PC. Take a look at the bottom, there must be a sticker with Medion numbers. 


Hello,
its an MD 97600,
looks like it does use the acer hotkeys (although i'm not entirely clear if it is essential to get wifi running?). Installation is somewhat painful since Karmic.

i'll try out your other suggestions and see if they alone can produce any results.

Thanks!

---

### Post by cholericfun on 2011-03-16
> **flash63 said:**
>  
By the way, ipw2200 don't work with **rfkill**.

Test it
```

sudo modprobe -rf ipw2200
sudo modprobe ipw2200 disable=0 led=1

```
(but i think it didn't work)


no it doesn't
> 
Unload the ipw2200 Module
```
sudo modprobe -rf ipw2200
```
The stick should now work.


YES IT DOES!  gladly without the acer hotkeys and its somewhat cumbersome setup.

will make it permanent with your other suggestions.
i'm practically clueless in regards to networks, so was really dependant on help.
Thanks a Million!

---

### Post by flash63 on 2011-03-16
See [http://forum.ubuntuusers.de/topic/acer-travelmate-291lci-funknetzwerk-nicht-akti/2/#post-2670605](http://forum.ubuntuusers.de/topic/acer-travelmate-291lci-funknetzwerk-nicht-akti/2/#post-2670605) (German)

For Ubuntu 10.04 (with Connection over Ethernet Cabel or WiFi-Stick)
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential acerhk-source
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 

```
Edit the Makefile and change Line 561
```
sudo gedit /usr/src/linux-headers-$(uname -r)/Makefile

```
```
# KBUILD_CFLAGS	+= -pg

```
Build
```

cd /usr/src/modules/acerhk
sudo su
make 
cp acerhk.ko /lib/modules/$(uname -r)/kernel/ubuntu/
depmod -a

```
acerhk parameter for your MD 97600 is
```
sudo modprobe acerhk force_series=95400 autowlan=1
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
```
Now the internal WiFi should work.

If it works ...
```
echo 'options acerhk force_series=95400 autowlan=1' | sudo tee /etc/modprobe.d/acerhk.conf
```
After a kernelupgrade you must recompile the module.

---

### Post by cholericfun on 2011-03-16
just a note,

the udev rules need to go into
```
/etc/udev/rules.d/
```
of course.

everything from there works nicely.
thanks a lot for your help.

---

### Post by flash63 on 2011-03-16
> the udev rules need to go into ...
Oh, sorry. That's right
```
sudo gedit /etc/udev/rules.d/10-wlan-stick.rules
```

---

