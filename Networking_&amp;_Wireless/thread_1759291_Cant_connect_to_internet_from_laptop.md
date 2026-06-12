---
title: "Cant connect to internet from laptop"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Lateralus138 on 2011-05-15
Sorry if this is already posted, but I wasnt sure the right keywords to use the search feature... I am somewhat familiar with older Ubuntu, but recently got 11.04 and installed it on my girlfriends laptop and during installation when it was scanning for the DHCP or whatever it says it failed to find it or something or other and it gave options to do it manually or to do it later so I chose to do it later and after booting into the OS I can not do anything via the internet, not even updates. I have tried looking at the network connections and the only thing there is a wired connection. This laptop accesses the internet through a desktop with Cox cable internet and a wireless router... I have no idea how to procede will someone help me please?

---

### Post by Plumtreed on 2011-05-15
...have you gone to " System>Additional Drivers" to see if you need to download a driver to support your laptop?

---

### Post by garvinrick4 on 2011-05-15
> **Lateralus138 said:**
> Sorry if this is already posted, but I wasnt sure the right keywords to use the search feature... I am somewhat familiar with older Ubuntu, but recently got 11.04 and installed it on my girlfriends laptop and during installation when it was scanning for the DHCP or whatever it says it failed to find it or something or other and it gave options to do it manually or to do it later so I chose to do it later and after booting into the OS I can not do anything via the internet, not even updates. I have tried looking at the network connections and the only thing there is a wired connection. This laptop accesses the internet through a desktop with Cox cable internet and a wireless router... I have no idea how to procede will someone help me please? 
Post results of these two, just need the network cards and drivers:
```
lspci -k
```
```
sudo lshw -C network
```

---

### Post by Lateralus138 on 2011-05-15
> **Plumtreed said:**
> ...have you gone to " System>Additional Drivers" to see if you need to download a driver to support your laptop?
This is what I get:
 
"Downloading package indexes failed, please check your network status. Most drivers will not be available."
 
 
> **garvinrick4 said:**
> Post results of these two, just need the network cards and drivers:
```
lspci -k
```
```
sudo lshw -C network
```
 
Will Check it out in a bit thanx...

---

### Post by Lateralus138 on 2011-05-15
Here ya go:
 
 
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
 Subsystem: Toshiba America Info Systems Device ff40
 Kernel driver in use: i915
 Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
 Subsystem: Toshiba America Info Systems Device ff40
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc6
 Kernel driver in use: HDA Intel
 Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: ahci
 Kernel modules: ahci
02:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: sdhci-pci
 Kernel modules: sdhci-pci
02:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
 Subsystem: Toshiba America Info Systems Device ffc0
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
 Subsystem: Toshiba America Info Systems Device ffc0
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
 Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
 Kernel driver in use: rtl819xE
 Kernel modules: r8192se_pci, r8192e_pci
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
 Subsystem: Toshiba America Info Systems Device ffc0
 Kernel driver in use: r8169
 Kernel modules: r8169
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] sudo lshw -C network
[sudo] password for jennifer: 
  *-network DISABLED      
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: wlan0
       version: 01
       serial: 00:24:d2:c4:48:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:c800(size=256) memory:fdffc000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:07:00.0"]pci@0000:07:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:26:18:7c:41:ff
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:e800(size=256) memory:fcfff000-fcffffff memory:fcfe0000-fcfeffff memory:febe0000-febfffff
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL]

---

### Post by garvinrick4 on 2011-05-15
Right click on Network icon in upper right and check enabled your network is disabled.
Drivers are in linux kernel so good there.

---

### Post by Lateralus138 on 2011-05-15
> **garvinrick4 said:**
> Right click on Network icon in upper right and check enabled your network is disabled.
Drivers are in linux kernel so good there.
 I see where it says the network is disabled here, but I just logged into Ubuntu, right clicked on Network and Enable Networking is check marked. I went to the connection and the only one there is under the "Wired":
 
Wired: Auto eth0
Wired 
Device MAC Adress: 00:26:18:7C:FF
MTU:automatic
 
IPv4 Settings
method: automatic (DHCP)
 
Require IPv4addressing for this connection tom complete is checked.

---

### Post by garvinrick4 on 2011-05-15
```
sudo ifconfig wlan0 up
```See if that gets it going.
```
iwconfig
```Above will tell you wlanO
If not check settings in Network connections

wireless. click on your SSID and hit edit
Mode- infrastructure
MTY- automatic
wireless security tab: connect auto, wpa or wep whatever yours is.
ipv4 settings Automatic (DHCP)
check require ipv4 on bottom
Hit save to save your settings.

---

### Post by Lateralus138 on 2011-05-15
Ok heres what I get:
 
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:24:d2:c4:48:a8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ffffc90011088000-ffffc90011088100 
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:24:d2:c4:48:a8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ffffc90011088000-ffffc90011088100 
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] ^C
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] 
 
Not sure about making that Wireless connection. It doesnt allow me rto save unless I enter something into the ssid and I have no idea what that is.

---

### Post by garvinrick4 on 2011-05-15
> Not sure about  making that Wireless connection. It doesnt allow me rto save unless I  enter something into the ssid and I have no idea what that is. 		                   		  		  		 		 			 				__________________
SSID is the name you gave for your internet when you set it up in your router. You need one
to set up your wireless. You gave it a name and a password when you set up your router.

---

### Post by garvinrick4 on 2011-05-15
> jennifer@JenniferWolf:~$ sudo ifconfig wlan0
You forgot the "up" on the end of line of code: It was to try and turn on wifi.
#You have to set up your network settings with SSID and password first.

---

### Post by uncaspi on 2011-05-15
Sorry to interrupt, but if I`am not completely wrong try if ssid is your router name.

---

### Post by garvinrick4 on 2011-05-15
> Sorry to interrupt, but if I`am not completely wrong try if ssid is your router name.
Not interrupting at all need to get her up and running with wifi, all help is cool.

---

### Post by Lateralus138 on 2011-05-15
> **garvinrick4 said:**
> You forgot the "up" on the end of line of code: It was to try and turn on wifi.
#You have to set up your network settings with SSID and password first.
 Actually I tried the up and it said something about not being a recognized command.

---

### Post by Lateralus138 on 2011-05-15
This is what I get:
 
 
 
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL] sudo ifconfig wlan0 up
[sudo] password for jennifer: 
SIOCSIFFLAGS: Operation not permitted
[EMAIL="jennifer@JenniferWolf:~$"]jennifer@JenniferWolf:~$[/EMAIL]

---

### Post by garvinrick4 on 2011-05-15
Did you find out what your SSID name is yet? You can not connect until you know
who you are. If you type 192.168.1.1 in your URL box on top of browser does it give
you your router. What kind of router do you have? Do you have a router?

---

### Post by garvinrick4 on 2011-05-15
Here is a link for a cox internet router. Your password is most likely on the bottom of
this router somewhere. Hopefully you can find your SSID and password and you can
set up your network connection as in previous post. The router basically configures itself
and the network manager in Ubuntu will configure itself. This code below will turn it off and on to look for your connection. 
Just needs to be configured like in previous post. The drivers are all in the linux kernel so that is no problem. Want to see you up and going.
[http://ww2.cox.com/residential](http://ww2.cox.com/residential)

```
sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start
```

---

### Post by Lateralus138 on 2011-05-16
Hey thanx I had already  went there  and looked at info on that and the netwoek connection itself and have enter all that info I do know what the name is and tried it. I tried all different variations of settings.... Not sure what the bssid is though. Please let me keep this post here i work so much that i will not be able to get back to fixing it til this Saturday. Thanx for all your help though. Ill be back on this post this weekend...

---

### Post by moaoci on 2011-05-16
There was a problem with the linux supplied rtl8192e driver. I am still with Ubuntu 10.04 so I don't know for sure if the problem still exists in 11.04.

If you see something that looks like a red exclamation mark ( ! ) in the top right corner near the wired network icon, it means that the linux supplied driver is still in problem.

Write to technical support at realtek ( [email]wlanfae@realtek.com[/email] ) to get the latest (and free) RTL8192E driver for Ubuntu 11.04.   You need to write them as only the windows driver is available for direct download.  They provide the instructions and will also help you if the driver they send is not working for you.  They provide excellent service.

You can also search my name (moaoci) and rtl8192e on the forums for more information.  The most recent is here: [http://ubuntuforums.org/showpost.php?p=10225476&postcount=4](http://ubuntuforums.org/showpost.php?p=10225476&postcount=4) 

Hope you get wireless soon ....

---

### Post by Lateralus138 on 2011-05-17
> **moaoci said:**
> There was a problem with the linux supplied rtl8192e driver. I am still with Ubuntu 10.04 so I don't know for sure if the problem still exists in 11.04.

If you see something that looks like a red exclamation mark ( ! ) in the top right corner near the wired network icon, it means that the linux supplied driver is still in problem.

Write to technical support at realtek ( [email]wlanfae@realtek.com[/email] ) to get the latest (and free) RTL8192E driver for Ubuntu 11.04.   You need to write them as only the windows driver is available for direct download.  They provide the instructions and will also help you if the driver they send is not working for you.  They provide excellent service.

You can also search my name (moaoci) and rtl8192e on the forums for more information.  The most recent is here: [http://ubuntuforums.org/showpost.php?p=10225476&postcount=4](http://ubuntuforums.org/showpost.php?p=10225476&postcount=4) 

Hope you get wireless soon ....
Thank you, Ill check into the exclamation mark later tonight, but I dont think it was there.

---

### Post by Lateralus138 on 2011-06-04
> **moaoci said:**
> There was a problem with the linux supplied rtl8192e driver. I am still with Ubuntu 10.04 so I don't know for sure if the problem still exists in 11.04.

If you see something that looks like a red exclamation mark ( ! ) in the top right corner near the wired network icon, it means that the linux supplied driver is still in problem.

Write to technical support at realtek ( [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL] ) to get the latest (and free) RTL8192E driver for Ubuntu 11.04.   You need to write them as only the windows driver is available for direct download.  They provide the instructions and will also help you if the driver they send is not working for you.  They provide excellent service.

You can also search my name (moaoci) and rtl8192e on the forums for more information.  The most recent is here: [http://ubuntuforums.org/showpost.php?p=10225476&postcount=4](http://ubuntuforums.org/showpost.php?p=10225476&postcount=4) 

Hope you get wireless soon ....
I have just emailed them and asked for the driver. Sorry that it's taking me long to respond... life is a bit crazy right now and don't have much time for a lot lately, but I want to eventually get the net running on here in Linux so I hope you can bear with me.

---

### Post by Lateralus138 on 2011-06-07
Great news.... I installed the new driver for Realtek and established an internet connection; can download update packages... bad news... can't Firefox can't connect to a web page!!!!! I have no idea why not. Any help please? by the way thank you very much!!! Can't figure out how to do the wlan0up thing.

---

### Post by Lateralus138 on 2011-06-08
Please any help? Sorry just not sure if anyone seen my post :(

---

### Post by bubbasmurf on 2011-06-08
I just made a comment about my post on connecting wireless ...

[http://ubuntuforums.org/showthread.php?p=10914402#post10914402](http://ubuntuforums.org/showthread.php?p=10914402#post10914402)

---

### Post by Lateralus138 on 2011-06-09
> **bubbasmurf said:**
> I just made a comment about my post on connecting wireless ...

[http://ubuntuforums.org/showthread.php?p=10914402#post10914402](http://ubuntuforums.org/showthread.php?p=10914402#post10914402)


Thanx a lot checking it out now.

---

### Post by Lateralus138 on 2011-06-09
I tried to do what [bubbasmurf]("http://ubuntuforums.org/member.php?u=1313296") said to do in his post and it did not work for me; although, I do appreciate your effort, I still need help please.

---

### Post by jon zendatta on 2011-06-09
Have you tried this:
in Firefox enter **about:config**
--> Network.dns.disableIPv6
right click to toggle this value from false to true

---

### Post by moaoci on 2011-06-09
Just to be sure...  You say Firefox can't reach internet: Can it reach your wireless router itself (something like 192.168.1.1).  If it can't, then the rtl8192e driver is not working yet.

You say you updated Ubuntu... if the update includes a new linux kernel number, the wifi will stop working and  you'll have to remove the staging rtl8192e driver from the new kernel and recompile the realtek rtl8192e driver. It happens once in a while. I hope it is your case...

---

### Post by Lateralus138 on 2011-06-10
> **jon zendatta said:**
> Have you tried this:
in Firefox enter **about:config**
--> Network.dns.disableIPv6
right click to toggle this value from false to true


Tried it thank you, but it did not work


> **moaoci said:**
> Just to be sure...  You say Firefox can't reach internet: Can it reach your wireless router itself (something like 192.168.1.1).  If it can't, then the rtl8192e driver is not working yet.

You say you updated Ubuntu... if the update includes a new linux kernel number, the wifi will stop working and  you'll have to remove the staging rtl8192e driver from the new kernel and recompile the realtek rtl8192e driver. It happens once in a while. I hope it is your case...

Ok I will check this out Sunday.... I really want to see this work so I'm not giving up.

---

