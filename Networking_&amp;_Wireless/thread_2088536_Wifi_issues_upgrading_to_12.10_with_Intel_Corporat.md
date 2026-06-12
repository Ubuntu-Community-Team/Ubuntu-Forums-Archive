---
title: "Wifi issues upgrading to 12.10 with Intel Corporation PRO/Wireless 3945ABG"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by aconsuma on 2012-11-26
Hello,

I am a Linux newbie and upgraded to 12.10, but my wifi doesn't work properly.  It connects, but then will ask for re-authentication after 20 seconds.  I know very few commands, but from searching other posts I found some commands with results show below:

Thanks for the assistance!

**lspci -nn | grep -i network**

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

  	 	 	 	 	 	   **ifconfig**
 

 eth0      Link encap:Ethernet  HWaddr 00:e0:b8:ea:fd:29   
           inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::2e0:b8ff:feea:fd29/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:61066 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:46783 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:71591698 (71.5 MB)  TX bytes:7349207 (7.3 MB) 
           Interrupt:16  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:2594 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2594 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:275892 (275.8 KB)  TX bytes:275892 (275.8 KB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:1b:77:2f:39:4c   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 

 **iwconfig wlan0**
 

 wlan0     IEEE 802.11abg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
 

 **sudo lshw -C network**
 

   *-network                
        description: Ethernet interface 
        product: 88E8038 PCI-E Fast Ethernet Controller 
        vendor: Marvell Technology Group Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: eth0 
        version: 14 
        serial: 00:e0:b8:ea:fd:29 
        size: 100Mbit/s 
        capacity: 100Mbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:43 memory:d4000000-d4003fff ioport:2000(size=256) 
   *-network 
        description: Wireless interface 
        product: PRO/Wireless 3945ABG [Golan] Network Connection 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: wlan0 
        version: 02 
        serial: 00:1b:77:2f:39:4c 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-18-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg 
        resources: irq:44 memory:d6000000-d6000fff 
 

 **dmesg | grep iwl**
 

 [   22.662679] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s 
 [   22.662685] iwl3945: Copyright(c) 2003-2011 Intel Corporation 
 [   22.719832] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels 
 [   22.719839] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG 
 [   22.720062] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X 
 [   22.740401] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs' 
 [   23.677505] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9 
 

 **sudo rfkill list all**
 

 0: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no

---

### Post by aconsuma on 2012-11-26
[B]I also found these commands to find the kernel driver
[/B]

**lspci -vv -s 03:00.0 **
 

 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 
 	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection 
 	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+ 
 	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
 	Latency: 0, Cache Line Size: 64 bytes 
 	Interrupt: pin A routed to IRQ 44 
 	Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K] 
 	Capabilities: <access denied> 
 	Kernel driver in use: **iwl3945 **
 	Kernel modules: iwl3945 
 

 

 **modinfo iwl3945 **
 

 filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko 
 firmware:       iwlwifi-3945-2.ucode 
 license:        GPL 
 author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com> 
 version:        in-tree:s 
 description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux 
 srcversion:     810E48600D145BC020E8365 
 alias:          pci:v00008086d00004227sv*sd*bc*sc*i* 
 alias:          pci:v00008086d00004222sv*sd*bc*sc*i* 
 alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i* 
 alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i* 
 alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i* 
 alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i* 
 depends:        iwlegacy,cfg80211,mac80211 
 intree:         Y 
 vermagic:       3.5.0-18-generic SMP mod_unload modversions 686  
 parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int) 
 parm:           swcrypto:using software crypto (default 1 [software]) (int) 
 parm:           disable_hw_scan:disable hardware scanning (default 1) (int) 
 parm:           fw_restart:restart firmware in case of error (int)

---

### Post by aconsuma on 2012-11-28
**sudo iwconfig ** 
 wlan0     IEEE 802.11abg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
             
 lo        no wireless extensions.  
 eth0      no wireless extensions. 



I've read the above tells me my driver isn't talking to the Kerenel so** I need to reinstall a new driver**.  From Intel's website [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) I foundThere used to be a driver specific for the 3945 hardware (ipw3945 hosted on [ipw3945.sourceforge.net]("http://ipw3945.sourceforge.net/")). This project is deprecated, please use the iwlwifi driver instead. 

I am led to [https://backports.wiki.kernel.org/index.php/Main_Page ]("https://backports.wiki.kernel.org/index.php/Main_Page")and this is where I'm at/stuck.  I'll research some more but if anyone could assist I'd appreciate it!

Additionally, from some more digging I found my Kernel is 

  	 	 	 	     **uname -r ** 
 3.5.0-18-generic

---

### Post by aconsuma on 2012-11-28
Hello,

since my kernel is 3.5 I went to this website that had drivers for stable kernels.  [http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases)

Am I on the right track?  Do I just pick any driver?

---

### Post by steeldriver on 2012-11-28
I'm no expert on wireless issues but I'm not seeing anything in your lspci / iwconfig to say it's not finding a driver (that's not to say the driver it *is* finding is not broken of course)

Before taking the step to install other drivers can you have another look at dmesg, this time looking for messages related to the interface rather than specifically the driver? this may indicate why the connection is dropping:

```
dmesg | grep wlan0
```

---

### Post by aconsuma on 2012-11-28
Hello...thanks for the response.[B]

dmesg | grep wlan0[/B]

[   24.321501] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.321937] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9342.436052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by steeldriver on 2012-11-28
Hmmm... I wonder if disabling IPv6 would make any difference? [choose your wireless connection in the nm-applet, then Edit --> IPv6 Settings --> Method and select 'Ignore' from the dropdown ; then disconnect and reconnect - or restart the network-manager service]

---

### Post by ahallubuntu on 2012-11-28
What is the exact make/model of the wireless router you are trying to connect to?  What type of wireless security is it using?

By chance is WPS (Wireless Protected Setup) enabled on the router?  Try disabling it if you can, at least as a test.  I've had issues with Linux compatibility with WPS a few times and disabling WPS helped.

---

### Post by aconsuma on 2012-11-28
trying to figure out where network-manager-applet is located...standby

---

### Post by aconsuma on 2012-11-28
> **ahallubuntu said:**
> What is the exact make/model of the wireless router you are trying to connect to?  What type of wireless security is it using?

By chance is WPS (Wireless Protected Setup) enabled on the router?  Try disabling it if you can, at least as a test.  I've had issues with Linux compatibility with WPS a few times and disabling WPS helped.

It is a Verizon Actiontec M1424-WR Rev. C

I believe I am using WEP

---

### Post by aconsuma on 2012-11-28
> **steeldriver said:**
> Hmmm... I wonder if disabling IPv6 would make any difference? [choose your wireless connection in the nm-applet, then Edit --> IPv6 Settings --> Method and select 'Ignore' from the dropdown ; then disconnect and reconnect - or restart the network-manager service]

steeldriver,

I am not sure how to access the nm-applet.  I haven't had much luck googling it...I will try again tomorrow.  Thanks for the assistance.

---

### Post by steeldriver on 2012-11-28
nm-applet is the thing on the task bar where you set up / monitor your connections

maybe if you bump the thread tomorrow one of the wireless gurus will step in - I did some googling and noticed a number of issues posted about iwl3945 and various suggested fixes including playing with the disable_hw_scan and/or fw_restart parameters - no very definitive answers though

---

### Post by ahallubuntu on 2012-11-29
It appears this version of your modem/router doesn't have WPS built in, but you can verify:

[http://wlanbook.com/turning-off-wifi-protected-setup-wps-in-verizon-fios-mi424wr-wireless-routers/](http://wlanbook.com/turning-off-wifi-protected-setup-wps-in-verizon-fios-mi424wr-wireless-routers/)

FYI, WEP is not considered very secure these days whether it has anything to do with your wireless issue or not.  WPA2 personal with AES is considered and reliable.  WEP is pretty easy to crack.

If you have the ability to do this, I'd probably try removing all wireless security first and if by chance that works, switch to WPA2 security.  It is remotely possible there is some WEP issue (keys can be entered as HEX code or in a different form for WEP).

How do you configure the router?  Try the manual and go to page 13:

[http://onlinehelp.verizon.net/consumer/bin/pdf/VzMI424WRUserManualv4.pdf](http://onlinehelp.verizon.net/consumer/bin/pdf/VzMI424WRUserManualv4.pdf)

It's worth trying a few things with your router just to see if it changes your issue.

---

### Post by aconsuma on 2012-11-30
I called Verizon to verify that I have WEP.  I asked if I could use WPA2 but they said I'd need a new router.  This doen't make sense to me bc I can click on the wireless icon on the top and at the bottom select "Edit Connections...".  I can click on my wireless and select the Edit then Wireless Security and the Security dropdown has WPA2 Personal.

I am still unable to find the nm-applet and I don't have it on my task bar where you set up / monitor your connections.  I'll do some more searching tomorrow.  I still haven't figured out how to disabling IPv6.  When I click on the IPv6 Settings tab next to the Wireless Security tab I don't see anything filled in.

---

### Post by steeldriver on 2012-11-30
sorry the applet *is* the wireless icon - the 'IPv6 Settings' tab should be right next to the 'Wireless Security' tab where you can choose between WEP / WPA etc. - it should have a 'Method:' dropdown which you can change from 'Automatic' to 'Ignore'

---

### Post by ahallubuntu on 2012-11-30
Your router should at least support support WPA which should be much more secure than WEP.  Go to page 30 of the Verizon manual I linked to above to see how to change it.  It's fairly easy.  (Page 13 tells you how to login with your web browser so you can figure your router's settings).

Of course, you can always buy your own wireless router to use instead of the built-in wireless in your modem. Any modern wireless router has WPA2.  But - I digress, because this may not solve your problem at all, anyway.

What I was hoping to get you to do was switch to WPA (at least) because first that is more secure than WEP, second it MIGHT solve your problem if there's some issue with how the WEP key is used.  Or get rid of security entirely temporarily, just to see if it connects.  (If connection no better without any wireless security, WPA sure won't work any better.)   If you have only the one wireless device (laptop) this should be an easy thing to change.

---

### Post by aconsuma on 2012-12-01
> **steeldriver said:**
> sorry the applet *is* the wireless icon - the 'IPv6 Settings' tab should be right next to the 'Wireless Security' tab where you can choose between WEP / WPA etc. - it should have a 'Method:' dropdown which you can change from 'Automatic' to 'Ignore'

Thanks for the response.  I tried doing this, but when I changed to "ignore" I was unable to save because the save button was greyed out.  I don't think I have the IPv6 capability.  My computer is over 5 years old and is a Gateway MT 6840 Laptop.

---

### Post by aconsuma on 2012-12-01
> **ahallubuntu said:**
> Your router should at least support support WPA which should be much more secure than WEP.  Go to page 30 of the Verizon manual I linked to above to see how to change it.  It's fairly easy.  (Page 13 tells you how to login with your web browser so you can figure your router's settings).

Of course, you can always buy your own wireless router to use instead of the built-in wireless in your modem. Any modern wireless router has WPA2.  But - I digress, because this may not solve your problem at all, anyway.

What I was hoping to get you to do was switch to WPA (at least) because first that is more secure than WEP, second it MIGHT solve your problem if there's some issue with how the WEP key is used.  Or get rid of security entirely temporarily, just to see if it connects.  (If connection no better without any wireless security, WPA sure won't work any better.)   If you have only the one wireless device (laptop) this should be an easy thing to change.

ahallubuntu thanks for the response.  I agree with you that I can change to WPA2.  I would rather keep is as WEP for now and try to troubleshoot.  Interestingly enough I changed the security to "none" and my wireless is working now.  Before I would type in the wireless code and it would ask to re authenticate every 20 seconds but I've used this for 20 minutes with now issues.  

Shouldn't WEP be less buggy since is is less secure?  I would think WPA2 would be more finicky.  I'll try to move to WPA2 later today or tomorrow.  I need to coordinate with other people in the house.

Thanks!

---

### Post by aconsuma on 2012-12-01
So when I first started this mess I only saw Auto linksys and Auto 56VZ1 as my networks.  When I changed my security to "none" on the Auto 56VZ1 and I went back to check if the security was gone I saw another wireless network show up labelled. 56VZ1.  I've included a image of this in my post (i hope anyway).  When I click on this and select Edit and then go to the Wireless Security tab on the far right I see my WEP security is back on (see other thumbnail).  I believe this is the wireless network I am on now.  I don't know how this was created or how I got switched from the Auto 56VZ1 (that still has "None" as its security) to the new 56VZ1.  

Long story short I think I am running on 56VZ1 with WEP security.  I logged into my Verizon Router and checked the Wirless security and it says YES.  

Does this make sense?

Thanks again

---

### Post by aconsuma on 2012-12-01
Hi All...I think its working!  I called Verizon to verify and they show my 56VZ1 as having WEP activated.  I'll update to WPA2 tomorrow.

```
**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:ea:fd:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128137 (128.1 KB)  TX bytes:128137 (128.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:2f:39:4c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe2f:394c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
  **        RX bytes:57496662 (57.4 MB)  TX bytes:4802655 (4.8 MB)**

**I didn't see any bytes in the above bold section when I first started troubleshooting.**

```
**iwconfig wlan0**
```

wlan0     IEEE 802.11abg  ESSID:"56VZ1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:EA:51:3B   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1234   Missed beacon:0

```
**sudo lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ea:fd:29
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d4000000-d4003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:2f:39:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-19-generic firmware=15.32.2.9 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d6000000-d6000fff


```
**dmesg | grep iwl**
```

[   23.611576] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   23.611581] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   23.652446] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   23.652452] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   23.652625] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   23.969107] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   24.005823] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

---

### Post by ahallubuntu on 2012-12-01
When you change settings in your router/modem via a web browser, you have to do "OK" or "Apply" to set them.  If you UN-check WEP and "OK" or "Apply" (or "Save" or whatever), the modem/router should reboot or change the settings.

You may have to delete the wireless network in Ubuntu as it will try to connect with your old WEP password.  Sometimes Ubuntu will "see" two networks for a short time because it still remembers the old one for a short time.  Eventually you'll have just one again, if you see two briefly.

If it works WITHOUT security, then I highly, highly suggest changing it again to WPA.    This is far more secure than WEP and may actually work perfectly and you can put this problem to bed until you get a WPA2-capable router.  Again, WEP occasionally has weird issued due to how the passcodes can be represented.  WEP is obsolete and ancient; I don't know how else to convince you to abandon this old standard that may have caused you a few hours of trouble already in favor of WPA which is much better, even if not as secure as WPA2.

FYI, while you are logged into Verizon wireless settings, you can also change the  name of your wireless network from the computer gibberish "56VZ1" to a human-readable name like "MyWirelessNetwork" or whatever makes sense.  You might choose something unique but doesn't identify the network to your neighbors explicitly as yours.

---

