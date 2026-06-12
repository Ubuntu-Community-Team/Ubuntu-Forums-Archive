---
title: "belkin micro usb wireless dongle model n300 f7d210 not working"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by sohlinux on 2012-09-02
Hi,

Just bought a new belkin micro usb wireless dongle model n300 f7d2102 but I cant get it working in ubuntu 12.04

I followed some instructions which I found, but still it doesnt work...

----
From the installation CD for the N300 nab the 3 XP files and put them in a folder on the home folder.
net8192su.cat
net8192su.inf
rtl8192su.sys
install and open the ndiswrapper tool
find the net8192su.inf file and install
plug in the usb wireless n300 and setup your wireless settings.
----

any ideas how to get his working?

here is the output from the following commands

lshw -C network
lsusb
iwconfig
ndiswrapper -l



lshw -C network

  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:e0:9e:ae
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f4a00000-f4a0ffff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: 54:42:49:f1:3d:be
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f2220000-f2223fff ioport:a000(size=256) memory:f2200000-f221ffff


----------------------------------------------

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 064e:a213 Suyin Corp. 
Bus 002 Device 005: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]
Bus 002 Device 004: ID 046d:c52e Logitech, Inc. 


----------------------------------

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.




----------------------------------

ndiswrapper -l

net8192cu : driver installed
	device (050D:2103) present (alternate driver: rtl8192cu)
r : invalid driver!

---

### Post by kurt18947 on 2012-09-02
WikiDevi says your adapter uses a RealTek 8192**CU** which is a different animal.
[http://www.wikidevi.com/wiki/Belkin_F7D2102](http://www.wikidevi.com/wiki/Belkin_F7D2102)
which is the reason to run "lsusb", to find out which chip set you really have.  Assuming your adapter really does use an 8192CU chip, here is RealTek's download site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
I don't have any experience with your model adapter.  I have used Realtek's drivers though for an RTL8188CUs adapter and once I figured out how to extract and run a BASH script, it was simple and worked very well.  RealTek does seem to have pretty good unix/linux support though there's more of a do-it-yourself element than click-here Windows.  Good luck, you should be able to get this running.

Edit: If I had read your original post I'd have seen you do have an 8192CU chip.  I'd download RealTek's 8192CU driver and see how you get along.   Note that the Realtek script must be run from an account with SUDO privileges.  You'd probably have to remove NDISwrapper first; NDISwrapper makes a lot of changes which may prevent  native drivers from working.  Also keep the RealTek files where you find them again.  If the kernel updates,  the wifi adapter may not work.  Rerun the installer script and you should be back in business.

---

### Post by sohlinux on 2012-09-03
> **kurt18947 said:**
> WikiDevi says your adapter uses a RealTek 8192**CU** which is a different animal.
[http://www.wikidevi.com/wiki/Belkin_F7D2102](http://www.wikidevi.com/wiki/Belkin_F7D2102)
which is the reason to run "lsusb", to find out which chip set you really have.  Assuming your adapter really does use an 8192CU chip, here is RealTek's download site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
I don't have any experience with your model adapter.  I have used Realtek's drivers though for an RTL8188CUs adapter and once I figured out how to extract and run a BASH script, it was simple and worked very well.  RealTek does seem to have pretty good unix/linux support though there's more of a do-it-yourself element than click-here Windows.  Good luck, you should be able to get this running.

Edit: If I had read your original post I'd have seen you do have an 8192CU chip.  I'd download RealTek's 8192CU driver and see how you get along.   Note that the Realtek script must be run from an account with SUDO privileges.  You'd probably have to remove NDISwrapper first; NDISwrapper makes a lot of changes which may prevent  native drivers from working.  Also keep the RealTek files where you find them again.  If the kernel updates,  the wifi adapter may not work.  Rerun the installer script and you should be back in business.

thanks for the info but after removing ndiswrapper and installing the realtek script it shows the belkin wireless usb dongle as "disabled".  is there an option to enable or disable? in the network manager the option to turn on wireless is greyed out? according to another forum I read the xp driver for this device should work in ubuntu and after installing it with ndsiwrapper the driver appears to be installed but the wireless is disabled.

I bought the wireless dongle because my sony vaio built in wireless stopped working. also the wired connections stopped working. in windows the new belkin dongle works fine,





thanks

---

### Post by steeldriver on 2012-09-03
iirc the lshw command usually reports 'Disabled' when there is a hard/soft switch (as opposed to 'Unclaimed' when the driver is not loaded) - have you tried

```
rfkill list all

sudo rfkill unblock all 
```

You may also find you need to 'unmanage' your internal (Atheros?) pci card so that network manager ignores it - but let's not go there until we know whether it is causing problems

---

### Post by kurt18947 on 2012-09-03
> **steeldriver said:**
> iirc the lshw command usually reports 'Disabled' when there is a hard/soft switch (as opposed to 'Unclaimed' when the driver is not loaded) - have you tried

```
rfkill list all

sudo rfkill unblock all 
```You may also find you need to 'unmanage' your internal (Atheros?) pci card so that network manager ignores it - but let's not go there until we know whether it is causing problems

Steeldriver has a good point.  It might also be worthwhile running "lsmod" and see what modules are loading.   I had a problem with the 'built-in' module and the installed RealTek driver conflicting.  When I ran 'lsmod' I'd see both "rtl8192ce"(the included module) and "8192ce" the RealTek module.  Both loaded, neither worked.   I had to blacklist the "rtl8192ce" module and reboot.  Then the adapter worked properly.

---

### Post by sohlinux on 2012-09-03
> **steeldriver said:**
> iirc the lshw command usually reports 'Disabled' when there is a hard/soft switch (as opposed to 'Unclaimed' when the driver is not loaded) - have you tried

```
rfkill list all

sudo rfkill unblock all 
```

You may also find you need to 'unmanage' your internal (Atheros?) pci card so that network manager ignores it - but let's not go there until we know whether it is causing problems

thanks for the info, I tried what you said, below is the output, still enable wireless is greyed out?

thanks

rfkill list all
0: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
4: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


sudo rfkill unblock all
~$

---

### Post by sohlinux on 2012-09-03
got it working! not sure how but when I rebooted after running sudo rfkill unblock all it worked!

---

### Post by kurt18947 on 2012-09-03
> **sohlinux said:**
> got it working! not sure how but when I rebooted after running sudo rfkill unblock all it worked!

COOL!!  Maybe mark the thread 'solved'?

---

### Post by sohlinux on 2012-09-03
> **kurt18947 said:**
> COOL!!  Maybe mark the thread 'solved'?

I spoke too soon, I thought it was working but it was the internal wireless that was working not the belkin usb wireless, the internal wireless for some strange reason has started working again but its extremely slow so I still need to get the usb working. its strange now because I can see the belkin active but if I turn off the internal wireless switch it also disables the belkin wireless, I cant get the belkin to work even when the internal is wireless is on, its very confusing.

---

### Post by steeldriver on 2012-09-03
You might want to try 'unmanaging' the internal card by its MAC address via /etc/NetworkManager/NetworkManager.conf

[http://ubuntuforums.org/showpost.php?p=11935484&postcount=2](http://ubuntuforums.org/showpost.php?p=11935484&postcount=2)

---

### Post by sohlinux on 2012-09-04
> **steeldriver said:**
> You might want to try 'unmanaging' the internal card by its MAC address via /etc/NetworkManager/NetworkManager.conf

[http://ubuntuforums.org/showpost.php?p=11935484&postcount=2](http://ubuntuforums.org/showpost.php?p=11935484&postcount=2)

this is what I have in /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

its strange in settings > networks , if I turn off the switch on the front of the laptop both the internal wireless and the belkin usb wireless are turned off, I cannot get the belkin usb to work on its own.

thanks

---

### Post by kurt18947 on 2012-09-04
Have you tried blacklisting the internal adapter?  I've run into something similar on a Thinkpad R61 with a USB adapter.  I could turn the Wifi hardware switch off and the USB adapter using the manufacturer's driver would still work with Ubuntu.  Same machine with Mint Maya switching off the hardware switch disabled both WiFi adapters like you're finding.  Tried blacklisting the internal adapter, no go.  I was finally able to turn off the internal WiFi adapter in Network Manager and have it stick.

---

### Post by sohlinux on 2012-09-04
> **kurt18947 said:**
> Have you tried blacklisting the internal adapter?  I've run into something similar on a Thinkpad R61 with a USB adapter.  I could turn the Wifi hardware switch off and the USB adapter using the manufacturer's driver would still work with Ubuntu.  Same machine with Mint Maya switching off the hardware switch disabled both WiFi adapters like you're finding.  Tried blacklisting the internal adapter, no go.  I was finally able to turn off the internal WiFi adapter in Network Manager and have it stick.

thanks but how do I black list it?

---

### Post by steeldriver on 2012-09-04
'blacklisting' usually refers to preventing a competing kernel module from being loaded - imo it's not necessary to do that unless you are getting driver conflicts and it would prevent *any* device which needs that driver from working

otoh 'unmanaging' tells n-m to ignore a specific device based on its MAC

I had almost the same issue as you (except that I replaced an internal PCI card with an external CardBus) hence why I recommended unmanaging your internal device

---

### Post by sohlinux on 2012-09-04
> **steeldriver said:**
> 'blacklisting' usually refers to preventing a competing kernel module from being loaded - imo it's not necessary to do that unless you are getting driver conflicts and it would prevent *any* device which needs that driver from working

otoh 'unmanaging' tells n-m to ignore a specific device based on its MAC

I had almost the same issue as you (except that I replaced an internal PCI card with an external CardBus) hence why I recommended unmanaging your internal device

thanks but its not possible to unmanage it, its not showing up in the conf file

this is what I have in /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

---

### Post by chili555 on 2012-09-04
If I may gently, without stepping on any toes, offer a suggestion. I suggest you run:```
sudo lshw -C network
```See what 'driver=' is for your internal ***wireless*** device. Be careful, don't accidentally pick the wired ethernet.

Then blacklist its driver. For example, suppose it's ath5k; then you'd do:```
sudo su
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```Substitute your driver here. Now reboot and troubleshoot your Belkin without interference.

OK, we return you to your regularly scheduled guru!

---

### Post by lillypad on 2012-09-04
I've got a similar problem to this but with this adapter:
```
Bus 001 Device 009: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]
```

The wireless state under the nm-tool is disconnected for some reason. I did however read somewhere that installing the RTL819CU driver from realtek might work but I did do this with no avail but you could try it download is [here.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true")

Just download and run the bash script install.sh as root.

```
sudo sh

chmod +x install.sh

./install.sh
```

something to this affect may work might want to get rid of ndiswrapper as well if your trying this

```
sudo apt-get remove --purge ndiswrapper
```

If anything is conflicting with the driver may want to try blacklisting something from the /etc/modprobe.d/blacklist.conf

I've tried these but no avail for me perhaps it might help you! Just lsusb to get the realtek driver name and that download page might have it for you!
[]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by steeldriver on 2012-09-04
> **sohlinux said:**
> thanks but its not possible to unmanage it, **its not showing up in the conf file**

You would need to ADD it to the conf file - using your lshw output we can see the MAC of the internal Atheros card is 4c:0f:6e:e0:9e:ae ("serial: 4c:0f:6e:e0:9e:ae"), so your conf file would become

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

[COLOR=Red][B][keyfile]
unmanaged-devices=mac:4c:0f:6e:e0:9e:ae[/B][/COLOR]
```Or do the blacklist as described by chili555 - choice is yours

---

### Post by sohlinux on 2012-09-04
thanks everyone for your help but I have tried everything in this thread , spent many hours and nothing will make it work. 

if I turn off the internal wireless at the switch I cannot even get get the usb wireless to enable, and when the internal wireless switch is on the belkin usb does not detect any networks. 

does anyone have any more ideas?

maybe if I re install ubuntu with the belkin wireless usb plugged in and the wireless switch tuned off will it automatically install the belkin driver? 

just so you know the belkin wireless does work ok in windows 7

thanks

---

### Post by chili555 on 2012-09-04
> does anyone have any more ideas?Yes. Leave the switch on and blacklist the internal as previously suggested.

---

### Post by sohlinux on 2012-09-04
> **chili555 said:**
> Yes. Leave the switch on and blacklist the internal as previously suggested.

I already tried black listing and unmanaging but the belkin will not work.

---

### Post by steeldriver on 2012-09-04
well now you've got the troublesome internal card safely out of the way,  I think you need to go back to square one and troubleshoot the Belkin from scratch  i.e.  

- check it's not blocked 
- check it is picking up the correct driver
- examine dmesg for any errors related to that driver

---

### Post by sohlinux on 2012-09-05
> **steeldriver said:**
> well now you've got the troublesome internal card safely out of the way,  I think you need to go back to square one and troubleshoot the Belkin from scratch  i.e.  

- check it's not blocked 
- check it is picking up the correct driver
- examine dmesg for any errors related to that driver

I dont think the internal wireless is out of the way because if I turn off the switch on the front of the laptop it also turns off the belkin wireless.

its not blocked

the correct driver for this device is installed

dmesg doesnt show any errors releated to networking


I will try a re install and see how I get on, I will be back.

---

### Post by sohlinux on 2012-09-05
rebooted and it now works, not sure exactly what has made it work since I tried so many things but I will mark this as solved! :p

---

### Post by sohlinux on 2012-09-05
ps.  allthough the belkin usb dongle is now working ok it will only work if the wireless network switch is tuned on at the front of the laptop. its strange but true, oh well no problem, I need the switch on because it also activates the blutooth. 

fyi in windows the switch doesnt need to be on for the belkin usb to work. :p

---

