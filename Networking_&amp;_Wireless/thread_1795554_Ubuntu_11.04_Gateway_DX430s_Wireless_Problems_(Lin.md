---
title: "Ubuntu 11.04/ Gateway DX430s/ Wireless Problems (Linksys)"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by chrisjoplin on 2011-07-02
Today I repartitioned my desktop to Ubuntu and cannot access my wireless internet. The house I live in is old and the only way to use a hardline ethernet cable would be to move the computer down to the basement with the wireless router (only one ethernet port in the house).
 
I have a laptop with perfect wireless connection but my desktop with Ubuntu cannot detect the wireless network and even when I try to type the specs from the wireless network into the appropriate places it still cannot connect. Is there a driver I need to install in order to have the computer recocnize the network?
 
I tried piggy-backing the connection through my laptop to the desktop but did not have much luck and i was wondering if there was anything I should do.
 
Again, I am a day 1 user of Ubuntu and generally I know my computer stuff, but being a windows user all my life and not knowing the problem with my computer I was in need of some help.
 
Any reccomendations would by much appriciated

---

### Post by MaindotC on 2011-07-03
Resolving wireless issues are a series of steps to determine the root cause.  The first place to start is the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---

### Post by chrisjoplin on 2011-07-03
I went through some of the trouble shooting with no luck. I used "nm-tool" and received:
 
Type: 802.11 WiFi
Driver: b43
State: unavailable
Default: no
 
Then under capabilities/wireless properties I get "yes" for WEP, WPA, WPA2 encryption.
 
After seeing that it was unavailable I moved to the troubleshooting guide. 
 
Make: Gateway
Model: DX430S
S/N: 0038903389
 
I dont have the original box for the machine, someone in my family had thrown it away previously and the driver discs that came with it could not be found. I assume that i could download new drivers if necessary. 
 
I then typed: "lshw -C network" and recieved:
 
*-network DISABLED
         description> Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:14:a5:c8:d6:10
         capabilities: ethernet physical wireless
         configuration: broadcast=yes  driver=b43  driverversion=2.6.38-8-generic  firmware=N/A  multicast=yes  wireless=IEEE 802.11bg
 
 
 
Past this point im not sure what to do because it continues on to PCI and USB and im not sure what the next step should be

---

### Post by MaindotC on 2011-07-04
That's ok about the disc - one thing you'll learn about modules (Linux term for drivers) is that typically they are already installed (like b43 is) or you download and install them.

From searching the source code it seems the "Unavailable" message has a few meanings but most of them indicate that the device is now being managed by network-manager.  The b43 driver is loaded - not precisely certain if that's the best driver for your card but it's there and detected.  The lshw output is saying your device is disabled.

I successfully brought down my wired interface with the command:
```
dvorjak@dvorjak:~$ sudo lshw -C network
[sudo] password for dvorjak: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:b7:39:1f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)
dvorjak@dvorjak:~$** sudo ifconfig eth0 down**
dvorjak@dvorjak:~$ sudo lshw -C network
  ***-network DISABLED**      
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
     
***removed for brevity *****
```

See if you can bring up your interface with:
```
sudo ifconfig wlan0 up
```

---

### Post by chili555 on 2011-07-04
I don't want to step on MaindotC, but I suspect this is the problem:> logical name: wlan0
serial: 00:14:a5:c8:d6:10
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=[COLOR="Red"]b43[/COLOR] driverversion=2.6.38-8-generic [COLOR="Red"]firmware=N/A[/COLOR] I think chrisjoplin needs b43-fwcutter or firmware-b43-installer; I think it does no harm to install both.

---

### Post by MaindotC on 2011-07-04
> **chili555 said:**
> I don't want to step on MaindotC, but I suspect this is the problem:I think chrisjoplin needs b43-fwcutter or firmware-b43-installer; I think it does no harm to install both.

Agreed - installing as many as drivers as you like is not an issue, but you have ensure your operating system is picking the correct one.  However, I do not believe the "firmware=N/A" message is of any concern - especially seeing as how I have the same message on several machines and the Changelog indicates a reason will be stated for any missing firmware errors.

---

### Post by chili555 on 2011-07-04
```
$ modinfo b43
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/b43/b43.ko
[COLOR="Red"]firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw[/COLOR]
firmware:       FW13
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     75BEA90BE9363EF1FF3ECE8
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,cfg80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
```Do you think dmesg suggests he's missing firmware?

---

### Post by MaindotC on 2011-07-04
> **chili555 said:**
> Do you think dmesg suggests he's missing firmware?

I don't know the dmesg output to which you are referring.  To my knowledge he hasn't pasted anything yet.

---

### Post by chili555 on 2011-07-04
> **MaindotC said:**
> I don't know the dmesg output to which you are referring.  To my knowledge he hasn't pasted anything yet.Quite correct. So why do you believe firmware is no concern?

---

### Post by chili555 on 2011-07-04
@chrisjoplin--

Please open Applications > Terminal and run and post:```
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by chrisjoplin on 2011-07-04
when i typed "dmesg \ grep b43" into the terminal i recieved
"dmesg [-c] [-n level] [-r] [-s bufsize]"
 
im not sure what that means. im not great with code so any advice would be great, this help is wonderful though, i really appriciate it.
 
News though, in case it helps: i currently have the desktop hardwired in the basement so it does have an ethernet connection as of now just in case it makes it easier to fix its wifi problems

---

### Post by chili555 on 2011-07-04
> when i typed "dmesg \ grep b43" into the terminal i recieved
"dmesg [-c] [-n level] [-r] [-s bufsize]"It's not dmesg \ grep b43, it''s:```
dmesg [COLOR="Red"]**|**[/COLOR] grep b43
```It's | not \.

---

### Post by chrisjoplin on 2011-07-04
my apologies, i typed in the code correctly this time and recieved:
 
[LEFT][    0.951948] b43-pci-bridge 0000:06:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.281403] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   12.408514] Registered led device: b43-phy0::tx
[   12.408545] Registered led device: b43-phy0::rx
[   12.408575] Registered led device: b43-phy0::radio
[   12.739664] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   12.739669] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   12.739673] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/LEFT]
 
Im assuming i should just follow this link and grab the right firmware? but i did not want to do anything out of step or wrong so whats the next step?

---

### Post by chili555 on 2011-07-05
> ERROR: Firmware file "b43-open/ucode5.fw" not foundThe driver b43 requires firmware that is not provided by default because it's proprietary. There are two packages that you can install that go out on the internet and download and install the firmware. Please hook up a wired ethernet connection and open a terminal and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After that's done, detach the cable and reboot. Your wireless should be working.

---

### Post by chrisjoplin on 2011-07-05
i typed in the code and immedietly everything i needed was installed and as soon as the terminal finished my wifi showed up and told me i was connected. 
 
Thank you so much for your help!

---

### Post by chili555 on 2011-07-05
I'm glad it's working! Please use the thread tools at the top and mark Solved.

Have fun!

---

### Post by MaindotC on 2011-07-06
> **chili555 said:**
> The driver b43 requires firmware that is not provided by default because it's proprietary...

Touche`

---

