---
title: "Bad Password Asus-n13"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by max1e6 on 2011-08-26
Followed all the posts to configure. I'm fairly confident I got it right. Network manager shows my wireless ssid connection just fine (also shows using wicd, with all green bars).

When I try to connect to my network it struggles for a while then pops-up with "Bad Password". (I positively have the password entered correctly.) This has been reproduced in two separate machines (Lucid & Natty). It has also reproduced on the Lucid machine after a reinstall.

So, I decided to wepcrack the connection and I found that when I monitor my wireless network ssid, it repeatedly dropped-out... failing to secure a handshake. Again, my signal is very strong.

Although it's of no use to me, this adapter connects without a glitch on Windows.

I saw a similar post @ thread t=182398. No resolution there.

Any ideas?

---

### Post by praseodym on 2011-08-26
Hi,

network-manager and wicd dont work in parallel. Deactivate NM, login again and try it again. Does your router work in DHCP-mode? Firmware is up-to-date?

---

### Post by northd_tech on 2011-08-26
You might want to take a look at post #5 on the following thread if you are getting "Bad Password" errors (and you are certain that your password is correct- including **CaSE**).

[B]wicd wpa_supplicant "bad password" problem & workaround (wireless connection)
[http://ubuntuforums.org/showthread.php?p=11190843#post11190843](http://ubuntuforums.org/showthread.php?p=11190843#post11190843)
[/B]

---

### Post by max1e6 on 2011-08-28
Network-manager completely uninstalled. WICD installed.

Tried the other fixes in the recommended post.

Still see the network with the usb but "bad password." 

Then, turned off, removed usb, installed an old pci wireless. It finds network and connects. Same password.

---

### Post by northd_tech on 2011-08-29
I've been reading about all sorts of issues with various USB wireless interfaces under Ubuntu lately.  The fact that the old PCI wireless card worked relatively painlessly leads me to believe there is a bug, conflict, disconnect, or 'void' in your ASUS N13 USB driver module with either the **wpasupplicant** or **wireless-tools** packages somewhere in the router authentication process.  I'm not certain why that is manifesting as a "bad password" though- perhaps that is the 'default case' when wpasupplicant gets confused and/or times out.

For the benefit of Ubuntuforums readers, here are links to some of the documentation and packages involved.  It might be worth re-installing those 2 packages to see if that somehow helps get  connected.  I'd also consider contacting the wireless interface manufacturer, but Broadcom and Realtek are the only 2 OEM's that have reasonably good wireless support from what I've seen personally.

**wpasupplicant** package
[http://packages.ubuntu.com/dapper/wpasupplicant](http://packages.ubuntu.com/dapper/wpasupplicant)

WPA Howto
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Network Manager Howto
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

WiFi Howto
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
[B]
wireless-tools[/B] package
[http://packages.ubuntu.com/search?searchon=names&keywords=wireless-tools](http://packages.ubuntu.com/search?searchon=names&keywords=wireless-tools)

Here are some more resources about ad-hoc networks and the new-ish WiFi Protected Setup (WPS) "pushbutton" wireless security:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

Bug #388553: Wi-Fi Protected Setup (WPS) not supported
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/388553](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/388553)

Blueprint: Integrate Wi-Fi Protected Setup in NetworkManager
[https://blueprints.launchpad.net/ubuntu/+spec/nm-wifi-protected-setup](https://blueprints.launchpad.net/ubuntu/+spec/nm-wifi-protected-setup)

Wi-FI Protected Setup supported? 
[http://ubuntuforums.org/showthread.php?t=1472847](http://ubuntuforums.org/showthread.php?t=1472847)

---

### Post by max1e6 on 2011-08-30
After reviewing posts in this and other forums it is clear that this device can be configured with certain distributions running certain kernels. Setup and configuration varies considerably. There are many posts where a user lost the device when upgrading kernels or distributions. If you mix and match your intuition and selected recommendations, you can often stumble upon a workout. Performance is marginal.

I pulled out several old and new Ubuntu install DVDs and installed them in VBOX machines. Sure enough, if you reproduce the kernel and distribution of a poster's machine, you can fly the device using some modification of his/her recommendations... failing utterly in most other cases. Sometimes WICD works, sometimes not. Sometimes versions of installed packages have to be forced to earlier versions. In recent kernels the native rt2870sta works. Other times installing 3rd party drivers works but you will need to edit several files before the make and move/rename files afterwards. Performance is never very good.

For example in a Natty VM, use the native rt2870sta, blacklist rt2800usb and rta2x00usb, and see t=1419504&page=6 post 58. This produces a working device with network-manager. You can obtain a marginal connection provided your signal is strong. The latency will be poor (pinging the router with 64 bytes will take 50 to 3000 ms... a Windows XP VM will take 0.5 to 5ms). Tweaking the limited iwconfig options will be unsatisfying. There will be no rt2870sta.dat file to edit. 

I could fly this device on a native install, but why bother. It's a great Windows device but it's not ready for Ubuntu primetime. I'm not mad though. Where else can you get 4 or 5 days of fun for $30. If you just want to use a wireless usb then avoid this one.

---

### Post by northd_tech on 2011-08-30
> **max1e6 said:**
> After reviewing posts in this and other forums it is clear that this device can be configured with certain distributions running certain kernels. Setup and configuration varies considerably. There are many posts where a user lost the device when upgrading kernels or distributions. If you mix and match your intuition and selected recommendations, you can often stumble upon a workout. Performance is marginal.

I pulled out several old and new Ubuntu install DVDs and installed them in VBOX machines. Sure enough, if you reproduce the kernel and distribution of a poster's machine, you can fly the device using some modification of his/her recommendations... failing utterly in most other cases. Sometimes WICD works, sometimes not. Sometimes versions of installed packages have to be forced to earlier versions. In recent kernels the native rt2870sta works. Other times installing 3rd party drivers works but you will need to edit several files before the make and move/rename files afterwards. Performance is never very good.

For example in a Natty VM, use the native rt2870sta, blacklist rt2800usb and rta2x00usb, and see t=1419504&page=6 post 58. This produces a working device with network-manager. You can obtain a marginal connection provided your signal is strong. The latency will be poor (pinging the router with 64 bytes will take 50 to 3000 ms... a Windows XP VM will take 0.5 to 5ms). Tweaking the limited iwconfig options will be unsatisfying. There will be no rt2870sta.dat file to edit. 

I could fly this device on a native install, but why bother. It's a great Windows device but it's not ready for Ubuntu primetime. I'm not mad though. Where else can you get 4 or 5 days of fun for $30. If you just want to use a wireless usb then avoid this one.
Hi max,

If you still have that Asus-n13 nearby, could you plug it in, restart ubuntu, and paste the output of the following commands if/when you get time (the diagnostic output might help someone here on the forum eventually):

```
lsusb
ifconfig
iwconfig
dmesg | grep rt28
nm-tool
sudo lshw -C network
sudo iwlist scan
cat /etc/lsb-release
cat /etc/modules
rfkill list all

```EDIT:  More as a note to myself, here is the Wicd forum (but I don't have an account there yet):

     [Wicd]("http://wicd.net/punbb/index.php")  » [Troubleshooting]("http://wicd.net/punbb/viewforum.php?id=2")
[http://wicd.net/punbb/viewforum.php?id=2](http://wicd.net/punbb/viewforum.php?id=2)

---

### Post by max1e6 on 2011-08-31
Here's the output from the Natty VBOX machine (that is connecting poorly). (Minor edits made to suppress false images.) Let me know if somethings amuck.  

:~$ lsusb
Bus 002 Device 002: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ ifconfig
eth0 & lo omitted for readability    

wlan0     Link encap:Ethernet  HWaddr ommitted  
          inet addr:192.168.57.29  Bcast:192.168.57.255  Mask:255.255.255.0
          inet6 addr: ommitted Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1293644 (1.2 MB)  TX bytes:59203 (59.2 KB)

:~$ iwconfig

wlan0     Ralink STA  ESSID:"xxx"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: omitted 
          Bit Rate=54 Mb/s   
          RTS thr=off   Fragment thr=off
          Link Quality=100/100  Signal level:-41 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ dmesg | grep rt28
{   30.116027} rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
{   31.855784} usbcore: registered new interface driver rt2870
{   46.645809} <==== rt28xx_init, Status=0
{   95.435880} <==== rt28xx_init, Status=0


:~$ nm-tool
NetworkManager Tool

State: connected omitted --------------------
 
- Device: wlan0  {Auto "xxx"} -------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           no
  HW Address:        omitted 

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *xxx:   Infra, omitted, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.57.29
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.57.1

    DNS:             192.168.57.1


:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
??     bus info: firewire@1   ??
       logical name: wlan0
       serial: xxx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.57.29 multicast=yes wireless=Ralink STA


:~$ sudo iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: omitted 
                    Protocol:802.11g/n
                    ESSID:"xxx"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-41 dBm  Noise level:-63 dBm
                    Encryption key=on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"


:~$ cat /etc/modules
lp


:~$ rfkill list all (nothing here, loads at plug)

a few pings

64 bytes from 192.168.57.1: icmp_req=188 ttl=64 time=21.6 ms
64 bytes from 192.168.57.1: icmp_req=189 ttl=64 time=19.5 ms
64 bytes from 192.168.57.1: icmp_req=190 ttl=64 time=3458 ms
64 bytes from 192.168.57.1: icmp_req=191 ttl=64 time=2453 ms
64 bytes from 192.168.57.1: icmp_req=192 ttl=64 time=1453 ms
64 bytes from 192.168.57.1: icmp_req=193 ttl=64 time=457 ms
64 bytes from 192.168.57.1: icmp_req=194 ttl=64 time=13.0 ms
64 bytes from 192.168.57.1: icmp_req=195 ttl=64 time=12.5 ms

---

### Post by wildmanne39 on 2011-08-31
Hi, post the results of this command please:
```
lsmod | grep rt2
```
Thank you

---

### Post by max1e6 on 2011-08-31
lsmod | grep rt2

rt2870sta    410104 1
crc_ccitt     12595 1  rt2870sta

---

### Post by wildmanne39 on 2011-08-31
Hi, I do not see anything wrong with the results you just posted, I suspected that there may have been another driver loaded as well, but that is not the case.

What kind of issue are you having with performance?
Thank you

---

### Post by nm_geo on 2011-08-31
Change the wireless router to WPA2 (only).  Others have had performance improvemnts by doing that... if you can. Remember if you do change that it will effect all users that hook up on the AP.  
 
*xxx: Infra, omitted, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 [B]WPA WPA2
[/B]

---

### Post by max1e6 on 2011-08-31
With the Natty install the performance problem is that the device is slow, choppy, and subject to crashes. Pinging the router with 64 bytes will take 10 to 50ms, with excursions to 3000 ms every 30 sec or so. (Note that a Windows XP VM will take 0.5 to 5ms steadily with the same device.) When viewing my connection in real time (say using aircrack-ng) the connection will drop the device as it momentarily becomes unresponsive - probably corresponding to the same effect that causes the intermittent 2000ms to 3500ms ping times. 

In the Lucid VM and in another Lucid native install, the same effect (I presume) is pronounced enough to crash either WICD or network-manager - throwing a "Bad Password" exception - before the connection is made. (Note that this occurs when WICD/NM are not installed side-by-side.)

Messing with the router is not an option. Ideally, the device should be willing to work with the various routers I encounter... all of my wireless PCIs are. Ultimately it's not the router or the device (it works in Windows). It seems to be either a glitch in the driver or some subtle failing in my implementation of it. 

Interesting puzzle.

---

### Post by wildmanne39 on 2011-08-31
Hi, the driver for your device is known to have issue connecting unless the encryption is set a certain way, here is a link it does not say that driver exactly but there are problems with all that brand of devices when using linux.

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)
Thank you

---

### Post by max1e6 on 2011-09-01
Thanks wildmanne39,

Gave it a try...no private ioctals:

root@bt:~# ifconfig wlan0 down
root@bt:~# dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

wlan0: unknown hardware address type 802
wlan0: unknown hardware address type 802
Listening on LPF/wlan0/
Sending on   LPF/wlan0/
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.57.1 port 67
root@bt:~# ifconfig wlan0 up
root@bt:~# iwconfig wlan0 essid "xxx"
root@bt:~# iwpriv wlan0 set AuthMode=WPAPSK
wlan0     no private ioctls.

From what I have seen this usually occurs with a driver glitch. Gave the r8.. drivers a shot too. No go. 

Using the previous setup, the device does scan and will go into monitor mode. I am connecting.  I had it in Natty only. Since then, I have it connecting in a Lucid 10.04 (Backtrack) machine. The Lucid machine performs a bit better than the Natty install. It's still sluggish, but the intermittent drops are improved.

---

### Post by wildmanne39 on 2011-09-04
Hi, your welcome! glad you got it working.

---

### Post by max1e6 on 2011-09-08
Just a final note:

(in 10.4) Although the adapter sees and makes a connection using the rt2870sta driver, it will not hold a monitor (say wepcrack/aircrack). But using the rt2800usb & rt2x00usb it will support wepcrack, but will not connect.

I simply need to switch according to my objective:

switch to enable connection:

root@bt:~/WepCrack# modprobe -r rt2800usb
root@bt:~/WepCrack# modprobe -r rt2x00usb
root@bt:~/WepCrack# modprobe rt2870sta

enable crack

root@bt:~# modprobe -r rt2870sta
root@bt:~# modprobe rt2800usb
root@bt:~# modprobe rt2x00usb

---

### Post by wildmanne39 on 2011-09-08
Hi, do you need help with this process?
Thank you

---

### Post by max1e6 on 2011-09-08
No,

Just posting the work-around. 

Thanks

---

### Post by wildmanne39 on 2011-09-08
Hi, your welcome! enjoy ubuntu.

---

