---
title: "Broadcom 4306: Unstable WiFi in Lubuntu 13.04 and Network-Manager"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by JasonStonier on 2013-05-19
I am a complete newbie with Linux, so I would appreciate being treated like an idiot in any replies.

I have an old HP Pavilion ze2000 (Athelon 1800MHz with 500MB ram) which a few days ago I installed Linux on so now I am dual booting Lubuntu 13.04 with Windows XP Home. 

I followed a few tutorials and got the wireless drivers working (B43 Broadcom), and for a couple of days the WiFi was rock solid during which time the laptop was rarely switched off. However one day, during which nothing had changed to the software, the WiFi suddenly went unstable - sometimes staying up for tens of minutes before dying, sometimes dying after a minute or two. Each time I would have to go into Network Manager > view hidden wireless networks to get it up again.

This happens on all of three different wireless networks I have tested the laptop with Lubutu on, and does NOT happen with any other device connected to the same network, nor with the same laptop booted to WinXP. The physical WiFi switch on the laptop is on (I never touch it). In WinXP it shows a solid blue light when on; in Lubuntu the light flashes blue except when receiving data, in which case it pulses like a hard drive light with the data.

I tried downloading WICD as an alternative to Network Manager, but could not get it working - it failed with a d-bus error and I have no real understanding of Linux to solve that. I uninstalled Network Manager, then re-added it from the .deb files downloaded from the ubuntu packages online in a different machine (Network Manager package and the gnome front end). The same effect is present. 

In researching this, I saw in the WICD wiki that over-agressive power management of the wifi card could produce this effect, but running the suggested command in a terminal (something like 'Wifi0 power off', I don't recall exactly) showed that the particular card doesn't have driver-manageable power settings. The BIOS on this laptop is incredibly restricted so there's no way to change the PCI power saving options usually found in the BIOS.

I am at a complete blank - I don't know enough to start problem solving this, and it is driving me crazy!

Any help, walk-throughs, or tips would be appreciated.

---

### Post by JasonStonier on 2013-05-20
Bump

---

### Post by JasonStonier on 2013-05-21
It was fine yesterday, today it won't stay up more than two minutes. ANyone able to help? Because right now I am about to throw Lubuntu in the bin!

---

### Post by Mariane on 2013-05-21
Have you tried connecting through wifi-radar? I have no idea whether it would work better or not, I simply think it is better to try this than to trash your computer :)

---

### Post by JasonStonier on 2013-05-21
No, haven't tried that, mainly because I don't know about it! Thanks for the tip. I really am a complete beginner, and just don't know these things. Ay other advice? Thanks.

---

### Post by hobgoblinn on 2013-05-21
I believe* there was an update for this issue, try typing *sudo apt-get update *and let it find any missing network updates. On a side note, do you have drivers for your wireless cards? Sometimes an outdated driver can cause isses

[SIZE=1]*not 100% sure but after fixing my update issue my wireless adapter is no longer randomly stopping from working [/SIZE]

---

### Post by squakie on 2013-05-21
If by any chance you followed old instructions that told you to use ndiswrapper/ndisgtk, post back and we'll walk you through getting rid of that and use Linux drivers instead - that would help.

---

### Post by JasonStonier on 2013-05-22
Thanks for the replies.

I followed the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The card is a B4306 and I used the instructions for adding the B43xx drivers from the B43 (Internet) section under Quantal Quetzal. I used B43 rather than B43 legacy.

The behaviour is really strange, sometimes it is fine, others it is terrible. Sometimes a reboot cures it, sometimes not. I can't spot a pattern to it at all. If it was just on my network I would suspect my router (a 3G MiFi since I am in in Africa miles from the nearest broadband), but it is the same on other networks.

I last did an apt-get update two days ago, and the problem persists.

It is stable on a wired network, so it looks like just a wifi issue.

Yesterday I had a load of popup windows saying the Ubuntu had encountered a problem with a module, and in the details the module was Network Manager - now at the time I was trying to get wifi-radar to work (unsuccessfully) so there is probably a link.

I have to be careful with downloads because I have a hard 2gig monthly cap on data, since it using 3G, so any big updates or downloads I have to take my laptop into town where I can get free wifi at a coffee shop...one of the many pains-in-the-butt of being a charity worker in Africa :-)

---

### Post by squakie on 2013-05-22
Is it the rev 3 adapter?  If not you need to use b43-legacy.  

Use lspci to check - unless it's USB - if USB post back the output of lsusb.

---

### Post by JasonStonier on 2013-05-22
It is rev 03.

---

### Post by praseodym on 2013-05-22
Please check:
```

dmesg | grep b43
```
If a firmware file named ucode4.fw (or "5") is mentioned, install this firmware file:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by JasonStonier on 2013-05-22
I can't post the output of the command because I can't get Ubuntu to connect to the wifi at all today, but ucode4.fw is not mentioned. There are three lines...

broadcom 4306 WLAN found core revision 5
found PHY: Analog 2, Type 2(G), Revision 2
loading firmware version 666.2 (2011-02-23 01:15:17)

thanks,

---

### Post by praseodym on 2013-05-22
Which module is loaded?
```

lsmod | grep b43
iwconfig
rfkill list
```
You can also upload screenshots.

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Download the file directly.

---

### Post by JasonStonier on 2013-05-22
Thanks:

> jason@JasonPavilion:~$ lsmod | grep b43b43                   351918  0 
bcma                   39645  1 b43
mac80211              526519  1 b43
cfg80211              436177  2 b43,mac80211
ssb                    50628  1 b43
jason@JasonPavilion:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"3MobileWiFi-f98c"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 0C:37:DC:5A:F9:8C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


jason@JasonPavilion:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jason@JasonPavilion:~$ 




---

### Post by praseodym on 2013-05-22
Looks goo. I recommend pure WPA2-AES encryption. Please show also:
```

iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by JasonStonier on 2013-05-22
Thanks:
> jason@JasonPavilion:~$ iwlist chanwlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)


lo        no frequency information.


eth0      no frequency information.


jason@JasonPavilion:~$ sudo iwlist scan
[sudo] password for jason: 
wlan0     Scan completed :
          Cell 01 - Address: 0C:37:DC:5A:F9:8C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"3MobileWiFi-f98c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000112ffd260
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 0010334D6F62696C65576946692D66393863
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C0000FF00000000000000000000008000000000000000000000
                    IE: Unknown: 3D1601000300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


jason@JasonPavilion:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
jason@JasonPavilion:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b2:ec:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87192 (87.1 KB)  TX bytes:87192 (87.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:90:4b:f3:34:46  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fef3:3446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3999222 (3.9 MB)  TX bytes:611105 (611.1 KB)


jason@JasonPavilion:~$ 




---

### Post by JasonStonier on 2013-05-22
Security on the router is WPA/WPA2-PSK and the key is encrypted AES-TKIP.

---

### Post by praseodym on 2013-05-22
Try pure WPA2-AES (CCMP)

---

### Post by JasonStonier on 2013-05-23
Will do, thanks. I have a new router arriving soon so will try it then. I am wondering if it is an interplay with the router because on one network I have now tried it on it is fine, on two others it is not, and on one other it is intermittent. I just wonder if the router is dropping the connection for a few milliseconds and the Ubuntu client is just much more sensitive to it that my iPad or my Windows 7 and xp installs.

---

