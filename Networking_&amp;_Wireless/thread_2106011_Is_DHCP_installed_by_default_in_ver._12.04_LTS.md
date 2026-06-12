---
title: "Is DHCP installed by default in ver. 12.04 LTS?"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-01-17
I'm painfully lost. Is Precise Pangolin using DHCP with any device automatically (as in Auto Eth)? How can I know if the device is or isn't found?

If the device cannot find it's way from itself to the computer, then what configging is needed to make the two devices talk to each other?

Does application software have to be involved before the ethernet connection is established? I'm guessing that the firmware/hardware would at least acknowledge it's presence to the computer's ethernet jack.

I have set the Network Manager to add a wired connection with IP=169.254.5.12 and mask of 255.255.0.0. Nothing gets found.

Oh! One more thing. I have this install of Ubuntu running wifi, as I share costs of dsl with my neighbor who has the wifi-router in his apartment. Is it possible to use the wifi for internet connectivity and the ethernet for another use simultaneously?

---

### Post by chili555 on 2013-01-17
> Is Precise Pangolin using DHCP with any device automatically (as in Auto Eth)? How can I know if the device is or isn't found?Run a terminal command:```
ifconfig
```Is there an eth0 found? If so, you have a wired ethernet interface and, if the ethernet cable is attached to a router, you should get an IP address automagically. DHCP is installed and runs by default.> I have set the Network Manager to add a wired connection with IP=169.254.5.12 and mask of 255.255.0.0. Nothing gets found.Where did you get that? 169.254.x.y is usually reserved for a placeholder indicating, roughly, 'I am a working interface but I can't connect because the router refused my connection, the cable is detached, the cable is defective, etc.'

Typically, you will need *NO* human intervention; Network Manager does everything for you.> Is it possible to use the wifi for internet connectivity and the ethernet for another use simultaneously?
Yes, although probably not with Network Manager. It defaults to wired if it's available and then turns off wireless. What you propose can be done with some manual configuration.

---

### Post by Mark_in_Hollywood on 2013-01-17
Per previous response:

mark@Lexington-19:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96786 (96.7 KB)  TX bytes:52737 (52.7 KB)
          Interrupt:43 Base address:0xe000 


Where did you get that?

169.254.x.y is usually reserved for a placeholder indicating, roughly, 'I am a working interface but I can't connect because the router refused my connection, the cable is detached, the cable is defective, etc.'

The "added" Network Connections Wired connection has been deleted.

What you propose can be done with some manual configuration.

Auto Ethernet requests a "wired network address" and eventually says: Wired network disconnected.

I cannot understand whether I have an ethernet connection or not from looking at what ifconfig reports. I can say that in Win7 (other partition, this drive) finds the device makes a connection.

---

### Post by chili555 on 2013-01-17
> Where did you get that?

169.254.x.y is usually reserved for a placeholder indicating, roughly, 'I am a working interface but I can't connect because the router refused my connection, the cable is detached, the cable is defective, etc.'
From working 16,000 cases here and on two other forums. [http://packetlife.net/blog/2008/sep/24/169-254-0-0-addresses-explained/](http://packetlife.net/blog/2008/sep/24/169-254-0-0-addresses-explained/) [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

You do not have an IP address; if you did, it would show as something like:```
$ ifconfig
eth0 Link encap:Ethernet HWaddr 40:61:86:06:56:14
[COLOR="Red"]inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]
inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:283 errors:0 dropped:0 overruns:0 frame:0
TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
```...or some such. The fact that you have packets sent and received suggest it's trying; that is, it's healthy.

Before we start some manual configuration of both wired and wireless connections, let's first try to fix the wired connection. What does this tell us?```
nm-tool
cat /etc/network/interfaces
dmesg | grep eth0
```A great many things work perfectly well in Windows and not Linux...and vice versa.

---

### Post by steeldriver on 2013-01-17
> **Mark_in_Hollywood said:**
> I'm painfully lost. Is Precise Pangolin using DHCP with **any device** automatically (as in Auto Eth)? How can I know if the **device** is or isn't found?

If the **device** cannot find it's way from itself to the computer, then what configging is needed to make the two devices talk to each other?

What device are you trying to connect to exactly? It sounds like you are trying to do some kind of peer-to-peer connection (no routing) which may work under Windows using APIPA (which would be consistent with a 169.x.x.x address I think)

There seems like there *might* be a provision to do that under NetworkManager (there is a 'Link-Local Only' option under the IPv4 settings tab) but I have never tried it

---

### Post by Mark_in_Hollywood on 2013-01-18
I am trying to install a SiliconDust HD HomeRun dual (tv) tuner. It's an external box that has an antenna input and an ethernet output. This device will supply a TV signal to my computer. It's not on a "network" in the sense that a cable/wifi sends the TV picture to another device on a network. At most, I might set the nVideo driver to "dual monitors" and pipe the picture over to a big screen TV via hdmi. The tuner's cable goes from the tuner into the computer's ethernet jack. This computer uses wifi to access the internet. I share a DSL ISP with a neighbor, for which I pay my share of service. It is unlikely that the neighbor would be willing to let me run ethernet cables into the ATT wifi-router. 

mark@Lexington-19:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyACM0 ------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:


- Device: eth0 ---------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        40:61:86:06:56:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan2  [2WIRE123 2] --------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        90:F6:52:0C:2D:A4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    
    *2WIRE123:       Infra, 00:22:A4:E2:6D:D9, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WEP

  IPv4 Settings:
    Address:         192.168.1.72
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


mark@Lexington-19:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


mark@Lexington-19:~$ dmesg | grep eth0
[    1.600867] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 40:61:86:06:56:14
[    8.674650] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.624031] eth0: no IPv6 routers present
[   84.520014] eth0: no IPv6 routers present

---

### Post by steeldriver on 2013-01-18
Ah OK - actually I have one of those myself but it is connected via a router and uses DHCP

Is the HDHR new out of the box? if not it's possible someone reconfigured it to a IP range that's different from the default 169.254.x.x.  I think you *should* be able to just set a static IP like you tried, iirc the HDHR doesn't even need a crossover as it is able to autodetect. Or you could try the 'Link-local Only' option if you are feeling adventurous. 

However NetworkManager by default will likely try to disable your wireless connection if it finds a wired connection - to prevent that you may need to define the static wired connection for the HDHR in /etc/network/interfaces instead and make sure 'ifupdown' is set to 'managed=false' in NetworkManager.conf (it should be false by default) - sometimes the 2 networking services don't play well together though.

---

### Post by chili555 on 2013-01-18
Let me hand this one off to you, steeldriver. You have the device and are well equiped to assist Mark.

---

### Post by steeldriver on 2013-01-18
OK I will give it a shot - but if it looks like there may be an actual problem with the ethernet port / driver we will call back the big guns!

---

### Post by Mark_in_Hollywood on 2013-01-18
Does "connected via a router" mean that you get your internet access and the HDHR via your router?

**Is the HDHR new out of the box?**

NO. This is a tan box with 2 F-59 male plugs at the back. This box's firmware is: 20120405. This device can be found within my Win7 (64-bit) partition, on same drive as Precise Pangolin ver. 12.04 LTS.

** if not it's possible someone reconfigured it to a IP range that's different from the default 169.254.x.x.  I think you *should* be able to just set a static IP like you tried, iirc the HDHR doesn't even need a crossover as it is able to autodetect. Or you could try the 'Link-local Only' option if you are feeling adventurous. **

FYI, the cable 'twixt the hdhr and 'puter is branded SiliconDust.

**However NetworkManager by default will likely try to disable your wireless connection if it finds a wired connection - to prevent that you may need to define the static wired connection for the HDHR in /etc/network/interfaces instead and make sure 'ifupdown' is set to 'managed=false' in NetworkManager.conf (it should be false by default) - sometimes the 2 networking services don't play well together though.**

You can say that again! Now, if you give me a URL or How-To on how to edit /etc/network/interfaces and what needs to be edited. I tried setting Network Connection / Wired to IP of 169.254.5.12 with subnet mask of 255.255.0.0. Yet the devices continue to not "see" one another, i.e., I have no presence of the hdhr in the OS/Networking apps.

I looked at the NetworkManager.conf and see that "managed" is set to "false". Screenshot attached.

From the MythTV SiliconDust HDHomeRun page:

[COLOR="Red"]Network Connection

The HDHomeRun normally expects to obtain a DHCP lease. However, with the latest firmware it is also possible to configure it statically. This is particularly convenient if you want to connect the HDHomeRun directly to a NIC on your MythTV system, rather than through a switch on your network. To do this, configure your local interface with a static IP address in the range of 169.254.x.x (eg. 169.254.1.10) with a subnet mask of 255.255.0.0 and no gateway. No need to configure routes, the HDHR's will not be accessible to devices on your existing network, but your backend should have no problem seeing them.

Alternatively add the following lines to your interfaces file ('ipv4ll' is a relatively new option, easier than using 'static'):

auto eth1
iface eth1 inet ipv4ll

The HDHomeRun uses UDP to communicate to the backend. Since UDP is connectionless, it does not retry if a packet is lost. This can cause a problem with hubs, especially with multiple HD video streams and other traffic. Any collision on the network generally results in part of the video stream being lost. This shows up as random blocks in the video being corrupt, generally with colors that stand out against the video. Switches resolve this problem since they break up the network into more collision domains, although this problem will still appear if then network becomes fully saturated with traffic.
[/COLOR]

I have added the 

auto eth1
iface eth1 inet ipv4ll

to etc/network/interfaces 

ooopppssss!!

mark@Lexington-19:~$ ifconfig -a | grep eth
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
mark@Lexington-19:~$ sudo /etc/init.d/networking restart
[sudo] password for mark: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Failed to get index for interface name 'eth1': No such device
Failed to bring up eth1.

Please advise "what next"?

---

### Post by chili555 on 2013-01-18
Your device is eth0, not eth1. Using manual methods usually is quite iffy with Network Manager installed and running. Before you remove it altogether, I'd try using it. Remove the erroneous settings in /etc/network/interfaces and edit connections in Network Manager to use Link Local as attached. I'm fairly confident that's what LL refers to here:> Alternatively add the following lines to your interfaces file ('ipv4[COLOR="Red"]ll[/COLOR]' is a relatively new option, easier than using 'static'):

auto eth1
iface eth1 inet ipv4[COLOR="Red"]ll[/COLOR]

---

### Post by steeldriver on 2013-01-18
Yes you would need to add an entry for eth0 since that is the label of your wired device

HOWEVER I agree with chili555 let's see if we can get it working with ONLY network manager - so I'd suggest reverting your changes to /etc/network/interfaces and then restarting the networking service

```
sudo service networking restart
```I have just hauled mine out of the basement and connected direct to the wired ethernet port of my laptop (running 12.04) and then went to the connection manager applet, selected the wired connection, and edited it to 'Link-local Only' and the interface popped up right away (as 169.254.7.20). The existing wireless connection does not seem to have been affected - suggesting that the 'wired takes precedence' rule is based on routes rather than just the physical interface presence maybe? However mine's the (newer?) gray one - ymmv

---

### Post by Mark_in_Hollywood on 2013-01-18
Is this it?

auto eth0
iface eth0 inet ipv4ll

I have "created" or "installed" the non-auto ethernet, as I understand you to mean it. I don't see an IP in the IPv4 screen. Screenshots attached.

mark@Lexington-19:~$ sudo service networking restart
[sudo] password for mark: 
stop: Unknown instance: 
networking stop/waiting

---

### Post by steeldriver on 2013-01-18
Your network manager GUI setup looks correct, but please revert your /etc/network/interfaces file to its original contents - probably just

```
auto lo
iface lo inet loopback

```There is no need to mess with that at all if we can get things working via network manager - my bad for even mentioning it in my earlier post

---

### Post by Mark_in_Hollywood on 2013-01-18
mark@Lexington-19:~$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting


I believe I have the "interfaces" set per original. Screenshot attached.

mark@Lexington-19:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67716 (67.7 KB)  TX bytes:28544 (28.5 KB)
          Interrupt:43 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet addr:169.254.4.60  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:43 Base address:0x4000

---

### Post by steeldriver on 2013-01-18
OK looks good - now does the link local wired connection show up when you attach the HDHR and then go to 'Connection Information' (or use 'ifconfig' in a terminal)?

EDIT: possibly you may need to delete the other wired connection ('Auto Ethernet') that is shown in your screenshot?

---

### Post by Mark_in_Hollywood on 2013-01-18
I'm not playing dumb, here. I don't know what's working and what's not. I was doing all the edits to "interfaces" and NetworkManager.conf while the hdhr was plugged in via ethernet cable and powered on. I'm not much up to speed on this stuff.

Auto Ethernet Connect deleted from Network Connections.

At present, even after "sudo service networking restart" command, ethernet LED on hdhr flashes (means no connectivity) and

mark@Lexington-19:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71478 (71.4 KB)  TX bytes:28544 (28.5 KB)
          Interrupt:43 Base address:0x4000

---

### Post by steeldriver on 2013-01-18
just edited my last post as you were replying - I wonder if the other wired connection definition is taking precedence (the 'Auto Ethernet' in your screenshot)? you could try deleting that - or at least unchecking its 'Connect automatically' box

---

### Post by Mark_in_Hollywood on 2013-01-18
> **steeldriver said:**
> just edited my last post as you were replying - I wonder if the other wired connection definition is taking precedence (the 'Auto Ethernet' in your screenshot)? you could try deleting that - or at least unchecking its 'Connect automatically' box


I tried the sudo service networking restart with both AutoEth and uncheck "connect automatically" and then I deleted the AutoEth entirely. Still no sugar.

I looked up the terminal message and see at:

[http://superuser.com/questions/218967/networking-stopped-working-on-ubunt:](http://superuser.com/questions/218967/networking-stopped-working-on-ubunt:)

[COLOR="Red"]If you tried sudo start networking or sudo service networking start and received networking stop/waiting then you probably don't have things quite properly configured.

In your /etc/network/interfaces file:

auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp

Implies that eth0 is the physical adapter which is currently plugged into your internet connection. My hunch would be that for some reason you're having a conflict with another device which is trying to use the same ip address. So you might try using a static ip address (If you're using a router which supports dhcp - e.g. Linksys/Cisco):

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    gateway 192.168.1.2
Where 192.168.1.2 is the address of your router. [/COLOR]

---

### Post by steeldriver on 2013-01-18
Just to be clear, the 'Auto Ethernet' that I'm talking about is not the  one you wrote in (and then removed from) your /etc/network/interfaces  file - I meant the one that shows up in the GUI list of Wired network  connections

You can forget about  [FONT=Courier New]service networking restart[/FONT] now that you reverted your /etc/network/interfaces - the GUI applet is for a separate service (called network-manager)

---

### Post by Mark_in_Hollywood on 2013-01-18
**Just to be clear, the 'Auto Ethernet' that I'm talking about is not the  one you wrote in (and then removed from) your /etc/network/interfaces  file - I meant the one that shows up in the GUI list of Wired network  connections**

YES. The only Wired Connection now available in the Network Connections applet is

HomeRunTuners.

that has a MAC address of: 00:18:DD:01:A7:99

and it is to connect automatically, available to all users and Method (of connecting) is

Link-Local only

Require IPv4 is UNCHECKED

---

### Post by steeldriver on 2013-01-18
Do you have multiple network cards? Your previous posts show eth0 as having H/W (MAC) address 40:61:86:06:56:14

Or maybe you are using MAC cloning?

Maybe you should delete ALL the listed wired connections and start from scratch with a new, clean  Link-Local connection definition - making sure that it's using eth0

---

### Post by Slim Odds on 2013-01-18
Is the cable between the computer and the HD Homerun a crossover cable?

If not, then you need a hub or something in between.

---

### Post by steeldriver on 2013-01-18
Hi Slim, I agree that's usually the case but it should not be necessary for the HDHomeRun devices - see here --> [http://www.silicondust.com/forum/viewtopic.php?t=4088](http://www.silicondust.com/forum/viewtopic.php?t=4088)

I have confirmed that mine works just fine with a regular (non crossover) cable (although mine is a different - possible newer - version, the auto-MDX feature is supposedly there from 2007)

---

### Post by Mark_in_Hollywood on 2013-01-18
> **Slim Odds said:**
> Is the cable between the computer and the HD Homerun a crossover cable?

If not, then you need a hub or something in between.


Please see attached screenshots of cable and it's plugs.

---

### Post by Mark_in_Hollywood on 2013-01-18
**Do you have multiple network cards? Your previous posts show eth0 as having H/W (MAC) address 40:61:86:06:56:14**

My bad, I tried to configure the wired connection myself. That connnection has been deleted.

**Or maybe you are using MAC cloning?**

Nope, just as I said, above.

**Maybe you should delete ALL the listed wired connections and start from scratch with a new, clean  Link-Local connection definition - making sure that it's using eth0**

I have deleted ALL wired connections. I have "Added" a new wired, link-local connection. Please see attached screenshots re above paragraph.

---

### Post by chili555 on 2013-01-18
> **Slim Odds said:**
> Is the cable between the computer and the HD Homerun a crossover cable?

If not, then you need a hub or something in between.Crossover detection can be set with:```
sudo modprobe -r forcedeth
sudo modprobe forcedeth phy_cross=1
```Please do so and now try to connect. If it helps, we'll need to write a quick configuration file to make it persistent.

---

### Post by Mark_in_Hollywood on 2013-01-18
Detection done.

Is this it?

From ifconfig:

inet addr:169.254.4.60  Bcast:169.254.255.255  Mask:255.255.0.0

Ethernet connectivity LED on device still flashes.

Net' Mgr. shows named Wired Network connection as connected.

However, HDHomeRun Config at last shows most recent firmware version and can scan for tv signal and show individual channel signal strength. MythTV Config still reports no connectivity.

---

### Post by chili555 on 2013-01-18
Knowing nothing about the device in question, it looks very good to me. Back to our regularly scheduled guru, steeldriver.

---

### Post by Mark_in_Hollywood on 2013-01-18
What about making it persistent?

---

### Post by steeldriver on 2013-01-18
The networking side all looks good to me too - can you view a channel stream using the HDHomeRun Config app? (it should pop up a VLC window when you press 'View') - if so then I would think it's a mythtv setup issue - possibly you need to run through the backend setup again and make sure it's finding the HDHR and the inputs are all correctly configured

---

### Post by chili555 on 2013-01-18
> **Mark_in_Hollywood said:**
> What about making it persistent?Please do:```
gksudo   gedit /etc/modprobe.d/forcedeth.conf
```Add a single line:```
options forcedeth phy_cross=1
```Proofread, save and close gedit.

---

### Post by Mark_in_Hollywood on 2013-01-18
**The networking side all looks good to me too - can you view a channel stream using the HDHomeRun Config app? (it should pop up a VLC window when you press 'View') - if so then I would think it's a mythtv setup issue - possibly you need to run through the backend setup again and make sure it's finding the HDHR and the inputs are all correctly configured**

MythTV message reads: **"Could not connect to the master backend server. Is it running? Is the IP address set for it in mythtv-setup correct?**

Supposedly: 

mark@Lexington-19:~$ mythtv-setup
mythtv-backend start/running, process 14576



quick run through of MythTV Frontend (gui) shows problem with connectivity. Humpphhh!

=======

gksudo   gedit /etc/modprobe.d/forcedeth.conf
Add a single line:
Code:
options forcedeth phy_cross=1

Proofread, save and close gedit.

Done, done and done.

VLC is now showing: The Big Bang Theory (with Dr. Sheldon Cooper)

---

### Post by steeldriver on 2013-01-18
OK that sounds like you are 90% of the way there - I'm off to bed now but we can compare mythtv backend setups tomorrow if you haven't solved it in the meantime

---

### Post by Mark_in_Hollywood on 2013-01-18
mark@Lexington-19:~$ /usr/bin/mythbackend
2013-01-18 20:44:07.423184 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-01-18 20:44:07.423210 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-01-18 20:44:07.423213 N  Enabled verbose msgs:  general
2013-01-18 20:44:07.423236 N  Setting Log Level to LOG_INFO
2013-01-18 20:44:07.423290 I  Added logging to the console
2013-01-18 20:44:07.423297 I  Added database logging to table logging
2013-01-18 20:44:07.423595 N  Setting up SIGHUP handler
2013-01-18 20:44:07.423722 N  Using runtime prefix = /usr
2013-01-18 20:44:07.423791 N  Using configuration directory = /home/mark/.mythtv
2013-01-18 20:44:07.424088 I  Assumed character encoding: en_US.UTF-8
2013-01-18 20:44:07.424649 N  Empty LocalHostName.
2013-01-18 20:44:07.424657 I  Using localhost value of Lexington-19
2013-01-18 20:44:07.460917 N  Setting QT default locale to EN_US
2013-01-18 20:44:07.461032 I  Current locale EN_US
2013-01-18 20:44:07.461104 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2013-01-18 20:44:07.472949 I  Current MythTV Schema Version (DBSchemaVer): 1299
2013-01-18 20:44:07.473583 I  Loading en_us translation for module mythfrontend
2013-01-18 20:44:07.475027 N  MythBackend: Starting up as the master server.
2013-01-18 20:44:07.482638 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2013-01-18 20:44:08.293190 E  HDHRSH(169.254.5.12-0): Unable to connect to device
2013-01-18 20:44:08.294245 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-01-18 20:44:08.700041 E  HDHRSH(169.254.5.12-0): Get request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:09.105239 E  HDHRSH(169.254.5.12-0): Set request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:09.105367 E  ChannelBase: CreateChannel() Error: Failed to open device 169.254.5.12-0
2013-01-18 20:44:09.105413 E  Problem with capture cardsCard 1failed init
2013-01-18 20:44:09.107789 E  TVRec(2): Problem finding starting channel, setting to default of '3'.
2013-01-18 20:44:09.918192 E  HDHRSH(169.254.5.12-0): Unable to connect to device
2013-01-18 20:44:09.918938 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-01-18 20:44:10.324230 E  HDHRSH(169.254.5.12-0): Get request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:10.729568 E  HDHRSH(169.254.5.12-0): Set request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:10.729703 E  ChannelBase: CreateChannel() Error: Failed to open device 169.254.5.12-0
2013-01-18 20:44:10.729764 E  Problem with capture cardsCard 2failed init
2013-01-18 20:44:10.732290 E  TVRec(3): Problem finding starting channel, setting to default of '3'.
2013-01-18 20:44:11.542877 E  HDHRSH(169.254.5.12-1): Unable to connect to device
2013-01-18 20:44:11.543936 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-01-18 20:44:11.949246 E  HDHRSH(169.254.5.12-1): Get request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:12.354488 E  HDHRSH(169.254.5.12-1): Set request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:12.354546 E  ChannelBase: CreateChannel() Error: Failed to open device 169.254.5.12-1
2013-01-18 20:44:12.354577 E  Problem with capture cardsCard 3failed init
2013-01-18 20:44:12.356187 E  TVRec(4): Problem finding starting channel, setting to default of '3'.
2013-01-18 20:44:13.166589 E  HDHRSH(169.254.5.12-1): Unable to connect to device
2013-01-18 20:44:13.167325 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2013-01-18 20:44:13.572372 E  HDHRSH(169.254.5.12-1): Get request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:13.977384 E  HDHRSH(169.254.5.12-1): Set request failed
			eno: Resource temporarily unavailable (11)
2013-01-18 20:44:13.977410 E  ChannelBase: CreateChannel() Error: Failed to open device 169.254.5.12-1
2013-01-18 20:44:13.977424 E  Problem with capture cardsCard 4failed init
2013-01-18 20:44:13.977453 W  MythBackend: No valid capture cards are defined in the database.
2013-01-18 20:44:13.979228 E  Scheduler: No channel sources defined in the database
mark@Lexington-19:~$

---

### Post by steeldriver on 2013-01-19
Good morning Mark

It looks like your mythtvbackend is looking for the HDHR by an out of date IP (169.254.[COLOR=Red]5.12[/COLOR] instead of the 169.254.[COLOR=Red]4.60[/COLOR] that your new link-local connection is coming up as)

You will probably need to go into the mythtv backend setup and delete / re-add your 'Capture Cards' so that it picks up the new IP.

---

### Post by Mark_in_Hollywood on 2013-01-19
[COLOR="Red"]GO FIGURE- not more than a minute after posting all the below, the hdhr LED stopped flashing. Making me shout: "Why ME, Lord?"[/COLOR]


Good Morning Steeldriver.

Upon powering up my 'puter, the hdhr box's ethernet LED began flashing. A sign that there is no connection.

Upon checking (per chili555)

gksudo gedit /etc/modprobe.d/forcedeth.conf

had a single line:

options forcedeth phy_cross=1

**it does.**

HDHomeRun Config (gui) now does not obtain tv signals. Not on either tuner. And VLC cannot be called (grayed out). By the bye, only one channel worked last night.

Active Network Connections shows appearance of ethernet. Screenshot attached for reference sake.

---

### Post by Mark_in_Hollywood on 2013-01-19
After my previous post about the hdhr LED blinking and then steady, I reset the IP in the myth setup gui.

Oddly, what showed was not: 169.254.5.12,

This is what the mythtv-setup gui showed:

[COLOR="Red"]169.254.250.4 [/COLOR]

for both tuners. I deleted all "capture cards" as the gui calls them and "added" two with the IP of: 169.254.4.60.

Now the HDHomeRun gui "sees" tv signals and VLC can play them, but on tuner-1 only, not tuner-0 and only above channel 6. (I would see 2, 4, 5)

Running mythtv-setup in the terminal brings up the GUI. But, I continue to see:

[COLOR="Navy"]Could not connect to the master backend server. Is it running? Is the IP address set for it in mythtv-setup correct?[/COLOR]

---

### Post by Mark_in_Hollywood on 2013-01-21
Please remember folks, that I'm new at this.

mark@Lexington-19:~$ hdhomerun_config discover
hdhomerun device 101A799A found at 169.254.64.142


If I set the tuners to the Network Manager supplied IP address: 169.254.4.60

then why won't the device find tv channels? How do I resolve the conflict?

---

### Post by steeldriver on 2013-01-21
Oops my apologies Mark - looking back at my last post I advised you wrong - 169.254.[COLOR=Red]4.60[/COLOR] is obviously your [COLOR=Red]computer's[/COLOR] link-local IP not what you need to use for the HDHR setup

In fact the mythtv setup should autodetect the IP - all you should need to do is choose the 2 tuners based on the 101A799A-0 and 101A799A-1 IDs, it should fill in the IP for you (probably 169.254.64.142)
[COLOR=Red] [/COLOR]

---

### Post by Mark_in_Hollywood on 2013-01-22
OK, so now that I'm not running in circles like a chicken with it's head cut off thinking I've got an IP conflict like Arabs & Jews, I have tv signal/sound in the HD HomeRun Config Gui. That can scan for tv on tuner-1 and using VLC plays tv/sound.

But where do I go from there? I have tried & re-tried to set up myth. When I create a capture card it has the 101A799A as the "device" (technically it's 101A799A-0 or -1), then it's off to tell it to use the antenna. But on channel scan, it balks, says it cannot find any and I'm stuck.

So, if you can point to a working how-to, I'ld be obliged. I looked at the MythTV Wiki, but (incredibly) it's often out-of-date. So the ideas there aren't working.

---

### Post by steeldriver on 2013-01-22
Once you have your capture cards defined, the next step is to define a Video Source. Then you need to define an Input Connection that links the Capture Device (card) to your Video Source

Hope this helps

---

### Post by Slim Odds on 2013-01-22
> **steeldriver said:**
> Hi Slim, I agree that's usually the case but it should not be necessary for the HDHomeRun devices - see here --> [http://www.silicondust.com/forum/viewtopic.php?t=4088](http://www.silicondust.com/forum/viewtopic.php?t=4088)

I have confirmed that mine works just fine with a regular (non crossover) cable (although mine is a different - possible newer - version, the auto-MDX feature is supposedly there from 2007)
Thanks for the info.
I did not realize that the HD HomeRun was that fancy. :p

---

### Post by Mark_in_Hollywood on 2013-01-22
1st - Thank you, steeldriver and chili555 (even though it is spelled chile).

2nd - This is not a case of "it just works". Maybe that is expecting too much, give the complexities but I have taken the time of four or five human beings. That is a lot of man hours on my part too. I'm not saying Windows/uSoft is better. It isn't.

3rd - I not marking this thread as solved, because the complexities are just too much to say: "This is the easy way to do this." There isn't one.

4th - After MythTV was setup, recording and I could watch television, the sound was a little too loud. So I opened the Audio Mixer applet. Tried to adjust the sound, added the "Headphones" and now I have no sound in VLC, MythTV, etc.

5th - I'm posting the no sound question in another post.

Again, thank you everyone who contributed.

---

### Post by chili555 on 2013-01-24
> and chili555 (even though it is spelled chile).Or chili: [http://en.wikipedia.org/wiki/Chili_pepper](http://en.wikipedia.org/wiki/Chili_pepper)

---

### Post by Mark_in_Hollywood on 2013-01-24
Yes, but as the Spanish first "heard the word" from the nativie Peruvians or Mexicans, and as the Peruvians called it *aji*. And as the Spanish too stupid and proud to learn the natives language, they corrupted it into chile and as they are the first Europeans to put the word into print, I'm sticking with the original spelling.

I think the English/Americans/Texans heard the chile and not likeing the language of the natives, changed the spelling due to their "intellectual" superiority.

That's my 2 cents.

thank you again for your kind support.

---

### Post by Mark_in_Hollywood on 2013-02-05
See here:


[http://ubuntuforums.org/showthread.php?t=2109070](http://ubuntuforums.org/showthread.php?t=2109070)


and here:


[http://ubuntuforums.org/showthread.php?t=2111329](http://ubuntuforums.org/showthread.php?t=2111329)


for the solution.

---

