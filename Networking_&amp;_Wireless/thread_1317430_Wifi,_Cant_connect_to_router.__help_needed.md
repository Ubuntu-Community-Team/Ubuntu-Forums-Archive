---
title: "Wifi, Cant connect to router.  help needed"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by sonny123 on 2009-11-06
nearly got wireless working can see card & router but cant connect to router
am a noob to ubuntu and have spent all day trying to do this  ](*,)

set up ndiswrapper and i think the driver is working because i now have green [power] led blinking on my card where as is wasnt before. Both LEDs lit up when i install the driver in the System>admin>windows wireless drivers. but once driver is installed power LED just blinks, it never goes solid

I can see the router from the little network button on the toolbar  and progress bar is at about 85%.  when i select the wireless network it asks for my wep key

after entering the key the icon spins then asks for the default keyring pwd
I enter that the icon spins some more then asks for wep key again.  and again...

my router says its 64bit Wep but the key its asking for is 40/128 bit ??? does this matter

i also have entered the mac address of the router into the BSSID box on the edit netwok conections dialogue and the mac address of the card into the MAC address box

ive checked 'connect automatically' and 'available to all users'

 have followed instructions here to set up ndiswrapper
[https://help.ubuntu.com/community/Wi...er/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I  Disabled bcm43xx driver, b43 and b43legacy,  because it will conflict with ndiswrapper.

used this to disable
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist


here are all the outputs that i think are relevant
many thanks for any help

root@rock:~#** ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
lsmvnds : driver installed
    device (11AB:1FAA) present

i dont know what this means exactly is the driver installed? is there a problem with it?

when i goto [ndisgtk] System>admin>windows wireless drivers. i get a warning dialogue 'unable to see if hardware is present'  but i click okay and it shows me a window that displays the driver and says 'hardware present  yes'

if i click on 'configure network' button it gives a dialoggue 'could not find network configuration tool' but i can see the card details at system>admin>network tools, displayed under 'network devices' wlan1

sorry if this is a long post but im going round in circles!

more outputs:---

  **lspci**
[SIZE=1]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller[/SIZE]
[COLOR=Red]00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  [this is wired and working][/COLOR]
[SIZE=1]00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter[/SIZE]
[COLOR=Red]02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) [this is wireless card]
[/COLOR]
~# **ifconfig**
[SIZE=1]eth0      Link encap:Ethernet  HWaddr 00:90:f5:2b:bf:a4  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe2b:bfa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3050870 (3.0 MB)  TX bytes:682482 (682.4 KB)
          Interrupt:11 Base address:0x2000 
[/SIZE]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KB)  TX bytes:1128 (1.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:14:bf:bc:b6:9a  
          inet6 addr: fe80::214:bfff:febc:b69a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:14010000-14020000 

~#** iwconfig**
[SIZE=1]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
[/SIZE]
wlan1     IEEE 802.11g  ESSID:eek:ff/any  
          Mode:Managed  Frequency:2.412 GHz  [COLOR=Red]Access Point: Not-Associated[/COLOR]   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:eek:ff
          Power Management:eek:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


~# **lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:2b:bf:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.65 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 0
       resources: irq:5
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 03
       serial: 00:14:bf:bc:b6:9a
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+lsmvnds driverversion=1.53+Linksys,10/13/2004,3.1.0.36 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:19:42:ca:87:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**~# iwlist scan**
[SIZE=1]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning[/SIZE].

wlan1     Scan completed :
          Cell 01 - Address: 00:24:17:31:B2:81
                    ESSID:"O2wirelessC30B56"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:eek:n
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:21:04:CE:05:1A  [THIS IS NOT MY ROUTER POSS NEIGHBOURS ROUTER]
                    ESSID:"BTHomeHub2-JNGR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:eek:n
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

---

### Post by chili555 on 2009-11-06
> my router says its 64bit Wep but the key its asking for is 40/128 bit ??? does this matterNope.

If it is 10-characters, try putting it in 40/128-bit HEX. My system likes lower case letters, like 096c7f etc. and not 096C7F etc. If you are still using the default 2wire key (naughty! You should change it now), it's probably all numbers and no letters.

---

### Post by sonny123 on 2009-11-06
thanks for the tip chili 
it is 10 characters specified on the router (o2 wireless) all in caps  eg E3A598FAXX
I entered the 10 charecters in lower case e3a598faxx under the 40/128-bit, but still did not connect

i am most concerned by >  #** ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
lsmvnds : driver installed
    device (11AB:1FAA) present

i dont know what this means exactly is the driver installed? is there a problem with it?
and by 
>  ** iwconfig**
............
............
          Mode:Managed  Frequency:2.412 GHz  [COLOR=Red]Access Point: Not-Associated[/COLOR]   but am a noob with linux and only a slightly above average windows user

>  If you are still using the default 2wire key (naughty! You should change it now), it's probably all numbers and no letters.

i dont understand what you mean.
the specified key has numbers and letters. what is the default 2wire key? 

gonna resort to drinking some beer i think  LOL

---

### Post by chili555 on 2009-11-06
> it is 10 characters specified on the routerFor security reasons, it should be changed, but, since you are a new user, perhaps that's a project for another day.> I entered the 10 charecters in lower case e3a598faxx under the 40/128-bitDid you enter it in 40/128-bit *Password* or *Key*? I think you want ***Key***.> i dont know what this means exactly is the driver installed? is there a problem with it? Nope. It means the device and the driver are both present and ready to go.> Access Point: Not-AssociatedThat simply means that you have not yet successfully connected to your router.

---

### Post by Tony Ricena on 2009-11-06
I have had that problem also for a long time.  I personally removed security and just enabled limited mac address.  Basically that means only certain mac addresses can access the router via wireless.  But you can also just set up 128bit wep encryption and that works too.  Its your call

---

### Post by sonny123 on 2009-11-06
Thankyou again

yes did it set as
wireless security  'WEP 40/128-bit key'

i tried it under 128 bit passphrase aswell  it changed the key automatically to a much longer series of numbers and lowercase letters when i tried it possibly cos i saved something with the default keyring when i was trying it earlier.. but it didnt work under the passphrase 128 bit option with either uppercase, lower case or the really long series that it tried to change it to by itself

wep index is set to '1(default)'
and
authentication set to 'open system'

---

### Post by Tony Ricena on 2009-11-06
Ok, well does your router have limited mac address option?

---

### Post by sonny123 on 2009-11-06
> **Tony Ricena said:**
> Ok, well does your router have limited mac address option?

I dont know

how do i find out?

---

### Post by Tony Ricena on 2009-11-06
Login to your router and look for MAC Address Control under Wireless settings (might be different depending on your router).  I am using Belkin Pre-N and my other router Netgear N has these options, so Im sure you have it as well.  If you have it you enter your mac address and select "allow".  You can find out your mac address by typing ifconfig in the terminal, or your router could have it in the DHCP Client List if you have it.. good luck!:D

---

### Post by sonny123 on 2009-11-06
> **Tony Ricena said:**
> Login to your router and look for MAC Address Control under Wireless settings (might be different depending on your router).  I am using Belkin Pre-N and my other router Netgear N has these options, so Im sure you have it as well.  If you have it you enter your mac address and select "allow".  You can find out your mac address by typing ifconfig in the terminal, or your router could have it in the DHCP Client List if you have it.. good luck!:D

cannot find any such controlls when i log in to router
my router was provided by my ISP. (o2)  

I can find some settings but i cannot really change anything

UPnP is suppoted
physical address and network name are given
interface type is 802.11b/g

security mode is 'WEP'
Allow new devices is enabled automatically

but there is no way to tell the router to accept connections from the MAC address of my network card ,  if that is what your alluding to

but hey thanks! keep the sugestions/advice comming please!

---

