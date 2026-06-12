---
title: "NEWBIE BCM 4311 Wireless Not Connecting"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by pilot26 on 2009-09-21
I am new to lynx and I have just gotten Ubuntu 9.06 and I'm having trouble connecting to my wireless, hard line works just fine. 

I have tried a number of other suggestions they did not work either due to do user error or not the right fix.

I have tried the download driver but that has not worked

I have a.

  *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:14:a5:d0:34:88
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11b

---

### Post by Ayuthia on 2009-09-21
> **pilot26 said:**
> I am new to lynx and I have just gotten Ubuntu 9.06 and I'm having trouble connecting to my wireless, hard line works just fine. 

I have tried a number of other suggestions they did not work either due to do user error or not the right fix.

I have tried the download driver but that has not worked

I have a.

  *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:14:a5:d0:34:88
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11b

Can you try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it produces wireless sites, we will need to blacklist the b43 and ssb modules:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl |sudo tee -a /etc/modules
```
This will prevent the b43 module from interfering with the Broadcom STA wireless module and then load the correct module when you restart your computer.  Hope that helps.

---

### Post by pilot26 on 2009-09-21
When I run:  
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan

it produces 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument


what should I do next.

thank you for all of your help

Matt

---

### Post by Ayuthia on 2009-09-21
Sometimes the Broadcom STA module will not list any sites the manual way because NetworkManager is running.  Are you able to see anything through NetworkManager (the GUI version)?

If not, can you once again post the results of:
```
lshw -C network
```
The information there should have changed because we loaded a different wireless module.

---

### Post by pilot26 on 2009-09-21
lshw -C network
I think that I am using GUI version of network manager but I dont see any thing

 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ba:02:e7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:d0:34:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:2e:3a:25:04:88
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Thank You
Matt

---

### Post by Ayuthia on 2009-09-21
It might be NetworkManager.  Can you try the following:
```
sudo /etc/init.d/NetworkManager stop
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it does not produce any wireless sites, you can turn Network Manager back on by doing the following:
```
sudo /etc/init.d/NetworkManager start
```or restart the computer.

This set of commands will stop Network Manager then reload the wireless modules to see if we can get it started again.

---

### Post by pilot26 on 2009-09-23
I tried

	 		**Re: NEWBIE BCM 4311 Wireless Not Connecting**
 		It might be NetworkManager.  Can you try the following:

any more sugestions


thanks much
Matt
 	Code:
 	sudo /etc/init.d/NetworkManager stop
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan




and it produced 

 sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.



[FONT=Verdana][/FONT]

---

### Post by pilot26 on 2009-09-23
bump

---

### Post by windom on 2009-09-24
I have a laptop with the BCM4311 wireless. It is a Compaq Presario 500, precisely a C571NR. I have spent way too many hours (literally full work weeks) chasing this around over the last several weeks. It started because I thought it was time to bite the bullet and get my WEP system switched over to WPA-AES. I *finally* have a reliable wireless connection. I made many, many changes so I will describe where I stand at the moment.

1) I found that the b43 driver was the last piece of my puzzle. When I switched to it there was much joy. This means ndiswrapper (with the few different windows drivers I tried with it) and wl are not on my preferred list. b43 can be used by:

	a) add these lines to /etc/modules
             ieee80211_crypt_tkip
             ieee80211_crypt_ccmp
             b43
	I am not sure the crypto modules need to be there but they don't hurt.

	b) add these lines to /etc/modprobe.d/blacklist.conf
		blacklist ndiswrapper
                blacklist wl

	   I tried many things and had all these modules installed on my system. Again, if you don't have wl and/or ndiswrapper installed this should not hurt.

Load the b43 module with the verbose parameter (modprobe -v b43). It will show the loading of a few other modules. Make sure they are not listed in /etc/modprobe.d/blacklist.conf. Check dmesg to make sure the firmware loaded. If you have a problem with it loading, there are a lot of sites that deal with this situation and at least one that serves the firmware directly so it does not need to be extracted with fw-cutter. Use the google on the internet machine. ;)

2) Remove NetworkManager. For whatever reason, it just didn't do the job for me.

3) Install wicd. For what ever reason, it works for me.

4) Grep the etc directory tree for references to the wireless device to make sure all references are in sync. I used 'cd /etc' then 'sudo grep -r wlan *'. I use the device name wlan0. I don't think if eth1 makes a difference but wlan0 is better than wlan1.  I can't be very specific because there can be a great variance depending on what is or is not installed on the system. Just check for consistency. One can change this device nickname in /etc/udev/rules.d/70-persistent-net.rules. I have the lines

# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:xx:xx:xx:xx:xx", ATTR{type}=="1", KERNEL=="eth*", NAME="wlan0"

One can see the MAC address (redacted with x's in this case) embedded in the second line. The second from last parameter denotes the kernel assigned name while the last parameter declares what I want the name to be. You need to research udev if you need more specifics

5) /etc/network/interfaces should not have any references to any interfaces other than the loopback. My file looks like this:

auto lo
iface lo inet loopback

wicd will take care of both the wired and wireless interfaces

6) wicd has a set of templates used for configuring wpa_supplicant. They are located in /etc/wicd/encryption/templates. As I mentioned, I started this odyssey based on the need for WPA-AES connectivity. The default template used by wicd for this senario is a one size fits all approach that really should work but my situation was so fragile I removed references to TKIP encryption and the RNS (WPA2) protocol. My make it work any harder than it has to? As I mentioned, I considered my situation to be fragile. A reference for doing this can be found at [http://wicd.sourceforge.net/templates.php](http://wicd.sourceforge.net/templates.php) One should also read [http://www.y3m.net/docs/gentoo-on-t42/configs/wpa_supplicant.conf](http://www.y3m.net/docs/gentoo-on-t42/configs/wpa_supplicant.conf) so one has some idea of what she is changing when working with wpa_supplicant configuration files. The link points to the documented configuration file supplied with the wpa_supplicant package and can be found online in many other places. Please take the time to read these documents (it doesn't take long) if you plan on making any changes. I sincerely doubt this step is necessary but I was desperate

7) Implied in #6 is that wpa_supplicant is installed

At this point, reboot for good measure. Do a lsmod|sort|less to check the loaded modules. The crypt modules, b43, and b43's associated modules should be loaded. ndiswrapper and wl should *not* be loaded. Open the wicd client applet. Select preferences. In general settings select wext for thw wpa_wupplicant driver and add your interface names. Leave the other tab alone. Your AP should be showing in the client. Click on the triangle to the left of the network name and then click on Advanced Settings. I set to use a static IP (again, trying to make it as easy as possible to connect). For the DNS I used 208.67.220.220 and 208.67.222.222 which is OpenDNS (opendns.com (a plug for the service)). Select your form of encryption. I entered my WPA key as an ascii phrase. Click OK. In my case I was connected before I could click the connect button. Probably because the 'automatically connect to this network' was already clicked.

For debugging use 'ps ax | grep wpa' to see if/how wpa_supplicant is running. It will show the config file wicd is using for it. wicd also has a log in /var/log/wicd/wicd.log. Go to wicd client --> Preferences --> General to enable debug mode.

Yeah this is a long post but wireless connectivity seems to be so precarious. And newbies will probably say I left an awful lot out. And others (or even the same people) will say I am not very definite about anything. It's true. I am just trying to document what worked for me. And I hope I did not omit anything of import. I think a big part of getting this working is not just the setup but also undoing others things that were tried and failed. Please note that there may be implied sudo's in some commands. I got tired of typing it and often just started with a sudo -s.

I saw a lot of similar problems while researching my problem. It made me so disappointed in Linux since the other OSs on my multiboot machine made the same connection as fast as I could type.

Good luck to all who find themselves in the same situation.

windom

---

### Post by pilot26 on 2009-09-24
Bump

---

### Post by Ayuthia on 2009-09-24
If you have a working internet connection, you can try using the b43 option instead of the Broadom STA option.  You can go into System->Administration->Hardware Drivers and disable the Broadcom STA option and enable the b43 option.  Once you do that, try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo iwlist scan
```

---

### Post by pilot26 on 2009-09-24
I cant find B34 

thanks for the try

Matt

---

### Post by windom on 2009-09-24
No wonder you are having a hard time. It's b43. I thought it was part of the default install but if you don't have it, install it.

windom

---

### Post by Cuba71 on 2009-09-24
Broadcom recommends the 802.11 STA linux driver for the BCM4311, are we trying to reinvent the wheel?

Look [here]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by windom on 2009-09-24
That's part of the problem. It just did not work for me if I wanted to use encryption other than WEP. It worked fine for that but started my nightmare when I tried to use it with WPA/WPA2. b43 is the only driver that gives me a consistently reliable connection to a WPA AP. I've tried them all. It is the only one that is totally free to boot (compared to ndiswrapper and wl). 

There are many different setups that people say are working for them but they won't work for others. This is too informal a setting to determine what causes the inconsistency. It seems the wheel we are using is quite wobbly.

windom

added: I should note that I am using jaunty.

---

### Post by pilot26 on 2009-09-24
I can find STA  is that the same thing

---

### Post by pilot26 on 2009-09-24
I have tried to install the new driver but I cant find it. where do I need to put it

thanks

---

### Post by pilot26 on 2009-09-24
I have run code

sudo /etc/init.d/NetworkManager stop
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
did this make it worse and what should I do to fix it


thanks
Matt

---

### Post by Ayuthia on 2009-09-24
> **Cuba71 said:**
> Broadcom recommends the 802.11 STA linux driver for the BCM4311, are we trying to reinvent the wheel?

Look [here]("http://www.broadcom.com/support/802.11/linux_sta.php")

Broadcom might recommend it, but theirs only came around in 8.04 (about a year ago).  The open source b43 driver has been around for much longer.  The b43 driver tends to work better with WEP and WPA.  Other than that, there are no real differences.

---

### Post by pilot26 on 2009-09-24
so how do I find the open source B34

---

### Post by Ayuthia on 2009-09-24
> **pilot26 said:**
> so how do I find the open source B34

It is actually b43.  If you cannot find it in System->Administration->Hardware Drivers, you can install it through Synaptic by installing b43-fwcutter or from the Terminal:
```
sudo apt-get install b43-fwcutter
```

---

### Post by pilot26 on 2009-09-24
So did I mess up?? and how do I fix this?

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


thanks
Matt

---

### Post by pilot26 on 2009-09-24
ok I have run

sudo apt-get install b43-fwcutter
I have made sure that STA is not activated 
then I restart 

and looked for B34 but I still cant find it

my wired conection is still working 

thanks
Matt

---

### Post by windom on 2009-09-24
You either have no functioning AP or else (more likely) your wireless NIC is not funtioning. My BCM4311 is on a laptop. It has a lighted buttton for the wireless. If there is no driver, there is no light. If the button is lit, then there is a driver problem. There are 3 different drivers for this NIC: wl, ndiswrapper, and b43. Choose only one. I recommend b43. 

Do a 'sudo modprobe -v b43'. Don't add any other drivers to the modprobe command. They other necessary drivers should load automatically. Using the -v option will report this. Then do a 'lsmod | sort | less' This will display all the loaded drivers in an alpha sorted list using the less pager. Look for the b43 driver. That's good. Look for ndiswrapper and wl. If you find one or both, that is bad. Remove them. Add them to blacklist.conf (refer to my previous post). Now do a 'dmesg | less'. Scrool to the bottom and check for a message like 

[   35.456133] b43-phy0: Loading firmware version 410.2160

to make sure the firmware loaded. If it didn't load you have to deal with that problem first. My previous post has more. If it loaded then try 'iwconfig' to see that the device is recognized and then 'iwlist' to see if it is working. If APs are reported, you are off to a good start.

windom

---

### Post by pilot26 on 2009-09-24
I cant find modules. can I just create that file

a) add these lines to /etc/modules
             ieee80211_crypt_tkip
             ieee80211_crypt_ccmp
             b43
	

	b) add these lines to /etc/modprobe.d/blacklist.conf
		blacklist ndiswrapper
                blacklist wl

it comes with a error: You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

any idea how to over come this

matt

---

### Post by windom on 2009-09-25
You can create the file. To edit a system file you need to be acting as the administrator aka superuser. Use 'sudo nano ***filename***'.

Something tells me you are in a bit over your head...

---

### Post by pilot26 on 2009-09-25
well I am the only user for this computer so I should be the administrator right or do I need to set that up as well.

In the blacklist I did find

# replaced by b43 and ssb.
blacklist bcm43xx

and

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb

could this be my problem?
thanks windom for all of your help

Matt

---

### Post by Ayuthia on 2009-09-25
Before adjusting the /etc/modules and /etc/modprobe.d/blacklist.conf files, let's work on making sure that the right modules are loaded and things are working.  It will save some time in cleaning up those configuration files.

It looks like you have b43-fwcutter installed since it is showing wlan0 now.  Did you do the following after you installed b43-fwcutter:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo iwlist scan
```

If you still get no scan results, please post the results of:
```
lspci -nn
lshw -C network
dmesg|grep b43
```

Also are you using encryption (WEP/WPA/WPA2) or have a hidden ssid?  Do you know if there are any other wireless sites in the area besides yours?

---

### Post by pilot26 on 2009-09-25
when I run:
lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]


lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ba:02:e7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.104 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:ca:e3:0f:2e:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:2 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:d0:34:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


dmesg|grep b43
[ 5335.246408] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5335.246430] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[ 5335.345558] b43-phy0: Broadcom 4311 WLAN found



I know of other sites but when when I search for them it comes back no wireless network found

I have run 
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo iwlist scan
with 
sudo iwlist scan lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


thanks again for your help
Matt

---

### Post by Ayuthia on 2009-09-25
> **pilot26 said:**
> 
lshw -C network

  *-network:2 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:d0:34:88
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 
sudo iwlist scan 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

These two items are showing that the wireless card is not starting.  There were no warnings that the firmware is missing and that the card is turned off.  Do you have NetworkManager running?  If so, you might want to make sure that wireless is enabled.  That is the only thing that I can think of right now that could cause the Network is down message.

---

### Post by pilot26 on 2009-09-25
I am using WICD and it is turned on as far as I know 

thanks
Matt

---

### Post by Ayuthia on 2009-09-25
> **pilot26 said:**
> I am using WICD and it is turned on as far as I know 

thanks
Matt

Can you check in preferences to see if the wireless interfaces is set to wlan0 instead of eth1?

---

### Post by pilot26 on 2009-09-25
it is set to eth1.. how do I change it?

Matt

---

### Post by pilot26 on 2009-09-25
does it matter what the WPA supplicant driver is set to?

---

### Post by Ayuthia on 2009-09-25
To change eth1 to wlan0 in wicd, you just need to click on the icon in the system tray, go to preferences, under the Wireless Interfaces section in the General Settings tab, change it to wlan0.

If WPA supplicant is set to eth1, you will need to change it to wlan0 also.

---

### Post by pilot26 on 2009-09-25
WPA supplicant options are

wext
hostap
madwifi
atmel
ndiswrapper
ipw
ralink legacy

---

### Post by Ayuthia on 2009-09-25
> **pilot26 said:**
> WPA supplicant options are

wext
hostap
madwifi
atmel
ndiswrapper
ipw
ralink legacy

Sorry, it has been a while since I last used wpa_supplicant.  If it is not at wext already, it should be at wext.

---

### Post by pilot26 on 2009-09-25
I have done that but I still cant find any wireless networks

what else can I try

---

### Post by pilot26 on 2009-09-25
Bump

---

### Post by kevdog on 2009-09-25
sorry I'm jumping in on the conversation,

sudo iwlist scan

That's the command to see wireless networks.  You need to see them prior to connecting to them.

---

### Post by pilot26 on 2009-09-26
when I run sudo iwlist scan

I get

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by pilot26 on 2009-09-27
Bump

---

### Post by kevdog on 2009-09-27
Ok, so since you can't see anything, there is obviously a problem with your driver installation.

---

### Post by pilot26 on 2009-09-27
so what can I do to fix this problem

---

### Post by pilot26 on 2009-09-27
bump

---

### Post by pilot26 on 2009-09-27
bump

thank you for your help

---

### Post by kevdog on 2009-09-27
Did Ayuthia help you out in the beginning of this thread?  Something with the wl driver?

---

### Post by pilot26 on 2009-09-27
I have tried Ayuthia suggestions but have not been able to get it to work

---

### Post by kevdog on 2009-09-27
I can see your frustration, however reviewing the entire thread -- well its a nightmare.  You're not providing much information.  What are you using as a driver b43 or wl?  What does lshw -C network show for a driver?  What about dmesg and searching for the driver you are trying to load.

Need much more info!  

Also you could use the openfwwf driver (I think):
[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

can you also post
lspci -nnm

---

### Post by pilot26 on 2009-09-28
any more suggestions

thanks

---

### Post by pilot26 on 2009-09-28
BUMP

thanks for helping

---

### Post by pilot26 on 2009-09-28
the driver that I am using is Broadcom STA wireless driver



lspci -nnm


00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" -r10 "Gateway 2000 [107b]" "Device [0367]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a36]" "" ""
00:05.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a37]" "" ""
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]" -r80 -p10 "Gateway 2000 [107b]" "Device [0367]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]" -r80 -p10 "Gateway 2000 [107b]" "Device [0367]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]" -r80 -p20 "Gateway 2000 [107b]" "Device [0367]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "IXP SB400 SMBus Controller [4372]" -r83 "Gateway 2000 [107b]" "Device [0367]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 IDE Controller [4376]" -r80 -p82 "Gateway 2000 [107b]" "Device [0367]"
00:14.2 "Audio device [0403]" "ATI Technologies Inc [1002]" "IXP SB4x0 High Definition Audio Controller [437b]" -r01 "ATI Technologies Inc [1002]" "IXP SB4x0 High Definition Audio Controller [437b]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-ISA Bridge [4377]" -r80 "Gateway 2000 [107b]" "Device [0367]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-PCI Bridge [4371]" -r80 -p01 "" ""
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS482 [Radeon Xpress 200M] [5975]" "Gateway 2000 [107b]" "Device [0367]"
02:00.0 "Ethernet controller [0200]" "Marvell Technology Group Ltd. [11ab]" "88E8038 PCI-E Fast Ethernet Controller [4352]" -r14 "Gateway 2000 [107b]" "Device [0367]"
05:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Broadcom Corporation [14e4]" "Device [0465]"
08:09.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx12 Cardbus Controller [8039]" "Gateway 2000 [107b]" "Device [0367]"
08:09.1 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "PCIxx12 OHCI Compliant IEEE 1394 Host Controller [803a]" -p10 "Gateway 2000 [107b]" "Device [0367]"
08:09.2 "Mass storage controller [0180]" "Texas Instruments [104c]" "5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [803b]" "Gateway 2000 [107b]" "Device [0367]"


Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.13)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

When I run dmesg how do I find my driver, I am very new and dont know enough to know what I dont know. I hope that the info provided helps to know what i am doing wrong

thanks again
Matt

---

