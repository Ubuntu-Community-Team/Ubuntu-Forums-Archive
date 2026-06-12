---
title: "network difficulties with the lovely BCM4318"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by thalo on 2009-08-14
i got back an old laptop that i had lent to family and decided to put on ubuntu.  it was installed in windows, has the dual boot option at startup.  running ubuntu 9.04.

it is an acer aspire 3002LCi with the Broadband BCM4318 wireless card.  i have followed the Sampbar blog instructions:
[http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/)

from following the above directions, i am able to get the little swirling icon attempting to connect to a network, but no success.  there are no networks that show up under the network icon.  i am only able to get the swirling icon moving if it try to connect to a hidden network, and type in the network i set up in the network details in the network manager.   i am not sure if it is setting up the card correctly or if i have not set up my passkeys, network details, etc. to connect.

results from *lshw -C Network*

 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:b4:1a:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:1d:a1:41
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,12/22/2004, 3.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:f2:35:86:92:b0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

any help would be appreciated

---

### Post by superprash2003 on 2009-08-14
do you have wifi networks around? post output of
1)iwconfig
2)sudo iwlist scanning

---

### Post by thalo on 2009-08-14
i do have wireless network available.  i am able to connect when i boot to win, and use with other computers.

iwconfig results:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
sudo iwlist scanning results

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```
thanks

---

### Post by jleaker on 2009-08-14
Good luck.  I had it working perfectly (with WPA even) under 7.10.  Every version after that it simply will not work.  I have tried every solution I could find...nothing worked.  I just wrote off the WiFI (luckily it's a desktop and I can run a wire).  

I don't know what they changed after 7.10, but whatever it was made that card apparently unusable.  If you find a solution that actually works, let me know.  

PS...Acer Aspire L310

---

### Post by superprash2003 on 2009-08-15
do ensure that the wireless switch on your laptop is set to ON ..
for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by thalo on 2009-08-15
wonderful call.  i had tried pushing the wireless button (on my computer it doesnt specifically show on or off, just a button with a light behind it that flashes when on.  on my other laptop it is the same, though it doesnt light up in openSuse so i figured it might be the same on the 3002).  i hit the button and rescanned, and got the following results:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:0A:B6:7C
                    ESSID:"MANBEARPIG"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1A:C4:C7:26:E1
                    ESSID:"2WIRE734"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:12:88:2D:F9:51
                    ESSID:"2WIRE982"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning.
```now my network manager shows the wifi networks around.  so i guess that my card has been turned off for all this time.  the network manager shows it trying to connect, and it asked for the password.  now just to get an actual connection.

thanks for making me aware of the (hidden) obvious.
cheers

---

### Post by thalo on 2009-08-15
now i can see networks, and it is trying to connect but has not been successful yet.  some questions:

1.  does the network manager automatically detect if, being WEP security, it is 40/128 bit key or 128 bit passphrase automatically?
2.  i seem to be getting things going piece by piece, is there something else that i may be missing?  i have looked over some links from another thread
[http://ubuntuforums.org/showthread.php?t=1240669](http://ubuntuforums.org/showthread.php?t=1240669)
but so far nothing is working.

---

### Post by superprash2003 on 2009-08-17
are you certain its a WEP key? if so , try various authentication types and see if it works

---

### Post by thalo on 2009-08-17
i know it is WEP because once i tried to set up my linsys router to the isp proved router/modem to try some stuff out and i wanted to make it WPA but it wouldnt let me (something like that).

anyway...
i was reading over another thread 
[http://ubuntuforums.org/showthread.php?t=1241079](http://ubuntuforums.org/showthread.php?t=1241079)
and it was suggested to try the **route** command in terminal.  i did that just to see what would come out.  there was an ip address that i had not seen before (nothing special, just the last two number sets were different) when i had tried to ping the router earlier.  so i pinged it and now i have connection.  i think that part of it is the computer really needed some hand holding to lead it to the router and tell it where it should be connected to.

thanks for all your help and hopefully this may help someone else.
cheers
i am sure i will be back soon with other problems as i learn how to work ubuntu.

---

### Post by thalo on 2009-08-19
well, i had a couple good days of wireless connection even after a couple restarts.  i fired up the machine today and i am having the same problem as before, it sees the different networks but doesnt connect to the desired one.  no password/settings have been changed from when i did have connection, and the wireless card is on (the light flashes every once in a while trying to connect).

i have run the **route** command again, but it doesnt give any info and when i try to ping the router address it tells me that the network is unreachable.

any thoughts/help?
cheers

---

### Post by thalo on 2009-08-20
i am back

i think the problem was my wireless modem.  there was a problem with one of my desktops running xp, it wouldnt connect to the internet.  restarted the modem and now i have connection.

moral of the story:  make sure that all parts are working correctly, even those not directly connected to your computer.

cheers

---

### Post by thalo on 2009-08-25
i need more help (with getting my wireless working also).

my first go at it was an installation in windows to see how ubuntu was, with the intention to wipe the hd clean and start with a new, complete install later.  so, all the previous stuff in this thread was under those conditions.  i figured if i could get the wireless going with that then i could with that then i could again.

i went through the processes again, but i have screwed something up.

lshw -C Network

```
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:1d:a1:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```sudo iwlist scanning
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```ndiswrapper -l
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 3: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with '-e'
WARNING: /etc/modprobe.d/blacklist line 9: ignoring bad line starting with '-e'
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
bcmwl5a : invalid driver!
```when i followed the Sampbar instructions and tried to install the bcmwl5a driver, it didnt take too well.  when i changed it to bcmwl5 it seemed to take.  i am confused why it would still refer to the bcmwl5a driver, unless there is some directing reference in the commands that were made from the .sh files given by sampbar.  i also blacklisted the bcmwl5 driver, in hopes that it would get rid of it and the 5a would take its place (i searched all around on how to uninstall a driver and followed the instructions which gave this as part of the directions).

so i dont know what i have done nor what to do to remedy the situation.  i would really appreciate some help on this.  i am not too frustrated (yet) but realize that i have really dug a hole for myself.
cheers

---

### Post by thalo on 2009-08-30
i think i figured out my problem.

i reinstalled ubuntu, to reset all the stuff i messed up before.  this time i made sure that i had and installed the most current versions of ndiswrapper-common and ndiswrapper-utils deb files before i started the sampbar instructions.  i put these two and the bcmwl5a.inf and bcmwl5.sys files on my desktop before starting the proceedures.

i rebooted, after following all the steps, and ran iwconfig and sudo iwlist scanning commands with no networks showing from the scan command.  made sure to hit my on/off wireless button and re-scanned.  i got connection.

even though it said that i had ndiswrapper-common and -utils installed, when i installed from the deb files, i re-installed to make sure all was okay.  i think that is why it didnt work on the first attempt.  also maybe because i connected with a wire and checked for updates (system-admin-update manager) before attempting to solve the wireless problem.

i hope that some of this info may help someone.
cheers

edit:
one thing that i forgot to mention is that after i ran the update manager and before i started the sampbar instructions, i selected ndisgtk from the synaptic package manager (it was not selected before).  i think/hope that it was getting all these updates current (and stuff) that got it going properly.

---

### Post by dbalascak on 2009-08-31
I finally got WEP working on a wireless Netgear card using ndiswrapper. NetworkManager does seem to recognise WEP 40/128 and WEP 128 Passphrase as the same element.  

I used 
WEP 40/128
Key Used uppercase A-F in the 26 character key
WEP Index 1(Default)
Authentication - Shared Key.

Do a *netstat -rn* to make sure the route table was flushed properly if you are switching between wireless and wired. The other thing is if you are running a firewall i.e. Firestarter.  The FW has an interface selection component to it.

---

### Post by kevdog on 2009-08-31
I thought b43 now supported the 4318 chipset rather than ndiswrapper.  Hmm, maybe that's incorrect.

---

