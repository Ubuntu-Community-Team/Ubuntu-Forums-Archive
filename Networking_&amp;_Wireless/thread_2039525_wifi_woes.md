---
title: "wifi woes"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by ferdi_t on 2012-08-09
I recently installed 12.04, but have been having trouble installing wireless. LAN works fine, and the adaptor works fine under Windows 7. During istallation from the live-cd, Ubuntu recognised it fine and was able to search for networks. But after the finished installation, nothing happens. Meh.

I ran lsusb, and it gets listed fine (as Realtek Semiconductor Corp RTL81188CUS). 

'Additional drivers' only lists nvidia drivers, but nothing for a wireless connection.

ndiswrapper fails because there's only an exe-file on the installation cd, and the archive manager isn't able to open the file to look for an inf.

Any thoughts?

---

### Post by Bucky Ball on 2012-08-09
Try the Realtek software available on their website. The Linux driver's down the page a little:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS)

There should be a read me file there to tell you what to do but fairly simple. Should be like; extract the downloaded file to a folder, in a terminal navigate to the folder you have extracted the the driver to, then these three commands one after the other:

```
sudo su
make
make install
```

Avoid ndiswrapper. Largely superseded.

---

### Post by ferdi_t on 2012-08-09
I downloaded the files, but there's no readme covering the subject of installing. So I'm down on my luck. What it does have is a tar.gz inside the folder 'drivers'. Which is kinda bad, because I have never been able to use them. Does 12.04 have an easy way of installing them? 

Or any other word of advice?

---

### Post by chamber on 2012-08-09
If you downloaded the drivers from the website then there should be a file in the unzipped folder called install.sh

In your terminal cd to the downloaded folder and the run 

```
sudo bash install.sh
```

---

### Post by ferdi_t on 2012-08-09
I have been able to install the drivers succesfully. I'm able to put in the network. However, there's no way to choose wpa2-psk? Just wep40/128 and wep 128.

How am I going to connect? Actually, i AM able to connect, it's just that the router refuses any data (obviously).

---

### Post by ferdi_t on 2012-08-09
Created a new entry in the wireless tab of Network Connections. Choose 'wpa & wpa2 personal' which worked fine. Gave in SSID, mode, BSSID & Device Mac saved... and now my machine won't even attempt to connect.

The connection icon greys out everything besides Connect to a hidden network, create new wireless network, and VPN connections.

How am I ever going to get my machine online? All help is appreciated.

---

### Post by ferdi_t on 2012-08-09
Did some youtubing. With other users, the network icon on the top right should display all neighbouring ssid's. Mine doesn't. Any idea how I get them there?

---

### Post by Egonosaur on 2012-08-09
Ferdi what wifi adapter and router are you using?
 
I'm trying to install a N600 netgear and i'm also using WPA2-PSK security on my network. I tried using ndiswrapper, I can see all the available networks in the area, I don't think I can connect to a secure one with that method though. 

When i try to connect to my WPA2-PSK secured network the password box will show up and it will try to connect and then after a while the password box will show up again.

---

### Post by Bucky Ball on 2012-08-09
> **Egonosaur said:**
> Ferdi what wifi adapter and router are you using?
 
I'm trying to install a N600 netgear and i'm also using WPA2-PSK  security on my network. I tried using ndiswrapper, I can see all the  available networks in the area, I don't think I can connect to a secure  one with that method though. 

When i try to connect to my WPA2-PSK secured network the password box  will show up and it will try to connect and then after a while the  password box will show up again.

You would be better to start a new thread with a descriptive title  and outlining your problem. Trying to fix two at once is confusing.

Tip: Avoid ndiswrapper if possible.

@Ferdi: Could you post the output of:

```
sudo lshw -C network
```

---

### Post by ferdi_t on 2012-08-10
Sure thing.

```

ferdi@Werkcomputer:~$ sudo lshw -C network
[sudo] password for ferdi:
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:a4:4e:a5
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:41 memory:fe02b000-fe02bfff ioport:d800(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:5
       logical name: wlan0
       serial: 80:1f:02:2e:06:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-27-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11b

```

I also checked the system settings > additional drivers. It lists Realtek Wireless Lan Driver right now, but it has the following message:

> This driver is activated but not currently in use

And it gets stranger. Although lsusb lists it as Realtek Semiconductor Corp RTL81188CUS, the installation-cd (which has worked on Windows Vista) has the brand and number Medion P89081 (MD86498 ). Ehm... I'm quite confused.

---

### Post by Bucky Ball on 2012-08-10
The brand is often irrelevant. The majority of manufacturers use Realtek, Broadcom, Atheros. Brand and manufacturer of the chip inside the dongle rarely match. Not an issue. ;)

Looks like all good. Could you check in Network icon, Edit Connections and make sure all is good there. You could also try disabling the driver, reboot and enable. Also, when you click (or right click) the Network icon, do you have 'Enable Networking' and Enable Wireless? Switch off Enable Wireless then back on again.

You might also try Wildmanne's suggestion in post #12 here:

[http://ubuntuforums.org/showthread.php?t=2039287&page=2](http://ubuntuforums.org/showthread.php?t=2039287&page=2)

PS: Most Medion gear isn't supported (or wasn't, maybe now) so avoid, but in this case you seem to have a friendly chip inside. ;)

---

### Post by ferdi_t on 2012-08-11
Nice to know the brand is not an issue.

I followed your advice and disabled the driver, rebooted and enabled it. Ubuntu immediately searched for my network and got a great connection.

Problem solved, or so I thought.

Problem is, it only works as long as I don't reboot. After a reboot, the problem is the same: in system setting > additional drivers, it says: This driver is activated but not currently in use.

Ehm, how do I solve this? Is there any way to make Ubuntu remember it at boot?

---

### Post by ferdi_t on 2012-08-11
Finally solved it by adding r8168 to /etc/modules.

---

### Post by Bucky Ball on 2012-08-12
Great news Ferdi. Enjoy!

Could you please mark this thread solved by clicking thread tools. It might help others to find a fix. ;)

See you round the forums.

---

### Post by ferdi_t on 2012-08-13
Done.

Btw, is there any way for the developers to take note? I'm obviously glad that the problem is solved, but I'm still a little but frustrated over the fact that I spend two evenings and a Saturdaymorning to get something running which would've taken about 5 mins in Windows.....

---

