---
title: "Wireless Solutions"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by icecreamcakez on 2009-02-23
d run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:11:62:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: c6:7b:99:a6:7d:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

//////////////////////////////////////////////////////////////////////////

jes@HACIENDA:~$ dmesg | grep -i -e wlan -e ath -e radio
[   13.545855] ath9k: 0.1
[   13.546915] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.546928] ath9k 0000:04:00.0: setting latency timer to 64
[   13.984747] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.154461] Registered led device: ath9k-phy0:radio
[   14.154479] Registered led device: ath9k-phy0:assoc
[   14.154501] Registered led device: ath9k-phy0:tx
[   14.154518] Registered led device: ath9k-phy0:rx
[   14.154536] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8ca0000, irq=17
[   42.823726] ADDRCONF(NETDEV_UP): wlan0: link is not ready

///////////////////////////////////////////////////////////////////////////
thank you Chris 
jes

---

### Post by Crafty Kisses on 2009-02-23
So I'm not sure what you're asking, you need help connecting to your wireless connection via that wireless card?

---

### Post by pytheas22 on 2009-02-23
It actually looks like things should be working.  Are you unable to see wireless networks?  Or can you see them but not manage to connect?  What is the output of:
```

sudo iwlist scan
```

> So I'm not sure what you're asking, you need help connecting to your wireless connection via that wireless card? 

Yes, she's trying to get her Atheros [168c:002a] (rev 01) wireless card going.  I had been helping via email (I guess she found me through the ndiswrapper database that I mirror on my personal website) but asked to move it to the forums, since it's a lot easier to communicate here.  I think I've gotten her close to a solution--I had her install the ath9k driver through the linux-backports-modules-interepid package, and blacklist ath_pci--but I guess she's not quite there.  Any insight you can offer is welcome, Codename.

---

### Post by icecreamcakez on 2009-02-23
after a left click on the network manager icon it displays 
wired network
auto etho
wireless networks

only the auto etho will highlight the others are inactive

---

### Post by icecreamcakez on 2009-02-23
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by Crafty Kisses on 2009-02-23
Hey there pytheas! I actually solved someone's problem very similar to this issue, I had them blacklist the following modules, and they actually said it solved their issues, so to the OP try blacklisting the following:
```
blacklist ath_pci
blacklist ath_hal
```
I'm aware that pytheas said he already told you to blacklist those, but I'd also like to know if you loaded the modules correctly, because in some cases people forget that step, they will check to see if the drivers are present, and they will get the "Drivers present" message, but that doesn't mean your done installing, so if you haven't done so, try loading the ndiswrapper module:
```
sudo modprobe ndiswrapper
```
Then make sure they load at every start so you don't have to keep loading them every time you reboot the computer, also you should try giving the modules names, so run the following commands:
```
sudo ndiswrapper -m
sudo ndiswrapper -ma
```
Then once you have done that, you should be able to connect to a wireless network, so once you have done all that, try running the following:
```
sudo ifdown wlan0
sudo ifup wlan0
```
Then try connecting through the Terminal and see if you have any different luck or get any error messages, you can connect to a unencrypted router via Terminal by running the following:
```
iwconfig eth1 essid <your_accesspoint_essid_here>
```
If you have an encrypted router, it's a bit different but still pretty simple, you can run this command:
```
iwconfig eth1 key <your_key_here>
```
Essentially this should get you up and running, if you have any problems let me or pytheas know.

---

### Post by icecreamcakez on 2009-02-23
thanks alot for helping out 
this is just incredible that people are really this cool to help

---

### Post by pytheas22 on 2009-02-23
Jess: that's strange that you can't see wireless networks, because by all other indications, your card should be working.

Are there usually several networks that you can see from your house?  Do you happen to know which channel (a number between 1 and 13) and mode (a letter, either a, b, g or n) your network is broadcasting on?

If not, type '192.168.1.1' into the address bar of your browser, you should be brought to a page where you can configure your wireless settings.  Look for a setting about the channel.  What does it say?

As Codename suggests, it may help to blacklist the ath_hal module (you already blacklist ath_pci before).  You can do that by typing:
```

echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by icecreamcakez on 2009-02-23
how do i open blacklist

---

### Post by icecreamcakez on 2009-02-23
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklis

do i run this thru the terminal at once or does the "|" symbolize two separate commands

---

### Post by pytheas22 on 2009-02-23
> how do i open blacklist

You can blacklist ath_hal simply by typing:

```

echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist
```

That command will edit the blacklist without your having to open it.  Alternatively, you could type:
```

sudo gedit /etc/modprobe.d/blacklist
```

to open the file itself, then add the line:
```

blacklist ath_hal
```

to the bottom, and save it.  Either method achieves the same result.
> 
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist

do i run this thru the terminal at once or does the "|" symbolize two separate commands

It's one single command.  Just copy and paste the whole line into the terminal, then press enter (and enter your password if prompted).

---

### Post by icecreamcakez on 2009-02-23
ive keyed in the ip a "lot" of times just now and nada keeps saying failed to connect
im not sure of numbers or letters

---

### Post by icecreamcakez on 2009-02-23
i ran the blacklist command 
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by icecreamcakez on 2009-02-23
well i just looked into blacklist dam im nosey lol

---

### Post by icecreamcakez on 2009-02-23
NDA:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-23
CIENDA:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
jes@HACIENDA:~$

---

### Post by pytheas22 on 2009-02-23
> ive keyed in the ip a "lot" of times just now and nada keeps saying failed to connect
im not sure of numbers or letters

Does this mean you're able to see a wireless network now?  What is the output now of:
```

sudo iwlist scan
```

If you still can't see any networks, reboot your computer and try again.

---

### Post by icecreamcakez on 2009-02-23
ENDA:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

---

### Post by icecreamcakez on 2009-02-23
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIEN

---

### Post by icecreamcakez on 2009-02-23
sudo iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIEN

---

### Post by pytheas22 on 2009-02-23
If you can't see any networks, where were you entering your key to connect?

Also, did you get a chance to go to 192.168.1.1 in your web browser and check on your wireless settings?

---

### Post by icecreamcakez on 2009-02-23
ENDA:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

---

### Post by icecreamcakez on 2009-02-23
192.168.1.1 was the "i tried alot" one lol
firefox states failed to connect and i tried it many times in browser

---

### Post by icecreamcakez on 2009-02-23
CIENDA:~$ iwconfig eth1 essid <your_accesspoint_essid_here>
bash: syntax error near unexpected token `newline'
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-23
ive tried 192.168.1.1 several times again and nada 
keeps sayin
ailed to Connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at 192.168.1.1.

---

### Post by icecreamcakez on 2009-02-23
Colonel i ran all of the commands through the terminal just like it says  ...nada
i posted after each

---

### Post by icecreamcakez on 2009-02-23
Captain C ive just looked into hardware drivers and nada 
should i restart sweetie

---

### Post by Crafty Kisses on 2009-02-23
Try rebooting, and see if you can connect then, if you're still having issues, I'll help you further.

---

### Post by sgosnell on 2009-02-23
Try this:

sudo modprobe ath9k

That's if you have the ath9k driver installed.  The ath5k is more common, and what I have on my Asus.  You need to have that run at every boot.

---

### Post by sgosnell on 2009-02-23
Duplicate post, somehow.

---

### Post by pytheas22 on 2009-02-23
> ive tried 192.168.1.1 several times again and nada
keeps sayin
ailed to Connect

Sorry, I misunderstood you before.  Please try 192.168.2.1 instead. That should work and bring you to the configuration page.  Right?

---

### Post by icecreamcakez on 2009-02-23
i sir

---

### Post by icecreamcakez on 2009-02-23
roger that Captn'C 

2.1

---

### Post by icecreamcakez on 2009-02-24
Captn it worked 2.1 which numbers did you need

---

### Post by icecreamcakez on 2009-02-24
Colonel i have rebooted and and no dice buddie

---

### Post by icecreamcakez on 2009-02-24
pytheas sweetie 
captn C i do have the numbers it went thru "2.1" worked 
which portion of this info is required

---

### Post by icecreamcakez on 2009-02-24
i have version info lan settings internet settings and features

---

### Post by icecreamcakez on 2009-02-24
if i load a xp partition and install driver will it carry over to ubuntu as well im faster with xp ..new to ubuntu

---

### Post by sgosnell on 2009-02-24
Have you tried entering
```
sudo modprobe ath9k
```
in a terminal?  If that doesn't work, try using ath5k instead.

---

### Post by icecreamcakez on 2009-02-24
should i reboot after trying each

---

### Post by icecreamcakez on 2009-02-24
sgosnell its a nada

---

### Post by icecreamcakez on 2009-02-24
pytheas i have the numbers you requested

---

### Post by sgosnell on 2009-02-24
Which Atheros driver did you download and install?

No need to reboot, it should work immediately if you have the right driver selected.

---

### Post by pytheas22 on 2009-02-24
> pytheas sweetie
captn C i do have the numbers it went thru "2.1" worked
which portion of this info is required

Look for information about which channel and which mode your router is operating on.  The channel will be a number between 1 and 13, and the mode will be a letter like a, b, g or n.  What is it?
> 
if i load a xp partition and install driver will it carry over to ubuntu as well im faster with xp ..new to ubuntu

No, unfortunately this won't work.

---

### Post by sgosnell on 2009-02-24
OK, I reread the thread, and see you have the ath9k driver.  Assuming that's the correct driver for your card, it should work.  You need to have the modprobe command run at each boot, one way or another, and there are several ways of doing it.

---

### Post by Crafty Kisses on 2009-02-24
I thought if you ran:
```
sudo ndiswrapper -m
```
You wouldn't have to modprobe after every boot.

---

### Post by icecreamcakez on 2009-02-24
pytheas i have many numbers before me 
im not finding anything listed under the terminology you specified 
please review 
items listed:

VERSION INFO
firmware version
boot version
hardware
serial no

INTERNET SETTINGS
wan mac address
connection type 
subnet mask
wan ip
default gateway
dns address

LAN SETTINGS
lan/wlan mac
ip
subnet mask
dhcp server

FEATURES
NAT 
firewall settings 
ssid 
security

---

### Post by sgosnell on 2009-02-24
I think mixing ndiswrapper and the Atheros driver is going to cause problems.  If she has the ath9k driver installed, she doesn't want to use ndiswrapper.

---

### Post by sgosnell on 2009-02-24
The router information isn't going to be helpful, I think.  If the wireless card isn't working, it makes no difference what the router settings are.

---

### Post by icecreamcakez on 2009-02-24
BLACKLIST

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
blacklist ath_pci
blacklist ath5k
blacklist ath_hal

---

### Post by pytheas22 on 2009-02-24
> pytheas i have many numbers before me
im not finding anything listed under the terminology you specified
please review
items listed:

VERSION INFO
firmware version
boot version
hardware
serial no

INTERNET SETTINGS
wan mac address
connection type
subnet mask
wan ip
default gateway
dns address

LAN SETTINGS
lan/wlan mac
ip
subnet mask
dhcp server

FEATURES
NAT
firewall settings
ssid
security

It's probably under Internet settings somewhere.  Please look there for information related to channel and mode.  If it's easier, you can take screenshots by going to Applications>Accessories>Take Screenshot, then attach the screenshot here.
> 
I think mixing ndiswrapper and the Atheros driver is going to cause problems. If she has the ath9k driver installed, she doesn't want to use ndiswrapper.

This is correct.  The card is already brought up successfully under ath9k, so ndiswrapper is not necessary (I also recall that ndiswrapper won't work with this particular card).
> 
The router information isn't going to be helpful, I think. If the wireless card isn't working, it makes no difference what the router settings are.

The wireless card is working, it just can't see networks.  That may be because of a problem with the driver, but it could also have to do with the wireless network being on a channel or mode that the driver can't see for some reason--for instance, some drivers can't see networks on channels 12 and 13 because of region settings.

Since dmesg doesn't mention anything about why the wireless card shouldn't be able to see networks, I think that next logical step here is to figure out information about the wireless network.

---

### Post by icecreamcakez on 2009-02-24
channel 11 pytheas

---

### Post by icecreamcakez on 2009-02-24
mode : 54G auto

---

### Post by icecreamcakez on 2009-02-24
hey friends going to bed now 
nite pytheas 
nite colonel
nite snellie
:) jes

---

### Post by sgosnell on 2009-02-24
I'm not convinced the card is enabled.  What do you get from System/Administration/Hardware Drivers?  Is the driver actually enabled?  If it is, you should be getting a connection, but the output you've been posting above doesn't seem to indicate that it is enabled.

---

### Post by sgosnell on 2009-02-24
OK, have a good night in the red stick.

Umm... why is ath5k blacklisted?  If it's not installed, there is no need to blacklist it, and it might confuse Ubuntu enough to blacklist ath9k also, but I'm far from sure of that.

---

### Post by icecreamcakez on 2009-02-24
hey all 
guys once again thank you so much for helping 
and good morning :)

---

### Post by icecreamcakez on 2009-02-24
wireless still flying around somewhere

---

### Post by pytheas22 on 2009-02-24
Channel 11 in g mode should definitely be visible, so we can rule out your router's settings as the problem.  I'm wondering at this point if the wireless card is simply turned off.  Is there a button on your computer that you press to enable the wireless, or a key combination (like function+F2)?  If so, please try flipping it.  Please also post the output at this point of:
```

lshw -C Network
dmesg | grep -e adio -e wlan -e ath
```

---

### Post by icecreamcakez on 2009-02-24
pytheas!! 
hey honey bear

---

### Post by icecreamcakez on 2009-02-24
jes@HACIENDA:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:11:62:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:b1:3d:85:d6:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by icecreamcakez on 2009-02-24
IENDA:~$ dmesg | grep -e adio -e wlan -e ath
[   13.624266] ath9k: 0.1
[   13.624315] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.624328] ath9k 0000:04:00.0: setting latency timer to 64
[   14.103156] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.286572] Registered led device: ath9k-phy0:radio
[   14.286590] Registered led device: ath9k-phy0:assoc
[   14.286608] Registered led device: ath9k-phy0:tx
[   14.286628] Registered led device: ath9k-phy0:rx
[   42.022560] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
switch is active sir 
led indication is a negative

---

### Post by pytheas22 on 2009-02-24
hmmm, I'm still very puzzled as to why the card won't see networks even though the radio seems to be turned on (at least, nothing says it's turned off).  Maybe it would help to install a more up-to-date version of the ath9k driver.  You can do that by first downloading [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2") and saving it to your desktop, then running these commands:
```

sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot.  Any more luck?  What is the output after the reboot of:
```

lshw -C Network
dmesg | grep -e ath -e wlan -e adio
sudo iwlist scan
modinfo ath9k
```

---

### Post by icecreamcakez on 2009-02-24
roger that honey bear will do 
should i do any pre-install removal of previous items 
or proceed

---

### Post by icecreamcakez on 2009-02-24
pytheas the file doesnt download do you have a http:// for it

---

### Post by icecreamcakez on 2009-02-24
We have enabled anti-hotlinking to the compat-wireless-2.6.tar.bz2 tarball. This ensures users directed to this tarball from random tutorials online will hopefully read this page. Anti-hotlinking prevents users from accessing the tarball directly before seeing this page. In summary, you cannot directly (for example using wget) this tarball before having viewed this introductory page. If you try to do so you will be redirected here. You can, however, directly download a dated version of the tarball, for example compat-wireless-2008-03-25.tar.bz2.

---

### Post by icecreamcakez on 2009-02-24
"this page" link did not load so i google searched tar -xjvf compat-wireless-2.6.tar.bz2 
and ended up here 
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
is this the correct site

---

### Post by pytheas22 on 2009-02-24
> "this page" link did not load so i google searched tar -xjvf compat-wireless-2.6.tar.bz2
and ended up here
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
is this the correct site 

Sorry, that website does stupid things that make it difficult for people to download the files.  Basically, you just need to go to [http://wireless.kernel.org/en/users/Download#Directlydownloadingthetarball](http://wireless.kernel.org/en/users/Download#Directlydownloadingthetarball) and click the link for 'compat-wireless-2.6.tar.bz2', then save it to your desktop.  After that, just run the commands from my last post.

---

### Post by icecreamcakez on 2009-02-24
roger that

---

### Post by icecreamcakez on 2009-02-24
jes@HACIENDA:~$ sudo apt-get install build-essential
[sudo] password for jes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libcommons-logging-java
  gtk2-engines-ubuntulooks libservlet2.3-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jes@HACIENDA:~$ cd ~/desktop
bash: cd: /home/jes/desktop: No such file or directory
jes@HACIENDA:~$ cd ~/desktop
bash: cd: /home/jes/desktop: No such file or directory
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:11:62:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:90:ea:8e:1c:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
~$ dmesg | grep -e ath -e wlan -e adio
[   13.394619] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.394633] ath9k 0000:04:00.0: setting latency timer to 64
[   13.889392] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.106869] Registered led device: ath9k-phy0::radio
[   14.106892] Registered led device: ath9k-phy0::assoc
[   14.106907] Registered led device: ath9k-phy0::tx
[   14.106923] Registered led device: ath9k-phy0::rx
[   41.648753] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by pytheas22 on 2009-02-24
It didn't work because you typed 'desktop' instead of 'Desktop'.  Case matters in Linux.  So please run these commands again, paying attention to capital letters:

```
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

---

### Post by icecreamcakez on 2009-02-24
sharp eye pytheas dam youre good

---

### Post by icecreamcakez on 2009-02-24
jes swithcing to copy/paste mode lol

---

### Post by icecreamcakez on 2009-02-24
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install

sweetie in the last post you left out sudo apt-get install build essential is this correct

---

### Post by icecreamcakez on 2009-02-24
/scripts/unload.sh
jes@HACIENDA:~/Desktop$ cd compat-wireless*
jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$ make
make: Nothing to be done for `all'.
jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$

---

### Post by icecreamcakez on 2009-02-24
ENDA:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:11:62:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:68:10:7a:33:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
nfiguration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jes@HACIENDA:~$ dmesg | grep -e ath -e wlan -e adio
[   13.921825] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.921842] ath9k 0000:04:00.0: setting latency timer to 64
[   14.361428] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.527866] Registered led device: ath9k-phy0::radio
[   14.527884] Registered led device: ath9k-phy0::assoc
[   14.527901] Registered led device: ath9k-phy0::tx
[   14.527917] Registered led device: ath9k-phy0::rx
[   47.387116] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jes@HACIENDA:~$

---

### Post by pytheas22 on 2009-02-24
> sweetie in the last post you left out sudo apt-get install build essential is this correct

Yes, you only needed to run that once and you already did.

What is the output of:
```

ls ~/Desktop/compat-wireless-2009-02-24
cd ~/Desktop/compat-wireless-2009-02-24
make all
```

---

### Post by icecreamcakez on 2009-02-24
ACIENDA:~$ sudo iwlist scan
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIEN

---

### Post by icecreamcakez on 2009-02-24
aster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIENDA:~$ modinfo ath9k
filename:       /lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BFAA1ED241270DAB9BB1CBB
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211,rfkill,cfg80211
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
NDA:~$ ls ~/Desktop/compat-wireless-2009-02-24
built-in.o      COPYRIGHT     Makefile        modules.order   scripts
compat          drivers       master-tag      Module.symvers
compat-release  git-describe  Module.markers  net
config.mk       include       modules         README
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
DA:~$ cd ~/Desktop/compat-wireless-2009-02-24
jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$

---

### Post by icecreamcakez on 2009-02-24
NDA:~$ make all
make: *** No rule to make target `all'.  Stop.
jes@HACIENDA:~$

---

### Post by pytheas22 on 2009-02-24
I have no idea why it's giving the message about 'no rule to make target all', unless the source code that you downloaded was corrupted or something.  What is the output of:
```

cat ~/Desktop/compat-wireless-2009-02-24/Makefile
```

---

### Post by icecreamcakez on 2009-02-24
jes@HACIENDA:~$ cat ~/Desktop/compat-wireless-2009-02-24/Makefile
export KMODDIR?=       updates
KMODDIR_ARG:=   "INSTALL_MOD_DIR=$(KMODDIR)"
ifneq ($(origin $(KLIB)), undefined)
KMODPATH_ARG:=  "INSTALL_MOD_PATH=$(KLIB)"
else
export KLIB:=          /lib/modules/$(shell uname -r)
endif
export KLIB_BUILD ?=	$(KLIB)/build
# Sometimes not available in the path
MODPROBE := /sbin/modprobe
MADWIFI=$(shell $(MODPROBE) -l ath_pci)
OLD_IWL=$(shell $(MODPROBE) -l iwl4965)

ifneq ($(KERNELRELEASE),)

include $(M)/$(COMPAT_CONFIG)

NOSTDINC_FLAGS := -I$(M)/include/ -include $(M)/include/net/compat.h $(CFLAGS)

obj-y := net/wireless/ net/mac80211/
ifeq ($(ONLY_CORE),)
obj-$(CONFIG_B44) += drivers/net/b44.o
obj-y += drivers/ssb/ \
	drivers/misc/eeprom/ \
	drivers/net/usb/ \
	drivers/net/wireless/
endif

else

export PWD :=	$(shell pwd)

# These exported as they are used by the scripts
# to check config and compat autoconf
export COMPAT_CONFIG=config.mk
export CONFIG_CHECK=.$(COMPAT_CONFIG)_md5sum.txt
export COMPAT_AUTOCONF=include/linux/compat_autoconf.h
export CREL=$(shell cat $(PWD)/compat-release)
export CREL_PRE:=.compat_autoconf_
export CREL_CHECK:=$(CREL_PRE)$(CREL)

include $(PWD)/$(COMPAT_CONFIG)

all: modules

modules: $(CREL_CHECK)
	@./scripts/check_config.sh
	$(MAKE) -C $(KLIB_BUILD) M=$(PWD) modules
	@touch $@

# With the above and this we make sure we generate a new compat autoconf per
# new relase of compat-wireless-2.6 OR when the user updates the 
# $(COMPAT_CONFIG) file
$(CREL_CHECK):
	@# Force to regenerate compat autoconf
	@rm -f $(CONFIG_CHECK)
	@./scripts/check_config.sh
	@touch $@
	@md5sum $(COMPAT_CONFIG) > $(CONFIG_CHECK)

install: uninstall modules
	$(MAKE) -C $(KLIB_BUILD) M=$(PWD) $(KMODDIR_ARG) $(KMODPATH_ARG) \
		modules_install
	@# All the scripts we can use
	@mkdir -p /usr/lib/compat-wireless/
	@install scripts/modlib.sh	/usr/lib/compat-wireless/
	@install scripts/madwifi-unload	/usr/sbin/
	@# This is to allow switching between drivers without blacklisting
	@install scripts/athenable	/usr/sbin/
	@install scripts/b43enable	/usr/sbin/
	@install scripts/iwl-enable	/usr/sbin/
	@install scripts/athload	/usr/sbin/
	@install scripts/b43load	/usr/sbin/
	@install scripts/iwl-load	/usr/sbin/
	@if [ ! -z $(MADWIFI) ]; then \
		echo ;\
		echo -n "Note: madwifi detected, we're going to disable it. "  ;\
		echo "If you would like to enable it later you can run:"  ;\
		echo "    sudo athenable madwifi"  ;\
		echo ;\
		echo Running athenable ath5k...;\
		/usr/sbin/athenable ath5k ;\
	fi
	@if [ ! -z $(OLD_IWL) ]; then \
		echo ;\
		echo -n "Note: iwl4965 detected, we're going to disable it. "  ;\
		echo "If you would like to enable it later you can run:"  ;\
		echo "    sudo iwl-load iwl4965"  ;\
		echo ;\
		echo Running iwl-enable iwlagn...;\
		/usr/sbin/iwl-enable iwlagn ;\
	fi
	@# If on distributions like Mandriva which like to
	@# compress their modules this will find out and do
	@# it for you. Reason is some old version of modutils
	@# won't know mac80211.ko should be used instead of
	@# mac80211.ko.gz
	@./scripts/compress_modules
	@/sbin/depmod -ae
	@echo
	@echo "Currently detected wireless subsystem modules:"
	@echo 
	@$(MODPROBE) -l mac80211
	@$(MODPROBE) -l cfg80211
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l adm8211
	@$(MODPROBE) -l at76c50x-usb
	@$(MODPROBE) -l ath5k
	@$(MODPROBE) -l ath9k
	@$(MODPROBE) -l b43
	@$(MODPROBE) -l b43legacy
	@$(MODPROBE) -l b44
	@$(MODPROBE) -l ssb
	@$(MODPROBE) -l rc80211_simple
	@$(MODPROBE) -l iwlcore
	@$(MODPROBE) -l iwl3945
	@$(MODPROBE) -l iwlagn
	@$(MODPROBE) -l ipw2100
	@$(MODPROBE) -l ipw2200
	@$(MODPROBE) -l libipw
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l lib80211_crypt
	@$(MODPROBE) -l libertas_cs
	@$(MODPROBE) -l libertas_tf
	@$(MODPROBE) -l libertas_tf_usb
	@$(MODPROBE) -l ub8xxx
	@$(MODPROBE) -l p54pci
	@$(MODPROBE) -l p54usb
	@$(MODPROBE) -l rt2400pci
	@$(MODPROBE) -l rt2500pci
	@$(MODPROBE) -l rt2500usb
	@$(MODPROBE) -l rt61pci
	@$(MODPROBE) -l rt73usb
	@$(MODPROBE) -l usbnet
	@$(MODPROBE) -l cdc_ether
	@$(MODPROBE) -l rndis_host
	@$(MODPROBE) -l rndis_wlan
	@$(MODPROBE) -l rtl8180
	@$(MODPROBE) -l rtl8187
	@$(MODPROBE) -l zd1211rw
	@echo 
	@echo Now run:
	@echo 
	@echo make unload
	@echo
	@echo And then load the wireless module you need. If unsure reboot.
	@echo

uninstall:
	@# New location, matches upstream
	@rm -rf $(KLIB)/$(KMODDIR)/net/mac80211/
	@rm -rf $(KLIB)/$(KMODDIR)/net/wireless/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/ssb/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/net/usb/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/net/wireless/
	@# Lets only remove the stuff we are sure we are providing
	@# on the misc directory.
	@rm -f $(KLIB)/$(KMODDIR)/drivers/misc/eeprom/eeprom_93cx6.ko*
	@rm -f $(KLIB)/$(KMODDIR)/drivers/misc/eeprom_93cx6.ko*
	@rm -f $(KLIB)/$(KMODDIR)/drivers/net/b44.ko*
	@/sbin/depmod -ae
	@echo
	@echo "Your old wireless subsystem modules were left intact:"
	@echo 
	@$(MODPROBE) -l mac80211
	@$(MODPROBE) -l cfg80211
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l adm8211
	@$(MODPROBE) -l at76c50x-usb
	@$(MODPROBE) -l ath5k
	@$(MODPROBE) -l ath9k
	@$(MODPROBE) -l b43
	@$(MODPROBE) -l b43legacy
	@$(MODPROBE) -l b44
	@$(MODPROBE) -l ssb
	@$(MODPROBE) -l rc80211_simple
	@$(MODPROBE) -l iwlcore
	@$(MODPROBE) -l iwl3945
	@$(MODPROBE) -l iwlagn
	@$(MODPROBE) -l ipw2100
	@$(MODPROBE) -l ipw2200
	@$(MODPROBE) -l libipw
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l lib80211_crypt
	@$(MODPROBE) -l libertas_cs
	@$(MODPROBE) -l libertas_tf
	@$(MODPROBE) -l libertas_tf_usb
	@$(MODPROBE) -l ub8xxx
	@$(MODPROBE) -l p54pci
	@$(MODPROBE) -l p54usb
	@$(MODPROBE) -l rt2400pci
	@$(MODPROBE) -l rt2500pci
	@$(MODPROBE) -l rt2500usb
	@$(MODPROBE) -l rt61pci
	@$(MODPROBE) -l rt73usb
	@$(MODPROBE) -l usbnet
	@$(MODPROBE) -l cdc_ether
	@$(MODPROBE) -l rndis_host
	@$(MODPROBE) -l rndis_wlan
	@$(MODPROBE) -l rtl8180
	@$(MODPROBE) -l rtl8187
	@$(MODPROBE) -l zd1211rw
	@
	@echo 

clean:
	@if [ -d net -a -d $(KLIB_BUILD) ]; then \
		$(MAKE) -C $(KLIB_BUILD) M=$(PWD) clean ;\
	fi
	@rm -f $(CREL_PRE)*
unload:
	@./scripts/unload.sh

load: unload
	@./scripts/load.shcj@HACIENDA:~$ cat ~/Desktop/compat-wireless-2009-02-24/Makefile
export KMODDIR?=       updates
KMODDIR_ARG:=   "INSTALL_MOD_DIR=$(KMODDIR)"
ifneq ($(origin $(KLIB)), undefined)
KMODPATH_ARG:=  "INSTALL_MOD_PATH=$(KLIB)"
else
export KLIB:=          /lib/modules/$(shell uname -r)
endif
export KLIB_BUILD ?=	$(KLIB)/build
# Sometimes not available in the path
MODPROBE := /sbin/modprobe
MADWIFI=$(shell $(MODPROBE) -l ath_pci)
OLD_IWL=$(shell $(MODPROBE) -l iwl4965)

ifneq ($(KERNELRELEASE),)

include $(M)/$(COMPAT_CONFIG)

NOSTDINC_FLAGS := -I$(M)/include/ -include $(M)/include/net/compat.h $(CFLAGS)

obj-y := net/wireless/ net/mac80211/
ifeq ($(ONLY_CORE),)
obj-$(CONFIG_B44) += drivers/net/b44.o
obj-y += drivers/ssb/ \
	drivers/misc/eeprom/ \
	drivers/net/usb/ \
	drivers/net/wireless/
endif

else

export PWD :=	$(shell pwd)

# These exported as they are used by the scripts
# to check config and compat autoconf
export COMPAT_CONFIG=config.mk
export CONFIG_CHECK=.$(COMPAT_CONFIG)_md5sum.txt
export COMPAT_AUTOCONF=include/linux/compat_autoconf.h
export CREL=$(shell cat $(PWD)/compat-release)
export CREL_PRE:=.compat_autoconf_
export CREL_CHECK:=$(CREL_PRE)$(CREL)

include $(PWD)/$(COMPAT_CONFIG)

all: modules

modules: $(CREL_CHECK)
	@./scripts/check_config.sh
	$(MAKE) -C $(KLIB_BUILD) M=$(PWD) modules
	@touch $@

# With the above and this we make sure we generate a new compat autoconf per
# new relase of compat-wireless-2.6 OR when the user updates the 
# $(COMPAT_CONFIG) file
$(CREL_CHECK):
	@# Force to regenerate compat autoconf
	@rm -f $(CONFIG_CHECK)
	@./scripts/check_config.sh
	@touch $@
	@md5sum $(COMPAT_CONFIG) > $(CONFIG_CHECK)

install: uninstall modules
	$(MAKE) -C $(KLIB_BUILD) M=$(PWD) $(KMODDIR_ARG) $(KMODPATH_ARG) \
		modules_install
	@# All the scripts we can use
	@mkdir -p /usr/lib/compat-wireless/
	@install scripts/modlib.sh	/usr/lib/compat-wireless/
	@install scripts/madwifi-unload	/usr/sbin/
	@# This is to allow switching between drivers without blacklisting
	@install scripts/athenable	/usr/sbin/
	@install scripts/b43enable	/usr/sbin/
	@install scripts/iwl-enable	/usr/sbin/
	@install scripts/athload	/usr/sbin/
	@install scripts/b43load	/usr/sbin/
	@install scripts/iwl-load	/usr/sbin/
	@if [ ! -z $(MADWIFI) ]; then \
		echo ;\
		echo -n "Note: madwifi detected, we're going to disable it. "  ;\
		echo "If you would like to enable it later you can run:"  ;\
		echo "    sudo athenable madwifi"  ;\
		echo ;\
		echo Running athenable ath5k...;\
		/usr/sbin/athenable ath5k ;\
	fi
	@if [ ! -z $(OLD_IWL) ]; then \
		echo ;\
		echo -n "Note: iwl4965 detected, we're going to disable it. "  ;\
		echo "If you would like to enable it later you can run:"  ;\
		echo "    sudo iwl-load iwl4965"  ;\
		echo ;\
		echo Running iwl-enable iwlagn...;\
		/usr/sbin/iwl-enable iwlagn ;\
	fi
	@# If on distributions like Mandriva which like to
	@# compress their modules this will find out and do
	@# it for you. Reason is some old version of modutils
	@# won't know mac80211.ko should be used instead of
	@# mac80211.ko.gz
	@./scripts/compress_modules
	@/sbin/depmod -ae
	@echo
	@echo "Currently detected wireless subsystem modules:"
	@echo 
	@$(MODPROBE) -l mac80211
	@$(MODPROBE) -l cfg80211
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l adm8211
	@$(MODPROBE) -l at76c50x-usb
	@$(MODPROBE) -l ath5k
	@$(MODPROBE) -l ath9k
	@$(MODPROBE) -l b43
	@$(MODPROBE) -l b43legacy
	@$(MODPROBE) -l b44
	@$(MODPROBE) -l ssb
	@$(MODPROBE) -l rc80211_simple
	@$(MODPROBE) -l iwlcore
	@$(MODPROBE) -l iwl3945
	@$(MODPROBE) -l iwlagn
	@$(MODPROBE) -l ipw2100
	@$(MODPROBE) -l ipw2200
	@$(MODPROBE) -l libipw
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l lib80211_crypt
	@$(MODPROBE) -l libertas_cs
	@$(MODPROBE) -l libertas_tf
	@$(MODPROBE) -l libertas_tf_usb
	@$(MODPROBE) -l ub8xxx
	@$(MODPROBE) -l p54pci
	@$(MODPROBE) -l p54usb
	@$(MODPROBE) -l rt2400pci
	@$(MODPROBE) -l rt2500pci
	@$(MODPROBE) -l rt2500usb
	@$(MODPROBE) -l rt61pci
	@$(MODPROBE) -l rt73usb
	@$(MODPROBE) -l usbnet
	@$(MODPROBE) -l cdc_ether
	@$(MODPROBE) -l rndis_host
	@$(MODPROBE) -l rndis_wlan
	@$(MODPROBE) -l rtl8180
	@$(MODPROBE) -l rtl8187
	@$(MODPROBE) -l zd1211rw
	@echo 
	@echo Now run:
	@echo 
	@echo make unload
	@echo
	@echo And then load the wireless module you need. If unsure reboot.
	@echo

uninstall:
	@# New location, matches upstream
	@rm -rf $(KLIB)/$(KMODDIR)/net/mac80211/
	@rm -rf $(KLIB)/$(KMODDIR)/net/wireless/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/ssb/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/net/usb/
	@rm -rf $(KLIB)/$(KMODDIR)/drivers/net/wireless/
	@# Lets only remove the stuff we are sure we are providing
	@# on the misc directory.
	@rm -f $(KLIB)/$(KMODDIR)/drivers/misc/eeprom/eeprom_93cx6.ko*
	@rm -f $(KLIB)/$(KMODDIR)/drivers/misc/eeprom_93cx6.ko*
	@rm -f $(KLIB)/$(KMODDIR)/drivers/net/b44.ko*
	@/sbin/depmod -ae
	@echo
	@echo "Your old wireless subsystem modules were left intact:"
	@echo 
	@$(MODPROBE) -l mac80211
	@$(MODPROBE) -l cfg80211
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l adm8211
	@$(MODPROBE) -l at76c50x-usb
	@$(MODPROBE) -l ath5k
	@$(MODPROBE) -l ath9k
	@$(MODPROBE) -l b43
	@$(MODPROBE) -l b43legacy
	@$(MODPROBE) -l b44
	@$(MODPROBE) -l ssb
	@$(MODPROBE) -l rc80211_simple
	@$(MODPROBE) -l iwlcore
	@$(MODPROBE) -l iwl3945
	@$(MODPROBE) -l iwlagn
	@$(MODPROBE) -l ipw2100
	@$(MODPROBE) -l ipw2200
	@$(MODPROBE) -l libipw
	@$(MODPROBE) -l lib80211
	@$(MODPROBE) -l lib80211_crypt
	@$(MODPROBE) -l libertas_cs
	@$(MODPROBE) -l libertas_tf
	@$(MODPROBE) -l libertas_tf_usb
	@$(MODPROBE) -l ub8xxx
	@$(MODPROBE) -l p54pci
	@$(MODPROBE) -l p54usb
	@$(MODPROBE) -l rt2400pci
	@$(MODPROBE) -l rt2500pci
	@$(MODPROBE) -l rt2500usb
	@$(MODPROBE) -l rt61pci
	@$(MODPROBE) -l rt73usb
	@$(MODPROBE) -l usbnet
	@$(MODPROBE) -l cdc_ether
	@$(MODPROBE) -l rndis_host
	@$(MODPROBE) -l rndis_wlan
	@$(MODPROBE) -l rtl8180
	@$(MODPROBE) -l rtl8187
	@$(MODPROBE) -l zd1211rw
	@
	@echo 

clean:
	@if [ -d net -a -d $(KLIB_BUILD) ]; then \
		$(MAKE) -C $(KLIB_BUILD) M=$(PWD) clean ;\
	fi
	@rm -f $(CREL_PRE)*
unload:
	@./scripts/unload.sh

load: unload
	@./scripts/load.sh

.PHONY: all clean install uninstall unload load

endif

clean-files += Module.symvers modules modules.order $(CREL_CHECK) $(CONFIG_CHECK)


.PHONY: all clean install uninstall unload load

endif

clean-files += Module.symvers modules modules.order $(CREL_CHECK) $(CONFIG_CHECK)

---

### Post by icecreamcakez on 2009-02-24
youre damn good with this pytheas 
again thank you

---

### Post by pytheas22 on 2009-02-24
Are you opening up a new terminal window for each of the commands?  Please type these commands, one per line, all in the same window, and post the output:
```

cd ~/Desktop/compat-wireless-2009-02-24
make
sudo make install
```

---

### Post by icecreamcakez on 2009-02-24
just one terminal window was used 

jes@HACIENDA:~$ cd ~/Desktop/compat-wireless-2009-02-24
jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$ make
make: Nothing to be done for `all'.
jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$ sudo make install
[sudo] password for jes: 

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/adm8211.ko
/lib/modules/2.6.27-11-generic/updates/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/ath9k.ko
/lib/modules/2.6.27-11-generic/updates/b43.ko
/lib/modules/2.6.27-11-generic/updates/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/b44.ko
/lib/modules/2.6.27-11-generic/updates/ssb.ko
/lib/modules/2.6.27-11-generic/updates/iwlcore.ko
/lib/modules/2.6.27-11-generic/updates/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko
/lib/modules/2.6.27-11-generic/updates/p54pci.ko
/lib/modules/2.6.27-11-generic/updates/p54usb.ko
/lib/modules/2.6.27-11-generic/updates/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/zd1211rw.ko

make -C /lib/modules/2.6.27-11-generic/build M=/home/jes/Desktop/compat-wireless-2009-02-24 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/b44.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/usb/cdc_ether.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/usb/rndis_host.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/usb/usbnet.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/adm8211.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/b43/b43.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/drivers/ssb/ssb.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/mac80211/mac80211.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/wireless/cfg80211.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/wireless/lib80211.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/jes/Desktop/compat-wireless-2009-02-24/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.27-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
/lib/modules/2.6.27-11-generic/volatile/ath_pci.ko

Currently detected wireless subsystem modules:

/lib/modules/2.6.27-11-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/at76c50x-usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/b44.ko
/lib/modules/2.6.27-11-generic/updates/ssb.ko
/lib/modules/2.6.27-11-generic/updates/iwlcore.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ipw2x00/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ipw2x00/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/p54/p54pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/p54/p54usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

jes@HACIENDA:~/Desktop/compat-wireless-2009-02-24$

---

### Post by icecreamcakez on 2009-02-24
my network manager icon changed after reboot
i looked into edit connections and nothing is listed in wireless connection one i have all but the bssid how do i determine this number

---

### Post by icecreamcakez on 2009-02-24
should this be edited or is this feature on auto

---

### Post by icecreamcakez on 2009-02-24
got it 
shouldnt this be filled out if so i know all of the required info except whats bssid

---

### Post by pytheas22 on 2009-02-24
You shouldn't need to be filling in those options.  Unless your network is hidden (which I assume is not the case), Ubuntu should be able to see it, and you should just click on its name in order to connect (if it needs a password, Ubuntu will ask you for it).  If you still can't see networks, then unfortunately something is wrong...

What is the output of:
```

lsmod | grep ath
modinfo ath9k
dmesg
sudo iwlist scan
```

The first command will dump a lot of output, but please post it all; hopefully it will explain why things are still not working as intended.

---

### Post by icecreamcakez on 2009-02-24
pytheas!!
muah!

---

### Post by icecreamcakez on 2009-02-24
jes@HACIENDA:~$ lsmod | grep ath
ath9k                 234928  0 
mac80211              224036  1 ath9k
rfkill                 17176  2 ath9k
cfg80211               67232  2 ath9k,mac80211
led_class              12164  1 ath9k
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
IENDA:~$ modinfo ath9k
filename:       /lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BFAA1ED241270DAB9BB1CBB
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211,rfkill,cfg80211
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
[    2.529256] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.529266] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.529271] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.529295] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.529333] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    2.529425] usb usb2: configuration #1 chosen from 1 choice
[    2.529452] hub 2-0:1.0: USB hub found
[    2.529458] hub 2-0:1.0: 2 ports detected
[    2.529679] No dock devices found.
[    2.547758] SCSI subsystem initialized
[    2.572110] libata version 3.00 loaded.
[    2.633360] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.633379] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.633383] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.633411] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.637321] ehci_hcd 0000:00:1a.7: debug port 1
[    2.637328] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.637345] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3404800
[    2.653028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.653189] usb usb3: configuration #1 chosen from 1 choice
[    2.653224] hub 3-0:1.0: USB hub found
[    2.653233] hub 3-0:1.0: 4 ports detected
[    2.861265] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.861276] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.861281] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.861308] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.861349] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.861466] usb usb4: configuration #1 chosen from 1 choice
[    2.861494] hub 4-0:1.0: USB hub found
[    2.861501] hub 4-0:1.0: 2 ports detected
[    2.964253] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.964264] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.964269] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.964299] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.964337] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.964431] usb usb5: configuration #1 chosen from 1 choice
[    2.964457] hub 5-0:1.0: USB hub found
[    2.964464] hub 5-0:1.0: 2 ports detected
[    2.972045] usb 3-3: new high speed USB device using ehci_hcd and address 2
[    3.069228] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.069238] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.069243] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.069267] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.069298] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.069390] usb usb6: configuration #1 chosen from 1 choice
[    3.069416] hub 6-0:1.0: USB hub found
[    3.069422] hub 6-0:1.0: 2 ports detected
[    3.117589] usb 3-3: configuration #1 chosen from 1 choice
[    3.173268] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.173284] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.173288] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.173313] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.177240] ehci_hcd 0000:00:1d.7: debug port 1
[    3.177247] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.177254] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3404c00
[    3.192028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.192129] usb usb7: configuration #1 chosen from 1 choice
[    3.192156] hub 7-0:1.0: USB hub found
[    3.192164] hub 7-0:1.0: 6 ports detected
[    3.400730] ata_piix 0000:00:1f.1: version 2.12
[    3.400743] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.400784] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.400892] scsi0 : ata_piix
[    3.400999] scsi1 : ata_piix
[    3.401735] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.401738] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.564448] ata1.00: ATAPI: Optiarc DVD RW AD-7563A, WX05, max UDMA/33
[    3.580390] ata1.00: configured for UDMA/33
[    3.616034] usb 7-4: new high speed USB device using ehci_hcd and address 2
[    3.748239] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7563A  WX05 PQ: 0 ANSI: 5
[    3.748335] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.748354] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.748374] r8169 0000:02:00.0: setting latency timer to 64
[    3.748762] eth0: RTL8101e at 0xf884c000, 00:21:cc:01:b1:0e, XID 34200000 IRQ 220
[    3.750554] ahci 0000:00:1f.2: version 3.0
[    3.750571] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.750678] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    3.750681] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.750687] ahci 0000:00:1f.2: setting latency timer to 64
[    3.751432] scsi2 : ahci
[    3.753023] scsi3 : ahci
[    3.753121] scsi4 : ahci
[    3.753236] ata3: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404100 irq 219
[    3.753240] ata4: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404180 irq 219
[    3.753243] ata5: SATA max UDMA/133 abar m2048@0xf3404000 port 0xf3404200 irq 219
[    3.768312] usb 7-4: configuration #1 chosen from 1 choice
[    3.779286] usbcore: registered new interface driver libusual
[    3.785773] Initializing USB Mass Storage driver...
[    3.786514] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.786617] usbcore: registered new interface driver usb-storage
[    3.786621] USB Mass Storage support registered.
[    3.786786] usb-storage: device found at 2
[    3.786788] usb-storage: waiting for device to settle before scanning
[    3.793343] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.072044] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.072655] ata3.00: _GTF unexpected object type 0x1
[    4.126609] ata3.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[    4.126612] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.127476] ata3.00: _GTF unexpected object type 0x1
[    4.127625] ata3.00: configured for UDMA/133
[    4.460036] ata4: SATA link down (SStatus 0 SControl 300)
[    4.796037] ata5: SATA link down (SStatus 0 SControl 300)
[    4.812120] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[    4.812271] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.843518] Driver 'sr' needs updating - please use bus_type methods
[    4.847881] Driver 'sd' needs updating - please use bus_type methods
[    4.852278] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.852282] Uniform CD-ROM driver Revision: 3.20
[    4.852378] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.852471] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.852487] sd 2:0:0:0: [sda] Write Protect is off
[    4.852489] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.852515] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.852575] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.852589] sd 2:0:0:0: [sda] Write Protect is off
[    4.852592] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.852617] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.852620]  sda: sda1 sda2 < sda5 >
[    5.095295] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.215073] PM: Starting manual resume from disk
[    5.215077] PM: Resume from partition 8:5
[    5.215079] PM: Checking hibernation image.
[    5.215249] PM: Resume from disk failed.
[    5.287962] kjournald starting.  Commit interval 5 seconds
[    5.287987] EXT3-fs: mounted filesystem with ordered data mode.
[    8.784288] usb-storage: device scan complete
[    8.790602] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   12.129724] udevd version 124 started
[   12.304595] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   12.304750] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   12.543912] Linux agpgart interface v0.103
[   12.661175] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.704365] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.722694] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.744038] ACPI: Power Button (FF) [PWRF]
[   12.744154] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   12.744467] ACPI: Lid Switch [LID0]
[   12.744538] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.761443] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.761743] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.774751] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.780039] ACPI: Power Button (CM) [PWRB]
[   12.780118] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   12.812037] ACPI: Sleep Button (CM) [SLPB]
[   12.882987] ACPI: AC Adapter [AC] (on-line)
[   12.947217] acpi device:0b: registered as cooling_device2
[   12.947616] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input6
[   12.968047] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.041777] ACPI: Battery Slot [BAT0] (battery present)
[   13.177226] iTCO_vendor_support: vendor-support=0
[   13.181219] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.181313] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   13.181417] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.503719] Linux video capture interface: v2.00
[   13.584218] uvcvideo: Found UVC 1.00 device Gateway USB 2.0 Webcam (04f2:b027)
[   13.585307] input: Gateway USB 2.0 Webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-3/3-3:1.0/input/input7
[   13.585356] usbcore: registered new interface driver uvcvideo
[   13.585360] USB Video Class driver (v0.1.0)
[   13.610116] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.610155] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.753285] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.760098] cfg80211: Using static regulatory domain info
[   13.760101] cfg80211: Regulatory domain: US
[   13.760103] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.760106] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   13.760109] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.760111] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.760114] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.760116] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.760119] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   13.760210] cfg80211: Calling CRDA for country: US
[   13.883134] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.883148] ath9k 0000:04:00.0: setting latency timer to 64
[   14.302424] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04711/0x0
[   14.319410] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.338880] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.465063] Registered led device: ath9k-phy0::radio
[   14.465085] Registered led device: ath9k-phy0::assoc
[   14.465102] Registered led device: ath9k-phy0::tx
[   14.465117] Registered led device: ath9k-phy0::rx
[   14.465136] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8d20000, irq=17
[   23.134062] lp: driver loaded but no devices found
[   23.258657] Adding 9084716k swap on /dev/sda5.  Priority:-1 extents:1 across:9084716k
[   23.799364] EXT3 FS on sda1, internal journal
[   24.802368] type=1505 audit(1235505361.831:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4191
[   24.970092] type=1505 audit(1235505361.999:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4196
[   24.970312] type=1505 audit(1235505361.999:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4196
[   25.147152] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.750314] ACPI: WMI: Mapper loaded
[   26.639521] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.734374] apm: BIOS not found.
[   26.881069] ppdev: user-space parallel port driver
[   35.379901] Bluetooth: Core ver 2.13
[   35.380157] NET: Registered protocol family 31
[   35.380164] Bluetooth: HCI device and connection manager initialized
[   35.380170] Bluetooth: HCI socket layer initialized
[   35.417360] Bluetooth: L2CAP ver 2.11
[   35.417370] Bluetooth: L2CAP socket layer initialized
[   35.450330] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.450341] Bluetooth: BNEP filters: protocol multicast
[   35.501415] Bridge firewalling registered
[   35.535461] Bluetooth: SCO (Voice Link) ver 0.6
[   35.535471] Bluetooth: SCO socket layer initialized
[   35.575612] Bluetooth: RFCOMM socket layer initialized
[   35.575634] Bluetooth: RFCOMM TTY layer initialized
[   35.575638] Bluetooth: RFCOMM ver 1.10
[   39.705528] r8169: eth0: link up
[   39.705539] r8169: eth0: link up
[   39.822180] [drm] Initialized drm 1.1.0 20060810
[   39.827759] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.827767] pci 0000:00:02.0: setting latency timer to 64
[   39.827916] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.858777] NET: Registered protocol family 17
[   43.824372] NET: Registered protocol family 10
[   43.825646] lo: Disabled Privacy Extensions
[   43.827614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.205021] eth0: no IPv6 routers present
[   75.935953] CPU0 attaching NULL sched-domain.
[   75.935969] CPU1 attaching NULL sched-domain.
[   75.940231] CPU0 attaching sched-domain:
[   75.940237]  domain 0: span 0-1 level MC
[   75.940240]   groups: 0 1
[   75.940246] CPU1 attaching sched-domain:
[   75.940248]  domain 0: span 0-1 level MC
[   75.940250]   groups: 1 0
[  102.807801] r8169: eth0: link down
[  255.743475] r8169: eth0: link up
[12987.372043] usb 7-1: new high speed USB device using ehci_hcd and address 3
[12987.506644] usb 7-1: configuration #1 chosen from 1 choice
[12987.508356] scsi6 : SCSI emulation for USB Mass Storage devices
[12987.515355] usb-storage: device found at 3
[12987.515366] usb-storage: waiting for device to settle before scanning
[12992.512210] usb-storage: device scan complete
[12992.512703] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[12992.513196] scsi 6:0:0:1: CD-ROM            SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0
[12992.515165] sd 6:0:0:0: [sdc] 15682559 512-byte hardware sectors (8029 MB)
[12992.515668] sd 6:0:0:0: [sdc] Write Protect is off
[12992.515674] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[12992.515680] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[12992.517172] sd 6:0:0:0: [sdc] 15682559 512-byte hardware sectors (8029 MB)
[12992.517665] sd 6:0:0:0: [sdc] Write Protect is off
[12992.517671] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[12992.517676] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[12992.517685]  sdc: sdc1
[12992.518912] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[12992.519090] sd 6:0:0:0: Attached scsi generic sg3 type 0
[12992.522532] sr1: scsi3-mmc drive: 48x/48x tray
[12992.522702] sr 6:0:0:1: Attached scsi CD-ROM sr1
[12992.522873] sr 6:0:0:1: Attached scsi generic sg4 type 5
[12992.685147] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.685156] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.685161] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.685167] end_request: I/O error, dev sr1, sector 196352
[12992.685172] Buffer I/O error on device sr1, logical block 49088
[12992.686019] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.686024] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.686028] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.686033] end_request: I/O error, dev sr1, sector 196356
[12992.686037] Buffer I/O error on device sr1, logical block 49089
[12992.686891] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.686895] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.686899] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.686904] end_request: I/O error, dev sr1, sector 196352
[12992.686907] Buffer I/O error on device sr1, logical block 49088
[12992.687765] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.687769] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.687772] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.687777] end_request: I/O error, dev sr1, sector 196356
[12992.687780] Buffer I/O error on device sr1, logical block 49089
[12992.688644] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.688648] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.688653] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.688658] end_request: I/O error, dev sr1, sector 196584
[12992.688661] Buffer I/O error on device sr1, logical block 49146
[12992.689518] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.689522] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.689526] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.689531] end_request: I/O error, dev sr1, sector 196588
[12992.689534] Buffer I/O error on device sr1, logical block 49147
[12992.690391] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.690396] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.690400] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.690404] end_request: I/O error, dev sr1, sector 196584
[12992.690408] Buffer I/O error on device sr1, logical block 49146
[12992.691264] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.691268] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.691272] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.691277] end_request: I/O error, dev sr1, sector 196588
[12992.691279] Buffer I/O error on device sr1, logical block 49147
[12992.693768] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.693773] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.693778] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.693783] end_request: I/O error, dev sr1, sector 196600
[12992.693787] Buffer I/O error on device sr1, logical block 49150
[12992.694643] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.694646] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.694650] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.694656] end_request: I/O error, dev sr1, sector 196600
[12992.694659] Buffer I/O error on device sr1, logical block 49150
[12992.695517] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.695522] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.695526] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.695531] end_request: I/O error, dev sr1, sector 196600
[12992.696393] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.696397] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.696401] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.696406] end_request: I/O error, dev sr1, sector 196600
[12992.697267] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.697271] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.697276] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.697281] end_request: I/O error, dev sr1, sector 196600
[12992.698142] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.698146] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.698150] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.698155] end_request: I/O error, dev sr1, sector 196600
[12992.699015] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.699019] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.699024] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.699028] end_request: I/O error, dev sr1, sector 196600
[12992.699891] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.699896] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.699900] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.699905] end_request: I/O error, dev sr1, sector 196536
[12992.700767] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.700771] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.700775] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.700780] end_request: I/O error, dev sr1, sector 196540
[12992.701640] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.701646] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.701649] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.701654] end_request: I/O error, dev sr1, sector 196592
[12992.702515] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.702520] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.702524] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.702529] end_request: I/O error, dev sr1, sector 196596
[12992.703392] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.703396] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.703400] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.703405] end_request: I/O error, dev sr1, sector 196600
[12992.704267] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.704272] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.704275] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.704280] end_request: I/O error, dev sr1, sector 196600
[12992.743627] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.743634] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.743639] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.743644] end_request: I/O error, dev sr1, sector 196352
[12992.745276] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.745283] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.745288] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.745293] end_request: I/O error, dev sr1, sector 196356
[12992.748145] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.748153] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.748158] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.748163] end_request: I/O error, dev sr1, sector 196352
[12992.749903] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.749911] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.749915] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.749920] end_request: I/O error, dev sr1, sector 196356
[12992.751635] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.751642] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.751647] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.751652] end_request: I/O error, dev sr1, sector 196584
[12992.753273] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.753281] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.753285] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.753290] end_request: I/O error, dev sr1, sector 196588
[12992.756642] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.756650] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.756655] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.756660] end_request: I/O error, dev sr1, sector 196584
[12992.759768] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.759776] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.759780] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.759786] end_request: I/O error, dev sr1, sector 196588
[12992.765028] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.765037] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.765041] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.765046] end_request: I/O error, dev sr1, sector 196600
[12992.767776] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.767784] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.767788] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.767794] end_request: I/O error, dev sr1, sector 196600
[12992.769519] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.769525] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.769530] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.769535] end_request: I/O error, dev sr1, sector 196600
[12992.771017] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.771023] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.771026] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.771031] end_request: I/O error, dev sr1, sector 196600
[12992.772516] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.772521] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.772524] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.772530] end_request: I/O error, dev sr1, sector 196600
[12992.774019] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.774024] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.774029] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.774034] end_request: I/O error, dev sr1, sector 196600
[12992.775390] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.775395] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.775399] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.775404] end_request: I/O error, dev sr1, sector 196600
[12992.778883] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.778890] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.778894] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.778899] end_request: I/O error, dev sr1, sector 196536
[12992.780520] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.780526] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.780531] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.780536] end_request: I/O error, dev sr1, sector 196540
[12992.782360] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.782366] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.782370] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.782375] end_request: I/O error, dev sr1, sector 196592
[12992.783883] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.783889] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.783893] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.783899] end_request: I/O error, dev sr1, sector 196596
[12992.785507] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.785513] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.785517] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.785522] end_request: I/O error, dev sr1, sector 196600
[12992.787007] sr 6:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[12992.787012] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[12992.787016] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[12992.787022] end_request: I/O error, dev sr1, sector 196600
[13078.997512] r8169: eth0: link down
[13095.273196] usb 7-1: USB disconnect, address 3
[13644.484681] r8169: eth0: link up
jes@HACIEN

/////////////////////////////////////////////////////////////
dmesg seemed to take up too much room in my terminal it wouldnt let me get to the top of the page i pasted everything i can see in terminal all the way up

---

### Post by icecreamcakez on 2009-02-24
97512] r8169: eth0: link down
[13095.273196] usb 7-1: USB disconnect, address 3
[13644.484681] r8169: eth0: link up
jes@HACIENDA:~$ sudo iwlist scan
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-24
i just went to system/admin/windows wireless drivers
i got a screenshot of it 
when i press install it allows me to browse and asks for an inf file

---

### Post by icecreamcakez on 2009-02-24
this is the second option listed after clicking my mouse lol on install driver

---

### Post by icecreamcakez on 2009-02-24
ill be @ 

[http://burnthesorbonne.com/stuff/index.php?m=01&y=08&d=06&entry=entry080106-170749](http://burnthesorbonne.com/stuff/index.php?m=01&y=08&d=06&entry=entry080106-170749)

---

### Post by icecreamcakez on 2009-02-24
lmao ...
so if you were an idiot, you generally wouldn't be able to pollute the Internet with your presence.
 
pytheas you are wild im gonna read ALL of the posts too 
luv it 
muah jes

---

### Post by pytheas22 on 2009-02-25
Installing the newer drivers from source doesn't seem to have made a difference, I guess.  The next possible solution is to run these commands:
```

sudo su
echo 0 > /sys/devices/platform/asus-laptop/bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan
```

According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270748"), which I think is relevant to your problem, this will solve it.  Please run those commands, then reboot and let me know what the output of:
```

sudo iwlist scan
```

is.

Also, what is the exact model of your laptop?

---

### Post by icecreamcakez on 2009-02-25
pytheas!!
roger that will do captain
in process

---

### Post by icecreamcakez on 2009-02-25
Gateway T6330u
im not a bulldike

---

### Post by icecreamcakez on 2009-02-25
jes@HACIENDA:~$ sudo su
root@HACIENDA:/home/jes# echo 0 > /sys/devices/platform/asus-laptop/bluetooth
bash: /sys/devices/platform/asus-laptop/bluetooth: No such file or directory
root@HACIENDA:/home/jes# echo 1 > /sys/devices/platform/asus-laptop/wlan
bash: /sys/devices/platform/asus-laptop/wlan: No such file or directory
root@HACIENDA:/home/jes#

---

### Post by icecreamcakez on 2009-02-25
jes@HACIENDA:~$ sudo iwlist scan
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-25
honey bear i have to go wash my hair 
i shouldnt be long ok 
jes

---

### Post by icecreamcakez on 2009-02-25
should i just reinstall ubuntu and start fresh 
i can do that if it will help

---

### Post by pytheas22 on 2009-02-25
Reinstalling Ubuntu could be the next step--I'm thinking in particular that 8.04 might work better than 8.10--but before going to that extreme, please post the output of:
```

sudo updatedb
sudo locate wlan | grep sys
```

---

### Post by icecreamcakez on 2009-02-25
will do

---

### Post by icecreamcakez on 2009-02-25
jes@HACIENDA:~$ sudo updatedb
jes@HACIENDA:~$ sudo locate wlan | grep sys
jes@HACIENDA:~$ 


....nada
ive moved everything to usb pytheas -picutres and music 
its not a big deal i can even get the same version you have if that will help out even more 
the fix on the wireless is the main thing sweetie 
its when me and my niece go to the kitchen to make things we have to go back to my room just listen to the music we have on here or research things for making cakes like colors etc 
please recommend the best one you can work on and i will get it and install it asap
ash says thank you so much for being so dam awesome !

---

### Post by pytheas22 on 2009-02-25
If you installed 8.04 instead of 8.10, I think that the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=902860") would get your card working.  It wouldn't hurt at this point to have a clean slate anyway.

You can download the ISO for Ubuntu 8.04 [here]("http://www.ubuntu.com/getubuntu/download")--just make sure to select the option that says 'Ubuntu 8.04 LTS Desktop' instead of 'Ubuntu 8.10'.  Once the download is finished, just right-click on the ISO file and select 'Write Image to Disk' to burn it to a CD.  Then boot to the new CD and use it to install Ubuntu 8.04 over the place of your current 8.10 system.

Let me know when you've gotten that far, and we can try to make your wireless card work by following the instructions in that thread.

---

### Post by icecreamcakez on 2009-02-25
pytheas please review my choice in download 
jes~

---

### Post by icecreamcakez on 2009-02-25
update ...
ash changed the download location to MIT and it reduced the download time from a 20 hours to 31 minutes 
shes smart for a dam 14 yr old

---

### Post by icecreamcakez on 2009-02-25
pytheas
got it !!
ash helped and we now have Hardy Heron 8.04
i have not installed any third party items or updates 
its fresh! lol

---

### Post by icecreamcakez on 2009-02-25
this is luscious to sweepea come in over 
ive got the Hardy Heron in my clutches lol 
8.04

---

### Post by icecreamcakez on 2009-02-25
pytheas
i installed youre hardy heron 
lol 
all i did was theme it 
i havent even done updates im waitin on you papa bear

---

### Post by pytheas22 on 2009-02-25
Alright, good that 8.04 is installed.  Now please run these commands, in this order:
```

sudo apt-get update
sudo apt-get upgrade ###this one may take a long time, but let it finish before going on to the next command
sudo apt-get install build-essential
wget http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz
tar -xzvf madwifi-hal-0.10.5.6.tar.gz
cd madwifi-hal-0.10.5.6
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
```

Then reboot.  With any luck, and if the directions I'm following are correct, your wireless will now work.  If not, please post the output of:
```

dmesg | grep -e ath -e adio
sudo iwlist scan
lshw -C Network
```

---

### Post by icecreamcakez on 2009-02-25
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

---

### Post by icecreamcakez on 2009-02-26
A. pytheas!!!!!
B. in progress tootz
C. thank you so very much !
D. how in the world do you put posts in before mine when i posted before you did

---

### Post by icecreamcakez on 2009-02-26
jes@NASA:~$ 
jes@NASA:~$ 
jes@NASA:~$ dmesg | grep -e ath -e adio
[   47.782726] ath_hal: module license 'Proprietary' taints kernel.
jes@NASA:~$ sudo iwlist scan
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jes@NASA:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
NASA:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
jes@NASA:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
ng state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jes@NASA:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jes@NASA:~$ wget [http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz](http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz)
--01:50:05--  [http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz](http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz)
           => `madwifi-hal-0.10.5.6.tar.gz.2'
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,858,083 (8.4M) [application/x-gzip]

100%[====================================>] 8,858,083    514.18K/s    ETA 00:00

01:50:22 (495.27 KB/s) - `madwifi-hal-0.10.5.6.tar.gz.2' saved [8858083/8858083]

jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
madwifi-hal-0.10.5.6/hal/public/powerpc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/alpha-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap43.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/ap51.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/wackelf.c
madwifi-hal-0.10.5.6/hal/public/armv4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips1-le-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/powerpc-be-eabi.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/arm9-le-thumb-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips-le-elf.inc
madwifi-hal-0.10.5.6/hal/public/armv4-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips1-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap30.inc
madwifi-hal-0.10.5.6/hal/public/x86_64-elf.inc
madwifi-hal-0.10.5.6/hal/public/mipsisa32-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap43.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap51.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/sparc64-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/powerpc-be-eabi.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap30.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/armv4-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/mips1-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/i386-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/powerpc-le-eabi.inc
madwifi-hal-0.10.5.6/hal/public/xscale-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap61.inc
madwifi-hal-0.10.5.6/hal/.svn/all-wcprops
madwifi-hal-0.10.5.6/hal/.svn/entries
madwifi-hal-0.10.5.6/hal/.svn/format
madwifi-hal-0.10.5.6/tools/man/wlanconfig.8
madwifi-hal-0.10.5.6/tools/man/athkey.8
madwifi-hal-0.10.5.6/tools/man/athdebug.8
madwifi-hal-0.10.5.6/tools/man/80211debug.8
madwifi-hal-0.10.5.6/tools/man/athctrl.8
madwifi-hal-0.10.5.6/tools/man/athstats.8
madwifi-hal-0.10.5.6/tools/man/80211stats.8
madwifi-hal-0.10.5.6/tools/man/athchans.8
madwifi-hal-0.10.5.6/tools/.svn/dir-prop-base
madwifi-hal-0.10.5.6/tools/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/.svn/entries
madwifi-hal-0.10.5.6/tools/.svn/format
madwifi-hal-0.10.5.6/tools/ath_info/eeprom.h
madwifi-hal-0.10.5.6/tools/ath_info/ath_info.8
madwifi-hal-0.10.5.6/tools/ath_info/README
madwifi-hal-0.10.5.6/tools/ath_info/Makefile
madwifi-hal-0.10.5.6/tools/ath_info/ath_info.c
madwifi-hal-0.10.5.6/ath_hal/.svn/entries
madwifi-hal-0.10.5.6/ath_hal/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_hal/.svn/format
madwifi-hal-0.10.5.6/ath_hal/.svn/all-wcprops
madwifi-hal-0.10.5.6/contrib/.svn/entries
madwifi-hal-0.10.5.6/contrib/.svn/format
madwifi-hal-0.10.5.6/contrib/.svn/all-wcprops
madwifi-hal-0.10.5.6/scripts/.svn/entries
madwifi-hal-0.10.5.6/scripts/.svn/format
madwifi-hal-0.10.5.6/scripts/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.c
madwifi-hal-0.10.5.6/ath_rate/minstrel/Makefile
madwifi-hal-0.10.5.6/ath_rate/minstrel/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.txt
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.h
madwifi-hal-0.10.5.6/ath_rate/sample/Makefile
madwifi-hal-0.10.5.6/ath_rate/sample/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/sample/sample.h
madwifi-hal-0.10.5.6/ath_rate/sample/sample.c
madwifi-hal-0.10.5.6/ath_rate/amrr/Makefile
madwifi-hal-0.10.5.6/ath_rate/amrr/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.h
madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.c
madwifi-hal-0.10.5.6/ath_rate/onoe/Makefile
madwifi-hal-0.10.5.6/ath_rate/onoe/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.h
madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.c
madwifi-hal-0.10.5.6/ath_rate/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/.svn/format
madwifi-hal-0.10.5.6/include/sys/queue.h
madwifi-hal-0.10.5.6/include/.svn/all-wcprops
madwifi-hal-0.10.5.6/include/.svn/entries
madwifi-hal-0.10.5.6/include/.svn/format
madwifi-hal-0.10.5.6/regression/wep/Makefile
madwifi-hal-0.10.5.6/regression/wep/test_wep.c
madwifi-hal-0.10.5.6/regression/tkip/Makefile
madwifi-hal-0.10.5.6/regression/tkip/test_tkip.c
madwifi-hal-0.10.5.6/regression/ccmp/Makefile
madwifi-hal-0.10.5.6/regression/ccmp/test_ccmp.c
madwifi-hal-0.10.5.6/regression/.svn/entries
madwifi-hal-0.10.5.6/regression/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/.svn/format
madwifi-hal-0.10.5.6/net80211/.svn/entries
madwifi-hal-0.10.5.6/net80211/.svn/dir-prop-base
madwifi-hal-0.10.5.6/net80211/.svn/format
madwifi-hal-0.10.5.6/net80211/.svn/all-wcprops
madwifi-hal-0.10.5.6/.svn/prop-base/kernelversion.c.svn-base
madwifi-hal-0.10.5.6/.svn/prop-base/release.h.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/BuildCaps.inc.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/COPYRIGHT.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/README.dfs.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/kernelversion.c.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/release.h.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/INSTALL.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/THANKS.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.inc.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/prop-base/install.sh.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Config.in.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Configure.help.patch.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Kconfig.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/install.sh.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_athioctl.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_hal_macros.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_ahb.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_athvar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_hal_wrappers.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_ahb.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_extensions.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_athioctl.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_macros.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_ahb.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_athvar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_radar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_wrappers.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_debug.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_ahb.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_radar.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_extensions.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/entries
madwifi-hal-0.10.5.6/hal/public/.svn/format
madwifi-hal-0.10.5.6/hal/public/.svn/all-wcprops
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah_desc.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/version.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah_devid.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_desc.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/version.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_devid.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/COPYRIGHT.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_soc.h.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/entries
madwifi-hal-0.10.5.6/tools/man/.svn/format
madwifi-hal-0.10.5.6/tools/man/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/.svn/prop-base/wireless_copy.h.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athstats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/80211stats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athchans.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/wlanconfig.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athkey.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athdebug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/80211debug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athctrl.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wireless_copy.h.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athstats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/80211stats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athchans.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wlanconfig.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athkey.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athdebug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/80211debug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athctrl.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wpakey.c.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/entries
madwifi-hal-0.10.5.6/tools/ath_info/.svn/dir-prop-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/ath_info/.svn/format
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_os.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_osdep.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_os.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/uudecode.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_os.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_osdep.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_target.inc.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/opt_ah.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_os.h.svn-base
madwifi-hal-0.10.5.6/contrib/.svn/text-base/madwifi.spec.in.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/if_ath_hal_generator.pl.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/find-madwifi-modules.sh.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/update_hal_unmangle.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/make-release.bash.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/madwifi-unload.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/madwifi-indent.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/if_ath_hal_generator.pl.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle.objcopy.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/find-madwifi-modules.sh.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/update_hal_unmangle.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle_log.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/make-release.bash.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle.sed.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/get_arch.mk.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/madwifi-unload.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/madwifi-indent.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/format
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/format
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/format
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/format
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/entries
madwifi-hal-0.10.5.6/include/sys/.svn/format
madwifi-hal-0.10.5.6/include/sys/.svn/all-wcprops
madwifi-hal-0.10.5.6/include/.svn/prop-base/compat.h.svn-base
madwifi-hal-0.10.5.6/include/.svn/text-base/compat.h.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/entries
madwifi-hal-0.10.5.6/regression/wep/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/wep/.svn/format
madwifi-hal-0.10.5.6/regression/wep/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/tkip/.svn/entries
madwifi-hal-0.10.5.6/regression/tkip/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/format
madwifi-hal-0.10.5.6/regression/tkip/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/ccmp/.svn/entries
madwifi-hal-0.10.5.6/regression/ccmp/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/format
madwifi-hal-0.10.5.6/regression/ccmp/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_media.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_llc.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_proto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_radiotap.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_tkip.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_linux.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_proto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_power.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_linux.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_var.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_monitor.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_power.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_wep.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_monitor.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan_ap.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_ethersubr.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_athproto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_output.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_input.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_none.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_acl.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_wireless.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan_sta.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_node.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_xauth.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_beacon.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_node.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/_ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_ccmp.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_media.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_ioctl.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_media.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_llc.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_proto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_radiotap.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_tkip.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_linux.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_proto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_power.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_linux.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_var.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_monitor.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_power.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_wep.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_monitor.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_skb.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_skb.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan_ap.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_ethersubr.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_athproto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_output.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_rate.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_input.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_none.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_acl.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_wireless.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan_sta.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_debug.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_rate.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_node.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_xauth.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_beacon.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_node.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/_ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_ccmp.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_media.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_ioctl.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/xscale-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mipsisa32-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-le-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/xscale-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/x86_64-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mipsisa32-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/alpha-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/armv4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips1-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/arm9-le-thumb-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/armv4-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips1-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-be-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/sparc64-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/i386-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/sh4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wackelf.c.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/wlanconfig.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athkey.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athdebug.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/80211debug.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athctrl.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athstats.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/80211stats.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athchans.8.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/eeprom.h.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/ath_info.8.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/ath_info.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.txt.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/prop-base/sample.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/prop-base/sample.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/sample.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/sample.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/prop-base/amrr.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/prop-base/amrr.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/amrr.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/amrr.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/prop-base/onoe.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/prop-base/onoe.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/onoe.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/onoe.c.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/prop-base/queue.h.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/text-base/queue.h.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/prop-base/test_wep.c.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/text-base/test_wep.c.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/prop-base/test_tkip.c.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/text-base/test_tkip.c.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/prop-base/test_ccmp.c.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/test_ccmp.c.svn-base
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
ifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/test_ccmp.c.svn-base
jes@NASA:~$ cd madwifi-hal-0.10.5.6
jes@NASA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
jes@NASA:~/madwifi-hal-0.10.5.6$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/jes/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@NASA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
SA:~/madwifi-hal-0.10.5.6$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/cj/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-23-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-23-generic/net
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_hal'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-23-generic/net
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_hal'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/sample'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/sample'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/net80211'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-23-generic/net; \
	done
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/net80211'
(export KMODPATH=/lib/modules/2.6.24-23-generic/net; /sbin/depmod -ae 2.6.24-23-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@NASA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
ke[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@NASA:~/madwifi-hal-0.10.5.6$ echo ath_pci | sudo tee -a /etc/modules
ath_pci
jes@NASA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
its a nada
i noticed that my network manager now has the option to edit wireless connections 
dunno

---

### Post by icecreamcakez on 2009-02-26
jes@NASA:~$ dmesg | grep -e ath -e adio
[   46.922323] ath_hal: module license 'Proprietary' taints kernel.
jes@NASA:~$ sudo iwlist scan
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jes@NASA:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
jes@NASA:~$

---

### Post by icecreamcakez on 2009-02-26
running iwlist scan on jes
!!!sleeepy as hell
...time for a bedtime snack
**              2.13 a.m.
99887 ////had no f@#5ing idea it was so late 
omg 
!!!!!!
THANK YOU FOR YOURE HELP PYTHEAS !! 
if it dont work it dont work 
the fact remains youre 
F##%ing Awesome Enough to Help 
thanks so much and Goodnight Honey Bear
....nite tootz 
jes 
xo

---

### Post by pytheas22 on 2009-02-26
Please reboot, then run these commands again:

```
rm -rf madwifi-hal*
wget http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz
tar -xzvf madwifi-hal-0.10.5.6.tar.gz
cd madwifi-hal-0.10.5.6
make
sudo make install
```

I realized that the instructions I sent yesterday may have had you build the module against the wrong kernel (if you built the module on an older kernel, then rebooted into a newer one that you would have downloaded through updates), so please give this another shot and let me know.  If after running the code above your wireless still won't work, please post again:

```
dmesg | grep ath
sudo iwlist scan
```

---

### Post by icecreamcakez on 2009-02-26
yes sir 
im at aunts but on the way home to try it out papa bear
THANK YOU
pytheas

---

### Post by icecreamcakez on 2009-02-26
its a negative captn
im all game for any guinea piggin you need to do 
so let it rip papa bear if you wanna experiment 

jes@HACIENDA:~$ dmesg | grep ath
[   48.095025] ath_hal: module license 'Proprietary' taints kernel.
jes@HACIENDA:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-26
if you would like i can run all commands again and post them as well 
its your call 
thank you pytheas!
jes xoxo

---

### Post by icecreamcakez on 2009-02-26
jes@HACIENDA:~$ rm -rf madwifi-hal*
jes@HACIENDA:~$ wget [http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz](http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz)
--21:26:23--  [http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz](http://burnthesorbonne.com/files/madwifi-hal-0.10.5.6.tar.gz)
           => `madwifi-hal-0.10.5.6.tar.gz'
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,858,083 (8.4M) [application/x-gzip]

100%[====================================>] 8,858,083    537.39K/s    ETA 00:00

21:26:40 (516.77 KB/s) - `madwifi-hal-0.10.5.6.tar.gz' saved [8858083/8858083]

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-26
madwifi-hal-0.10.5.6/hal/public/i386-elf.inc
madwifi-hal-0.10.5.6/hal/public/armv4-le-elf.inc
madwifi-hal-0.10.5.6/hal/public/mips1-le-elf.inc
madwifi-hal-0.10.5.6/hal/public/x86_64-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mipsisa32-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/arm9-le-thumb-elf.inc
madwifi-hal-0.10.5.6/hal/public/powerpc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/sh4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/wisoc.inc
madwifi-hal-0.10.5.6/hal/public/xscale-le-elf.inc
madwifi-hal-0.10.5.6/hal/public/alpha-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/wisoc.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/armv4-le-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/mips1-le-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/sparc64-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap43.inc
madwifi-hal-0.10.5.6/hal/public/arm9-le-thumb-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/armv4-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/mips1-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/powerpc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/alpha-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap43.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/ap51.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/wackelf.c
madwifi-hal-0.10.5.6/hal/public/armv4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips1-le-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/powerpc-be-eabi.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/arm9-le-thumb-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips-le-elf.inc
madwifi-hal-0.10.5.6/hal/public/armv4-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/mips1-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap30.inc
madwifi-hal-0.10.5.6/hal/public/x86_64-elf.inc
madwifi-hal-0.10.5.6/hal/public/mipsisa32-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap43.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap51.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/sparc64-be-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/powerpc-be-eabi.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/sparc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6/hal/public/ap30.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/armv4-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/mips1-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/i386-elf.hal.o.uu
madwifi-hal-0.10.5.6/hal/public/powerpc-le-eabi.inc
madwifi-hal-0.10.5.6/hal/public/xscale-be-elf.inc
madwifi-hal-0.10.5.6/hal/public/ap61.inc
madwifi-hal-0.10.5.6/hal/.svn/all-wcprops
madwifi-hal-0.10.5.6/hal/.svn/entries
madwifi-hal-0.10.5.6/hal/.svn/format
madwifi-hal-0.10.5.6/tools/man/wlanconfig.8
madwifi-hal-0.10.5.6/tools/man/athkey.8
madwifi-hal-0.10.5.6/tools/man/athdebug.8
madwifi-hal-0.10.5.6/tools/man/80211debug.8
madwifi-hal-0.10.5.6/tools/man/athctrl.8
madwifi-hal-0.10.5.6/tools/man/athstats.8
madwifi-hal-0.10.5.6/tools/man/80211stats.8
madwifi-hal-0.10.5.6/tools/man/athchans.8
madwifi-hal-0.10.5.6/tools/.svn/dir-prop-base
madwifi-hal-0.10.5.6/tools/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/.svn/entries
madwifi-hal-0.10.5.6/tools/.svn/format
madwifi-hal-0.10.5.6/tools/ath_info/eeprom.h
madwifi-hal-0.10.5.6/tools/ath_info/ath_info.8
madwifi-hal-0.10.5.6/tools/ath_info/README
madwifi-hal-0.10.5.6/tools/ath_info/Makefile
madwifi-hal-0.10.5.6/tools/ath_info/ath_info.c
madwifi-hal-0.10.5.6/ath_hal/.svn/entries
madwifi-hal-0.10.5.6/ath_hal/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_hal/.svn/format
madwifi-hal-0.10.5.6/ath_hal/.svn/all-wcprops
madwifi-hal-0.10.5.6/contrib/.svn/entries
madwifi-hal-0.10.5.6/contrib/.svn/format
madwifi-hal-0.10.5.6/contrib/.svn/all-wcprops
madwifi-hal-0.10.5.6/scripts/.svn/entries
madwifi-hal-0.10.5.6/scripts/.svn/format
madwifi-hal-0.10.5.6/scripts/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.c
madwifi-hal-0.10.5.6/ath_rate/minstrel/Makefile
madwifi-hal-0.10.5.6/ath_rate/minstrel/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.txt
madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.h
madwifi-hal-0.10.5.6/ath_rate/sample/Makefile
madwifi-hal-0.10.5.6/ath_rate/sample/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/sample/sample.h
madwifi-hal-0.10.5.6/ath_rate/sample/sample.c
madwifi-hal-0.10.5.6/ath_rate/amrr/Makefile
madwifi-hal-0.10.5.6/ath_rate/amrr/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.h
madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.c
madwifi-hal-0.10.5.6/ath_rate/onoe/Makefile
madwifi-hal-0.10.5.6/ath_rate/onoe/Makefile.kernel
madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.h
madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.c
madwifi-hal-0.10.5.6/ath_rate/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/.svn/format
madwifi-hal-0.10.5.6/include/sys/queue.h
madwifi-hal-0.10.5.6/include/.svn/all-wcprops
madwifi-hal-0.10.5.6/include/.svn/entries
madwifi-hal-0.10.5.6/include/.svn/format
madwifi-hal-0.10.5.6/regression/wep/Makefile
madwifi-hal-0.10.5.6/regression/wep/test_wep.c
madwifi-hal-0.10.5.6/regression/tkip/Makefile
madwifi-hal-0.10.5.6/regression/tkip/test_tkip.c
madwifi-hal-0.10.5.6/regression/ccmp/Makefile
madwifi-hal-0.10.5.6/regression/ccmp/test_ccmp.c
madwifi-hal-0.10.5.6/regression/.svn/entries
madwifi-hal-0.10.5.6/regression/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/.svn/format
madwifi-hal-0.10.5.6/net80211/.svn/entries
madwifi-hal-0.10.5.6/net80211/.svn/dir-prop-base
madwifi-hal-0.10.5.6/net80211/.svn/format
madwifi-hal-0.10.5.6/net80211/.svn/all-wcprops
madwifi-hal-0.10.5.6/.svn/prop-base/kernelversion.c.svn-base
madwifi-hal-0.10.5.6/.svn/prop-base/release.h.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/BuildCaps.inc.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/COPYRIGHT.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/README.dfs.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/kernelversion.c.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/release.h.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/INSTALL.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/THANKS.svn-base
madwifi-hal-0.10.5.6/.svn/text-base/Makefile.inc.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/prop-base/install.sh.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Config.in.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Configure.help.patch.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/Kconfig.svn-base
madwifi-hal-0.10.5.6/patch-kernel/.svn/text-base/install.sh.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_athioctl.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_hal_macros.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_pci.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_ahb.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_athvar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_hal_wrappers.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/prop-base/if_ath_ahb.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_extensions.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_athioctl.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_macros.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_pci.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_ahb.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_athvar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_radar.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_wrappers.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_debug.h.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_ahb.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_radar.c.svn-base
madwifi-hal-0.10.5.6/ath/.svn/text-base/if_ath_hal_extensions.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/entries
madwifi-hal-0.10.5.6/hal/public/.svn/format
madwifi-hal-0.10.5.6/hal/public/.svn/all-wcprops
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah_desc.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/version.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/prop-base/ah_devid.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_desc.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/version.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_devid.h.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/COPYRIGHT.svn-base
madwifi-hal-0.10.5.6/hal/.svn/text-base/ah_soc.h.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/entries
madwifi-hal-0.10.5.6/tools/man/.svn/format
madwifi-hal-0.10.5.6/tools/man/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/.svn/prop-base/wireless_copy.h.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athstats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/80211stats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athchans.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/wlanconfig.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athkey.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athdebug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/80211debug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/prop-base/athctrl.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wireless_copy.h.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athstats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/80211stats.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athchans.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wlanconfig.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athkey.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athdebug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/80211debug.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/athctrl.c.svn-base
madwifi-hal-0.10.5.6/tools/.svn/text-base/wpakey.c.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/entries
madwifi-hal-0.10.5.6/tools/ath_info/.svn/dir-prop-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/all-wcprops
madwifi-hal-0.10.5.6/tools/ath_info/.svn/format
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_os.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_osdep.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/prop-base/ah_os.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/uudecode.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_os.c.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_osdep.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_target.inc.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/opt_ah.h.svn-base
madwifi-hal-0.10.5.6/ath_hal/.svn/text-base/ah_os.h.svn-base
madwifi-hal-0.10.5.6/contrib/.svn/text-base/madwifi.spec.in.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/if_ath_hal_generator.pl.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/find-madwifi-modules.sh.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/update_hal_unmangle.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/make-release.bash.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/madwifi-unload.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/prop-base/madwifi-indent.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/if_ath_hal_generator.pl.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle.objcopy.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/find-madwifi-modules.sh.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/update_hal_unmangle.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle_log.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/make-release.bash.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/hal_unmangle.sed.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/get_arch.mk.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/madwifi-unload.svn-base
madwifi-hal-0.10.5.6/scripts/.svn/text-base/madwifi-indent.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/format
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/format
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/format
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/entries
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/dir-prop-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/format
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/all-wcprops
madwifi-hal-0.10.5.6/ath_rate/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/entries
madwifi-hal-0.10.5.6/include/sys/.svn/format
madwifi-hal-0.10.5.6/include/sys/.svn/all-wcprops
madwifi-hal-0.10.5.6/include/.svn/prop-base/compat.h.svn-base
madwifi-hal-0.10.5.6/include/.svn/text-base/compat.h.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/entries
madwifi-hal-0.10.5.6/regression/wep/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/wep/.svn/format
madwifi-hal-0.10.5.6/regression/wep/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/tkip/.svn/entries
madwifi-hal-0.10.5.6/regression/tkip/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/format
madwifi-hal-0.10.5.6/regression/tkip/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/ccmp/.svn/entries
madwifi-hal-0.10.5.6/regression/ccmp/.svn/dir-prop-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/format
madwifi-hal-0.10.5.6/regression/ccmp/.svn/all-wcprops
madwifi-hal-0.10.5.6/regression/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_media.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_llc.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_proto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_radiotap.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_tkip.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_linux.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_proto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_power.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_linux.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_var.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_monitor.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_power.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_wep.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_monitor.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan_ap.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_ethersubr.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_athproto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_output.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_input.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_none.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_acl.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_wireless.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan_sta.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_node.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_xauth.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_beacon.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_node.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/_ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_scan.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto_ccmp.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_crypto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/if_media.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/prop-base/ieee80211_ioctl.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_media.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_llc.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_proto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_radiotap.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_tkip.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_linux.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_proto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_power.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_linux.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_var.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_monitor.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_power.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_wep.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_monitor.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_skb.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_skb.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan_ap.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_ethersubr.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_athproto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_output.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_rate.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_input.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_none.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_acl.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_wireless.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan_sta.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_debug.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_rate.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_node.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_xauth.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_beacon.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_node.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/_ieee80211.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_scan.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto_ccmp.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_crypto.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211.c.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/if_media.h.svn-base
madwifi-hal-0.10.5.6/net80211/.svn/text-base/ieee80211_ioctl.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/xscale-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mipsisa32-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-le-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/xscale-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/x86_64-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mipsisa32-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/alpha-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/armv4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips1-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/arm9-le-thumb-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/armv4-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/mips1-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/powerpc-be-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/sparc64-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/i386-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/prop-base/sh4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sh4-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wisoc.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/alpha-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/wackelf.c.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-le-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/arm9-le-thumb-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips-le-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/x86_64-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mipsisa32-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap51.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc64-be-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-be-eabi.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/sparc-be-elf.opt_ah.h.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap30.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/armv4-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/mips1-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/i386-elf.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/powerpc-le-eabi.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/xscale-be-elf.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap61.inc.svn-base
madwifi-hal-0.10.5.6/hal/public/.svn/text-base/ap43.hal.o.uu.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/wlanconfig.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athkey.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athdebug.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/80211debug.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athctrl.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athstats.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/80211stats.8.svn-base
madwifi-hal-0.10.5.6/tools/man/.svn/text-base/athchans.8.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/eeprom.h.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/ath_info.8.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/README.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/tools/ath_info/.svn/text-base/ath_info.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.txt.svn-base
madwifi-hal-0.10.5.6/ath_rate/minstrel/.svn/text-base/minstrel.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/prop-base/sample.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/prop-base/sample.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/sample.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/sample/.svn/text-base/sample.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/prop-base/amrr.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/prop-base/amrr.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/amrr.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/amrr/.svn/text-base/amrr.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/prop-base/onoe.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/prop-base/onoe.c.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/Makefile.kernel.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/onoe.h.svn-base
madwifi-hal-0.10.5.6/ath_rate/onoe/.svn/text-base/onoe.c.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/prop-base/queue.h.svn-base
madwifi-hal-0.10.5.6/include/sys/.svn/text-base/queue.h.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/prop-base/test_wep.c.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/wep/.svn/text-base/test_wep.c.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/prop-base/test_tkip.c.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/tkip/.svn/text-base/test_tkip.c.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/prop-base/test_ccmp.c.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/test_ccmp.c.svn-base
jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-26
-0.10.5.6/regression/ccmp/.svn/text-base/Makefile.svn-base
madwifi-hal-0.10.5.6/regression/ccmp/.svn/text-base/test_ccmp.c.svn-base
jes@HACIENDA:~$ cd madwifi-hal-0.10.5.6
jes@HACIENDA:~/madwifi-hal-0.10.5.6$ make
Checking requirements... ok.
Checking kernel configuration... ok.
svn: This client is too old to work with working copy '.'; please get a newer Subversion client
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/jes/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath/if_ath.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath/if_ath_radar.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath/if_ath_hal_extensions.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath/if_ath_pci.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath/ath_pci.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath_hal/ah_os.o
  HOSTCC  /home/jes/madwifi-hal-0.10.5.6/ath_hal/uudecode
  UUDECODE /home/jes/madwifi-hal-0.10.5.6/ath_hal/i386-elf._hal.o
  UNMANGLE /home/jes/madwifi-hal-0.10.5.6/ath_hal/i386-elf.hal.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_hal/ath_hal.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr/amrr.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel/minstrel.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe/onoe.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/sample/sample.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/if_media.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_skb.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_beacon.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_none.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_input.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_node.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_output.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_power.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_proto.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_scan.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_wireless.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_linux.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_monitor.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_rate.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_acl.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_scan_ap.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_scan_sta.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/ieee80211_xauth.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_wep.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_tkip.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_acl.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_xauth.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/jes/madwifi-hal-0.10.5.6/ath/ath_pci.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath/ath_pci.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/ath_hal/ath_hal.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_hal/ath_hal.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr/ath_rate_amrr.ko
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/ath_rate/sample/ath_rate_sample.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_acl.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_acl.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_ccmp.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_ap.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_scan_sta.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_tkip.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_tkip.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_wep.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_wep.ko
  CC      /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_xauth.mod.o
  LD [M]  /home/jes/madwifi-hal-0.10.5.6/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@HACIENDA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@HACIENDA:~/madwifi-hal-0.10.5.6$ sudo make install
sudo: unable to resolve host HACIENDA
[sudo] password for jes: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/cj/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-23-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-23-generic/net
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_hal'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-23-generic/net
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_hal'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/amrr'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/onoe'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/sample'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/sample'
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-23-generic/net
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate/minstrel'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/ath_rate'
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/net80211'
test -d //lib/modules/2.6.24-23-generic/net || mkdir -p //lib/modules/2.6.24-23-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-23-generic/net; \
	done
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/net80211'
(export KMODPATH=/lib/modules/2.6.24-23-generic/net; /sbin/depmod -ae 2.6.24-23-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/jes/madwifi-hal-0.10.5.6/tools'
jes@HACIENDA:~/madwifi-hal-0.10.5.6$

---

### Post by icecreamcakez on 2009-02-26
jes@HACIENDA:~$ dmesg | grep ath
[   47.963120] ath_hal: module license 'Proprietary' taints kernel.
jes@HACIENDA:~$ sudo iwlist scan
sudo: unable to resolve host HACIENDA
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

jes@HACIENDA:~$

---

### Post by icecreamcakez on 2009-02-27
: Ubuntu 8.1 64-bit, Atheros AR928X & ATH9K Problems ...
Turns out that this has something to do with the Wireless & Bluetooth being on the same chip (or perhaps not, still working on it). In /sys/devices/platform/asus-laptop/ there are two files that I had to modify in order to make this work:

/sys/devices/platform/asus-laptop/bluetooth
/sys/devices/platform/asus-laptop/wlan

They each contain a single boolean value. The bluetooth value contained a 1 and the wlan contained a 0. You cannot modify this values while your system is running, therefore, the solution was to add two lines to my /etc/rc.local file:

echo 0 > /sys/devices/platform/asus-laptop/bluetooth # disable bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan # enable wireless

As soon as I restarted, it came up with absolutely no problems.

Now, it may be that they can both be enabled at the same time, I haven't tested that far yet.
__________________
[http://anarchia.ath.cx/](http://anarchia.ath.cx/)
F4RR4R is offline Report Post   	Reply With Quote

---

### Post by pytheas22 on 2009-02-27
ahhh I'm really sorry this still won't work.  I don't understand what's wrong.  But here's another thing to try:

First, go to [this page]("http://linuxwireless.org/download/compat-wireless-2.6/") and click the link for 'compat-wireless-old.tar.bz2'.  Save that file to your desktop.  Then run these commands:

```
sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf compat-wireless*
cd compat-wireless*
make
sudo make install
echo ath9k | sudo tee -a /etc/modules
```

Then reboot.  Any luck?  If not, please post the output again of:
```

dmesg | grep -e ath -e wlan
lshw -C Network
sudo iwlist scan
```

Again, I'm sorry this is so complicated--I rarely run into situations where getting the wireless to work seems so futile.  But every problem in Linux can be solved if you try hard enough...

---

### Post by icecreamcakez on 2009-02-27
pytheas!!
thank you friend 
im trying it now 
xo
jes

---

### Post by icecreamcakez on 2009-02-27
jes@HACIENDA:~$ dmesg | grep -e ath -e wlan
[   41.976159] ath9k: 0.1
[   42.411706] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   42.523214] Registered led device: ath9k-phy0:radio
[   42.523232] Registered led device: ath9k-phy0:assoc
[   42.523247] Registered led device: ath9k-phy0:tx
[   42.523262] Registered led device: ath9k-phy0:rx
[   66.127441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jes@HACIENDA:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:21:cc:01:b1:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:11:62:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
jes@HACIENDA:~$ sudo iwlist scan
sudo: unable to resolve host HACIENDA
[sudo] password for jes: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

jes@HACIENDA:~$ 

/////////////////////////////////////////////////////////////////////
it is VERY ! close to being connected i have some pictures for you 
thank you so much pytheas!
jes

---

### Post by icecreamcakez on 2009-02-27
its naptime lol 
thank you so much pytheas for helping like this 
xo 
jes

---

### Post by pytheas22 on 2009-02-27
Sorry for the slow response.  Unfortunately, it looks like it's doing the same thing as before--the card should be working, but the radio doesn't look like it's turned on.  What is the output of:
```

sudo updatedb; locate radio
```

---

### Post by icecreamcakez on 2009-02-28
i brought it to a friend of the family 
mom suggested a friend who does computer repair 
and luckily he also uses ubuntu !
i really really do thank you so very much for youre help 
i will let you know waht happens and also provide all the details of what methods/commands were used in the fix 
i sure do hope he can fix it 
and thank you so much pytheas !
xo
jes

---

### Post by icecreamcakez on 2009-03-02
pytheas !!
i called Gateway cust service and they talked with my moms friend who was trying to fix also 
it is determined that i have faulty hardware and its going off 
to TX. in the morn for service free of charge 
i will def keep you up to date
thank you friend !
please keep in touch 
jes!

---

### Post by Atrophy on 2009-03-02
I recently had similar wireless problems (as far as the beginning of this thread goes...) where my hardware was seeming to be uncooperative. I followed a lot of the steps and advice given here, and nothing worked for me either. However, I solved the problem in the end. Here is what I did:

First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot.

Surprisingly simple, and now i'm connecting via wifi everytime (posting now over wireless, in fact!). For reference, this was done on 64 bit 8.10 with an Atheros AR928x adapter.

---

### Post by icecreamcakez on 2009-03-02
Cool! im glad to hear that you fixed it and was able to stay with linux! we had to reset mine to vista and still no dice ...wireless just wouldnt budge i shipped it back and now theyre sending me a new one the online tech support had me run a series of tests and labeled it defective and sent me a return voucher im cool with that though because the desktop we have is b.c. the bottom task bar is about an inch thick lol ...so glad to have a new laptop !
thank you friends for helping so much and 
EXTRA EXTRA THANK YOU TO THE ONE AND ONLY 
P Y T H E A S !
jes

---

### Post by pytheas22 on 2009-03-02
I'm sort of glad to hear it was faulty hardware--not because you have to go through the hassle of getting it replaced, but because it was really puzzling me why the wireless wouldn't turn on.  I guess the device was just broken.

---

