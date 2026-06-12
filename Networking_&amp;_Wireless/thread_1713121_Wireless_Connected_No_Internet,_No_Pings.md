---
title: "Wireless Connected No Internet, No Pings"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by jage on 2011-03-23
Ubuntu 10.10 fresh install, I've gone through several troubleshooting guides, from everything I can tell it is set up and connected.  Linksys Wireless G WMP54G PCI adapter.  Downloaded and installed drivers, configured for my router.  Router is not broadcasting SSID.

Here is what I get, I'm at a loss for what to do next (FYI I masked part of the MAC addresses):
> jeremiah@rockhop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unmanaged
  Default:           no
  HW Address:        00:90:27:AA:AA:AA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [wireless manual connection] ----------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        00:18:39:AA:AA:AA

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Oak Hill:        Infra, 00:1D:7E:AA:AA:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    *wireless:       Infra, 30:46:9A:AA:AA:AA, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


lspci lists:
> 
00:12.0 Network controller: RaLink RT2561/RT61 802.11g PCI
iwconfig:
> 
jeremiah@rockhop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:46:9A:AA:AA:AA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
*with sudo iwconfig the Encription key matches

Ping router:
> 
jeremiah@rockhop:~$ ping 192.168.1.1 -c3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.8 icmp_seq=1 Destination Host Unreachable
From 192.168.1.8 icmp_seq=2 Destination Host Unreachable
From 192.168.1.8 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
pipe 3
*pings with ethernet cable connected

Checked logs in router:
> [DHCP IP: (192.168.1.9)] to MAC address 00:18:39:AA:AA:AA, Wednesday, Mar 23,2011 11:59:26So all good except I can't ping the router or any other device on the network unless the LAN cable is in... one of the help guides actually said, "If it says connected, someone should really write a guide for what to do next at this piont" and went on for if it didn't say connected.... so... what next?

---

### Post by BruisedQuasar07 on 2011-03-29
You may not have enough signal strength reaching the location or there is interference. If you have a cordless phone that operates in the 2.4 range, 
so do wireless routers.If there are other networks around your dwelling, especially if you live in an apartment, at least some are likely using the same channel as your router. 

Install wicd network manager and activate it (it will appear in your menu under "Applications" > "Internet". An icon willappear on the top right corner of your display,to the left of your wifi icon. Right click on it and you will get a list of Networks, including yours. Check the signal strength bars. You also get % of signal, security you're using and the channel. Note the channel.

Routers have 11 channels, 1-11. I had connection problems like yours until I 
found a channel that works well for the location of my laptops and gets no interference from other network routers. 

By the way, I found my alfa high gain USB adaptor never drops and always gets high speeds. Plug it in BEFORE booting and it just automatically works, no driver needed.

The internal card in my Thinkpad Edge (both run Ubuntu !0.10, the Edge has 64-bit; the Thinkpad T-60 with the Alfa USB has 32-bit. It's also possible that while you were setting up, some punk cracker began piggybacking off yourInternet. That can negatively affect you from keeping you from connecting to Internet to significantly slowing you down. Few do but all Router makers should instruct users to never have the router connected to the Internet service modem while they setup their router. 

Once you get wifi working, go into setup and do the following, change from default name and password for entering setup. Change the name and passphrase you gave your router. Shut off broadcasting (makes your network hidden and keeps out the punks. Out of sight, out of mind).

Make sure you select WPA2 security. A final measure I employ after I am sure I have everything working top notch is I use the MAC Address Filter. All Internet devices (including phones and Roku boxes, Play Station 3, etc) have a unique Internet identity, called a MAC Address. The "MAC" has nothing to do with either Apple or Mac Computers. You can get the MAC address of any device that has indows by going into prompt and entering IPCONFIG/all...They are other ways to get it. I believe it is listed in BIOS for example. Once you have the MAC for all your computers that will connect wifi, enter them in Router's settings under filter list and activate it. This way only listed computers and\or devices can connect.

Whenever I am not using Internet for a few hours or more, I either disconnect the Ethernet cable to the Internet or I power off my router (I power off before I go to bed or leave the house for the day). This gives crackers less opportunity to find and crack your Network.

Crackers are low level computer users who do not really know that much. Unfortunately, there are sophistocated crackers who write and distribute programs for these loons. Several of them are free Linux programs. They range all the way to programs that help a cracker find hidden Networks, their security type,
passwords, MAC Address.

Each layer of security requires time to penetrate and increasing sophistication. Since few people bother with security beyond WPA, your having layers will encourage crackers to piggyback or snoop other Networks.

Once I have everything up to snuff, I take other measures such as lower the broadcast range and strength of my signal and use powerful, high gain Alfa USB adaptors to make up for the lowered broadcast strength. I place my router on the floor and away from any window. The higher a router is placed, the better it can broadcast outside, beyond your dwelling.

--Bruised

---

