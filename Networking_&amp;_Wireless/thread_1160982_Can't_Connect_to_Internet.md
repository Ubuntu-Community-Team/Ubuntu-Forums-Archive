---
title: "Can't Connect to Internet"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by Mastermind1980 on 2009-05-16
Hi dear Linux (and hopefully Kubuntu) users!

I just Installed Kubuntu 8.0.4 and the first problem I had was getting internet to work.
I though it was the same as with windows; Linux is good and automaticially installs the drivers for my WPN111 Netgear USB Adapter....FAIL I had to install Ndiswrapper and install the Drivers for the WPN111. So I did, succesfully. But I still have these problems:

-the Adaptar doesn't start automaticially with Kubuntu it only starts when I put in this command in the konsole: sudo modprobe ndiswrapper
-I can see the networks once its active; but I can't connect to any of them! They keep saying Connection Failed, this happends with  Unsecured and Secured networks!

Please help me!

BTW I am eating: :popcorn: while wtriting this ;P

---

### Post by Mastermind1980 on 2009-05-16
Ok, update: Uninstalled KNetwork Mananger, installed wcid.
It doesn't detect my USB Adaptar now! and yes its on....
I heard I had to do something (editing a file) as root.
But I dont know how to login as root....

Help?

---

### Post by SuperSonic4 on 2009-05-16
To do something as root preface your command with sudo. What did it say to edit?

I think startup programs go into /etc/init.d - so wicd would be /etc/init.d/wicd - there may be a deamons line for you to edit

---

### Post by Mastermind1980 on 2009-05-16
when I used suda it said my account -mastermind- doesn't have the right permissions, it sais:

Error: "/var/tmp/kdecache-mastermind" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-mastermind" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-mastermind" is owned by uid 1000 instead of uid 0.

Then I get a empety text file, (I was supposed to have to file that I open with:  sudo kate /ect/modules. BTW: its not to add wicd in it but ndiswrapper.

---

### Post by SuperSonic4 on 2009-05-16
Hmm, it could be a sudo thing which is beyond my knowledge but there have been threads on it. Normally one would use kdesu for graphical apps as root. What if you try ```
kdesu /etc/modules
```.

---

### Post by Mr.Ice Cold on 2009-05-16
I have the exact same problem here! I have a WPN111 too and did everything that stands here, but nothing so far! I will continu doing what stands here until I solved the problem with you guys! I rlly hope I can fianlly use my kubuntu once this deccenia....

---

### Post by SuperSonic4 on 2009-05-16
KMenu -> System Settings -> Autostart is where scripts can go to run on boot, idk if you need to put in your password each time

---

### Post by piratelv on 2009-05-16
Hi
i have got a similar problem, I just a wpn111 and i did a fresh install of kubuntu (my first kubuntu install only had a ubuntu one before) but got nothing working. after some looking around here i got the windows drivers installed using ndiswrapper but no luck, can see networks but it just won't connect to them. Hope this threat brings some anwsers.

---

### Post by Mastermind1980 on 2009-05-17
The command
kdesu kate /etc/modulesDid work! It autostarts without me having to do anything, it only doesn't autoshutdown when kubuntu shuts down. Wich file for the autoshutdown (the command for wich text I mean)

But the wicd still doesn't detect my Adaptar  to use it!

---

### Post by Mastermind1980 on 2009-05-17
We have 140 views, but I wonder why only one person is really helping me.. :(

---

### Post by Mastermind1980 on 2009-05-17
> **piratelv said:**
> Hi
i have got a similar problem, I just a wpn111 and i did a fresh install of kubuntu (my first kubuntu install only had a ubuntu one before) but got nothing working. after some looking around here i got the windows drivers installed using ndiswrapper but no luck, can see networks but it just won't connect to them. Hope this threat brings some anwsers.

Because I assume you use max network security (WPA2), remove the KDE (kubuntu) standard network maganger and install WICD because the stabdard can't handle WPA2.

---

### Post by Mastermind1980 on 2009-05-17
Update: wicd can now see networks after I looked in preferences and added 'wlan0' next to 'wireless interface' Only it wont connect to anything. It tries to connect for a few secs then it stops and says its not connected to anything. Please help!

---

### Post by piratelv on 2009-05-17
> **Mastermind1980 said:**
> Because I assume you use max network security (WPA2), remove the KDE (kubuntu) standard network maganger and install WICD because the standard can't handle WPA2.
Yes i do. thanks i'll  try that in a few moments.

---

### Post by SuperSonic4 on 2009-05-17
Is your SSID hidden?
What is the output of ```
iwlist scan
```

---

### Post by pytheas22 on 2009-05-17
I think the WPN111 doesn't work with WPA encryption.  Is that what you're using?  I spent a long, long time last summer trying to help someone get his WPN111 to connect to a WPA-protected network in [this thread]("http://ubuntuforums.org/showthread.php?t=853762"), and we never really got it to work.  Using wpa_supplication from the command line, he was able to connect a few times, but the connection would drop within a couple of hours.

If your network uses WPA, you may be out of luck.  But just to check that your version of the WPN111 is the same as the one of the user I helped last summer, please post the output of:

```
lsusb
```

---

### Post by Mastermind1980 on 2009-05-17
> **pytheas22 said:**
> I think the WPN111 doesn't work with WPA encryption.  Is that what you're using?  I spent a long, long time last summer trying to help someone get his WPN111 to connect to a WPA-protected network in [this thread]("http://ubuntuforums.org/showthread.php?t=853762"), and we never really got it to work.  Using wpa_supplication from the command line, he was able to connect a few times, but the connection would drop within a couple of hours.

If your network uses WPA, you may be out of luck.  But just to check that your version of the WPN111 is the same as the one of the user I helped last summer, please post the output of:

```
lsusb
```

No, thats not it because I couldn't connect to a network without any security either :(

---

### Post by Mr.Ice Cold on 2009-05-17
Bump!

---

### Post by pytheas22 on 2009-05-17
> No, thats not it because I couldn't connect to a network without any security either

If you (and everyone else here with the WPN111 who can't connect) could please post the output of the following commands, it would help:
```

lsusb
sudo iwlist scan
uname -rm
ndiswrapper -l
```

Please also let me know the names of the wireless networks you're trying to connect to.

I think the next step should be to see if you can connect to the networks directly from the command line with WEP/WPA turned off.  If even that fails, then it's time to look at a new driver for the card (and there is indeed a good chance that switching to a different Windows driver would help).

---

### Post by Mastermind1980 on 2009-05-18
mastermind@ubuntu:~$ lsusb
Bus 005 Device 009: ID 08ec:0020 M-Systems Flash Disk Pioneers
Bus 005 Device 008: ID 12bd:a02f
Bus 005 Device 007: ID 046d:089d Logitech, Inc.
Bus 005 Device 006: ID 07b8:e004 D-Link Corp.
Bus 005 Device 005: ID 1385:5f01 Netgear, Inc
Bus 005 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:00cb Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000


mastermind@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:62:15:8A
                    ESSID:"DS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:80:C8:14:A3:A3
                    ESSID:"Quentin"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:15:F2:7A:C9:D6
                    ESSID:"HEIMERSTEIN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0




mastermind@ubuntu:~$ uname -rm
2.6.24-23-generic i686
mastermind@ubuntu:~$ ndiswrapper -l
netwpn11 : driver installed
        device (1385:5F01) present

---

### Post by Mastermind1980 on 2009-05-18
P.S.: I wanna connect to DS. But I tried Qeustin to because it doesn't have security.

---

### Post by pytheas22 on 2009-05-18
Mastermind1980: please disable the security on your router, then run these commands:
```

sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 mode managed essid "DS" channel 1
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

This should connect you from the command line.  Please post all output.  If even this fails, then we know there's a problem with the driver.

---

### Post by Mastermind1980 on 2009-05-18
Ill try that qeuntin before I remove all my security, that ok?

---

### Post by pytheas22 on 2009-05-18
> Ill try that qeuntin before I remove all my security, that ok?

The commands I gave you won't work if WEP is enabled.  You would need to add another line to deal with WEP.  But unless it's a major hassle for you to turn off WEP, I think it's better if you see if you can get online with security disabled; if that works, we can add in the line to negotiate WEP and see how that goes.

---

### Post by Mastermind1980 on 2009-05-19
Security set to none, then did the commands you said:

mastermind@ubuntu:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for mastermind:
sudo: /etc/init.d/NetworkManager: command not found
mastermind@ubuntu:~$ sudo iwconfig wlan0 mode managed essid "DS" channel 1
mastermind@ubuntu:~$ sudo ifconfig wlan0 up
mastermind@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:4d:39:ff:2b
Sending on   LPF/wlan0/00:18:4d:39:ff:2b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
egrep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.2 -- renewal in 36938 seconds.

[B]It says its connected in wicd.
But I can't open any webpages or log in to skype.[/B]
**Also I couldn't download pakages and it acts like it doesn't have internet at all.**

---

### Post by pytheas22 on 2009-05-19
It looks like it connected, but I think there may have been a DNS problem.  Try running the two commands in the terminal again, and when they finish, type:
```

sudo -s
echo 'nameserver 151.197.0.38' > /etc/resolv.conf
```

Then try accessing web pages.  If it still fails, please post the output of:
```

ls -l /etc/resolv.conf
ping -c 5 google.com
ping -c 5 74.125.67.100
```

---

### Post by Mastermind1980 on 2009-05-19
It didn't work at all this time! I rebooted my router + modem 3 times. Security was op none again but I got this:

mastermind@ubuntu:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for mastermind:
sudo: /etc/init.d/NetworkManager: command not found
mastermind@ubuntu:~$ sudo iwconfig wlan0 mode managed essid "DS" channel 1
mastermind@ubuntu:~$ sudo ifconfig wlan0 up
mastermind@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6744
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:4d:39:ff:2b
Sending on   LPF/wlan0/00:18:4d:39:ff:2b
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.



But I have even worser news. My dad wont let me restart the router anymore or acces it from the lan connected PC. So I can only change things that dont need a reboot and can be don from wireless..... ](*,)

---

### Post by pytheas22 on 2009-05-19
> It didn't work at all this time! I rebooted my router + modem 3 times. Security was op none again but I got this:

That's strange.  Were you within solid range of the router?  Did you try rebooting, or reinserting ndiswrapper by typing:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

And are you sure the WEP key wasn't turned on when you tried to connect?

The additional command for connecting manually with WEP turned on is to add a line like this to the sequence:

```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 mode managed essid "DS" channel 1
*sudo iwconfig wlan0 key **a1b2c3d4e5***
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

This assumes that your WEP key is a1b2c3d4e5 (it's not case-sensitive); you would replace that string with whatever the key actually is.  Also, if your WEP key is ASCII--meaning that it's a word rather than a hexidecimal string--then the command is more complicated.  And if your router uses restricted rather than open authentication, an additional step is also required.  On most routers this shouldn't be necessary, but it's all explained in [this thread]("http://ubuntuforums.org/showthread.php?t=571188").

---

### Post by Mastermind1980 on 2009-05-20
> **pytheas22 said:**
> That's strange.  Were you within solid range of the router?  Did you try rebooting, or reinserting ndiswrapper by typing:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```And are you sure the WEP key wasn't turned on when you tried to connect?

The additional command for connecting manually with WEP turned on is to add a line like this to the sequence:

```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 mode managed essid "DS" channel 1
*sudo iwconfig wlan0 key **a1b2c3d4e5***
sudo ifconfig wlan0 up
sudo dhclient wlan0
```This assumes that your WEP key is a1b2c3d4e5 (it's not case-sensitive); you would replace that string with whatever the key actually is.  Also, if your WEP key is ASCII--meaning that it's a word rather than a hexidecimal string--then the command is more complicated.  And if your router uses restricted rather than open authentication, an additional step is also required.  On most routers this shouldn't be necessary, but it's all explained in [this thread]("http://ubuntuforums.org/showthread.php?t=571188").

Sure security was off! Also I did do the modprobe again and rebooted my PC a few times. Any way to connect to WPA2-PSK [AES]cuz of my stupid dad who doesn't know a **** about PC's?

---

### Post by pytheas22 on 2009-05-21
> **Mastermind1980 said:**
> Sure security was off! Also I did do the modprobe again and rebooted my PC a few times. Any way to connect to WPA2-PSK [AES]cuz of my stupid dad who doesn't know a **** about PC's?

Connecting to WPA via the command line is much more difficult than WEP, and as I mentioned earlier, I don't think the WPN111 will work with WPA, unfortunately, based on my experience in [this thread]("http://ubuntuforums.org/archive/index.php/t-837751.html").  If you want to try to connect manually, however, instructions are available [here]("http://ubuntuforums.org/showthread.php?t=571188").

Unfortunately, I think you may be out of luck if you need to use WPA.  If that's the case, you should probably just spend 20 euro on a card that [works out-of-the-box in Ubuntu]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

### Post by Mastermind1980 on 2009-05-21
Maybe I am out of luck indeed and then I should just give it up :( .
I just wanted those freaky amazing linux Desktop Effects! Any program that makes them for windows?

---

### Post by pytheas22 on 2009-05-22
No, no desktop effects for Windows, unfortunately.  I'm sorry we couldn't figure out wireless out.  But you could always buy a cheap new wireless card...

---

### Post by Mastermind1980 on 2009-05-23
I am not going to buy another card because I just lost &#8364;405,- BUT: Maybe I am going to buy a PCI Wireless card. That may help! Kubuntu still on for a little while until I am sure I am really screwed.

---

