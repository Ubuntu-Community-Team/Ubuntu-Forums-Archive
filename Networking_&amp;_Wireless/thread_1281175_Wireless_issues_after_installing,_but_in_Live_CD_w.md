---
title: "Wireless issues after installing, but in Live CD works perfectly"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by sendblink23 on 2009-10-03
***UPDATE***

Low Signal has been fixed, used:
> System > Administration > Hardware Drivers

And I noticed it offered: Alternate Atheros "madwifi" driver

*below Info:
Quote:
Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.

After Activating it, it fixed my wireless signal


***Only Issue Left***
Now do you have any idea of a command or script or something with my issue of the wireless card when its not recognized(upon booting OS)... anything to force it to recognize it, its a real hassle having to reboot like 2 - 3 times for it to be recognized sometimes. Under the Live CD, as well as under win7 & Mac osx 10.5.8 it never fails to read my wireless card.

Any help on that side?





***OLD POST***
--------------------------------------------------------------------------------------
Here is my issue, for no apparent reason after installing Ubuntu 9.04, the wireless sometimes *is recognized & sometimes it isn't(i have to reboot a couple of times)... and sometimes it is recognized but the connection is extremely low.


But if I run Ubuntu 9.04 through the Live CD, the wireless connection always runs perfectly fine.
***I'm getting really LOW SIGNAL, when I'm close to the router***
Live CD: 85% -85%
After OS Istalled: 26% - 37%

On both testings I'm really close to my wireless router... something must have been going wrong after installing ubuntu (I have formatted & reinstalled  Ubuntu many times to see if the issue persisted & indeed it always acts the same way after installing the OS) & did the installing with 2 different copies (DVD & CD) of Ubuntu 9.04 at the slowest burning speed to make sure the burn is perfectly made.  

So any help here, why Live CD has better Wifi functionality than from after Installing the OS?

Here is my: lshw -C network 
*From when my Wireless is recognized from After Installing the OS(after a few reboots).

```

sudo lshw -C network
*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:f3:25:c0
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:bc:cd:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=10.0.0.71 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:c9:fe:5f:0c:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Currently I'm updated to the latest updates of Jaunty 9.04...(I expected a change for my wireless, but still stayed acting the same way... so Any help would be greatly appreciated.

---

### Post by sendblink23 on 2009-10-03
is there a way...  a terminal command, to Force to be recognized my wireless card... that I could run when I boot up my installed ubuntu os?

---

### Post by sendblink23 on 2009-10-04
Aybody....  I just want to force to recognize my wireless hardware by a terminal command or by a start up command...  so I don't keep getting my issue.

Alsois there a way to improve my wireless signal? I'm being honest when I run the Live CD the signal of exactly where my laptop is at its at 89%-85%...  but now after Installing OS its at 37% - 26%(it goes up & down randomly, my laptop is laying on a desk table never moved)...   So any way of improving it by any terminal commands?  I have updated to the latest updates and the wireless has stayed acting the same exact way..  :/

I did try running the Live CD and wireless always has way better signal

---

### Post by houstonbofh on 2009-10-04
First, those signal bars can lie...  so don't take them to seriously. :)

Now lets look at things.  Is it an internal card, or can you pull it hot, and reset it hot after a few seconds?  This reloads the driver...  Does it help?

If not, try disabling WiFi by right clicking on the network manager icon near the clock. After a bit, re-enable it, and see if that helps.

Also, look at the output from commands like ifconfig and iwlist in both the installed version and the LiveCD version and see what is different.

It may not fix it right away, but I at least gave you some places to look. :)

---

### Post by sendblink23 on 2009-10-04
> **houstonbofh said:**
> First, those signal bars can lie...  so don't take them to seriously. :)

Now lets look at things.  Is it an internal card, or can you pull it hot, and reset it hot after a few seconds?  This reloads the driver...  Does it help?

If not, try disabling WiFi by right clicking on the network manager icon near the clock. After a bit, re-enable it, and see if that helps.

Also, look at the output from commands like ifconfig and iwlist in both the installed version and the LiveCD version and see what is different.

It may not fix it right away, but I at least gave you some places to look. :)


Its an internal wireless card (so I can't pull it off =P) 

I've done that (Un-check wireless - wait about 5 minutes and re-check wireless & reconnect and its still the same)

By the way the BARS are always CORRECT on my laptop(On Windows *win 7 & Mac *osx 10.5.8 it reads above 80% signal), I said clearly on LIVE CD the Signal always stays perfectly fine which means above 80% (so the bars are acting correctly through linux *Jaunty 9.04) and I'm extremely close to my wireless router... its After installing the OS in which the signal went *BLOP* a huge drop of signal its below 30% signal 


*Installed OS*
ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:16:36:f3:25:c0  
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
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:bc:cd:52  
          inet addr:10.0.0.71  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:febc:cd52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6383925 (6.3 MB)  TX bytes:720040 (720.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-BC-CD-52-64-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwlist:
> Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 




I'm going to get the LIVE CD and run those commands to Post the Output of them... I'll update in a bit

---

### Post by houstonbofh on 2009-10-04
I think I was unclear in the commands...  "iwlist wlan0 scanning"

Also try "lspci" to see if it is seeing the same things...

---

### Post by sendblink23 on 2009-10-04
*LIVE CD*
iwlist wlan0 scanning:
> wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:FD:1F:D5
                    ESSID:"SpeedTouch67C694"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=86/100  Signal level:-44 dBm  Noise level=-93 dBm
                    Encryption key:off
                    IE: Unknown: 00105370656564546F756368363743363934
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020200
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000529a1cb18a
                    Extra: Last beacon: 40ms ago



lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



just incase...

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:16:36:f3:25:c0  
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
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:bc:cd:52  
          inet addr:10.0.0.71  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:febc:cd52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2152259 (2.1 MB)  TX bytes:280845 (280.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-BC-CD-52-64-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwlist:
> Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 



I'm going to run those last 2 commands on the Installed OS, just incase to see if there is any different output.

---

### Post by sendblink23 on 2009-10-04
*Installed OS*

iwlist wlan0 scanning:
> wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:FD:1F:D5
                    ESSID:"SpeedTouch67C694"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level:-72 dBm  Noise level=-92 dBm
                    Encryption key:off
                    IE: Unknown: 00105370656564546F756368363743363934
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020200
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000052c51e7004
                    Extra: Last beacon: 1604ms ago



lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



There done...  notice any difference? Look at the scanning one there is some difference.  :/

---

### Post by houstonbofh on 2009-10-04
I just found this...
[http://www.psychocats.net/ubuntucat/impressed-with-karmic-koala-beta/](http://www.psychocats.net/ubuntucat/impressed-with-karmic-koala-beta/)

"One little bug (which I filed) is that the hardware drivers for Broadcom 4312 install fine during the live CD session, but once you install Karmic, the drivers need to be uninstalled and reinstalled to work, and then only after a reboot. Hoping that gets fixed before final release."

Are you on the beta?

---

### Post by sendblink23 on 2009-10-04
> **houstonbofh said:**
> I just found this...
[http://www.psychocats.net/ubuntucat/impressed-with-karmic-koala-beta/](http://www.psychocats.net/ubuntucat/impressed-with-karmic-koala-beta/)

"One little bug (which I filed) is that the hardware drivers for Broadcom 4312 install fine during the live CD session, but once you install Karmic, the drivers need to be uninstalled and reinstalled to work, and then only after a reboot. Hoping that gets fixed before final release."

Are you on the beta?


No sorry normal Jaunty 9.04...  not koala 9.10

Anyways was bored on my OS I clicked System > Administration > Hardware Drivers

And I noticed it offered: Alternate Atheros "madwifi" driver

*below Info:
> Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.


Should I give that a try? If I go installing it and it doesn't work... how would I uninstall it... I have never used that Hardware Drivers application..

---

### Post by houstonbofh on 2009-10-04
Try it.  If it fails, you can remove it with the same application.

---

### Post by sendblink23 on 2009-10-04
*gave it a try, so weird... after I activated it...  I didn't notice any change...

But after a few seconds I looked at my bars and they went up, put my mouse over it, guess what... *81% =)

I guess that fixed it ;)


Now do you have any idea of a command or script or something with my issue of the wireless card when its not recognized(upon booting OS)... anything to force it to recognize it, its a real hassle having to reboot like 2 - 3 times for it to be recognized sometimes. Under the Live CD, as well as under win7 & Mac osx 10.5.8 it never fails to read my wireless card.

Any help on that side?

---

### Post by sendblink23 on 2009-10-04
Updated my Thread Post, so that its easier to notice what's my next needed help.

---

### Post by houstonbofh on 2009-10-04
> **sendblink23 said:**
> Now do you have any idea of a command or script or something with my issue of the wireless card when its not recognized(upon booting OS)... anything to force it to recognize it, its a real hassle having to reboot like 2 - 3 times for it to be recognized sometimes. Under the Live CD, as well as under win7 & Mac osx 10.5.8 it never fails to read my wireless card.

Define "not recognize."  I assume the enable and disable in Network Manager does nothing...  Another thing to look at is modprobe.

---

### Post by Bucky Ball on 2009-10-04
Fairly simple, you just need to put the commands in the boot file with everything else that starts with the machine. I think you might be barking up the wrong tree. If you can do it manually, just a matter of making it persistent.

I've never had to do this so don't know the file you should be adding the commands to nor the commands but hopefully someone that does can chirp up. Think it might be in the /etc/init.d directory. Any help coding gurus? :)

---

### Post by sendblink23 on 2009-10-04
> **houstonbofh said:**
> Define "not recognize."  I assume the enable and disable in Network Manager does nothing...  Another thing to look at is modprobe.


*define "not recognized"... exactly what you may assume, not detected in the OS, like if I do not have a wireless card, its just plain random when it happens.. so I have to reboot a couple of times for it to Show that I indeed have a wireless card (the OS to read it)

Anyways...  what's modprobe? I typed it on search... I thinks its related to ndiswrapper in which I have never used in the past...  any help on that side?

---

### Post by sendblink23 on 2009-10-04
> **Bucky Ball said:**
> Fairly simple, you just need to put the commands in the boot file with everything else that starts with the machine. I think you might be barking up the wrong tree. If you can do it manually, just a matter of making it persistent.

I've never had to do this so don't know the file you should be adding the commands to nor the commands but hopefully someone that does can chirp up. Think it might be in the /etc/init.d directory. Any help coding gurus? :)

that's exactly what I need... a command inside the boot file, so that it can be persistent. 

Or maybe a saved command in the *System > Preferences > Startup Applications ...  pretty sure its not for this kind of stuff but its a start up related thing =P

---

### Post by Bucky Ball on 2009-10-04
Yep. Needs to be modprobed in a startup script at boot. As I say, not sure how to do it. 

Another way to get networking up though is with this command in a terminal:

```
sudo /etc/init.d/networking start
```... and you can also use 'stop' in place of 'start' if you need to stop it. That might be a workaround for now. I think that might even be the file you need to change. Have a look in there and see what gives:

```
nano /etc/init.d/networking
```Second thoughts, this script is probably called by another at boot, possibly an .rc file. This is outta my league for the moment and haven't got a lot of time to look. Will have a snoop later. There's some clues anyhow and good luck.

* Update: don't think .rc file. Have a look in:

```
nano /etc/network/interfaces
```

... and post that here if you could.

Hopefully someone out there can throw a little more light on the subject. ;-)

---

### Post by sendblink23 on 2009-10-05
I'll give that a check tomorrow, I'm not at my computer right now...

So you want me to execute the last 2 commands & post here what it has inside so others can see & maybe try to help out?


I liked the first command, I'll give that a try when the not recognized issue happens to see if it works...  I'd say if that works ... I'll use that better, since its me forcing it when to use it & when to stop using it.

I'll report tomorrow laters & thanx

---

### Post by Bucky Ball on 2009-10-05
No probs. I'm just stabbing around really and hopefully someone that knows what file to tweak to get your card up at boot will chime in shortly.

In the meantime, have a look at this file:

```
nano /etc/network/interfaces
```That I think will show you what is being brought up at boot(?). If 'auto wlan0' is not there issue:

```
sudo nano /etc/network/interfaces
```... and at the bottom add:

```
auto wlan0

``` Hit 'ctl/x' to exit and 'y' to save then:

```
sudo /etc/init.d/network stop
sudo /etc/init.d/network start
```... or to see if this has worked reboot. Good luck.


* NB: I am presuming your card is 'wlan0'. If it is something else, substitute that ('ath0' or whatever it might be).

---

