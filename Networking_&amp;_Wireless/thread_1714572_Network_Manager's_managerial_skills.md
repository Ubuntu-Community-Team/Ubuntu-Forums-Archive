---
title: "Network Manager's managerial skills?"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by swedstal on 2011-03-25
I recently got an Edimax EW-7128g (**RT2561/RT61)** which was reported to work "out of the box" here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

I feel like I have honed in on the problem but just need a little help to get over the top. 

Though I should have noticed this sooner, Network Manager does not allow me to select 'Wlan0' from its drop down menu. I used information on this site: ([https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo))  to try and remedy this problem.

I did
```
iwconfig
```the result of which matched the guide.

I then used

```
sudo ifdown eth0
```to shut off my wired connection so that the only thing showing up on 'ifconfig' is 'lo

I then used

```
sudo ifup wlan0
```but got back

```
Ignoring unknown interface wlan0=wlan0
```I think this is my problem but am unsure where to go from here. Any help would be much appreciated. Thanks!

---

### Post by conneco on 2011-03-25
post the result of for me

```
sudo lshw -C network
```

---

### Post by swedstal on 2011-03-26
Thanks for your response. Here it is:

```
*-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 90:e6:ba:cd:f9:7f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:c800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:a8:24:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fbff8000-fbffffff
```

---

### Post by swedstal on 2011-04-08
Hmmm...I am still stuck. Anyone else be able to provide some insight?

---

### Post by grahammechanical on 2011-04-08
I have just noticed that you are using Ubuntu Studio. I have that installed but not as my main Ubuntu. I know that network manager is not installed in Ubuntu Studio. You have to install it yourself. Have you done this? Ubuntu studio is not designed for networking for technical reasons.

This is what I worked out for Ubuntu Studio;

> 1) Something is needed to indicate that an Internet of networking connection has been made.

Right click the top panel and select Add to Panel. In the list presented by the dialog box select Network Monitor [Monitor network activity]. Click Add.

This action will put an icon of two connected monitors (screens) that will flash when there is network activity. It is reassuring to have this.

2) Setting up connections. Click on the Ubuntu Studio icon on the left of the top panel. Go to System>Administration>Network.

Do not go to System>Preferences>Network. It is the wrong type of network.

In the dialog box that appears select the Connections tab. Click the shield icon at the bottom and in the middle of the dialog box. It has "Click to make changes" alongside it.

Enter your login password. A list of available connections will appear. Select either Wireless Connection, Wired connection (eth1) or Wired connection (eth0) and click the Properties button.

For a Wireless connection put a tick mark against the box "Enable this connection".

Make sure that the network name (ESSID) is the correct one.

Set the password type WPA Personal.

Enter the Network password. This is the wireless key or WPA-PSK key.

Set the configuration to Automatic configuration (DCHP) if that is the correct setting.

Enter if necessary the IP address, Subnet mask, Gateway address.

Click OK.

Click the make changes shield to prevent any further changes.

Click close and then reboot. Cross your fingers. You may need to shutdown and boot more than once. It is strange, I know but there you are.

Some other information: Left or right click the Network Monitor icon to see the Connection Properties of wlan0

A dialog will appear that will give the connection name, its status, an activity report (packets and Kilo bits received and sent) and signal strength. There is also a button to Configure the connection. Every time I click this button I get a Interface does not exist message even though there is an active connection.

If all else fails you can also type in a terminal sudo ifconfig wlan0 up and sudo ifup -v eth0 or sudo ifup -v eth1

I found from experience that I can either have a wired connection or a wireless connection but not both at the same time. (I can do this in standard Ubuntu). Whichever one you choose seems to block off the other one.

I was thinking of writing a guide with screen shots and sending it to the Full Circle magazine. I was waiting to see what changes 11.04 brings.

regards.

---

### Post by swedstal on 2011-04-08
Thank you for your response. Something is still not quite right.

I do have the Network Manager on the panel already.

I am doing
```
network-admin
```to see my network settings.

This GUI only has three tabs: "General", "DNS" and "Hosts." I do not have a connections tab. Am I looking in the wrong place for this?

I have also done
```
sudo ifdown eth0
```and as you suggested
```
sudo ifconfig wlan0 up
```
I shut down completely and crossed my fingers (as instructed) on restart. Still, The only thing showing up in the Connection drop down box of Network Manager is 'lo'

It does not appear I have anywhere to enter the ESSID or my WPA.

Am I a crazy person?

---

### Post by swedstal on 2011-04-18
I don't know if it will help anyone but I did fix this problem. All I needed to do was uninstall Network Manager and install wicd instead. At the time of this post I could not figure out how to install a program without an internet connection but I was eventually able to figure it out.

All I did was find the dependencies (3 of them, I think), install, reboot and I was connected.

This seemed like a 'Deus Ex Machina' fix which is why I did not try it sooner, but I would encourage anyone with wifi issues to try wicd first.

---

