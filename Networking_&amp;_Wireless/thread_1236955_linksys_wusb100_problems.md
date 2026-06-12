---
title: "linksys wusb100 problems"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by gbrettj on 2009-08-10
I just purchased a linksys wusb100 wireless adapter for my computer. I'm running Ubuntu 9.04. I've racked my brain and my search engine for a week and still have no connectivity for my ubuntu installation. I've installed ndiswrapper and here are the results from some of my inquiries. 

[COLOR=RoyalBlue]brett@Brett:~$ ndiswrapper -l
rt2870 : driver installed
    device (1737:0078) present
brett@Brett:~$ 
brett@Brett:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:b5:f0:56  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:feb5:f056/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8170079 (8.1 MB)  TX bytes:1307887 (1.3 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

brett@Brett:~$ 
brett@Brett:~$ lsusb
Bus 001 Device 003: ID 1737:0078 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brett@Brett:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.[/COLOR]

[COLOR=Black]Someone please help, this is driving my crazy.

Thanks

Brett
[/COLOR]

---

### Post by claudiac on 2009-08-19
>brett@Brett:~$ ndiswrapper -l

remove ndiswrapper and compile your own rt2870/rt3070 driver

download the rt3070 from ralink:
  [http://www.ralinktech.com.tw/data/drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2](http://www.ralinktech.com.tw/data/drivers/2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2) 

tar xvjf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2 

cd 2009_0525_RT3070_Linux_STA_v2.1.1.0

vi os/linux/usb_main_dev.c
  - change: USB_DEVICE(0x1737,0x0070)
        to: USB_DEVICE(0x1737,0x0078)

modify os/linux/config.mk as needed (see README_STA_usb)

* fix common/rtmp_init.c:
  find reference to os_alloc_mem and fix (PUTCHAR) to (PUTCHAR *)
  
make

make install

cd os/linux
insmod rt3070sta.ko

ifconfig ra0 up

show available networks:
  iwlist scan

-- for some basic settings to connect to an unprotected network:
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=OPEN
iwpriv ra0 set EncrypType=NONE
iwpriv ra0 set SSID="dummy"
iwpriv ra0 set Channel=1

to see if the settings above *stuck*: 
  iwconfig ra0

then, to get a dhcp address:
  /sbin/dhclient ra0

-claudia

---

### Post by claudiac on 2009-08-19
in my haste to get you something to work with, I forgot two steps:


1) either modify source to use the correct file or
     ln -s /etc/Wireless/RT3070STA /etc/Wireless/RT2870STA

2) out of the common directory, copy the rt2870.bin to the above directory

-claudia

---

### Post by nmgraywiz on 2009-09-25
Awesome!!!  Good excellent instructions...  I've been attempting to get my WUSB100 Version 2 Linksys adaptor to operate on a dell Latitude laptop for 2 weeks now...  The above instructions provided by Claudiac are the first ones to actually work..  GREAT WORK!!!  And thanks for posting such a complete procedure.  I for one would call this excellent HOW TO Material.  Thanks again..

L8

The Gray Wizard
(aka: Matt)

---

### Post by nmgraywiz on 2009-09-25
P.S.   As an additional side note...

I modified

os/linux/usb_main_dev.c

to include the setups for both WUSB100 Version 1 and 2 Adapters (I have both versions, and was troubleshooting version 2 for a customer as Version 1 was already working properly with ndiswrapper)   I added...

	{USB_DEVICE(0x1737,0x0070)}, /* Linksys-WUSB100-V1 */
	{USB_DEVICE(0x1737,0x0078)}, /* Linksys-WUSB100-V2 */

re-compiled and now I've discovered that I can interchangeably use one or the other adapter.  Even tested without re-booting (removing one, and re-inserting the other) and both adapters work perfectly with the one driver.

Thanks again Claudiac for an awesome job and a major life saving heheh.. 

L8

The Gray Wizard
(aka: Matthew Romero)

---

### Post by flash63 on 2010-01-01
Hello,
a little Trick to add the ID **1737:0078** for the WUSB100v2 to the System and simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver if necessary:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```
If you previously did not manually compile the driver from Ralink start here. 

Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```
The solution works? Ok, load the driver at startup
```

echo rt2870sta | sudo tee -a /etc/modules

```
alternativ automatic driver load when the stick was plugged in:
```

sudo gedit /etc/udev/rules.d/10-wusb100.rules

```
contents:
```

# UDEV-Rule for wusb-100v2 ID 1737:0078
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"

```
make it ready to work
```

sudo service udev reload 

```.. or restart

Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

---

### Post by Jainith on 2010-01-05
Thanks Flash63 your solution worked Great!!!:KS
> 

Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```


---

### Post by Jainith on 2010-01-05
Hmm... I notice that the wireless didn't come up automatically. 

I ran the last 3 lines again and it did. What would be the appropriate way to best have the system do this on startup?

---

### Post by flash63 on 2010-01-06
Hello Jainith,
edit the file **/etc/modules** as root and add the drivermodul rt2870sta.

The same in one line:
```
echo rt2870sta | sudo tee -a /etc/modules
```

The required options to add the ID are already into the /etc/modprobe.d/rt2870.conf

---

### Post by Jainith on 2010-01-06
Thanks for getting back to me. I had already figured out to put the rt2870sta in /etc/modules. I also tried adding the 'iwconfig' to my startup applications. Interestingly if I go back to startup applications now, I do not see this entry. 

Anyway, my connection is coming up automatically, but at somewhat of a delay (it doesn't get started until after gmail-notify so I get a no connection message.

If you can think of a way to better tune the startup so the wireless connection starts before gmail-notify, that would be great. If not, its ok, as it only takes an additional 30 seconds or so to startup. 

-Jainith

---

### Post by flash63 on 2010-01-06
I think gmail-notify starts before your WLAN-connection was established.

Delete gmail-notify from the autostart-menu and start it with the **/etc/rc.local** and a little delay.

```

...
sleep 20
gmail-notify
exit 0

```

---

### Post by ralinkDebian on 2010-01-14
I couldn't get WPA2 to with my wusb100 v2 until I recompiled wpa_supplicant with support for the Ralink driver.  I'm using Debian and it seems that the wpa_supplicant that Debian uses doesn't have support for the Ralink driver.

---

### Post by RavanH on 2010-02-21
> **flash63 said:**
> Hello,
a little Trick to add the ID 1737:0078 for the WUSB100v2 to the System an simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```
Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```
Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

Thank you Rainer! 

Thanks to your solution I finally have my Linksys RangePlus WUSB100v2 (ID 1737:0078 Linksys) working **WITH** scanning ability, actually able to connect **AND** with WPA all at the same time !!! :)

Took me half the night and lots of not-or-half-working fixes before I found your post. I am happy now :popcorn:

EDIT: One note, because the driver would not auto-load when hot-plugging the dongle I had to add the rt2870sta to /etc/modules to load it at startup. Running without Ndiswrapper, it is all just perfect now :)

---

### Post by peepingtom on 2010-02-23
Edit: gaah wrong thread. Thanks a lot for this, I knew there was a udev or sysfs solution to this USB Dev ID problem!

What's the point of running the install command at every boot? Would echoing the USB Dev ID to /sys/bus/usb/drivers/rt2870/new_id not work on its own?

---

### Post by GrandTheft on 2010-02-28
Flash63, you made my day.

Thanks! 

GT

---

### Post by flash63 on 2010-03-06
> **peepingtom said:**
> Edit: gaah wrong thread. Thanks a lot for this, I knew there was a udev or sysfs solution to this USB Dev ID problem!

What's the point of running the install command at every boot? Would echoing the USB Dev ID to /sys/bus/usb/drivers/rt2870/new_id not work on its own?

Hello,
peepingtom, try the udev-rule if you won't load the module at startup.

[http://ubuntuforums.org/showthread.php?p=8591348#post8591348](http://ubuntuforums.org/showthread.php?p=8591348#post8591348)

---

### Post by GeniusGeeko on 2010-03-07
> **flash63 said:**
> Hello,
a little Trick to add the ID 1737:0078 for the WUSB100v2 to the System an simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```The solution works? Ok, load the driver at startup
```

echo rt2870sta | sudo tee -a /etc/modules

```alternativ automatic driver load:
```

sudo gedit /etc/udev/rules.d/10-wusb100.rules

```contents:
```

# UDEV-Rule for wusb-100v2 ID 1737:0078
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"

```make it ready to work
```

sudo /etc/init.d/udev reload 

```.. or restart

Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

I followed this tutorial on my Debian Lenny Distro, I got to the "sudo modprobe rt2870sta" with a error, saying "Cannot write to /sys/bus/usb/drivers/rt2870/new_id , file or directory doesn't exist" Or something very similar.

I have searched the drivers folder and I get a few folders, I will post the tree below. 
Hub, snd-usb-audo, usbfs, snd-usb-cauiaq, usb, usb-storage

---

### Post by flash63 on 2010-03-09
Hello,
do you really have a wusb100v2 ? Check:
```

lsusb
lsmod

```

---

### Post by GeniusGeeko on 2010-03-09
> Bus 001 Device 004: ID 1737:0078 Linksys
Bus 001 Device 003: ID 0930:6544 Toshiba Corp.
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I didn't much output from lsmod, am I supposed to have any options set to it?
> Module                  Size  Used by

---

### Post by flash63 on 2010-03-11
Hello,
> I followed this tutorial on my Debian Lenny Distro, I got to the "sudo modprobe rt2870sta" with a error, saying "Cannot write to /sys/bus/usb/drivers/rt2870/new_id , file or directory doesn't exist" Or something very similar.
Debian Lenny, that could be the real cause. It seems that it works different from ubuntu. Sorry, i don't know. :confused:

---

### Post by jgrocha on 2010-03-27
Thanks, Rainer! You are the best. :KS

I was able to install the WUSB100 in 9.10. I hope that 10.04 will automatically recognize it.

---

### Post by Pjotr123 on 2010-03-28
> **flash63 said:**
> Hello,
a little Trick to add the ID 1737:0078 for the WUSB100v2 to the System an simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

greetings and a happy new year :)

Rainer

Works great in Lucid! Thanks a lot for sharing this information. :D

---

### Post by yrhen on 2010-04-10
hello anybody out there,
after following 10 threads and leads i 'll start afresh with the 15th or 20th virgin installation of Kubuntu karmic. kernel  2.6.---.20 amd64. trying to get wifi through linksys wusb100v.2. [id 1737 0078]
It'll take me a bout half an hhour (to 3/4) to download 185 bug fixes.
anyone feeling up to talking me through an installation without me messing up my system again?

---

### Post by yrhen on 2010-04-11
I guess that I can limit the options to three:
   ***Flash63/Elektronenblitz63***: [[http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339]](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339])
  add the ID 1737:0078 for the WUSB100v2 to the System an simply use the rt2870sta V1.4.0.0. that comes with the system
   
  ***Claudiac***: [this thread]

  Use 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2 from Ralink, if you can find it
   
  ***Peepingtom***: [[http://ubuntuforums.org/showthread.php?t=1342593]](http://ubuntuforums.org/showthread.php?t=1342593])

  Uses 2009_0820_RT2870_Linux_STA_V2.2.0.0 and extensive blacklisting of rt drivers; though MTXColl insists on using an unspecified RT3070 [2009_1110_RT3070_Linux_STA_v2.1.2.0?] driver instead and installing RT2870 on top of it.
  
so what order of trying makes most sense?

---

### Post by yrhen on 2010-04-11
after flipping a coin I started with the flash63 routine.
echo does fine
modprobe -rf doesn't hurt (nothing was loaded anyway)
modprobe rt2870sta runs into an error:
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent.
which in itself is peculiar as I actually visited that directory and saw the file sitting there

what the heck goes wrong?

---

### Post by yrhen on 2010-04-11
ah, I see: it existed before my 20th virgin installation. apparently i have to modprobe rt2870 inorder to -rf it in order to load it again with the adapted ID

---

### Post by yrhen on 2010-04-11
Rainer, Herzlichen Dank. Flash is the greatest
For the first time since I started 3 weeks ago I have a Wifi usb that is on air, scans and actually sees my network.
Only it won't connect because the router is WPA2SHK and network manager is not.
If I set the router to open connection, the ubuntu machine connecgts, but the XP laptops loose connection. If i switch to WPA2 the XP's reconnect and the ubuntu drops.
What am I missing? help?!

---

### Post by yrhen on 2010-04-11
ok. WICD did the trick that networkmanager failed to:
[http://ubuntuforums.org/showthread.php?t=1360173&highlight=kubuntu+wpa2](http://ubuntuforums.org/showthread.php?t=1360173&highlight=kubuntu+wpa2)

I'll have a bottle of champaign

---

### Post by ki4anr on 2010-04-17
Flash,
Thanks so much for the answer to my WUSB100v2 problem. I have been searching for months on end and yours is the first I have used that worked. Thanks a million!:):):)
Kevin



> **flash63 said:**
> Hello,
a little Trick to add the ID 1737:0078 for the WUSB100v2 to the System an simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```
Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```
The solution works? Ok, load the driver at startup
```

echo rt2870sta | sudo tee -a /etc/modules

```
alternativ automatic driver load:
```

sudo gedit /etc/udev/rules.d/10-wusb100.rules

```
contents:
```

# UDEV-Rule for wusb-100v2 ID 1737:0078
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"

```
make it ready to work
```

sudo /etc/init.d/udev reload 

```.. or restart

Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

---

### Post by J. Baker on 2010-04-22
When I use cd RT2870_LinuxSTA_V2.3.0.0 I get no such file or directory? Any help would be great, thanks.

---

### Post by bkratz on 2010-04-22
> **J. Baker said:**
> When I use cd RT2870_LinuxSTA_V2.3.0.0 I get no such file or directory? Any help would be great, thanks.

Well the path depends on where you saved the file.

---

### Post by flash63 on 2010-05-02
Hello,
if you 	previously did not manually compile the driver from Ralink, you can forget these instructions.
```
cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall
```

Start immediate at "Add the ID:" and so on ...

Rainer

---

### Post by J. Baker on 2010-05-02
Thanks guys!

---

### Post by angvzp0x on 2010-05-06
Wow... that piece of linux magic...

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

...worked for me after 4 or 5 other failed attempts.

I have a Dlink DWA-130 USB stick, it has a different usb id to the one in this thread, but i replaced the "1737 0078" with the "07d1 3c13" that lsusb returned and boom it hooked right up to my wireless n router at 300Mb/s

i think i also added 'blacklist rt2800usb' to /etc/modprobe.d/blacklist.conf

and 'rt2870sta' to /etc/modules

thankyou ubuntu forums

---

### Post by ddmits on 2010-05-22
Rainer 
many many thanks for your solution.  I have been trying to make my Belkin N150 Wireless USB to work for a week now. I have tried everything.

Your solution works perfectly!:popcorn:
You made my day!

The only error I get is the following:
[   86.567125] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat

but the device works....

---

### Post by flash63 on 2010-05-24
Hello,

> [ 86.567125] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
Copy the config file from the Ralink driver package and configure out for the right country and channel settings. Please note the **README_STA_usb**

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

RT3070STA.dat (Example for Germany/DE)
```
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=1
CountryCode=DE
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
...
```
Allowed wireless channels: [http://de.wikipedia.org/wiki/Wlan#Frequenzen_und_Kan.C3.A4le](http://de.wikipedia.org/wiki/Wlan#Frequenzen_und_Kan.C3.A4le)

Restart an checkout the settings
```

iwlist chan
```

---

### Post by xylude on 2010-07-09
It worked like a charm.

---

### Post by roston on 2010-08-04
This is my exact problem and I am so pleased that there is a solution.  Sadly, I am so new that I do not understand ANY of this thread.  Can anyone point me in the direction where I can learn what it all means? I have just installed Ubuntu 10.4.

---

### Post by mikepry on 2010-09-05
Thanks so much as I have been trying for days to get this to work!!!

---

### Post by mikepry on 2010-09-05
> **flash63 said:**
> Hello,
a little Trick to add the ID **1737:0078** for the WUSB100v2 to the System and simply use the rt2870sta V1.4.0.0. that comes with the system if the new driver v2.3.0.0 or the rt3070 from Ralink don't work properly.

First remove the new compiled driver if necessary:
```

cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall

```
If you previously did not manually compile the driver from Ralink start here. 

Add the ID:
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```
The solution works? Ok, load the driver at startup
```

echo rt2870sta | sudo tee -a /etc/modules

```
alternativ automatic driver load when the stick was plugged in:
```

sudo gedit /etc/udev/rules.d/10-wusb100.rules

```
contents:
```

# UDEV-Rule for wusb-100v2 ID 1737:0078
SUBSYSTEM=="usb", SYSFS{idVendor}=="1737", SYSFS{idProduct}=="0078", RUN+="/sbin/modprobe rt2870sta"

```
make it ready to work
```

sudo service udev reload 

```.. or restart

Link: [http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339](http://forum.ubuntuusers.de/topic/linksys-wusb100-wireless-stick/#post-2264339)

greetings and a happy new year :)

Rainer

Thanks a 1,000,000!!!! I have been pulling my hair out on this one.

---

### Post by noran on 2010-11-13
Hello,

I tried using the instructions by claudiac but it did not work. I cannot find the lines to edit in the os/linux/usb_main_dev.c. When I type make, I get a permission denied error (even as sudo). I've been stuck at this first step for a week.

Thanks,

Noran

---

### Post by Mr.Bl on 2010-12-14
This is the easy way...

1.- Open Synaptic Package Manager...
2.- Search & install ndiswrapper gtk...
3.- System --> Administration --> WIndows Wireless Drivers
4.- Im using Ub... 10.10 64bts ... so I installed this one -->> [http://homedownloads.cisco.com/downloads/driver/WinXP_64_v1.4.6.zip](http://homedownloads.cisco.com/downloads/driver/WinXP_64_v1.4.6.zip)

5.- Restart... 

6.- DONE & GOOD LUCK!

---

### Post by derxen on 2010-12-20
Thank you very much Rainer, this works for me on 10.10, after wasting a day and half trying other things. Do you know if there is a way to get the link speed up? Mine is stuck at 54mbps. Another thing I wondered: what happens if you compile and install the latest driver from ralink, and then apply your method to fix the id?

derxen

---

### Post by Dutchman976 on 2010-12-23
Hello Flash63
 
Do I have to install the firmware for the driver as well or will it work with just instructios you have posted?

---

### Post by derxen on 2010-12-24
For me it worked without installing the firmware.

---

### Post by Spartako on 2010-12-27
Thank you very much Flash63, your solution worked very well on my SMCWUSBS-N3

For someone interest im running this kernel version: 2.6.32-27 in lucid lynx.

---

### Post by Ecthelion on 2011-07-30
@ flash63: Thanks a lot for your guide. I finally got my wireless card working with it!

---

### Post by Ericyue on 2012-03-20
hi claudiac,

i have follow your steps in post number 2 and i have a problem when i type "sudo make"

it give the the result like this -->

root@pc3-desktop:~/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# sudo make
make -C tools
make[1]: Entering directory `/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-38-generic/build SUBDIRS=/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
  CC [M]  /root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c: In function ‘RTMPAllocAdapterBlock’:
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c:234: error: ‘PUTCHAR’ undeclared (first use in this function)
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c:234: error: (Each undeclared identifier is reported only once
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c:234: error: for each function it appears in.)
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c:234: error: expected expression before ‘)’ token
/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.c:234: error: too few arguments to function ‘os_alloc_mem’
make[2]: *** [/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/root/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
[COLOR=Red]make: *** [LINUX] Error 2[/COLOR]

can help me how to fix it ? thanks in advance

---

