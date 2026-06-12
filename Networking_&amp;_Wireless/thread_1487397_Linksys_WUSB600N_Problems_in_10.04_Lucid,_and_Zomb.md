---
title: "Linksys WUSB600N Problems in 10.04 Lucid, and Zombies"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Dev0 on 2010-05-18
[B]UPDATE: 
[/B]
Compiling the driver from source doesn't seem to work on Maverick. Some have had luck with blacklisting alone, as mentioned below.

[I]See post #34 on page 4 of this thread for a partially automated solution to the rt2870 problem in Lucid Lynx 10.04: [http://ubuntuforums.org/showthread.php?p=9534492#post9534492](http://ubuntuforums.org/showthread.php?p=9534492#post9534492)
or check out post #43 on page 5 for another: [http://ubuntuforums.org/showthread.php?p=9725320#post9725320](http://ubuntuforums.org/showthread.php?p=9725320#post9725320)[/I]

I know this is long.  Bear with me, please.

There are lots of threads out there about the Linksys WUSB600N, but most are [FONT=Impact]living dead [FONT=Verdana]threads[/FONT][/FONT] explaining how to get the card working in Hardy or Ibex.  How about some fresh (or at least, re-confirmed) methods?  I **didn't** need to use ndiswrapper, compile my own drivers, or <ugh> recompile the kernel to get the rt2870 working in 32-bit 9.10 Karmic.  Why should it be so difficult to get the same working in Lucid?

My tried and true method for 9.10 -as stated below- doesn't work for the new release.  It seems that there aren't m*any* solved threads about getting the card up and running in **Lucid**, so here goes:


I have a Linksys WUSB600n v1 that works perfectly in 9.10 with only the minor modification posted by chili555 in this thread" [HTML]http://ubuntuforums.org/showthread.php?t=1423100[/HTML]That solution was:
"
```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```"

I've tried the same in a clean install of 32-bit 10.04, but no connection is made and a prompt comes up every few minutes asking for the password. I've used the included rt2870 driver in 9.10 without problems. My wireless-N network uses WPA2 personal encryption.

Though there have been no issues with it in 9.10, it may be possible that the WPA2 encryption is causing the connection problem in 10.04.  Lithaerien posted a similar problem in his own thread here: [HTML]http://ubuntuforums.org/showthread.php?t=1468938&highlight=wusb600n[/HTML]Blacklisting all other 10.04 included rt drivers does not solve the issue either.

The usb id of my adapter, per lsusb, is ID 1737:0071
I used ```
lsmod | grep -e rt2 -e rt3
```to see what drivers load in both versions of Ubuntu.  The results are:
for 9.10:     rt2870sta             488820  1 
for 10.04: rt2870sta             461811  1 

It would be great to find another simple way of restoring functionality to a device that worked perfectly in an older release.

Ideas?

---

### Post by pytheas22 on 2010-05-19
You might have better luck connecting using wicd instead of NetworkManager.  I've often seen NM have issues with WPA for various strange reasons; wicd's approach to dealing with WPA is totally different and sometimes works better.  You can install wicd using the Software Center or with:
```

sudo apt-get install wicd
```

If wicd doesn't help, I would next try compiling the rt2870sta module from source using the code available at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  It's possible that that version will work better than the one built by Ubuntu.

You could also try ndiswrapper, which should also work.

You seem pretty familiar with Ubuntu, but if you need more specific instructions on how to do any of the above let me know.

---

### Post by Dev0 on 2010-05-21
Thanks for the inhumanly fast response, pytheas22!  wicd installed and initialized without a hitch, but ran into what I assume to be the same problem as Network manager; I received a "Bad password" message, even though I had a Windows 7 laptop connected to the same network with the same pw.  It appeared that the problem was with how the kernel/driver was handling the WPA encryption, not NM.

I took up your second suggestion, though I'd already tried compiling the driver more than a few times.  I'm posting now from 10.04 with my WUSB600n v1, though it took some tweaking to get here.  I had the fortune of stumbling across this guide by Chris Barker:
[COLOR=Blue][http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)[/COLOR]

In the guide he walks through how to get the rt2860 up and running in 10.04, and specifies a line of code that has not been mentioned in any other post I've read; I believe this line (step 3 in my guide below) is what enabled my rt2870 chipset to work.  The rt2860 is an older cousin of the rt2870, and I found what I think are easier ways to do some things, so I have taken the liberty of modifying his instructions and posting them here.  Full credit to Mr. Barker for figuring it out first, though.

To any n00bies here, the WUSB600n v1 by Linksys/Cisco uses the rt2870 chipset, and Ubuntu needs the drivers to the chipset in order to get the card working.  Type "lsusb" into the terminal, which can be found under Applications/Accessories in the main menu on  the top left of the screen.  If you see "ID 1737:0071 Linksys", then you're in the right place!

**[FONT=Comic Sans MS][SIZE=4]One Way to get the rt2870 (WUSB600n v1, lsusb ID: 1737:0071) working in 10.04 Lucid Lynx:[/SIZE][/FONT]**
[SIZE=2]NOTE: There is a better way to install the modified driver, explained in post #34 on page 4 of this thread: [http://ubuntuforums.org/showthread.php?t=1487397&page=4](http://ubuntuforums.org/showthread.php?t=1487397&page=4)[/SIZE]

1. Go to [COLOR=Blue][http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)[/COLOR] as pytheas22 suggested and download the source code called "RT2870USB(RT2870/RT2770)", which is version 2.3.0.0 at the time of writing.  You'll have to enter a name and email address, but no follow-up info is requested.

To make things easier, stick the file right in your Downloads folder.  Right click the file and select "Extract here".  That leaves you with the folder "RT2870_LinuxSTA_V2.3.0.0".  Do yourself a favor; right click and rename it "RT2870" so that you don't have to type as much working in the terminal later.

The path for this source code folder should now be "/home/{your username}/Downloads/RT2870".  From now on, I'll write paths starting in the RT2870 folder.  When you see "~RT2870/os/linux/config.mk", the whole path is actually "/home/{your username}/Downloads/RT2870/os/linux/config.mk".

2. Open up the source code file in "~RT2870/os/linux/config.mk".  Find these two lines (should be the fourth and fifth lines in black; they are separated by a comment line in blue) and make sure they both have "=y" at the end as follows:    
```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```You should only have to change two "=n" to "=y" at most. Nothing too difficult here.  Save and close the file.

3. Open ~rt2870/common/cmm_wpa.c - For gedit to open the file, I had to change the character encoding to Western in the drop down menu.  In gedit, do a control+f to open up the Find menu.  Search for
```
 MIX_CIPHER_NOTUSE
```Highlight the MIX_CIPHER_NOTUSE and copy/paste this code into its place:
```
WPA_TKIPAES_WPA2_TKIPAES
```Save and exit. Navigate this window back to ~RT2870 and leave it open.

4. Open Terminal.  Navigate to the source code folder in the terminal by using cd, the change directory command.  Be sure to put your username in where I have creatively placed {your username}!
    cd /home/{your username}/Downloads/RT2870
Execute the following commands one at a time. Let each finish before starting the next. I saw some warnings about frame sizes while "sudo make" was running, but it executed correctly.

```
sudo make
sudo make install
sudo ifconfig wlan0 down
sudo rmmod rt2870sta
```5. Cool beans - Driver compiled!  We need to rename the driver included with the kernel so it doesn't interfere with the one we just made.  Open **another** terminal window and execute the following, which runs a superuser browser called Nautilus:
    ```
sudo nautilus
```In the window that pops up, click "File System" in the left pane, then proceed to this directory: 
"lib/modules/{**current/highest** kernel number, as in 2.6.32-22-generic}/kernel/drivers/staging/rt2870".
In that folder is the old driver.  Right click and rename it **rt2870sta.ko.dist** so it wont be recognized.

6. Now, in the non-nautilus window you still have open from step 3, navigate to the os/linux folder and drag+drop the file named **rt2870sta.ko** into the Nautilus window - the same folder in which you just renamed the old driver.  Now the kernel has a permanent copy of the driver we just compiled, and the included driver is preserved but unrecognizable to Ubuntu.

7. We have to tell Ubuntu to load our driver at startup, so use
    ```
gksudo gedit /etc/modules
```and add ```
rt2870sta
``` at the end of the file.  Save and close.

Reboot.  Enter your password into the startup prompt.  Use network manager or wicd, as pytheas22 mentioned, and connect to your wireless network.  Success! (Hopefully)

Let me know if something needs clarifying or if the guide worked/didn't work for anyone.  Thanks again to pytheas22 for getting the train rolling :)

---

### Post by mizunoX on 2010-05-23
Hi, thanks for the guide.

I presume that we will need to recompile the driver each time we receive a kernel update - correct?

---

### Post by pytheas22 on 2010-05-24
> I presume that we will need to recompile the driver each time we receive a kernel update - correct?

I can't speak from experience, but I would think so.  Dev0 might be able to say for sure.

---

### Post by Dev0 on 2010-05-24
> **mizunoX said:**
> 
I presume that we will need to recompile the driver each time we receive a kernel update - correct?

Hey mizunoX!  I believe the first Ubuntu forum post I ever read was your "**Linksys WUSB600N working in hardy and ibex[B]"**[/B].

You presume correctly; at the moment, the guide will only help compile a driver for the current kernel.  An update from the clean install kernel 2.6.32-21 to the latest 2.6.32-22 makes a whole new /lib/modules directory, which "reinstates" the unusable included driver.

The only way I know of not having to recompile the driver every time is by making a script to do it automatically.  I'll be working on one soon, but no guarantees yet.  

If anyone knows another way to automatically reinstall a manually compiled driver after a kernel update, please share!

---

### Post by star_scream_2002 on 2010-05-25
[FONT=Courier New][SIZE=2]Hi all,

I have [/SIZE][/FONT][FONT=Courier New][SIZE=2]successfully managed to connect to our home wireless network by following these steps.

I'm a definite Noob here with Linux (first time ever messing with Linux) but Dev0 pretty much got the info right thanks to his resources as well.  I mean no disrespect at all to any of the contributors in my correction (for without them I would not be able to be successful in this matter), but only to help those who need to correctly connect wirelessly.

I followed Dev0's steps to the "T" in this thread

HOWEVER

in Step 4 there is one entry in Terminal that caused me an error.

The Very last entry in Terminal:[/SIZE][/FONT]
[FONT=monospace]
..............................
sudo rmmod rt2860sta
..............................

[FONT=Courier New][SIZE=2]All I did was change it to this:[/SIZE][/FONT]

..............................
sudo rmmod rt2870sta
..............................

[FONT=Courier New][SIZE=2]Meaning ALL I did was change the "6" to a "7"


After following Dev0's Every step before and after (this correction), I was 100% successful.
So, Readers, Please follow Dev0's steps except for my tiny contribution.

I assure you it works Completely.

Thanks Dev0 and all the contributors who helped steer you and myself in the correct direction.[/SIZE][/FONT]
[/FONT]

---

### Post by Dev0 on 2010-05-25
> **star_scream_2002 said:**
> [FONT=Courier New][SIZE=2]
The Very last entry in Terminal:[/SIZE][/FONT][FONT=monospace]
..............................
sudo rmmod rt2860sta
..............................
[FONT=Courier New][SIZE=2]All I did was change it to this:[/SIZE][/FONT]
..............................
sudo rmmod rt2870sta
..............................
[FONT=Courier New][SIZE=2]Meaning ALL I did was change the "6" to a "7"[/SIZE][/FONT]
[/FONT]

That one slipped by me, I've made the change to the guide.  Thanks for the edit, star_scream_2002, and thanks for letting everyone know it worked for you!

---

### Post by dtra on 2010-05-28
Hi
I followed the instructions to the letter...
I just got this Linksys WUSB600n adapter, but I can't get it to work
I've tried plugging it into a windows machine, and it installed and the lights came up, so I know it should work

lsusb gives me
Bus 001 Device 002: ID 1737:0079 Linksys
I have a wireless card in the machine at the moment, so then there is a wlan0, if I remove this card, then I don't have a wlan0 interface, so that ifconfig wlan0 down step gives me an error
and then the rmmod rt2870sta step says
ERROR: Module rt2870a does not exist in /proc/modules

So Network Manager doesn't even give me the option to connect to a wireless network without the card (g support only), like the driver isn't loaded at all.
lsmod | grep -e rt2 -e rt3
rt2870sta             555601  0

anything else I can try? I started from "One Way to get the rt2870 working in 10.04 Lucid Lynx:", should I have started earlier?

dave

---

### Post by pytheas22 on 2010-05-28
**dtra**: I googled your lsusb output and it looks like you have  WUSB600Nv2, while the other posters in this thread have a WUSB600Nv1.  According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165"), the v2 device won't work with the rt2870 driver.

However, users in that bug report report success using the rt3572 driver available from Ralink's website.  This driver is not available in Ubuntu by default, but you can install it manually.  See post #38 in particular for instructions on how to do that.  Note that, as explained in post #38, you have to make a few minor modifications to the source code before compiling and installing the driver.

The instructions in post #38 of the bug report might be hard to follow if you don't have a lot of Linux experience.  If you need a more user-friendly list of steps, let me know and I'll write out more exactly what you need to do to install the driver.

If you are able to install the driver without any errors but it still doesn't solve your problem, please post the output of these commands:
```

lshw -C Network
dmesg | grep -e rt2 -e rt3 -e wlan
lsmod | grep rt
```

---

### Post by dtra on 2010-05-28
thanks pytheas
that got it going, except it won't connect to the 5Ghz band
I'm pretty sure it's not too far away, pretty much the next room, when I try to connect to the 5Ghz, it just sits there with the blue light on (not flashing)
I ran the commands as suggested

```

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0c:6e:03:c0:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 multicast=yes
       resources: irq:19 ioport:8800(size=256) memory:ad000000-ad000fff memory:bffe0000-bfffffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:25:9c:f0:c0:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 multicast=yes wireless=Ralink STA
dmesg | grep -e rt2 -e rt3 -e wlan
[   15.925602] usbcore: registered new interface driver rt2870
[   16.040702] Error: Driver 'rt2870' is already registered, aborting...
[   16.040752] usbcore: error -16 registering interface 	driver rt2870
[   19.481578] <==== rt28xx_init, Status=0
[  913.937862] <==== rt28xx_init, Status=0
lsmod | grep rt
rt3572sta             609615  1 
gameport                9089  2 ns558
parport_pc             25962  1 
agpgart                31724  3 ttm,drm,sis_agp
parport                32635  3 ppdev,parport_pc,lp

```

---

### Post by star_scream_2002 on 2010-05-28
Yeah, I forgot to mention I am using WUSB600N V1.
 
dtra:
 
I'm glad you got it up and running...
 
Mine is still going strong, even after having to **re-work** Dev0's steps after Lucid Lynx did it's normal updates.

---

### Post by pytheas22 on 2010-05-29
**dtra**: please post the output of this command:
```

sudo iwlist scan
```

and let me know the name of the network you're trying to connect to.

Also, which application are you using to try to connect?  Are you using NetworkManager, which ships by default with Ubuntu, or something else?

---

### Post by dtra on 2010-05-29
```

sudo iwlist scan
[sudo] password for dtra: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:26:F2:F2:CB:83
                    Protocol:802.11b/g/n
                    ESSID:"homenet"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:57/100  Signal level:-67 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```
What do you mean by "name of the network"? is that just the SSID?

Yeah, I'm just using Network Manager, I tried WICD once, but didn't really like it, plus I'm not sure that I got it to work :).

---

### Post by pytheas22 on 2010-05-30
Yes, by network name I just mean the SSID.  I assume it's homenet since that looks like the only network in range.

The settings on your network look relatively standard, so I'm not positive why NetworkManager won't connect.  It could be worth giving wicd a try, just in case that works better.

You could also try changing the settings on your router; for example, disable 11n mode, change the channel or disable security entirely for a temporary period just to see if it allows you to connect.  That will help to narrow down the causes of what could be wrong, and we can proceed from there.

---

### Post by dtra on 2010-05-30
thanks
wicd, was no better (it wouldn't even connect to G), I'll try turning off wpa2, and turning broadcasting on, to see if it even shows up tomorrow

---

### Post by dtra on 2010-05-31
I don't know, I don't think it's working properly, I tried without security, broadcasting the SSID, and even then, Ubuntu wouldn't find the N network.
Even in Windows, it wouldn't connect to the N network. I think I'll probably return it, and just go back to my old adapter, if I can use G, that's fine.

Thanks for your help though

---

### Post by pytheas22 on 2010-05-31
If it wouldn't connect to 11n networks in Windows, that's strange.  There's a possibility we could still get it to work in Ubuntu using ndiswrapper rather than the driver from Ralink.  Let me know if you want to take that approach.  Otherwise, I'll assume you ended up just returning the adapter for one that works in Windows and Linux.

---

### Post by dtra on 2010-05-31
OK, thanks
I'm going to contact linksys tech support and see if I can get it working in Windows first (which I have to do to make sure it works or not, so that I can return it). If I can get it working in Windows, then I'll be back here looking for assistance in Ubuntu ;).

---

### Post by ReginaldPerrin3 on 2010-06-21
Now this is interesting.  I have just upgraded from 9.04 to 9.10, then immediately to 10.04. As expected, my WUSB600N v1 didn't work. I followed all the same steps I took to get it working properly in 9.04, to no avail. I followed all the instructions in this forum that I could find, and now Network Manager won't show the adapter, but WifiRadar and Wicd does! They both see all the 2.4GHz and 5GHz networks around, but attempting to connect using them results in either the 'connecting' screen showing but no connection made, or, as in the case of Wicd, it freezes the system requiring a hard reboot. Any reason why Network Manager won't show ra0? Is it only looking for something called wlan0? I would like to connect, obviously, but this is now getting to be a headache. Any help?

---

### Post by pytheas22 on 2010-06-21
> ReginaldPerrin3: it's strange that NetworkManager doesn't recognize the interface, and that using it in Wicd causes a hard freeze.  What is the output of these commands:
```

cat /etc/NetworkManager/nm-system-settings.conf
ifconfig
sudo iwlist scan
dmesg | grep -e wlan -e rt -e ra
lshw -C Network
```

---

### Post by ReginaldPerrin3 on 2010-06-22
Thanks for replying. I managed to kill Ubuntu (wouldn't even boot properly!), so I have done a clean install of 10.04 64Bit from disc. I have done all updates from the Update Manager, then added the Medibuntu repository, then added Ubuntu Tweak. These are the only changes from stock.
The network manager recognises the WUSB600N immediately, and shows all the networks properly, including the 5GHz ones.
When trying to connect, the Network Manager correctly asks for the WPA2 PSK, but after that, it will not connect. Just sits there trying to get an IP address.
I know the DHCP server is working properly, as other systems (Win7) will connect and get one.

cat /etc/NetworkManager/nm-system-settings.conf
ifconfig
sudo iwlist scan
dmesg | grep -e wlan -e rt -e ra
lshw -C Network
testrig4ub64@testrig4ub64-desktop:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
testrig4ub64@testrig4ub64-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:e4:be:76  
          inet addr:132.181.12.139  Bcast:132.181.15.255  Mask:255.255.248.0
          inet6 addr: fe80::219:d1ff:fee4:be76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5314060 (5.3 MB)  TX bytes:410049 (410.0 KB)
          Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:ea:61:73  
          inet6 addr: fe80::21e:e5ff:feea:6173/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4147 (4.1 KB)  TX bytes:588 (588.0 B)

testrig4ub64@testrig4ub64-desktop:~$ sudo iwlist scan
[sudo] password for testrig4ub64: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:33:E2:86:90
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key: on
                    ESSID:"Cisco1252"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000148986bb11
                    Extra: Last beacon: 1310ms ago
                    IE: Unknown: 0009436973636F31323532
                    IE: Unknown: 01088C9298A4B0C8E0EC
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3D162C0D0400000000000000000000000000000000000000
                    IE: Unknown: 851E000090000F00FF0319006170000000000000000000000000000000000031
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 02 - Address: 00:12:44:B5:8C:22
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=61 dBm  
                    Encryption key: on
                    ESSID:"UCwireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000562134e046
                    Extra: Last beacon: 1370ms ago
                    IE: Unknown: 000A5543776972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 03 - Address: 00:12:44:B1:8C:42
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key: on
                    ESSID:"UCwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000562120dec9
                    Extra: Last beacon: 2650ms ago
                    IE: Unknown: 000A5543776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 04 - Address: 00:12:44:B0:FE:52
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=63 dBm  
                    Encryption key: on
                    ESSID:"UCwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050126beae6
                    Extra: Last beacon: 2330ms ago
                    IE: Unknown: 000A5543776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 05 - Address: 00:12:44:B0:FE:53
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-190 dBm  
                    Encryption key: on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050126de578
                    Extra: Last beacon: 2330ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 06 - Address: 00:12:44:B0:FE:51
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=63 dBm  
                    Encryption key: off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000501269c20e
                    Extra: Last beacon: 2350ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 07 - Address: 00:24:C4:o2:93:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-188 dBm  
                    Encryption key: on
                    ESSID:"UCwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019205bf488a
                    Extra: Last beacon: 2170ms ago
                    IE: Unknown: 000A5543776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E150095000F00FF0319004D4143532D6C766C2D322D535700000009000036
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 08 - Address: 00:12:44:B5:8C:23
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=61 dBm  
                    Encryption key: on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005621368077
                    Extra: Last beacon: 1390ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 09 - Address: 00:12:44:B1:8C:43
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=61 dBm  
                    Encryption key: on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000562122dffa
                    Extra: Last beacon: 2650ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 10 - Address: 00:12:44:B0:FE:50
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key: off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000501268318c
                    Extra: Last beacon: 2320ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
          Cell 11 - Address: 00:24:C4:o2:93:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-188 dBm  
                    Encryption key: off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019205bea997
                    Extra: Last beacon: 2190ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E150095000F00FF0319004D4143532D6C766C2D322D535700000009000036
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 12 - Address: 00:24:C4:o2:93:03
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-189 dBm  
                    Encryption key: on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019205bea978
                    Extra: Last beacon: 2160ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E150095000F00FF0319004D4143532D6C766C2D322D535700000009000036
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 13 - Address: 00:12:44:B5:8C:20
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=62 dBm  
                    Encryption key: off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005621303044
                    Extra: Last beacon: 1420ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050401020000
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I am trying to connect to Cell 01.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
testrig4ub64@testrig4ub64-desktop:~$ dmesg | grep -e wlan -e rt -e ra
[    0.000000] KERNEL supported cpus:
[    0.000000] MTRR fixed ranges enabled:
[    0.000000] MTRR variable ranges enabled:
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] No NUMA configuration found
[    0.000000] Zone PFN ranges:
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 7f000000 (gap: 7f000000:80e00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Hierarchical RCU implementation.
[    0.000000] Fast TSC calibration using PIT
[    0.020007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4262.07 BogoMIPS (lpj=21310380)
[    0.020039] Security Framework initialized
[    0.022196] mce: CPU supports 6 MCE banks
[    0.033100] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033105] ftrace: allocating 22518 entries in 89 pages
[    0.310721] Trying to unpack rootfs image as initramfs...
[    0.310721] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.310721] PCI: Using configuration type 1 for base access
[    0.323897] ACPI: (supports S0 S3 S4 S5)
[    0.323953] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.332825] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.332885] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.332914] pci 0000:00:03.2: reg 10 io port: [0x3160-0x3167]
[    0.332918] pci 0000:00:03.2: reg 14 io port: [0x317c-0x317f]
[    0.332923] pci 0000:00:03.2: reg 18 io port: [0x3158-0x315f]
[    0.332928] pci 0000:00:03.2: reg 1c io port: [0x3178-0x317b]
[    0.332932] pci 0000:00:03.2: reg 20 io port: [0x3120-0x312f]
[    0.332975] pci 0000:00:03.3: reg 10 io port: [0x3150-0x3157]
[    0.333073] pci 0000:00:19.0: reg 18 io port: [0x30c0-0x30df]
[    0.333106] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.333148] pci 0000:00:1a.0: reg 20 io port: [0x30a0-0x30bf]
[    0.333193] pci 0000:00:1a.1: reg 20 io port: [0x3080-0x309f]
[    0.333292] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.333374] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.333436] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.333501] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.333564] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.333627] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.333691] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.333739] pci 0000:00:1d.0: reg 20 io port: [0x3060-0x307f]
[    0.333784] pci 0000:00:1d.1: reg 20 io port: [0x3040-0x305f]
[    0.333831] pci 0000:00:1d.2: reg 20 io port: [0x3020-0x303f]
[    0.337049] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.337225] pci 0000:00:1f.2: reg 10 io port: [0x3148-0x314f]
[    0.337231] pci 0000:00:1f.2: reg 14 io port: [0x3174-0x3177]
[    0.337236] pci 0000:00:1f.2: reg 18 io port: [0x3140-0x3147]
[    0.337241] pci 0000:00:1f.2: reg 1c io port: [0x3170-0x3173]
[    0.337247] pci 0000:00:1f.2: reg 20 io port: [0x3110-0x311f]
[    0.337252] pci 0000:00:1f.2: reg 24 io port: [0x3100-0x310f]
[    0.337271] pci 0000:00:1f.2: PME# supported from D3hot
[    0.337309] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
[    0.337346] pci 0000:00:1f.5: reg 10 io port: [0x3138-0x313f]
[    0.337352] pci 0000:00:1f.5: reg 14 io port: [0x316c-0x316f]
[    0.337357] pci 0000:00:1f.5: reg 18 io port: [0x3130-0x3137]
[    0.337362] pci 0000:00:1f.5: reg 1c io port: [0x3168-0x316b]
[    0.337368] pci 0000:00:1f.5: reg 20 io port: [0x30f0-0x30ff]
[    0.337373] pci 0000:00:1f.5: reg 24 io port: [0x30e0-0x30ef]
[    0.337394] pci 0000:00:1f.5: PME# supported from D3hot
[    0.337454] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.337519] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.337617] pci 0000:03:00.0: reg 10 io port: [0x1018-0x101f]
[    0.337625] pci 0000:03:00.0: reg 14 io port: [0x1024-0x1027]
[    0.337632] pci 0000:03:00.0: reg 18 io port: [0x1010-0x1017]
[    0.337641] pci 0000:03:00.0: reg 1c io port: [0x1020-0x1023]
[    0.337648] pci 0000:03:00.0: reg 20 io port: [0x1000-0x100f]
[    0.337696] pci 0000:03:00.0: supports D1
[    0.337698] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.337749] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.337978] pci 0000:07:03.0: supports D1 D2
[    0.337980] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
[    0.338027] pci 0000:00:1e.0: transparent bridge
[    0.347592] NetLabel:  unlabeled traffic allowed by default
[    0.347746] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
[    0.347746] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.347746] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.347746] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.347746] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.347746] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.347746] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.347746] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[    0.347746] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[    0.347746] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.347746] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.347746] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.347746] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.347746] system 00:07: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.366000] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.366006] pcieport 0000:00:01.0: setting latency timer to 64
[    0.366110] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.366117] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.366229] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.366236] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.366350] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.366358] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.366475] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.366482] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.366597] pcieport 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.366604] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.370146] Linux agpgart interface v0.103
[    0.370178] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.372199] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.374064] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.374233] ehci_hcd 0000:00:1a.7: debug port 1
[    0.378117] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.392423] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.392534] usb usb1: configuration #1 chosen from 1 choice
[    0.392578] hub 1-0:1.0: 4 ports detected
[    0.392732] ehci_hcd 0000:00:1d.7: debug port 1
[    0.396612] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.412411] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.412518] usb usb2: configuration #1 chosen from 1 choice
[    0.412556] hub 2-0:1.0: 6 ports detected
[    0.412854] usb usb3: configuration #1 chosen from 1 choice
[    0.412887] hub 3-0:1.0: 2 ports detected
[    0.413088] usb usb4: configuration #1 chosen from 1 choice
[    0.413117] hub 4-0:1.0: 2 ports detected
[    0.413316] usb usb5: configuration #1 chosen from 1 choice
[    0.413346] hub 5-0:1.0: 2 ports detected
[    0.413527] usb usb6: configuration #1 chosen from 1 choice
[    0.413558] hub 6-0:1.0: 2 ports detected
[    0.413745] usb usb7: configuration #1 chosen from 1 choice
[    0.413775] hub 7-0:1.0: 2 ports detected
[    0.413865] PNP: No PS/2 controller found. Probing ports directly.
[    0.416902] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.416910] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.417093] rtc_cmos 00:03: RTC can wake from S4
[    0.417130] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.417154] rtc0: alarms up to one month, 114 bytes nvram
[    0.419628] rtc_cmos 00:03: setting system clock to 2010-06-22 15:35:15 UTC (1277220915)
[    1.009463] usb 2-6: configuration #1 chosen from 1 choice
[    1.295425] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.362190] udev: starting version 151
[    1.435736] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.486217] usb 4-1: configuration #1 chosen from 1 choice
[    1.634292] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.655563] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1/input0
[    1.965486] usb 5-1: configuration #1 chosen from 1 choice
[    1.982731] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input4
[    1.982797] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.0-1/input0
[    2.006583] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input5
[    2.006673] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.0-1/input1
[   12.605395] udev: starting version 151
[   12.823961] type=1505 audit(1277177727.900:2):  operation="profile_load" pid=570 name="/sbin/dhclient3"
[   12.824751] type=1505 audit(1277177727.900:3):  operation="profile_load" pid=570 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.825099] type=1505 audit(1277177727.900:4):  operation="profile_load" pid=570 name="/usr/lib/connman/scripts/dhclient-script"
[   12.874037] fb0: VGA16 VGA frame buffer device
[   12.881289] parport_pc 00:09: reported by Plug and Play ACPI
[   12.881367] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   12.900974]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.902827] ppdev: user-space parallel port driver
[   12.961435] lp0: using parport0 (interrupt-driven).
[   13.064819] Console: switching to colour frame buffer device 80x30
[   13.460384] type=1505 audit(1277177728.540:5):  operation="profile_load" pid=761 name="/usr/share/gdm/guest-session/Xsession"
[   13.461901] type=1505 audit(1277177728.540:6):  operation="profile_replace" pid=762 name="/sbin/dhclient3"
[   13.462542] type=1505 audit(1277177728.540:7):  operation="profile_replace" pid=762 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.462886] type=1505 audit(1277177728.540:8):  operation="profile_replace" pid=762 name="/usr/lib/connman/scripts/dhclient-script"
[   13.465513] type=1505 audit(1277177728.540:9):  operation="profile_load" pid=763 name="/usr/bin/evince"
[   13.473745] type=1505 audit(1277177728.550:10):  operation="profile_load" pid=763 name="/usr/bin/evince-previewer"
[   13.478896] type=1505 audit(1277177728.550:11):  operation="profile_load" pid=763 name="/usr/bin/evince-thumbnailer"
[   14.344559] phy0: Selected rate control algorithm 'minstrel'
[   14.345192] Registered led device: rt2800usb-phy0::radio
[   14.345209] Registered led device: rt2800usb-phy0::assoc
[   14.345225] Registered led device: rt2800usb-phy0::quality
[   14.345588] usbcore: registered new interface driver rt2800usb
[   14.346407] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.350720] rtusb init --->
[   14.350752] usbcore: registered new interface driver rt2870
[   14.371955] rt2800usb 2-6:1.0: firmware: requesting rt2870.bin
[   14.861351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  107.926791] __ratelimit: 9 callbacks suppressed
[  107.926793] type=1505 audit(1277177823.000:15):  operation="profile_load" pid=1681 name="/usr/sbin/ntpd"
[  164.126135] usb 2-6: configuration #1 chosen from 1 choice
[  164.159888] phy1: Selected rate control algorithm 'minstrel'
[  164.160740] Registered led device: rt2800usb-phy1::radio
[  164.160763] Registered led device: rt2800usb-phy1::assoc
[  164.160785] Registered led device: rt2800usb-phy1::quality
[  164.172469] rt2800usb 2-6:1.0: firmware: requesting rt2870.bin
[  164.450951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  412.910992] usb 2-5: configuration #1 chosen from 1 choice
[  412.966609] Initializing USB Mass Storage driver...
[  412.966751] scsi6 : SCSI emulation for USB Mass Storage devices
[  412.966944] usbcore: registered new interface driver usb-storage
[  412.966948] USB Mass Storage support registered.
[  412.967550] usb-storage: device found at 5
[  412.967553] usb-storage: waiting for device to settle before scanning
[  417.960190] usb-storage: device scan complete
[  449.032615] wlan0: deauthenticating from 00:23:33:e2:86:90 by local choice (reason=3)
[  449.042709] wlan0: direct probe to AP 00:23:33:e2:86:90 (try 1)
[  449.043469] wlan0: direct probe responded
[  449.043472] wlan0: authenticate with AP 00:23:33:e2:86:90 (try 1)
[  449.044333] wlan0: authenticated
[  449.044349] wlan0: associate with AP 00:23:33:e2:86:90 (try 1)
[  449.045459] wlan0: RX AssocResp from 00:23:33:e2:86:90 (capab=0x11 status=0 aid=1)
[  449.045462] wlan0: associated
[  449.073804] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  457.872653] wlan0: direct probe to AP 00:23:33:e2:86:90 (try 1)
[  457.873410] wlan0: direct probe responded
[  457.873413] wlan0: authenticate with AP 00:23:33:e2:86:90 (try 1)
[  457.874025] wlan0: authenticated
[  457.874045] wlan0: associate with AP 00:23:33:e2:86:90 (try 1)
[  457.875155] wlan0: RX AssocResp from 00:23:33:e2:86:90 (capab=0x11 status=0 aid=1)
[  457.875158] wlan0: associated
[  459.320008] wlan0: no IPv6 routers present
[  465.903031] wlan0: direct probe to AP 00:23:33:e2:86:90 (try 1)
[  465.903788] wlan0: direct probe responded
[  465.903791] wlan0: authenticate with AP 00:23:33:e2:86:90 (try 1)
[  465.904403] wlan0: authenticated
[  465.904420] wlan0: associate with AP 00:23:33:e2:86:90 (try 1)
[  465.905528] wlan0: RX AssocResp from 00:23:33:e2:86:90 (capab=0x11 status=0 aid=1)
[  465.905531] wlan0: associated
[  473.892658] wlan0: direct probe to AP 00:23:33:e2:86:90 (try 1)
[  473.893412] wlan0: direct probe responded
[  473.893415] wlan0: authenticate with AP 00:23:33:e2:86:90 (try 1)
[  473.894027] wlan0: authenticated
[  473.894044] wlan0: associate with AP 00:23:33:e2:86:90 (try 1)
[  473.895154] wlan0: RX AssocResp from 00:23:33:e2:86:90 (capab=0x11 status=0 aid=1)
....
....lots of similar text
....

[ 1206.945287] wlan0: associated
[ 1207.992473] wlan0: deauthenticating from 00:23:33:e2:86:90 by local choice (reason=3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
testrig4ub64@testrig4ub64-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:e4:be:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-0 ip=132.181.12.139 latency=0 multicast=yes
       resources: irq:30 memory:93200000-9321ffff memory:93224000-93224fff ioport:30c0(size=32)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:e5:ea:61:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Not sure where to proceed from here.

---

### Post by pytheas22 on 2010-06-22
It looks like you're using the rt2870sta driver.  Ubuntu comes with a version of this driver built-in, but you may have better luck with it if you install it from the latest source code from the website of Ralink, the company which manufactured your wireless card's chipset.

You can download the driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  Choose the link for RT2870USB(RT2870/RT2770).  If you need help compiling and installing the driver, let me know--I'm not sure how much Linux experience you have and compiling drivers from source is pretty advanced stuff, so if you need step-by-step instructions on what to do, I can provide them.

With any luck, you will be able to connect once you have the manufacturer's version of the driver.

---

### Post by b k on 2010-06-22
> **ReginaldPerrin3 said:**
> 
 
Not sure where to proceed from here.
 
Hi there, I think you have a problem with two conflicting drivers rt2870sta and rt2800usb.
 
You do not need to install any additional drivers or software but will be using the native drivers that are within Ubuntu 10.04 LTS
 
It is important to use copy and paste technique to get the codes into the Terminal window (via a text file and usb dongle if you do not have a wired connection) to prevent typo errors.
 
Firstly please confirm your device id:
 
```
lsusb
```
 
Somewhere in one of the output lines you should either have:
 
1737:0071 (if you have Linksys WUSB600N v1) [COLOR=red]or[/COLOR]
 
[COLOR=black]1737:[COLOR=black]0079[/COLOR] (if you have Linksys WUSB600N v2)[/COLOR]
 
_IF YOU HAVE DEVICE ID 1737:[COLOR=red]0071[/COLOR]_ do this in a Terminal window:
 
```
[COLOR=blue]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]
```
 
add the following line to the end of the opened file:
 
[COLOR=blue]blacklist rt2800usb[/COLOR]
 
[COLOR=blue]save[/COLOR] and close (ensuring that the file blacklist.conf is saved in the etc/modprobe.d directory)
 
[COLOR=blue]Reboot[/COLOR] 
 
It should then work if you do not have other complications.
 
 
_IF YOU HAVE DEVICE ID 1737:[COLOR=red]0079[/COLOR]_ do this in a Terminal window:
 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
add the following line to the end of the opened file:
 
[COLOR=#0000ff]blacklist rt2800usb[/COLOR]

[COLOR=#0000ff]save[/COLOR][COLOR=#000000] and close (ensuring that the file blacklist.conf is saved in the etc/modprobe.d directory)[/COLOR]
 
 
```
[COLOR=blue]sudo gedit /etc/udev/rules.d/network_drivers.rules[/COLOR]
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
[COLOR=blue]ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1737", ATTR{idProduct}=="0079", RUN+="/sbin/modprobe -qba rt2870sta"[/COLOR]
```
 
Proofread carefully (ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=blue]save[/COLOR] and close gedit.
 
 
Next do this:
 
```
[COLOR=blue]sudo gedit /etc/modprobe.d/network_drivers.conf[/COLOR]
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
[COLOR=blue]install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id[/COLOR]
```
 
Proofread carefully (ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
[COLOR=blue]Reboot[/COLOR]
 
Your wireless adapter should now work.
 
In the event that the procedures do not work, you can execute the codes again and remove whatever you have added in the opened files.
 
Good luck and let us know if you are successful.
 
PS : Sorry did not read post #1 before posting so procedure for device id _1737:0071_ may not work (but suggest you try it first).
If it does not work, then try procedure for device id 1737:0079 but **[COLOR=black]substitute[/COLOR]** 0079 for 0071 very very carefully in the two long lines of code.

---

### Post by ReginaldPerrin3 on 2010-06-22
Thanks for everyone's help.
I have solved this by doing a clean install of 10.04 (didn't take long).
Blacklisted the default Ubuntu drivers, added the (slightly modified) Ralink driver, rebooted, and bingo it all works properly.
I can correctly connect to my 300Mbps 5GHz 802.11n network.

Cheers all.

---

### Post by lindenle on 2010-06-23
Hi All,

I have followed the instructions above and I am trying to test if it has been successful. However, I only have an Ad-Hoc network to test with at the moment. Does this work with for anyone else? I seem to be having no luck in this mode. Also is there any issue with X86_64 (I am running lucid).

Thanks.

Alex

```

$iwconfig ra0

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ifconfig ra0

ra0       Link encap:Ethernet  HWaddr 00:1e:e5:e9:4c:c0  
          inet6 addr: fe80::21e:e5ff:fee9:4cc0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:922560 (922.5 KB)  TX bytes:514460 (514.4 KB)


```
P.S. Note I can see the Ad-Hoc network as well as a bunch of other WPA networks around me. I will test with a manged WPA2 when I get home this evening.

---

### Post by pytheas22 on 2010-06-23
**ReginaldPerrin3**: glad you got it sorted.  Thanks b k for the tips; I didn't think of conflicting modules.

**lindenle**: I would think that ad-hoc mode would work but can't confirm from experience.  How is your ad-hoc network configured?  Are you trying to create a new ad-hoc network from your Ubuntu computer, or are you trying to connect to one that already exists?  How are you doing all this--from the command line or using NetworkManager?  Are you using dhcp or are you setting addresses statically?

---

### Post by lindenle on 2010-06-23
Trying to connect to one that already exists (from my android phone)
using DHCP. Not that important that it works, just wanted to test the
card before I left for the day. I will report from home how it does on
a normal wireless router.

Alex

---

### Post by lindenle on 2010-06-24
So I got home last night and tested it with my AP. It would not
connect and after that I tried again and the machine hung there was a
kernel oops in dmesg from the first attempt. I am running under
x86_64, any thoughts2~?

Alex

---

### Post by pytheas22 on 2010-06-25
What exactly did you do to get this working?  Did you install the driver using the source code from Ralink's site?  If not, I would try that; those drivers may work better.  It shouldn't matter that your kernel is 64-bit; if it works for others on 32-bit Ubuntu, it should work as well for you on 64-bit.

If you were using the Ralink driver and it's still not working, perhaps ndiswrapper is the next best solution to try.  In that case, do you know where you can download Windows drivers for your device or do you have those drivers on a CD somewhere?  You will need 64-bit Windows drivers.

---

### Post by freek_zero on 2010-06-28
> **ReginaldPerrin3 said:**
> I have solved this by ....
Blacklisted the default Ubuntu drivers, added the (slightly modified) Ralink driver, rebooted, and bingo it all works properly.
I can correctly connect to my 300Mbps 5GHz 802.11n network.

Same here, and that's 5GHz with WPA2 even (which never worked before, with either driver).

HOWEVER... the performance is unusable. Frequent (as in about 25% of requests) huge lags plague both HTML and even SSH requests. A couple pages will work fine then one will hang for several seconds. Yet thruput and ping are good when doing a speedtest. I changed back to 2.4GHz (which gets interrupted every time the cordless phone is used) and it works fine.

---

### Post by ReginaldPerrin3 on 2010-07-01
Performance on my test machines is just fine. Can happily achieve TCP rates somewhere around 80Mbps and UDP around 130Mbps. Equipment used is a Cisco 1252 Access Point, and an Apple Airport Extreme, as well as several WUSB600Ns.
I used Netperf to get these results.

Best results come using the 5GHz network, obviously. The 2.4GHz networks will always be plagued by cordless telephones, baby monitors, garage door openers, microwave ovens, and of course all the other 2.4GHz home networks within any sort of range.

---

### Post by ReginaldPerrin3 on 2010-07-01
And now I realise, of course, that the process of ensuring that Ubuntu is using the correct driver should be repeated (ie: the driver reinstalled) with every update to the kernel. This only means altering the command (in previous posts) to insert the driver (rt2870sta) into the correct kernel-version folders.
It would be nice to write a script to do all of that automatically upon detection of kernel version change, but I am not familiar enough with scripting to write one up.
I suppose that the script would have to be somewhat customised seeing as how the compiled driver may not be stored in the same place in all people's computers.

I will give this much thought, and see what I can come up with (open source of course!).

I have some test machines that I can sort of afford to break a few times, so this will not be much of a problem.

---

### Post by Dev0 on 2010-07-01
> Originally Posted by **ReginaldPerrin3** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9498420#post9498420")
I suppose that the script would have to be somewhat customised seeing as how the compiled driver may not be stored in the same place in all people's computersNot necessarily, especially if the guide itself is revised.  Here's how to modify the source code from scratch, then install the user-compiled rt2870 driver via BASH script. The first three steps here are identical to those of the original instructions on the first page of this thread.

1. Download the rt2870USB driver to your downloads file from the Ralink website: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Right click to extract the file.  Rename the extracted file "RT2870".

2. Open the source code file "~/Downloads/R2870/os/linux/config.mk" and change the following two values from "=n" to "=y" so that the result is:
```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```Save and exit.

3. Open "~/Downloads/R2870/common/cmm_wpa.c" and change the character encoding to Western if needed. Use control+f to search for
```
MIX_CIPHER_NOTUSE
```Highlight MIX_CIPHER_NOTUSE and copy-paste
```
WPA_TKIPAES_WPA2_TKIPAES
```into its place. Save and exit.

4. In Terminal, run ```
gksudo gedit /etc/modules
``` and add ```
rt2870sta
``` at the bottom to tell Ubuntu to load the driver at startup.

Now you've modified the source files in the same was as in the first guide. I'm working on a way to automate this, but it will have to be manual for now.

4. It would be annoying to edit that code every time the driver needed recompiling, so we want to put it somewhere permanently.
```
sudo mv ~/Downloads/RT2870 /usr/src/
```5. Now for the script. It reads from the /usr/src/RT2870 directory no matter what kernel version you have. Copy and paste the following into a blank gedit document. Save it as "rt2870_install.sh" in your Documents directory.

```
#!/bin/bash

cd /usr/src/RT2870
make
make install
ifconfig wlan0 down
rmmod rt2870sta

cd /lib/modules/`uname -r`/kernel/drivers/staging/rt2870/
sudo mv rt2870sta.ko rt2870sta.ko.dist

cd /usr/src/RT2870/os/linux
sudo cp rt2870sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt2870/

modprobe rt2870sta
exit 0

```6. Any time you need to reinstall the modified driver, open up Terminal and type
```
sudo sh ~/Documents/rt2870_install.sh
```which will run the script and do the dirty work for you.

*About the script: the modprobe rt2870sta is intended to start the modified driver immediately, without having to reboot. However, I've always had to reboot to initialize the module. Also, I have found a way to determine if there has been a kernel update through a bash script and then automatically reinstall the modified driver, but I don't know how to use Upstart to initialize it with root privileges at startup. If anyone knows how to do this or clean up the above script, let us know!

---

### Post by pytheas22 on 2010-07-02
> This only means altering the command (in previous posts) to insert the driver (rt2870sta) into the correct kernel-version folders.

Just to be clear, you can't simply copy the rt2870sta.ko file into the new kernel folder under /lib/modules; you have to recompile the module against the new kernel (i.e., you have to compile it while running the new kernel, or pass arguments to the compiler to specify which kernel the module needs to work with before it gets compiled) or it won't work with that kernel.

Dev0's instructions above should help you out.  If you wanted, I suppose you could follow them so that you could recompile the module with one simple command.  Then you could [create a boot script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") that would test during boot to see if your currently running kernel has the rt2870sta module installed, and if not, compile and install it automatically.  Of course, there are plenty of other ways you do this; that's just an idea.

---

### Post by Ons308 on 2010-08-12
> **Dev0 said:**
> Not necessarily, especially if the guide itself is revised.  Here's how to modify the source code from scratch, then install the user-compiled rt2870 driver via BASH script. The first three steps here are identical to those of the original instructions on the first page of this thread.

1. Download the rt2870USB driver to your downloads file from the Ralink website: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Right click to extract the file.  Rename the extracted file "RT2870".

2. Open the source code file "~/Downloads/R2870/os/linux/config.mk" and change the following two values from "=n" to "=y" so that the result is:
```
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```Save and exit.

3. Open "~/Downloads/R2870/common/cmm_wpa.c" and change the character encoding to Western if needed. Use control+f to search for
```
MIX_CIPHER_NOTUSE
```Highlight MIX_CIPHER_NOTUSE and copy-paste
```
WPA_TKIPAES_WPA2_TKIPAES
```into its place. Save and exit.

4. In Terminal, run ```
gksudo gedit /etc/modules
``` and add ```
rt2870sta
``` at the bottom to tell Ubuntu to load the driver at startup.

Now you've modified the source files in the same was as in the first guide. I'm working on a way to automate this, but it will have to be manual for now.

4. It would be annoying to edit that code every time the driver needed recompiling, so we want to put it somewhere permanently.
```
sudo mv ~/Downloads/RT2870 /usr/src/
```5. Now for the script. It reads from the /usr/src/RT2870 directory no matter what kernel version you have. Copy and paste the following into a blank gedit document. Save it as "rt2870_install.sh" in your Documents directory.

```
#!/bin/bash

cd /usr/src/RT2870
make
make install
ifconfig wlan0 down
rmmod rt2870sta

cd /lib/modules/`uname -r`/kernel/drivers/staging/rt2870/
sudo mv rt2870sta.ko rt2870sta.ko.dist

cd /usr/src/RT2870/os/linux
sudo cp rt2870sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt2870/

modprobe rt2870sta
exit 0

```6. Any time you need to reinstall the modified driver, open up Terminal and type
```
sudo sh ~/Documents/rt2870_install.sh
```which will run the script and do the dirty work for you.

*About the script: the modprobe rt2870sta is intended to start the modified driver immediately, without having to reboot. However, I've always had to reboot to initialize the module. Also, I have found a way to determine if there has been a kernel update through a bash script and then automatically reinstall the modified driver, but I don't know how to use Upstart to initialize it with root privileges at startup. If anyone knows how to do this or clean up the above script, let us know!


I followed the below steps but still nothing. There is an error when  running the "sudo sh ~/Documents/rt2870_install.sh" command in the  terminal

The following is the error i get when installing the source code from the script.

make -C tools
make[1]: Entering directory `/usr/src/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/src/RT2870/tools'
/usr/src/RT2870/tools/bin2h
cp -f os/linux/Makefile.6 /usr/src/RT2870/os/linux/Makefile
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/usr/src/RT2870/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/RT2870/os/linux/../../common/rtmp_mcu.o
  LD [M]  /usr/src/RT2870/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /usr/src/RT2870/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make -C /usr/src/RT2870/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/usr/src/RT2870/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /usr/src/RT2870/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-24-generic
make[1]: Leaving directory `/usr/src/RT2870/os/linux'
wlan0: ERROR while getting interface flags: No such device


That is the entire output of the command when run. This output is the  second time running the script. I originally did all the steps and then  ran the script and it got errors similar to the one above but it also  listed a directory not found. Following rebooting the computer, and  wireless still not working i ran the script again and the above is the  entire output.

Please help as to what i'm doing wrong, or how to fix this flag error.

---

### Post by pytheas22 on 2010-08-12
> That is the entire output of the command when run. This output is the second time running the script. I originally did all the steps and then ran the script and it got errors similar to the one above but it also listed a directory not found. Following rebooting the computer, and wireless still not working i ran the script again and the above is the entire output.

Please help as to what i'm doing wrong, or how to fix this flag error.

I suspect you're getting that error message because of the line in the script that reads:
```

ifconfig wlan0 down
```

It looks like the interface 'wlan0' doesn't exist.  Chances are it's named 'wlan1' or something similar on your computer--this is normal.  Changing the script accordingly should allow it to complete without errors.

To find the name of your wireless interface, type:
```

ifconfig -a
```

You'll get output that looks something like:

```
**wlan0**      Link encap:Ethernet  HWaddr 00:19:21:85:0d:87  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe85:d87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1501422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1037223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1840839745 (1.8 GB)  TX bytes:161668870 (161.6 MB)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16715204 (16.7 MB)  TX bytes:16715204 (16.7 MB)
```


In the example above, the name of my interface is in bold.  Look for an interface in your outupt whose name starts with 'wlan...', then edit your script so that the name of this interface replaces 'wlan0', then try running the script again.  Does this work?

---

### Post by Ons308 on 2010-08-13
The following is the output of the terminal of the iwconfig command and ifconfig -a command.

output:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:3c:58:3c  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe3c:583c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42320515 (42.3 MB)  TX bytes:1808534 (1.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

not sure what i'm looking for when it comes to getting the information about what the right flag is. it doesn't look like any wireless exists. how would i go about getting that to show up that i have plugged in a wireless device and that i have another device to show up in this list.



Many Thanks, 

Ons

---

### Post by daibak on 2010-08-13
> **Ons308 said:**
> The following is the output of the terminal of the iwconfig command and ifconfig -a command.

output:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:3c:58:3c  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe3c:583c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42320515 (42.3 MB)  TX bytes:1808534 (1.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

not sure what i'm looking for when it comes to getting the information about what the right flag is. it doesn't look like any wireless exists. how would i go about getting that to show up that i have plugged in a wireless device and that i have another device to show up in this list.



Many Thanks, 

Ons
Post #46 on page 5 of thread Re: Howto: Ralink RT2860 (m)PCI(e) (RT2760/RT2790/RT2860/RT2890) on Intrepid
will supply a once and for all definitive solution to any Ralink RT2860 Wireless (WPA2 encrypted) not working with Ubuntu 10.04 Netbook Edition.

Your travails trying to understand the Linux world remind me of the agony I used to suffer before I went back to "Simple is beautiful". There is nothing easier than installing Ubuntu 10.04 as a virtual machine in VMware Player 3.1.1, which is completely free for home or personal non-profit use. 

Anybody who says this is overkill is correct but I don't need to waste any time trying to get things to work, they just do... straight out of the box.

---

### Post by Dev0 on 2010-08-13
> **daibak said:**
> Post #46 on page 5 of thread Re: Howto: Ralink RT2860 (m)PCI(e) (RT2760/RT2790/RT2860/RT2890) on Intrepid
will supply a once and for all definitive solution to any Ralink RT2860 Wireless (WPA2 encrypted) not working with Ubuntu 10.04 Netbook Edition.

Hi daibak. I believe this is what you are referring to:
[http://ubuntuforums.org/showthread.php?p=9716483#post9716483](http://ubuntuforums.org/showthread.php?p=9716483#post9716483)

A virtual OS is one of many possible solutions because it avoids the problem of dealing with a Linux driver entirely. However, this thread has been focused on getting the RT2870 chipset to function properly on a physical machine, sans Windows or any other OS to hold Ubuntu's hand. Lucid should be versatile enough to run on its own, and we're trying to get it there :)

---

### Post by pytheas22 on 2010-08-13
> **Ons308 said:**
> The following is the output of the terminal of the iwconfig command and ifconfig -a command.

output:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:3c:58:3c  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe3c:583c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42320515 (42.3 MB)  TX bytes:1808534 (1.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

not sure what i'm looking for when it comes to getting the information about what the right flag is. it doesn't look like any wireless exists. how would i go about getting that to show up that i have plugged in a wireless device and that i have another device to show up in this list.



Many Thanks, 

Ons

Thanks for your output.  It looks like the problem runs deeper than I originally thought--as you say, no wireless interface exists at all.  That's probably (although not certainly) because the driver you tried to install was not the right one for your particular card.

Sorry to ask for more output, but if you could please run these commands (with your wireless card plugged in) and post the results here, it should allow us to know for sure what driver you need, or, if that's not the issue, figure out what's going wrong:
```

lshw -C Network
dmesg | grep -ie rt -ie wlan
lsusb
lspci -nn
modinfo rt2870sta
```

---

### Post by Ons308 on 2010-08-15
I ran all the commands you gave to me and these are the outputs. Thanks for all the help.

Ons

"lloyd@Anne:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1f:e2:3c:58:3c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.145 latency=0 multicast=yes
       resources: irq:29 memory:feafc000-feafffff ioport:e800(size=256) memory:feac0000-feadffff(prefetchable)"

"lloyd@Anne:~$ dmesg | grep -ie rt -ie wlan
[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at b0000000 (gap: b0000000:4ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] virtual kernel memory layout:
[    0.004220] mce: CPU supports 5 MCE banks
[    0.029856] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.176004] ACPI: (supports S0 S3 S4 S5)
[    0.186290] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.186328] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.186362] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.186427] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.186435] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.186442] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.186449] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.186457] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.186721] pci 0000:00:12.2: supports D1 D2
[    0.186723] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.186944] pci 0000:00:13.2: supports D1 D2
[    0.186946] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.187071] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.187079] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.187086] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.187093] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.187100] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.187211] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.187462] pci 0000:01:05.0: reg 20 io port: [0xc000-0xc0ff]
[    0.187477] pci 0000:01:05.0: supports D1 D2
[    0.187493] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.187545] pci 0000:02:00.0: reg 20 io port: [0xd000-0xd0ff]
[    0.187572] pci 0000:02:00.0: supports D1 D2
[    0.187640] pci 0000:02:00.1: supports D1 D2
[    0.187694] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.187753] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.187804] pci 0000:03:00.0: supports D1 D2
[    0.187806] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187862] pci 0000:00:05.0: bridge io port: [0xe000-0xefff]
[    0.188151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.188286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.188328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.188375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.188417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.188474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.201169] system 00:07: ioport range 0x200-0x20f has been reserved
[    0.201172] system 00:07: ioport range 0x220-0x233 has been reserved
[    0.201175] system 00:07: ioport range 0x240-0x253 has been reserved
[    0.201177] system 00:07: ioport range 0x260-0x273 has been reserved
[    0.201180] system 00:07: ioport range 0x280-0x293 has been reserved
[    0.201182] system 00:07: ioport range 0x388-0x389 has been reserved
[    0.201185] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.201188] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.201190] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.201193] system 00:07: ioport range 0xb00-0xb0f has been reserved
[    0.201195] system 00:07: ioport range 0xb30-0xb3f has been reserved
[    0.201198] system 00:07: ioport range 0xc00-0xc01 has been reserved
[    0.201201] system 00:07: ioport range 0xc14-0xc14 has been reserved
[    0.201203] system 00:07: ioport range 0xc50-0xc51 has been reserved
[    0.201206] system 00:07: ioport range 0xc52-0xc52 has been reserved
[    0.201209] system 00:07: ioport range 0xc6c-0xc6c has been reserved
[    0.201211] system 00:07: ioport range 0xc6f-0xc6f has been reserved
[    0.201214] system 00:07: ioport range 0xcd0-0xcd1 has been reserved
[    0.201217] system 00:07: ioport range 0xcd2-0xcd3 has been reserved
[    0.201219] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
[    0.201222] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
[    0.201224] system 00:07: ioport range 0xcd8-0xcdf has been reserved
[    0.201227] system 00:07: ioport range 0x800-0x89f has been reserved
[    0.201230] system 00:07: ioport range 0xb20-0xb2f has been reserved
[    0.201233] system 00:07: ioport range 0x900-0x90f has been reserved
[    0.201235] system 00:07: ioport range 0x910-0x91f has been reserved
[    0.201238] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.201249] system 00:09: ioport range 0xe00-0xe0f has been reserved
[    0.201252] system 00:09: ioport range 0xe80-0xe8f has been reserved
[    0.201254] system 00:09: ioport range 0xf40-0xf4f has been reserved
[    0.201257] system 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.382939] pcieport 0000:00:02.0: irq 25 for MSI/MSI-X
[    0.382945] pcieport 0000:00:02.0: setting latency timer to 64
[    0.383020] pcieport 0000:00:05.0: irq 26 for MSI/MSI-X
[    0.383024] pcieport 0000:00:05.0: setting latency timer to 64
[    0.383090] pcieport 0000:00:06.0: irq 27 for MSI/MSI-X
[    0.383094] pcieport 0000:00:06.0: setting latency timer to 64
[    0.389233] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.390850] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.391569] ehci_hcd 0000:00:12.2: debug port 1
[    0.440835] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.440974] hub 1-0:1.0: 6 ports detected
[    0.441134] ehci_hcd 0000:00:13.2: debug port 1
[    0.484839] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.484935] hub 2-0:1.0: 6 ports detected
[    0.548722] hub 3-0:1.0: 3 ports detected
[    0.608594] hub 4-0:1.0: 3 ports detected
[    0.668591] hub 5-0:1.0: 3 ports detected
[    0.728592] hub 6-0:1.0: 3 ports detected
[    0.788121] hub 7-0:1.0: 2 ports detected
[    0.788635] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.788642] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.788851] rtc_cmos 00:02: RTC can wake from S4
[    0.788890] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.788917] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.790812] Using IPI No-Shortcut mode
[    0.791364] rtc_cmos 00:02: setting system clock to 2010-08-14 14:12:49 UTC (1281795169)
[    0.808641] udev: starting version 151
[    0.885008] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.925520] ata3: SATA max UDMA/133 abar m1024@0xfe6ff800 port 0xfe6ff900 irq 28
[    0.925525] ata4: SATA max UDMA/133 abar m1024@0xfe6ff800 port 0xfe6ff980 irq 28
[    0.925529] ata5: SATA max UDMA/133 abar m1024@0xfe6ff800 port 0xfe6ffa00 irq 28
[    0.925533] ata6: SATA max UDMA/133 abar m1024@0xfe6ff800 port 0xfe6ffa80 irq 28
[    1.405670] USB Mass Storage support registered.
[    1.574282] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.322494] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.595389] kjournald starting.  Commit interval 5 seconds
[   12.181260] udev: starting version 151
[   12.219164] rtusb init --->
[   12.219209] usbcore: registered new interface driver rt2870
[   12.332802] Linux agpgart interface v0.103
[   12.461915] acer-wmi: No or unsupported WMI interface, unable to load
[   12.601230] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   12.601805] [fglrx] Kernel PAT support is enabled
[   13.338787] ppdev: user-space parallel port driver
[   14.279787] [fglrx] Gart USWC size:864 M.
[   14.279791] [fglrx] Gart cacheable size:342 M."

"lloyd@Anne:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1737:0079 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub"

"lloyd@Anne:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7911]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 Display controller [0380]: ATI Technologies Inc Radeon 2100 [1002:796e]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV620 LE [Radeon HD 3450] [1002:95c5]
02:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
04:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]"

"lloyd@Anne:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     6B9FEFA2731EB671D7F508E
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32-24-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)"

---

### Post by pytheas22 on 2010-08-15
**Ons308**: it looks like it's not working because the build of the driver that you're using doesn't support your particular device (with PCI ID 1737:0079).  However, you can compile the driver with support for your card by making a few small modifications to the source code.

There are instructions [here]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N") for doing that.  Please try following them and let me know if you have any troubles.

The one thing those instructions don't mention is that you'll need to install the build-essential package before compiling the driver.  You probably already have it, but in case you don't, run:
```

sudo apt-get install build-essential
```

to download it.

I think the script that you tried running a fews days ago assumed that your source code had already been modified to insert the correct PCI ID for your device, so that's why it wasn't working.

If the wiki doesn't get your device working, please post any error messages you get while trying to compile the module, along with the output of:

```
modinfo rt3572sta
dmesg | grep -r rt35 -e wlan
```

---

### Post by Ons308 on 2010-08-17
Nice i got it working. Thanks for all the help that you've given me. I've been wanting wireless Internet for a while. Because I had two monitors sitting in my room that has no ethernet cable. :D have a good day


Ons308

---

### Post by glutinous on 2010-08-22
Just ran into this issue again (on 10.04) after updating my kernel. Downloading the RT2870 source, making the modifications, compiling, and loading that seems to fix the issue (i.e., steps outlined in post [#34]("http://ubuntuforums.org/showpost.php?p=9534492&postcount=34")).

On top of this, I have rt2800usb blacklisted (by adding "blacklist rt2800usb" to a new file in /etc/modprobe.d). Not sure if this is necessary now, I needed to do it before to get it to work (before the problem re-emerged again).

After doing all that, my Linksys WUSB600N (v1 - NOT v2) is connecting once again with my D-Link wireless router.

I re-opened a bug similar to this too. It's [bug #433019]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433019").

---

### Post by pyite on 2010-09-23
The blacklist worked for me with the rt2800usb.  I added these lines to /etc/modprobe.d/blacklist.conf and rebooted:

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

---

### Post by Ons308 on 2010-10-26
> August 22nd, 2010 07:55 PM
glutinous     
Re: Linksys WUSB600N Problems in 10.04 Lucid, and Zombies
Just ran into this issue again (on 10.04) after updating my kernel. Downloading the RT2870 source, making the modifications, compiling, and loading that seems to fix the issue (i.e., steps outlined in post #34).

On top of this, I have rt2800usb blacklisted (by adding "blacklist rt2800usb" to a new file in /etc/modprobe.d). Not sure if this is necessary now, I needed to do it before to get it to work (before the problem re-emerged again).

After doing all that, my Linksys WUSB600N (v1 - NOT v2) is connecting once again with my D-Link wireless router.

I re-opened a bug similar to this too. It's bug #433019. As glutinous mentions in his post the problem has reoccurred in a kernel update. I'm currently using the v2 of the hardware and i'm curious how i should be going about fixing this problem again. 

The fix above is mentioned to only have worked so far on v1. Is this the same procedure used to fix the v2 hardware. Or is a different procedure needed. I will test this process above but I just didn't wish to mess up what I had done on the previous kernel if i didn't have to. But I believe it has come time to update.

Many Thanks,

Ons308

---

### Post by pytheas22 on 2010-10-27
> As glutinous mentions in his post the problem has reoccurred in a kernel update. I'm currently using the v2 of the hardware and i'm curious how i should be going about fixing this problem again.

The fix above is mentioned to only have worked so far on v1. Is this the same procedure used to fix the v2 hardware. Or is a different procedure needed. I will test this process above but I just didn't wish to mess up what I had done on the previous kernel if i didn't have to. But I believe it has come time to update.

The steps in post #43 should solve the issue again for you on the v2 hardware.  Each time you update your kernel, you need to recompile the driver (while you're booted into the new kernel) for the wireless to work, because the driver needs to be built "against" the kernel.

Hopefully this is what you need to know to get back online; if not let me know.

---

### Post by amiliv on 2011-01-03
FWIW:

Looks like things are different a bit in Ubuntu 10.10:

Using generic rt2870sta driver (blacklisting rt2x00 drivers), I'm able to connect to my WiFi-G network, and so far it looks stable.  However, my WiFi-N network (operating at 5GHz) is not visible at all.

Using generic rt2x00 drivers (blacklisting rt2870sta driver), I'm able to connect to my WiFi-N network at 5GHz for short period of time after boot.  However, within minutes, the connection is dropped and sub-sequent attempts to reconnect fail (although all WiFi networks are still visible).

---

### Post by pytheas22 on 2011-01-03
**amiliv**: thanks for the information; that's good to know.  I wonder if you'd have better stability on an 11n network using the rt2x00 drivers if you compiled them using the latest source code.

Also, according to the [Debian wiki entry for rt2870sta]("http://wiki.debian.org/rt2870sta"), "Ralink 802.11n PCI devices are supported by the rt2860sta driver."  Maybe that means you need to use rt2860sta instead of rt2870sta if you want 11n support (and don't want to use the rt2x00 drivers)?  I'm not positive.

---

### Post by Dev0 on 2011-04-21
I was able to get by with blacklisting the three conflicting drivers for a while on Maverick with no problems. After a reinstall neither that fix nor compiling from source worked. Installing "linux-backports-modules-compat-wireless-2.6.36-maverick-generic" in Synaptic with the second automatically added package works, but the connection cuts out randomly and is stuck at 54 Mb/s. We'll see if Natty is any different in a week.

---

### Post by pytheas22 on 2011-04-21
**Dev0**: that's good to know, thanks.  In case Natty doesn't make a difference, I wonder if you'd have better a more stable connection if you reduced the rate using iwconfig (e.g., "iwconfig wlan0 rate 1M" to set it to 1MB/s).  You would sacrifice speed, of course, but unless you're transferring files over your local network it probably doesn't matter, since few residential Internet connections provide anything close to 54 megabits.

---

### Post by Dev0 on 2011-05-08
I ran that bit of code 

```
iwconfig wlan0 rate 1M
```

in the terminal but got this error:

Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not permitted.

Adding a sudo in front let the op complete but did not change the link speed. Updating the kernel after my last post seemed to clear up all the connectivity issues. Natty does load a driver that automatically works, but the resulting connection was ungodly slow. Not sure if that was just a release day thing, though Natty's Unity desktop scared me off for the moment.

For whatever reason I lose connection to my WiFi almost every minute while on Facebook or using Skype. Strange because they work just fine under Windows XP and I can torrent Ubuntu ISOs (using Ubuntu) without an issue.

---

### Post by pytheas22 on 2011-05-08
> For whatever reason I lose connection to my WiFi almost every minute while on Facebook or using Skype. Strange because they work just fine under Windows XP and I can torrent Ubuntu ISOs (using Ubuntu) without an issue.

If changing the rate didn't help, I'm afraid I'm out of ideas, other than to try using ndiswrapper instead of the native Linux driver.  ndiswrapper might give better performance in a case like this.

---

### Post by Dev0 on 2011-05-08
At this point I'm not worried about it. I figure the hardware might be shot anyway so I'm on the lookout for a new usb wireless-n adapter. Any suggestions?

---

### Post by pytheas22 on 2011-05-08
> At this point I'm not worried about it. I figure the hardware might be shot anyway so I'm on the lookout for a new usb wireless-n adapter. Any suggestions? 

[This page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") can be helpful for finding a device.  It's kind of old, but cards that were reported to work two years ago should still work now.

Be careful, however, to make sure that the revision number of the device you buy is the same one confirmed to work by other users.  Hardware manufacturers have a tendency to change chipsets while still selling a product under the same name, with the result that "Acme USB Wireless Stick rev. A1" could be completely different from "Acme USB Wireless Stick rev. B1," as far as Linux is concerned.  In other words, make sure to do your research before purchasing; or at least buy from a place where you can return easily if necessary.

---

### Post by Dev0 on 2011-05-21
Thanks for the link. Turns out the adapter was shot. I ended up going off some comments on Newegg and went with the Rosewill RNX-N180UB (1T2R): [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166049]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166049")

lsusb in 10.10 reports it as "0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter"

10.04 - Not plug and play, driver not automatically loaded
10.10 - Not PNP with fresh install, but is PNP with a patch to latest kernel (2.6.35-28 at this time)
11.04 - PNP out of the box, drivers load automatically.

Is there a good place to report this?

---

### Post by pytheas22 on 2011-06-02
> 
Is there a good place to report this?

Sorry for not responding sooner; your post got lost in my shuffle till now for some reason.  You could always file a bug report on [http://launchpad.org](http://launchpad.org), but if the card is working in the latest kernel, I suspect the developers are aware--probably the module needed to drive the card was introduced, at least to Ubuntu, as of kernel 2.6.35-28.

On older kernels you could probably install the driver manually by compiling the compat-wireless code from linuxwireless.org.

---

