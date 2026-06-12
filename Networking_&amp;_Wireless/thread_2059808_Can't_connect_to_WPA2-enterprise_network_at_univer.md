---
title: "Can't connect to WPA2-enterprise network at university"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by kemtnbkr on 2012-09-18
I am unable to connect with Xubuntu 12.04 to the wifi in the library at my university.  I am on that network right now on the same laptop, but booted into windows.  (Windows connects with no problems.)  

Network's specs are as follows (asterisks demarcate censored info):


[LIST]
[*]** Security Type:** IEEE 802.1x Authentication
[*]**SSID**: **edited**
[*] **Network Authentication:** WPA2
[*]** Data Encryption:** AES
[*]** EAP type:** Protected EAP (PEAP)
[*]**Authentication Method:** Secured password (EAP-MSCHAP v2 )
[*] **Credentials: **Username and Password
[*] **Trust Root Certification Authority: **GlobalSign Root CA
[*]**Certificate Issued to**: **edited**
[/LIST]
I followed instructions I found on my school's website for Ubuntu, although it was for 8.10.  Basically all it had me do was download the CA certificate from GlobalSign for use when trying to connect to the network.  I don't have much confidence that this step was completed satisfactorily; the names of the files didn't match exactly, so I had to apply some guesswork.


Anyways, that doesn't (to me) seem to be the biggest problem-- Once I try to connect, nothing happens for a bit, and then a popup window appears saying something along the lines of 'You need a username and password to connect to this network.  Please enter yours here'.  My username and password (both which I know are correct) are already in the proper fields; I press 'connect' and the process repeats, indefinitely as far as I can tell.  



Any suggestions for how to fix this?  I found a similar thread from '08 but it didn't have a solution affiliated with it.


Thanks in advance for any advice.


PS- I'm busy this week, and often won't be on campus/ need internet, so I'll likely be pretty slow to try solutions.

---

### Post by kemtnbkr on 2012-09-18
Realized I left out some potentially important info:

Running Xubuntu, my laptop's wifi works perfectly fine on both my home (WPA) and work wireless networks, so I think the driver is fine for it.  My laptop model is a HP Pavilion dv6, and my wireless adapter is:
"Intel(R) Centrino(R) Advanced-N 6200 AGN"

Thanks again in advance for any potential advice.

Also, everything is up to date, and I'm running kernel version 3.2.0-30-generic-pae

---

### Post by ranger1021994 on 2012-09-19
1)Go to network setings
2)Go to wireless
3)Click Add
4)Go to wireless Security
5)Select WPA/WPA2 Enterprise
6)Authentication : PEAP
7)In identity and anonymous identity enter your username and in private key password enter your password
8)Link your CA certificate on the CA certificate field
9)Enter the name of SSID in wireless (It should match the name of your college ssid...that what i do)
10)Click SAve
I guess that should be all

---

### Post by kemtnbkr on 2012-09-19
> **ranger1021994 said:**
> 1)Go to network setings
2)Go to wireless
3)Click Add
4)Go to wireless Security
5)Select WPA/WPA2 Enterprise
6)Authentication : PEAP
7)In identity and anonymous identity enter your username and in private key password enter your password
8)Link your CA certificate on the CA certificate field
9)Enter the name of SSID in wireless (It should match the name of your college ssid...that what i do)
10)Click SAve
I guess that should be all

I've been trying all that, save step 7; I left the anonymous identity blank.  I'll double check my CA certificate and try it with that additional setup.  Thanks, I'll let you know how it goes.  I should be able to test it out this evening at some point.

---

### Post by ranger1021994 on 2012-09-19
Try filling up the anonymous id also because i fill both at my college

---

### Post by kemtnbkr on 2012-09-19
Alright, I tried all the proper settings, including putting my username in both the normal spot and the anonymous spot too.  I also verified that i had the correct CA certificate.   Still no dice on connecting to the university wireless though.

I guess now I'll try connecting via terminal so I can see if any error messages appear.  Also, I don't know if it is still the case, but I have read in a few places that Network Manager can cause problems with connections, so I'll give it a try thru terminal.

I'll post results, hopefully later tonight, on any results (if any).

---

### Post by kemtnbkr on 2012-09-19
To start with, I'll post some output from some commands:

(Note that all of these are on my home network, which is working fine.)

```
$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3658]
    Kernel driver in use: r8169

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:0d:ee:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:239012 (239.0 KB)  TX bytes:239012 (239.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:0e:92:c8  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:14ff:fe0e:92c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32809035 (32.8 MB)  TX bytes:4881807 (4.8 MB)

```

```
$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        C8:0A:A9:0D:EE:49

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [The Network] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:23:14:0E:92:C8

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    
    *The Network:    Infra, 94:44:52:B3:D5:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 91 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

```
This last one, I removed all the other available wireless networks listed, as I live in the "student ghetto" and pretty much every other name is at least mildly offensive :lolflag:

```
$ sudo rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by kemtnbkr on 2012-09-19
Solved it!!!!!!!

I followed this thread: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

For others having this problem, Here are the steps I took:

0. Make sure wpasupplicant is installed

1. Removed network manager from startup apps; logged out and logged back in

2. changed my /etc/network/interfaces to:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wpa-ssid **censored**
wpa-ap-scan 1
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-EAP
wpa-eap PEAP
wpa-identity **censored**
wpa-password **censored**
wpa-phase1 fast_provisioning=1
wpa-pac-file /home/kyle/Downloads/chain2.cer
``` 

3. With terminal:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo dhclient wlan0 -v

```

4. wha-BAM!! Connected!!


Now, I still have work to do to clean up the mess I've made with my system.  I still would like to use network manager to manage my other connections.  I need to make sure I haven't screwed my other connections up with this fix.  I need to automate the process, at least somewhat, of getting connected.

However, all that is doable.  

Signing off from the university network,

and thanks for the replies, although I just needed to read more stuff to find my solution.


Oh yeah, now to work on my homework I've neglected for the past 2 hours.........

---

