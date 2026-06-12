---
title: "Configuring WEP with DWL-G122 rev C1, Ralink RT73 drivers."
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Sondar on 2006-06-13
Hi, Everyone,

I've recently configured my laptop to use the DWL-G122 rev C1 USB wireless adapter. My experiences in setting this device up are recorded in this wiki page:
[https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT73](https://wiki.ubuntu.com/WifiDocs/Driver/RalinkRT73)

I am now trying to configure the device to use WEP encryption, but I'm not having much luck. For a start, there are two files to configure - a rt73sta.dat file, and the /etc/network/interfaces file.

Which one takes precedence? I would guess the dat file, as it is specifically mentioned in the driver sources, but then how does the interfaces file fit in?

All I know is that, whenever I enter 'ifup rausb0' to try and (re-)bring the interface, my whole system hangs.

Here are the relevant variables from the driver configuration file:

rt73sta.dat
```

[Default]
SSID=<my essid>
NetworkType=Adhoc
Channel=6
Authmode=WEPAUTO
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=<my WEP key, in hex>
AdhocOfdm=1
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
PSMode=CAM

```
All other variables have been commented out.

I've tried to use various combinations of iwconfig, iwpriv and so in the the 'interfaces' file to try and connect, but no luck.

The driver supports the following optional (private) parameters:
```

$ iwpriv
rausb0    Available private ioctls :
          set             (8BE2) : set 1024 char  & get   0
          stat            (8BE9) : set 1024 char  & get 1024 char
          get_site_survey (8BED) : set 1024 char  & get 1024 char
          get_RaAP_Cfg    (8BEF) : set 1024 char  & get   0
          auth            (8BE7) : set    1 int   & get   0
          enc             (8BE8) : set    1 int   & get   0
          wpapsk          (8BEA) : set   64 char  & get   0
          psm             (8BEB) : set    1 int   & get   0

```

Does anyone have any idea as to the commands I should give, and where I should give them, to enable WEP on my device?

---

### Post by ncruiser on 2006-11-12
I have the same usb card, but with the newest drivers, the system doesn't hang when ifdown/upping the interface. however, i didn't succeed yet to make it work with security, like for example WEP. Did you already?

---

### Post by FrodoB on 2006-11-12
Just ignore the rt73sta.dat file and make sure that it is installed   with all of its defaults that it came with.  The interfaces file will setup the device correctly. I am using a Belkin F5D7050 ver 3000 with the same chipset.

---

### Post by ncruiser on 2006-11-12
FrodoB, can you post your /etc/network/interfaces file please?

---

### Post by FrodoB on 2006-11-12
This is the relevant section:

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid Your_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto rausb0

The device is asleep before the "pre-up ifconfig rausb0 up" from what I can tell.

---

### Post by FrodoB on 2006-11-12
This thread contains what I had to go through to get the rt73 working with my Belkin. 

[http://www.ubuntuforums.org/showthread.php?t=296281](http://www.ubuntuforums.org/showthread.php?t=296281)

---

### Post by ncruiser on 2006-11-12
thanks, but i have already successfully installed the driver, and everything works fine without security. but when i configure a wep key, then when i ifdown and ifup, i get an error message saying it can't set Encode and can't set ESSID. when I do iwconfig, the essid isn't showed (just says "") and the mode is set on Auto, what -i guess- should be Managed.
iwlist rausb0 scan finds the network fine, says the essid and that the encryption is on. but I can't ping anything except the usb wlan card ip address. this is in Edgy.
In the router I configured security as WEP, 128 bit, and filled in a 26-chars long HEX string, which I also filled in /etc/network/interfaces, in the line wireless-key.
I just want some security, don't care if it's wep or wpa or whatever, if that might be easier to do.

---

### Post by FrodoB on 2006-11-12
You did make sure by copying a new copy of rt73sta.dat into the correct place and you used my working interfaces lines as well?

---

### Post by FrodoB on 2006-11-12
If everything is working then you really need to look hard at the keys. These cause a lot of problems at this point.

---

### Post by ncruiser on 2006-11-12
I tried with 64 bit, and a 10-chars hex key: 0123456789
I'm sure it's the same key in the router as in the /interfaces file.
yes your lines are the same, except I use a static ip address, which the interface also gets. 
and the dat file is the original, unchanged one.

but whatever I do, the mode stays on auto, the essid isn't showing (it's broadcasted in the router), and when i restart the networking it says can't set the essid and the encode things.
in the router, the channel is set to 6, could that be any problem?
what do you get when you type iwconfig ?

Edit: I changed the authentication type to OPEN instead of shared key, and added the line in /interfaces, and now it works. looks like shared key isn't supported...

---

### Post by FrodoB on 2006-11-12
So the open key did it?

I always run open key on wep.  Open is, believe it or not, more secure. If you do a search on the web there are some articles that explain this.

At any rate can we say that your problem is now solved or not?

---

### Post by FrodoB on 2006-11-12
Article that explains the open is the more secure:

[http://arstechnica.com/articles/paedia/security.ars/2](http://arstechnica.com/articles/paedia/security.ars/2)

Note this quote:

"Ironically, the most secure setting of this feature is 'open authentication', allowing anyone to associate with your access points, and relying on other methods to handle security."

After all you have to know the key to communicate at all.

Another site says:

"Contrary to most peoples' perception, "Open" authentication is considered safer to use with WEP because of a flaw in the 802.11 standards for the "shared" authentication algorithm."

Also see:

[http://seclists.org/security-basics/2005/Jan/0094.html](http://seclists.org/security-basics/2005/Jan/0094.html)

And finally note the last post of this: "Bottom line: Shared Authentication does not add any security, and may weaken your security. Don't bother with it."

[http://www.broadbandreports.com/forum/remark,8645211~mode=flat](http://www.broadbandreports.com/forum/remark,8645211~mode=flat)

---

### Post by ncruiser on 2006-11-13
yes, my problem is solved, thanks a lot!
for other people who would have the same prob, it just comes down to this.
this is the wireless section in my current /etc/network/interfaces

# D-Link wireless usb card
iface rausb0 inet static
pre-up ifconfig rausb0 up
pre-up iwpriv rausb0 set Channel=6
pre-up iwpriv rausb0 set AuthMode=open
pre-up iwpriv rausb0 set EncrypType=WEP
wireless-essid ILiveHere
wireless-key s:XXXXXXXXXXXXX
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
auto rausb0

the s: before the 13 characters key means string (i assume), so i can put a 
13 chars long ascii word. without the s: i have to use 26 hex chars. in the router i set a 128 bits ascii encryption, auth mode to open and everything works :-D
note that I use static ip. dns information is in /etc/resolv.conf instead of the interfaces file. it just says: nameserver 192.168.1.1
actually it wasn't that hard to get it working :mrgreen:

---

