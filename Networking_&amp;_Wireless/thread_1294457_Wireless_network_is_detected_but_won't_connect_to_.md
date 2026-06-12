---
title: "Wireless network is detected but won't connect to WEP"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by danbaark on 2009-10-18
Hi,

I'm currently dual booting windows and Ubuntu 9.04 but am very new to linux. Initially I got the wireless to work at home (RTL8187b card) with ndiswrapper but no WEP. I've just moved to a house at Uni though with WEP wireless and although the network is detected in Network manager when I try to connect it just spins round for ages and then asks me for my WEP key again.

I'm using the key provided on the bottom of the router (o2 wireless) which works fine on my windows partition but I've read that that gets converted into a longer string by the router do I need that maybe and if so how would I get it?


-l shw network returned:

sudo lshw -c network
[sudo] password for dan: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:84:8f:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.69 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:8a:ac:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.53+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 8a:5b:19:3b:06:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



iwconfig returned:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Any help would be hugely appreciated.

Thanks

---

### Post by ajgreeny on 2009-10-18
You can only get that long string of the encrypted WEP keyword from the router as far as I'm aware,which means you need to get into the router setup page with your web-browser, often i92.168.0.1, but it could be different, I think, depending on the router itself.  You will then need a password, which may or may not be known to you, so perhaps this is not very helpful.

---

### Post by Bucky Ball on 2009-10-18
You could go into System->Administration->Network, unlock and click your wireless device then 'Properties' and make sure the details for you wireless card match what's in your router (ESSID and WEP key). Switch 'Enable Roaming' off. 

As mentioned by ajgreeny, you are going to need to get into the router config to get these details if you don't know them already. The WEP or WPA key on the bottom of the router is generally it on that style of router though. The ESSID seems to be what you are missing (name of the router or AP (Access Point)). 

Once you've made all the changes, open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo /etc/init.d/networking start
```

---

### Post by danbaark on 2009-10-18
Thanks very much for the reply,

Tried your suggestion but I still can't connect and the command you gave me returned:


$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

Have also tried using wicd but that didn't help either. I am wondering though my router says it uses a 64bit WEP key but ubuntu only gives me the option of a 40/128 key could this be the problem? 

Thanks for the help!

---

### Post by bkratz on 2009-10-18
> **danbaark said:**
> Thanks very much for the reply,

Tried your suggestion but I still can't connect and the command you gave me returned:


$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

Have also tried using wicd but that didn't help either. I am wondering though my router says it uses a 64bit WEP key but ubuntu only gives me the option of a 40/128 key could this be the problem? 

Thanks for the help!


From Wikipedia:

Standard 64-bit WEP uses a [40 bit]("http://en.wikipedia.org/wiki/40-bit_encryption") key (also known as WEP-40), which is concatenated with a 24-bit [initialization vector]("http://en.wikipedia.org/wiki/Initialization_vector") (IV) to form the RC4 traffic key. At the time that the original WEP standard was being drafted, U.S. Government [export restrictions on cryptographic technology]("http://en.wikipedia.org/wiki/Export_of_cryptography") limited the key size. Once the restrictions were lifted, all of the major manufacturers eventually implemented an extended 128-bit WEP protocol using a 104-bit key size (WEP-104).
 A 128-bit WEP key is almost always entered by users as a string of 26 [hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal") (base 16) characters (0-9 and A-F). Each character represents four bits of the key. 26 digits of four bits each gives 104 bits; adding the 24-bit IV produces the final 128-bit WEP key.
 A 256-bit WEP system is available from some vendors, and as with the 128-bit key system, 24 bits of that is for the IV, leaving 232 actual bits for protection. These 232 bits are typically entered as 58 hexadecimal characters. (58 × 4 = 232 bits) + 24 IV bits

---

### Post by danbaark on 2009-10-18
Ok thanks. Anything else I could try? Would really love to make Ubuntu my main OS but without working wireless I can't really.

It just doesn't seem to like the WEP (Wicd always hang up on acquiring IP address but I'm guessing it's the same problem)

Thanks guys

---

### Post by fanto on 2009-10-18
Hi there,

I'm brand new to this and having the exact same problem described above.  I have an eeePC 1005HA and am dual booting with windows.

I've also tried wicd as advised elsewhere.  With wicd the connection just hangs at 'validating authentication' (which would appear to me to be the same problem, but described differently).

I really want to use ubuntu on my netbook as the main os but, again, without wireless it's useless.

Any help would be seriously appreciated.

---

### Post by ajgreeny on 2009-10-18
As I said, use your web-browser to go to your router page and then the wireless security setup.  Mine looks like the attached pic.  I entered my passphrase in the box and the long alphanumeric appeared in the lower 4 boxes.  It is that long alphanumeric that needs to be entered in the wireless setup on your machines, I think, not the original passphrase.

---

### Post by danbaark on 2009-10-18
Thanks again,

I'm using the router supplied by O2 Wireless and it doesn't give me any of that. I've logged into the security section where it has the WEP encryption key (10 alpha-numerical digits) but this is just the key I've been using and it doesn't have the four boxes below or anything else telling me what key has been generated. 

I'm sharing the connection with 8 housemates who all have this working on windows so I can't really turn encryption off or change to WPA but is there anything else I can do to make this work? Any other way of figuring out what WEP key is being generated?

Thanks a lot!

---

### Post by danbaark on 2009-10-18
Have now tried connecting to random unsecured networks network manager found and again the two green dots light up but the icon just spins for ages and eventually says wireless networks now disconnected so I'm not sure that the problem is with WEP and not with my setup.

Please help?

---

### Post by bkratz on 2009-10-18
> **danbaark said:**
> Have now tried connecting to random unsecured networks network manager found and again the two green dots light up but the icon just spins for ages and eventually says wireless networks now disconnected so I'm not sure that the problem is with WEP and not with my setup.

Please help?

Did you actually have this working at anytime? According to
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

it should have worked out of the box and not even required ndiswrapper at all.  (as of 8.10)

See the above it may help you.

---

### Post by Bucky Ball on 2009-10-18
> **bkratz said:**
> 

... it should have worked out of the box and not even required ndiswrapper at all.  (as of 8.10)



+1

Exactly. ndiswrapper could well be the problem now. Whenever you install Ubuntu, plug in an ethernet cable, get updates and install ubuntu-restricted-extras immediately. It sure can save some screwing around.

ndiswrapper is a known nightmare.

---

### Post by danbaark on 2009-10-19
Thanks very much for that link. Could you tell me how to uninstall ndiswrapper completely so I can give that a go?

Again I really appreciate all the help so thanks everyone!

---

### Post by bkratz on 2009-10-19
> **danbaark said:**
> Thanks very much for that link. Could you tell me how to uninstall ndiswrapper completely so I can give that a go?

Again I really appreciate all the help so thanks everyone!



There is a thread (really long! 27 pages) which is about your device.  It starts in 2008 and continues on through August this year.  Here it is

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

It looks like a complete discussion on using your device with either ndiswrapper or natively.

---

### Post by danbaark on 2009-10-19
Hi thanks a lot! Followed the instructions in that post about replacing network manager with Wifi-radar and it seems to be working fine now!

Thanks again!

---

### Post by Bucky Ball on 2009-10-19
Good news. Please mark as solved. :)

---

