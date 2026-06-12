---
title: "Getting Wireless on Netbook"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by theudanjoz on 2009-03-18
Hiya

I haven't used Ubuntu all that much. My only experience is with 8.04 Hardy Heron (Server Edition).

I recently just got a nice little netbook pre-formatted with DOS on it and installed Ubuntu server and installed the ubuntu-desktop and got it all up and running. It's working great, but I'm a bit stumped as to how to get the wireless functions of the netbook to work with Ubuntu.

Here are the features of the netbook itself:
[list]
[*]Intel® Atom 1.6GHz
[*]1GB DDR2 Memory
[*]120GB Hard Drive
[*]Pre-loaded Free DOS
[*]10.2” 1024 x 600 color LCD
[*]10 / 100M Ethernet
[*]802.11 b/g WLAN
[*]81-Key Keyboard
[*]2 Button Touch Pad
[*]3-cell battery / AC Adapter
[*]Integrated 2 Channel Audio
[*]10.2 x 7.4 x 1.1 in. / 2.8 lbs.
[*]3 x USB / 1 x 4-in-1 Card Reader
[*]Webcam (30 Fps)
[/list]

I put Ubuntu server on it because (A) it's what I used before on a desktop at work and (B) I'd like to set up a local php/mysql environment easily for messing/testing some various crap.

Thanks a bunch in advance.

Oh, and sorry if this has come up before.

---

### Post by pastalavista on 2009-03-18
If you can connect to the net via ethernet, you should be able to install the drivers you need to run wireless. If it doesn't find them automatically after you go online, open System > Administration > Hardware Drivers.

---

### Post by theudanjoz on 2009-03-18
I checked out the hardware drivers but it simply says "No proprietary drivers are in use on this system."

However, in Network Settings it does list a Wireless connection with Roaming mode enabled. I spose I'll swing by the library after work and poke around with it in their wireless zone.

---

### Post by basketcase on 2009-03-18
What brand notebook?  Any idea what the chipset is on the wifi?

---

### Post by theudanjoz on 2009-03-18
No, I'm not quite sure who the wifi manufacturer is. All I know about it is that it is 802.11 b/g WLAN.

My trip to the local library was unsuccessful. They do have wifi available, but I was unable to find it anywhere. It seems like my computer wants me to tell it all the information: dns and ip's etc etc. Shouldn't going to system -> network list available wireless networks? I'm unable to figure it out.

The netbook works just fine with an ethernet cable; I'm connected on it right now.

Also, this is probably a nooby question, but is there a way with ubuntu to list all the installed hardware? Something similar to device manager in windows.

Thanks again.

---

### Post by basketcase on 2009-03-18
lspci from the terminal...paste everything back.

---

### Post by ugm6hr on 2009-03-18
Have a look at the wifi help? link below.

It lists useful information so we can help.

Although, the most important:

```
lspci
lshw -class network
```

---

### Post by theudanjoz on 2009-03-19
lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

lshw -class network:
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:b1:63:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.102 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:27:37:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```

---

### Post by ugm6hr on 2009-03-19
You must have an internal usb card, since lspci does not see any wifi cards, but it appears in lshw (as disabled wlan0).

Give the output from:
```
lsusb
ifconfig
iwconfig
```

---

### Post by theudanjoz on 2009-03-19
lsusb
```
Bus 005 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:b1:63:8a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:feb1:638a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11615259 (11.0 MB)  TX bytes:1059837 (1.0 MB)
          Interrupt:20 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91800 (89.6 KB)  TX bytes:91800 (89.6 KB)
```

iwconfing
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by svijay02 on 2009-03-19
OK which manufacturers netbook are you using and what series.

---

### Post by theudanjoz on 2009-03-19
It's not a Dell or HP or ASUS. I bought it from a wholesale site my dad uses for his shop. The manufacturer is Equus Computer Systems. The model is something like Nobilis. The little Nobilis netbooks are called "Nobis"

[This isn't where I bought the system, but](http://discount-computer-sales.com/Nobilis-Computers/index.php?main_page=product_info&cPath=3&products_id=15&zenid=1ce20ac18c5170d79a30baaa66a13cfe) here you can take a look at it to see if you can figure it out. The site I bought it from requires login etc etc, that's why I had to find some site via google.

[http://discount-computer-sales.com/Nobilis-Computers/index.php?main_page=product_info&cPath=3&products_id=15&zenid=1ce20ac18c5170d79a30baaa66a13cfe](http://discount-computer-sales.com/Nobilis-Computers/index.php?main_page=product_info&cPath=3&products_id=15&zenid=1ce20ac18c5170d79a30baaa66a13cfe)

---

### Post by ugm6hr on 2009-03-19
Unfortunately, you have a chipset that had a driver that was problematic with Hardy.

A bit of ggogling revealed it is an "internal USB" device using the Realtek 8187B chipset.

Apparently, it should just work with Intrepid out-of-the-box, so that is an option you might like to consider.

If not, ndiswrapper + Win98 driver also (apparently) works:
[http://mycirilo.com/?p=24](http://mycirilo.com/?p=24)
[http://ubuntuforums.org/showthread.php?p=5398929#post5398929](http://ubuntuforums.org/showthread.php?p=5398929#post5398929)

Native driver can be made to work:
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)
[http://ubuntuforums.org/showpost.php?p=5414422&postcount=99](http://ubuntuforums.org/showpost.php?p=5414422&postcount=99)

It also appears there may be 3 slightly different versions of this chipset, and there are differing reports re: WEP and WPA support for all these methods...  I'm afraid I can't fathom it all out.  Perhaps someone who has successfully installed an RTL8187B might be able to enlighten you!

---

### Post by theudanjoz on 2009-03-20
I checked out [http://mycirilo.com/?p=24](http://mycirilo.com/?p=24). It looked simple enough.

I downloaded the two files, put them on my desktop, went into terminal, pointed it to the desktop, and the first command responds with "bash: sudondiswrapper: command not found"

```
sudondiswrapper -i net8187b.inf
```

That's the line he gives. I double checked the file I downloaded, and the name matches correctly. I switched user to root, and it acts the same way. I tried doing sudo ndiswrapper -i net8187b.inf, and it responded the same way.

It looked so easy, lol :(

---

### Post by ugm6hr on 2009-03-20
There should be a space there:
```
sudo ndiswrapper -i net8187b.inf
```

---

### Post by theudanjoz on 2009-03-20
A line break must have broken up what I showed. I did try doing it with a space:```
sudo ndiswrapper -i net8187b.inf
```
Error I get:```
sudo: ndiswrapper: command not found
```
:confused:


.. wait a tick. I tried just typing "ndiswrapper" to see how it would respond. Apparently ndiswrapper is not even installed. I'll try installing that quick.

---

### Post by ugm6hr on 2009-03-20
Try this first:

```
sudo apt-get ndisgtk
```

Then try again.

---

### Post by theudanjoz on 2009-03-20
Okay so after installing ndiswrapper-common and utils I was able to get through all of the steps.

On reboot now, it still acts the same. I can click the network icon on the topbar and I get a few options. When I click on "Connect to Other Wireless Network..." a screen comes up asking for specific information: network name and wireless security.

I did notice that when I put lsusb in the terminal it says that I have a realtek 8189. Are 8189 and 8187b basically the same thing?

At the end of aaron cirilo's article, he says > After I rebooted, I click on my network manager it i showed my wireless!!!! Then I just had to get select my &#8220;network&#8221; and it automatically assigned me an IP address and I am online posting this.So it sounds like I should be able to see available wireless networks and connect to them without having to enter all kinds of information.

---

### Post by ugm6hr on 2009-03-20
> **theudanjoz said:**
> On reboot now, it still acts the same. I can click the network icon on the topbar and I get a few options. When I click on "Connect to Other Wireless Network..." a screen comes up asking for specific information: network name and wireless security.


What options do you get?

Do you hide your access point SSID? If yes - unhide it.

---

### Post by theudanjoz on 2009-03-20
3 options appear:
 1. Connect to Other Wireless Network...
 2. Create New Wireless Network...
 3. Manual Configuration...

I don't remember seeing or changing anything concerning an SSID, so I have no idea. Where do I check that?

Thanks for all the help so far and being patient with a nooby :)

---

### Post by theudanjoz on 2009-03-20
I did find [this](http://ubuntuforums.org/showpost.php?p=4792383&postcount=7) in the last forum post you linked to. I haven't tried it yet though, I'm not sure if it would conflict with the ndiswrapper solution we just tried. What do you think?

---

### Post by ugm6hr on 2009-03-20
Just before giving up on ndiswrapper, check that it is listed as the driver in:
```
lshw -class network
```

---

### Post by theudanjoz on 2009-03-20
```
theudanjoz@swtnetbook:/var/www$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:b1:63:8a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:27:37:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```
It looks like it's installed fine for the ethernet connection, but nothing is there for the wireless connection. It's disabled, even, it looks like.

---

### Post by ugm6hr on 2009-03-20
Doesn't look like ndiswrapper has installed.

Check with:
```
sudo ndiswrapper -l
```

---

### Post by theudanjoz on 2009-03-20
And the plot thickens.```
theudanjoz@swtnetbook:~$ sudo ndiswrapper -l
[sudo] password for theudanjoz: 
net8187b : driver installed

```

---

### Post by ugm6hr on 2009-03-20
Appears that the driver is installed, but isn't associated with the wifi card.

I haven't used ndiswrapper for a long time, but I think that probably means that the driver won't work.

Try a different route...

```
sudo apt-get remove ndiswrapper-common
```

The remove ndiswrapper from the modules file:
```
gksudo gedit /etc/modules
```

Then reboot and try another path.

---

### Post by theudanjoz on 2009-03-23
I tried this:```
wget http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz

wget http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 
```

I was able to get as far as the second-to-last command. When I tried entering "./makedrv" it returned: ```
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-23-server/build M=/home/theudanjoz/rtl8187b-modified/ieee80211 CC=gcc modules
make: *** /lib/modules/2.6.24-23-server/build: No such file or directory.  Stop.
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-23-server/build M=/home/theudanjoz/rtl8187b-modified/rtl8187 CC=gcc modules
make: *** /lib/modules/2.6.24-23-server/build: No such file or directory.  Stop.
make: *** [modules] Error 2
```

---

### Post by theudanjoz on 2009-03-23
I tried a few things, and the results are confusing...

I checked out Synaptic Package Manager to see if I could find a simple program that could find hardware, install devices, and then browse any available wlans. I found and installed two packages.

The first was ndisgtk, version 0.8.3-1. It is described as a graphical frontend for ndiswrapper--the installation of Windows WiFi drivers. I figured maybe I messed something up in the terminal and perhaps this gui could do the trick. Well, when I open it, it does recognize net8187b; however, it declares "Hardware present: No". Okay, so I figured I can just click the "Install new Driver" button, direct it to the driver I downloaded, and then it should at least declare "Hardware present: Yes." When I do that, it responds with "Driver already installed." Why would it say there is no hardware, but that the driver is installed?

The second was wlassistant, version 0.5.7-2. It doesn't have the little Ubuntu logo next to its name in the SPM, so I don't know if its fully compatible, but I am able to run it. It is described as a user friendly KDE frontend for wireless network connection. When I open it up, its main window shows what should be a list of available wireless networks with columns titled ESSID, Channel, Link Quality, WEP/WPA and AP. It says though that no networks are found. The options button shows little promise, with such options as "auto connect on startup" and "group ap with the same ESSID."

I don't get it. Is there some sort of "switch" I have to flip in the terminal to actually get the hardware to turn "on"?

---

### Post by pastalavista on 2009-03-23
Have you yet tried the ```
sudo wlan0up
``` command? If so, what happened? Have you looked everywhere on the machine or in the bios for some kind of manual on/off enable switch? My Acer Aspire Atheros Wireless has a switch on the front that usually comes on automatically, but sometimes I have to manually switch it on... I don't know why, but there you are.

---

### Post by theudanjoz on 2009-03-24
Oh my, goodness gracious me! I never thought to check the bios. Yes, wireless was disabled. Turning it to enabled turned the wlan light on the machine itself on, at least. However, yes I did try using "sudo wlan0up" before, and it just says it can't find the command??

---

