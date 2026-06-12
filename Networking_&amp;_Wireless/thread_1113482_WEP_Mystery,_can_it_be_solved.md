---
title: "WEP Mystery, can it be solved??"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by kilgore9 on 2009-04-01
Using Ubuntu 8.04 32bit on an Acer Extensa 5630Z.
Wireless card: acer nplify 802.11b g draft-n wlan

I cannot connect to routers using WEP or WPA security.  When I don't need these, like in a hotel or on an unsecured network, things work fine.  When I put in the WEP or WPA key, depending on which router I'm trying, it always bounces back, as if its the wrong password.  I know it is correct, and have the same problem on different routers.  I have tried using different versions of Ubuntu but the problem is always the same.  

Could it be a problem with the wireless card or driver?  I had to install an extra driver to get Ubuntu to recognize the card.  The driver (rt2860, i believe) was not the exact same number as the one given for my card but was supposed to work.  Maybe thats why it only works halfway?

Any help would be greatly appreciated!

---

### Post by freonchill on 2009-04-01
are you using network manager, going into the network and changing it, or manually editing the conf files?

---

### Post by kilgore9 on 2009-04-01
I am using the network manager.  I have also tried doing in manually in the terminal with no luck....

---

### Post by freonchill on 2009-04-01
check synaptic, see if wpa supplicant is installed (dont know if the exact synatax for it)

---

### Post by kilgore9 on 2009-04-02
Yes I do have the WPA Supplicant.  Going through the readme, it looks like I should be able to add my WEP key to the file etc/network/interfaces.  There is a readme on how to do that but it might as well be in sanskrit because I'm still not sure how to do that....

---

### Post by kilgore9 on 2009-04-02
just to clarify, and why I'm having trouble setting it up through wpa supplicant:
What I need to put in (somewhere) are three bits of info:
1) WEP key to access the router
2)Username (provided by my ISP)
3) password (provided by my ISP)

SO far I can't get passed the WEP point, as the network manager keeps asking me for it, as if it were a wrong or invalid password.  maybe what I need is to set up wpa supplicant and the etc/network/*interface with this info?  I've read all the readme's and manual files on this but can't seem to find what i'm looking for...

---

### Post by chili555 on 2009-04-02
> 2)Username (provided by my ISP)
3) password (provided by my ISP)May I please assume this is a DSL connection using PPPoE? Even if you provide a double-checked bullet-proof WEP password, if you do not provide a user-name and password, you will be denied a connection.

My last router and my DSL modem both allow me to set the PPPoE details; that is, user-name and password, so that my computers simply need to provide encryption details; WEP, WPA, etc. I suggest you try that first.

---

### Post by manadi on 2009-04-02
^+1

Also are you sure you are providing the password in the right format. There is a drop box which gives you options like hex etc.

---

### Post by wkulecz on 2009-04-02
There be bugs in WPA and 8.04.  My problem is even weirder.  

Initially I was a happy camper, after lots of web searching for the "right" 802.11g hardware for Linux I ended up with AirLink 101 AWLL3055 USB adaptor and AirLink AR525W MIMO router.  104/128 bit WPA worked out of the box as long as I used the 26 character Hex key, using Ascii or Passphrase wouldn't work at all.  But its been great for a couple of years (setup initially on 7.04).

Now it seems the transmitter on my router has partially died as I cannot connect from 8.04 and my Windows notebook can only connect when close to the router and even then gets a 1-2 mps connection.

So I buy replacements.  The Airlink AR430W (on sale for $10!!!) works great with my Windows notebook, but will only connect to my Linux box if I use open acces, then its fine.  So I try a Linksys WRT610N figuring I'd upgrade the wired to Gigabit ethernet and the wireless to draftN dual band with better than WEP security once I found the "right" draftN adapter for Ubuntu 8.04.

The WRT610N wouldn't accept my original WPA Hex key or the passphrase I used to generate it initially so I generated another, entered the Hex Key in into 8.04 and connection is strong.  Unfortunately the WRT610N I have appears dead on the Internet side failing to connect at all to my DSL modem! The LAN side works perfectly for SAMBA etc. but no Internet access!

So until this is resolved, I went back to the AR430W and used a Linksys WGA600N "wireless gaming adaptor".  Configured in on Windows for my WPA settings, enabled DHCP on it and let it reboot.  Unplugged it, and hooked it to the wired ethernet port on 8.04 and everything just worked!  Ubuntu thinks its got a wired connection, the gaming adaptor handles the WEP which I will update to WPA2 as soon as the WRT610N is replaced.

They make an 802.11g version of the game adaptor thats about $70, instead of the $100 for the draft-N dual band I got.  But considering the headaches with Linux and wireless, this may be the most pain free solution as I haven't had problems with wired networking on Linux since about RedHat 3.

You configure the gameing adaptor from Windows with fill support and then it just works to turn any ethernet port to a wireless connection -- I'd bought it for our new Direct TV DVR "on demand" function since I didn't want to run another ethernet cable, but hadn't had a chance to connect it yet.  Looks like I'll be buying another!

--wally.

---

### Post by kilgore9 on 2009-04-02
> **chili555 said:**
> May I please assume this is a DSL connection using PPPoE? Even if you provide a double-checked bullet-proof WEP password, if you do not provide a user-name and password, you will be denied a connection.

My last router and my DSL modem both allow me to set the PPPoE details; that is, user-name and password, so that my computers simply need to provide encryption details; WEP, WPA, etc. I suggest you try that first.

Thanks for your response!

Yes I am using PPPoE, which is how I connect through the (wired) DSL. I also have realized the problem that there is nowhere for me to enter my username and password...but since it won't even accept the WEP I figure that the problem starts there.  I have also tried with other routers that are configured how you describe but the WEP (or WPA in this case) always bounces back.

I would like to set the router to do what you say, but cannot seem to access it.  The standard IP for the router (siemens SL2-141-I) doesn't work... in other forums people keep saying that my IP must be "in the same range" in order for it to work, but I don't know what that means or how to check... But even if I do gain access, I still have the problem of Ubuntu and the WEP/WPA being accepted...

---

### Post by wkulecz on 2009-04-02
Its pretty universal that you have to setup the router with a web browser from a wired connection to setup WEP keys and PPPoE username and password.  If you haven't done this you are prety much dead in the water.

Sound like you need to use a cable to setup your router and throw away the windows software your provider gave you to connect to your DSL modem.

You may also have to do a "factory reset" to your router to undo any incorrect changes that are locking you out.  Proceedure varies, but usually there is a small switch you push with a straightened paper clip and hold in for 10 seconds or as the device is powered up.

The factory default for the old Siemen's router I had (not wireless) was 192.168.0.1, Linksys always seems to use 192.168.1.1 on their consumer line, so maybe Siemen's kept theirs constant, OTOH RTFM may be your only solution.

HTH,
--wally.

---

### Post by chili555 on 2009-04-02
I understand the administration pages for your Siemens will be accessed by opening [http://192.168.1.1](http://192.168.1.1) in a browser. If that doesn't work, see if there is a little reset button on the back or the bottom of the router which should reset it to factory defaults.

What does your WEP password look like? Is it like 'ilovecoldbeer' or is it more like 072f280e2bbb8ba...'? The first will never work and the latter in either 13 or 26 characters, will work.

Again, however, unless your DSL provider receives a username and password, either from your computer or from your router, you will not connect. I have never tried, but you may be able to get to the router, but not to the internet, with a correct WEP key.

From 'man iwconfig':> Passphrase is currently not supported.The reasoning, I assume, is that different manufacturers of routers use different algorithms to convert a phrase to a proper HEX or ASCII key.

---

### Post by kilgore9 on 2009-04-02
I've just been through a WEP/WPA Wild Journey.  I gained access to my router, and there was even a website to guide me through setting up the router from my internet provider. I could change the security from WEP to WPA-PSK, and chose a password with numbers and letters, actually just the WEP key that came standard with the thing, 13 characters (like "d6s5uutt45678" for example.)  In the end, it always appeared as if I was connected 100% though I could get no internet connection.  I know was entering the correct username and password, but it still wouldn't work.  Connecting using DSL with cable also stopped working at that point.  I set everything back to factory settings, set back my settings in Ubuntu, and now I'm sort of back to the start.
WPA-PSK seemed to work better in that Ubuntu didn't keep asking me for a password, but it still never really connected.  I'm skeptical if Ubuntu is sending the password correctly... But now I'm back to square one with the WEP key that bounces back....

With my old computer it was simple to enter in the WEP key, then also the username and password without having to go into the router, thats why this is new to me i guess...

---

### Post by chili555 on 2009-04-02
You seem to use WEP and WPA interchangeably, however, they are two different things and not equivalent. I suggest, for the moment, we stay with WEP and get the whole thing sorted and working. Then, if you want WPA, we can change. The trouble with changing several things at once is that you will have difficulty telling what is working and what is not.

I suggest you attempt to get back to the router's admin pages and see if you enter your username and password as in the attached. Then when you press 'Connect' the router should get an IP address. Then computers attached to it should have the internet.

---

### Post by kilgore9 on 2009-04-02
Yes I will stick to WEP for now.  I have all my settings back to where they were before I started tinkering.

Ok I have done like you say and have connected through the router, and the connection is working with the cable.  The router says that wireless is turned on, the little light is blinking too... but in the end it still won't connect.  next step?

---

### Post by chili555 on 2009-04-02
Let's try the manual method for now:```
sudo iwconfig wlan0 essid <your_router's_essid>
sudo iwconfig wlan0 key <your_13-character_HEX_key>
sudo dhclient wlan0
```Substitute your interface, if it's not wlan0.

Does it connect? Any error messages?

---

### Post by kilgore9 on 2009-04-03
Hey Chili,

OK I've tried what you ask.  giving the essid gives no problems, but when I give the key it say this:

kilgore@kilgore-laptop:~$ sudo iwconfig ra0 key "my13digitkey"
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "my13digitkey"

I remember somewhere along the line reading that you need to add "s:" in front of this kind of key so I tried:

sudo iwconfig ra0 key s:"my13digitkey"

And it was accepted with no error.

After sudo dhclient ra0, it gave me this error message:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:24:2b:32:21:8b
Sending on   LPF/ra0/00:24:2b:32:21:8b
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.





The strange thing is, once again, that Ubuntu shows that I'm connected to the Router, although its not really connected. 

Next step?

---

### Post by chili555 on 2009-04-03
If your key is really 13 digits, it's a HEX key and does not need s:. Are you sure you are using the right key? A 13-character HEX key will be numbers from 0 to 9 and letters from a to f.

If you think *my13digitkey* is actually your key, it doesn't qualify. Also the key should not be in quotes.

---

### Post by kilgore9 on 2009-04-03
Chili,

"my13digitkey" was just a place holder, I did use my actual key which is 13 digits, letters and numbers.  Just trying not to spill my passwords on the wofrum :).  It is printed on the bottom of the router as the WEP key, so you can't go wrong.  It is not HEX because one of the letters is not a-f (there is a g).  I guess that makes it ASCII?  I also know that the key works because I used it without trouble with my old laptop (macos).

I also tried entering the WEP key as a hexadecimal translation, a bit long string of numbers. It gives no error message, but also does not connect in the end, same story.

---

### Post by chili555 on 2009-04-03
> "my13digitkey" was just a place holderExcellent!

Here are some guidelines:> ASCII input

WEP 64: 5 digits
WEP 128: 13 digits

HEX input

WEP 64: 10 digits
WEP 128: 26 digitsSo it would appear that your 13 character key is, indeed ASCII. So you should enter:```
sudo iwconfig wlan0 essid <your_router's_essid>
sudo iwconfig wlan0 key **s:**01234efg...
sudo dhclient wlan0
```Please let us know.

---

### Post by kilgore9 on 2009-04-03
Yes this is what I tried before and it gave me the error message.  Heres the fresh one:

kilgore@kilgore-laptop:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 8648
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:24:2b:32:21:8b
Sending on   LPF/ra0/00:24:2b:32:21:8b
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2009-04-03
I wonder if Network Manager might be working against us. Please try:```
sudo /etc/init.d/NetworkManager stop
```Then run the three commands above and let us know the result.

Also, when you log into the administration page of the router, does it confirm that you are connected and have an IP address?

---

### Post by kilgore9 on 2009-04-03
The router does confirm that I am connected to the net, and I assume it gives an IP address...not sure how to check that.  At any rate, its set on DHCP to give it automatically.

I will try turning off network manager, but before I do, How do I turn it back on in case it doesn't work? Using "Start" instead of "stop" ?

---

### Post by chili555 on 2009-04-03
> **kilgore9 said:**
> The router does confirm that I am connected to the net, and I assume it gives an IP address...not sure how to check that.  At any rate, its set on DHCP to give it automatically.

I will try turning off network manager, but before I do, How do I turn it back on in case it doesn't work? Using "Start" instead of "stop" ?Almost. 'start' with a lower-case s.

---

### Post by kilgore9 on 2009-04-03
it tells me:

sudo: /etc/init.d/NetworkManager: command not found


I also looked in the folder /etc/init.d/ and NetworkManager is not in there...

---

### Post by chili555 on 2009-04-03
Hmmm. This is from post #3: > I am using the network manager.I wonder how you are using it if it's not there!

What does this tell us?```
cat /etc/network/interfaces
```

---

### Post by CyberMando on 2009-04-03
For WAP
auto wlan0
iface wlan0 inet dhcp
      wpa-ssid essid
      wpa-psk passphrase

for WEP
auto wlan0
iface wlan0 inet dhcp
       wireless-essid essid
       wireless-key key
       wireless-keymode open

These will work with most setups but there are more specific things you can add.

Actually the easiest way to use wireless is
sudo aptitude install wicd
It is very stable and usable and it will even configure you wireless to come up before you login.

---

### Post by kilgore9 on 2009-04-03
** cat /etc/network/interfaces**
auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0





iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto ppp0

iface eth0 inet dhcp
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.10





auto eth0





Strange that ra0, my wireless, is not listed there.

CyberMando, you mean I should add that to the interfaces file?  Or put it in the terminal?  I have not tried it with wicd yet....

---

### Post by xzero1 on 2009-04-03
Run ifconfig and post the results. This will tell you your connection status (the inet address is your routers local ip address. Remember you are connecting to the *router*; the router connects to the *internet*. Once connected to the router, you should be able to get further status *from* the router. The router must be set up correctly to complete the connection.

---

### Post by CyberMando on 2009-04-03
I mean that to have your system establish a wireless 802.11 connection on boot you should add one of those to the interfaces file. Which one you add depends on the encryption system your access point/router is requesting.

I recently saw another user who needed to get wireless running and then run pon to get connected. Are you in Italy by any chance?

wicd makes life quit easy if you need to find access points at different venues.

---

### Post by kilgore9 on 2009-04-03
I am in Germany...

Yes, I realize that connecting to the router is the problem.  I think it has something to do with the way ubuntu is sending the wep key...

Here is **ifconfig**

eth0      Link encap:Ethernet  Hardware Adresse 00:1d:72:ef:fa:22  
          inet Adresse:192.168.1.3  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21d:72ff:feef:fa22/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:55075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35524 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:81736711 (77.9 MB)  TX bytes:2881175 (2.7 MB)
          Interrupt:16 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1276 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:63800 (62.3 KB)  TX bytes:63800 (62.3 KB)

ppp0      Link encap:Punkt-zu-Punkt-Verbindung  
          inet Adresse:85.177.90.160  P-z-P:213.191.89.5  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metrik:1
          RX packets:54930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35353 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:80294498 (76.5 MB)  TX bytes:1947261 (1.8 MB)

ra0       Link encap:Ethernet  Hardware Adresse 00:24:2b:32:21:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:37255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6149 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6728745 (6.4 MB)  TX bytes:0 (0.0 B)
          Interrupt:17

---

### Post by kilgore9 on 2009-04-03
SOLVED!

After weeks of trying....

I installed wicd.  immediately I could connect wirelessly with no problem. 

Thanks all, especially chili, for the help!  I learned a lot along the way... :)

---

### Post by chili555 on 2009-04-03
> Thanks all, especially chili, for the help!Thank you for your kind words. Glad it's working.

---

### Post by CyberMando on 2009-04-03
One thing I want to warn you about in case you run into it. In /etc/network/if-up.d are anumber of scripts that get run when a network interface is brought up. Both ifipdown and network-manager run these scripts. wicd does not. So if you want to automount nfs or smbfs filesystems from /etc/fstab that will fail unless you put that in  the scripts for your connection. 

If that makes no sense don't worry about it, unless youstart to run into problems.

---

### Post by xzero1 on 2009-04-03
If ra0 is your wireless connection, then no inet address means no connection.  I think Chili is on the right track. This article has a lot of useful info including a troubleshooting section: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Encryption](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Encryption)

---

### Post by kilgore9 on 2009-04-04
Hey CyberMando,

Yes, that means nothing to me, so I won't worry :)

Like I said, configuring my router and then connecting using wicd did the trick.  jippi!!!!!!!!!!!!!!!!! :guitar:

---

### Post by an.elusive.one on 2009-04-04
I am having a similar issue to this one, and was curious about a command line someone mentioned earlier. 

I can connect just fine to any unsecure network, but with my own WEP enabled one I keep getting rejected.

We are setup on a 128-Bit Hex Key on Open System, Linksys Router. 

Netgear WG111v2 USB Adapter

Would this be the correct command line to enter into the Terminal?

sudo iwconfig wlan0 essid <your_router's_essid>
sudo iwconfig wlan0 key s:01234efg...
sudo dhclient wlan0

Reason I ask is because it was posted for the Original Poster's issue, but he is using ASCII so I wanted to be sure it was still the valid command regardless of the Key type.

---

### Post by kilgore9 on 2009-04-04
sudo iwconfig wlan0 essid <your_router's_essid>
sudo iwconfig wlan0 key 01234efg...
sudo dhclient wlan0

If sou are using a HEX key I believe you just remove the "s:" before your WEP key.... just out of curiosity, are you suing network manager or wicd?

---

### Post by an.elusive.one on 2009-04-04
Am using the Network Manager -- the wireless connection I am using for the time being is incredibly so.. I can't exactly download the wicd.

I checked the site but couldn't find an alternate means of downloading it. :<

---

### Post by an.elusive.one on 2009-04-04
Okay, I managed to get WICD installed and running, it recognizes all my networks and will still connect to the unsecured ones, but not my own WEP-Secured one.

:|

---

### Post by an.elusive.one on 2009-04-04
Anyt thoughts, guys? It inkered with the issue for house this morning and made 0 progress.

---

### Post by kilgore9 on 2009-04-05
Well now i have to confess.  I got the wireless running and it was doing fine for a couple days.... now all of a sudden I can also no longer connect to wireless.  It authenticates, and then tries to get an IP address, then just says "not connected".  For me this is typical Ubuntu, works one day, the next day it decides it doesn't want to anymore...

---

### Post by kilgore9 on 2009-04-05
Update.  I tinkered with the settings, basically unsetting them, then setting them back, and now I can connect again wirelessly...again typical ubuntu in my epxerience...I really don't understand this at all!

---

### Post by snickity on 2009-04-12
This thread solved my issue. In case anyone else is in the same boat...

I was being prompted to enter my wireless network key repeatedly by network manager it would attempt to connect and then ask me for the key again. 

Intrepid Ibex
network manager 0.7.0
Realtek 8187 USB wireless adapter
driver ndiswrapper
network key WEP HEX

Here is what fixed it. 

sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 essid <your_router's_essid>
sudo iwconfig wlan0 key <your_13-character_HEX_key>
sudo dhclient wlan0

thanks chili555!! 

Kilgore,

It looks like the IP address is renewed after 40,000 secs (11 hours). I am guessing that is why you had to redo it.

---

### Post by kilgore9 on 2009-04-13
I believe I had my IP reset thingy set to 0 seconds...but I'm not sure.  Anyways, since that one glitch I haven't had anymore problems.  Glad its working out for you too!
Anyone know how to mark this topic as "solved"?

---

