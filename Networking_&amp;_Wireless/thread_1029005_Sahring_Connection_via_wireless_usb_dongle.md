---
title: "Sahring Connection via wireless usb dongle"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by tednumber8 on 2009-01-02
I want to use my ubuntu desktop version as a simple server for my windows desktop to connect to the internet.

Is this possbile and how do I do it if it is?

I have a wifi usb dongle that works on ubuntu evrythings fine and i have it ubuntu connected to the internet via ethernet to my router.

Im really confused :-(

---

### Post by albinootje on 2009-01-02
> **tednumber8 said:**
> I want to use my ubuntu desktop version as a simple server for my windows desktop to connect to the internet.


Try, and see whether Firestarter can handle this.
-> apt://firestarter in Firefox.

---

### Post by tednumber8 on 2009-01-02
Im a noob. Please cn you explain all i want to do is to use ubuntu so that windows can connect to it via wifi usb dongle to connect to the internet essentially ubuntu being a firewall/server. Is it possible?

---

### Post by albinootje on 2009-01-02
> **tednumber8 said:**
> Im a noob. Please cn you explain all i want to do is to use ubuntu so that windows can connect to it via wifi usb dongle to connect to the internet essentially ubuntu being a firewall/server. Is it possible?

It is possible, install Firestarter first :

1)
-> System -> Administration -> Synaptic Package Manager 
search for "firestarter", select it, apply the changes

2) 
Start Firestarter

3)
At the "internet connection sharing setup" :
[http://www.fs-security.com/pics/wizard3.png](http://www.fs-security.com/pics/wizard3.png)
make sure to choose the right device for the local network

Here's an example description from the Firestarter website :
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Try it. If you have more questions about it, post back here if you like.

---

### Post by mrjohnston on 2009-01-02
If you have issues with firestarter let us know if you are interesting in just sharing your internet connection from ubuntu.  

I personally have always used this guide with success.
[http://ubuntuforums.org/showthread.php?t=91370&highlight=ics](http://ubuntuforums.org/showthread.php?t=91370&highlight=ics)

Does require some CLI work, but its not too involved.

---

### Post by tednumber8 on 2009-01-02
I have a wireless wifi dongle that is fully compatible with ubuntu. Only problem is I don't know how to configure ubuntu to share the internet connection wirelessly with my windows desktop.

Any ideas?

---

### Post by Tim Sharitt on 2009-01-03
I can't say I have much experience with it, but you can look at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) to see if that helps.

---

### Post by tednumber8 on 2009-01-03
nope I cant find the solution there.. :-(

---

### Post by tednumber8 on 2009-01-03
I want to connect my winmdows pc to ubuntu pc. The ubuntu pc has an ethernet cable attatched to router and one fully working wifi usb dongle. 

Please someone help without sending me a link to the page here about internet connection sharing because it doesn't explain how to do it through usb dongle!

I appreciate all your helps.

Thank You

Ted

---

### Post by tednumber8 on 2009-01-03
anyone have any ideas?

---

### Post by tednumber8 on 2009-01-03
I want o conmfigure my ubuntu server(GUI inteface) as an access poiny for my windows computer to connect to the internet but sadly I've no ideaq as I'm an absolute beginner just today!

I have a wirless usb device that i expect the windows com to connect to the ubuntu server.

HAs anyone got a tutorial for a beginner to do this?

---

### Post by tednumber8 on 2009-01-03
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
**Bus 003 Device 002: ID 0cde:0008 Z-Com Sitecom Wireless Network Adapter 100G+ WL**

How do I get the drivers for this installed?

Im a beginner by the way so please be kind :)

---

### Post by superprash2003 on 2009-01-03
has ubuntu recognized your usb ?? post output of ifconfig and iwconfig from the terminal

---

### Post by ieee488 on 2009-01-03
If you want to use ndiswrapper, read the Sticky at the top of the 1st page.

---

### Post by overdrank on 2009-01-03
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by tednumber8 on 2009-01-03
Im a beginner and that stick is very confusing :-( Please can someone explain when i go here   [http://cateee.net/lkddb/web-lkddb/P54_COMMON.html](http://cateee.net/lkddb/web-lkddb/P54_COMMON.html)

what happens next I dont see drivers on there but that is the correct usb device. Also I found the link to that here [http://cateee.net/lkddb/web-lkddb/P54_USB.html](http://cateee.net/lkddb/web-lkddb/P54_USB.html)

Please explain. I'll be delighted

---

### Post by tednumber8 on 2009-01-03
**> **superprash2003 said:**
> has ubuntu recognized your usb ?? post output of ifconfig and iwconfig from the terminal**

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:a6:15:8e  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fea6:158e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13086555 (13.0 MB)  TX bytes:936238 (936.2 KB)
          Interrupt:23 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800640 (800.6 KB)  TX bytes:800640 (800.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:60:b3:c9:76:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-60-B3-C9-76-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 


**and**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**Also when I search for drivers for my wirles device becasue I presume it is causing the problem I get this website but do not understand how to use the information to make it work**

[http://cateee.net/lkddb/web-lkddb/P54_USB.html](http://cateee.net/lkddb/web-lkddb/P54_USB.html)

---

### Post by tednumber8 on 2009-01-03
Bump.

---

### Post by tednumber8 on 2009-01-03
PLEASE PLEASE PLEASE someone help me or point me in the right direction I have endlessly searched for 15 hours and found nothing. Take pity on me please!

---

### Post by tednumber8 on 2009-01-03
I've now got my wireless usb drivers working using ndiswrapper but one more problem arises, when I use firestarter to share the connection and select it to be shared by Wlan0, it still doesn't work.. hmmmm wonder whats next on the agenda to sort this

---

### Post by tednumber8 on 2009-01-03
I have now got my wirless device and drivers working with the help of ndiswrapper but still confused as to how I now force it to share my internet connection with my windows desktop via the wirless usb adapter connected to my ubunut desktop.

I hope that this cn be answered as I'm at my wits end with firestarter as it seems to be problematic when choosing to share it over Wlan0.

Thanks gain everyone for your support and hope you're all enjoying ubuntu as much as I am.

---

### Post by tednumber8 on 2009-01-03
could the kind person that was here last night please return to help me lol

---

### Post by cabbiinc on 2009-01-04
> **tednumber8 said:**
> I've now got my wireless usb drivers working using ndiswrapper but one more problem arises, when I use firestarter to share the connection and select it to be shared by Wlan0, it still doesn't work.. hmmmm wonder whats next on the agenda to sort this

Could you sum up where your at? Your wireless now works but what's not working?

---

### Post by tednumber8 on 2009-01-04
I now have the wireless working but trying to create internet connection share using firestarter but thats not working because it always says "device wlan0 is not ready" 

Im starting to presume maybe device wlan0 is not my wirless adpater and maybe the sitecom wirless adapter isnt compatible for internet connection share. Can anyone confirm this?

Is there another way to do it apart from firestarter because I think that it could be the problem!

---

### Post by bsh on 2009-01-04
afaik you can not share internet (network) using only the wireless.
i think you want to do this: internet is received by your wireless on the ubuntu box, right? then you want this to go to the router and share it with the windows pc, right?
then just set up routing from wlan to eth0 (if that is your wired interface), then connect the lan cable from your eth0 to your router's wan port, and finally connect your windows pc to the router as normal.
btw, this is not that simple to set up, you must take care of dhcp and dns, and setting up routing properly on ubuntu is also not that simple.

---

### Post by tednumber8 on 2009-01-04
> **bsh said:**
> afaik you can not share internet (network) using only the wireless.
i think you want to do this: internet is received by your wireless on the ubuntu box, right? then you want this to go to the router and share it with the windows pc, right?
then just set up routing from wlan to eth0 (if that is your wired interface), then connect the lan cable from your eth0 to your router's wan port, and finally connect your windows pc to the router as normal.
btw, this is not that simple to set up, you must take care of dhcp and dns, and setting up routing properly on ubuntu is also not that simple.

There wouldn't be much point in me setting up an "internet connection share" then still continue to connect my windows to the router... It doesn't make sense!

---

### Post by tednumber8 on 2009-01-04
Ok I'm now deciding upon a different route to share my internet connection to windows via ethernet cable through LAN card.

So im connected to internet wirelessly on ubuntu but when using firestarter to share the connection via eth0 it doesnt work and says eth0 is not ready.

I understand that there may have been soemthing I should hvae done before configuring firestarrter but dont know what it is.

I have the network card on ubuntu linked up to windows network card via ethernet cable but still confused as to how I make that link work.

Can someone guide me please :-)

ta very much

ted

---

### Post by bsh on 2009-01-04
it does make sense. you won't need a crossover cable. the router gives you firewall protection, so you won't have to set up firewall on ubuntu and thus decreasing the load on the ubuntu machine.. you can share internet with other machines too. the router may help with dhcp and dns and stuff, which you otherwise have to put on your ubuntu machine...
and i could continue with other advantages, but do as you wish.
then skip the router and connect the two pc's with a crossover cable.

---

### Post by Iowan on 2009-01-04
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page for connection sharing?

---

### Post by tednumber8 on 2009-01-04
Mine is ubuntu weirlessly connected to the internet via sitecom wirless adapter(usb)

then I want this connection to be shared athrough somehow via etherent from network card to0 network card.

Does anyone understand how to do this?

r.

---

### Post by Iowan on 2009-01-04
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a connection sharing How-To... there's a link near the end for wireless.

---

### Post by tednumber8 on 2009-01-04
upon trying to stop network manager it says - command not found. 

why is the command not found and it works for everyone else?

---

### Post by tednumber8 on 2009-01-04
I've found these forums to be highly populated with people that dont know how to work or fix stuff, so in interest of that could someone please point me to where I can actually get someone that can help me set this bloody server up.


thank you

---

### Post by howefield on 2009-01-04
Write to "Jim'll fix it" !!

---

### Post by tednumber8 on 2009-01-04
[SIZE="6"]No Network Configuration tools found[/SIZE]










WHAT, can someone please recommend me somewhere I can get some advice and quick... please

---

### Post by cabbiinc on 2009-01-04
> **bsh said:**
> it does make sense. you won't need a crossover cable. the router gives you firewall protection, so you won't have to set up firewall on ubuntu and thus decreasing the load on the ubuntu machine.. you can share internet with other machines too. the router may help with dhcp and dns and stuff, which you otherwise have to put on your ubuntu machine...
and i could continue with other advantages, but do as you wish.
then skip the router and connect the two pc's with a crossover cable.

I think he makes a point here. You would need an ethernet crossover cable to make it work, not just an ethernet patch cable.

I have a slightly different situation. My Vista computer is connected to the internet, and it's also connected via 50' ethernet crossover cable to Ubuntu. On the Vista machine I went into Control Panel > Network and Sharing Center > Network Connection and added both local area connections to the Mac Mini Bridge (right click the locals and select Add to Bridge). I had to update the driver for the bridge and after that and configuring the Ubuntu's Network Manager correctly it's been working fine. I've also done something similar with an XP machine but that was a while ago and forget the exact steps. I do remember that it was extremely easy with XP though.

I'm sure someone can tell you how to do the same thing with Ubuntu as the bridge.

---

### Post by tednumber8 on 2009-01-04
How do I host a network between my ubuntu desktop to my windows desktop via my wirless adapter.

is it even possible or anyone that could possible show me how to do it properly.

everything i've tried always resulted in "wlan0" nt ready or even "eth0 not ready", that was mainly with firestarter. I am really new to all this and just need a little bit of guidance as to what this type of network is even called so I could google it too.

Please someone help me. Please

> mark@server-station:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@server-station:~$ sudo apt-get install network-manager-gnome network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
network-manager is already the newest version.
network-manager set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@server-station:~$ sudo gedit /etc/network/interfaces
mark@server-station:~$ sudo iwconfig wlan0 mode Ad-Ho
mark@server-station:~$ sudo iwconfig wlan0 mode Ad-Hoc
mark@server-station:~$ sudo iwconfig wlan0 mode Ad-Hoc
mark@server-station:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mark@server-station:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:80:09:40
                    ESSID:"SKY05101"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.

mark@server-station:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mark@server-station:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:a6:15:8e  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fea6:158e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15804175 (15.8 MB)  TX bytes:3652690 (3.6 MB)
          Interrupt:23 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:864100 (864.1 KB)  TX bytes:864100 (864.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:60:b3:c9:76:88  
          inet6 addr: fe80::260:b3ff:fec9:7688/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)



---

### Post by tednumber8 on 2009-01-04
I've came a cross lots of tutorials stating to go to **system > netoworking**

I dont have something in "system" called networking so I presumed it was where the two computer screens at top are.

This doesnt seem to be the case as it all the tutorials explain changin properties setting ip address etc.

Please can someone help or point me in the direction of a live help service as it has been 40 hours and counting and still no-one has solved my problem. Maybe this is why people avoid linux, but I like it. Please

---

### Post by Xanatos Craven on 2009-01-04
If you have the latest version of Ubuntu ("Intrepid Ibex" or 8.10), all graphical network configuration is done through Network Manager. Those "two computer screens at top" are its system tray icon. The tutorials you're looking at are most likely for older versions of Ubuntu.

---

### Post by tednumber8 on 2009-01-04
Oo tyhank you is any other tips cos i cant get network manager to stop or start or restart, but it is installed... im nearly about to fire computer folowed by me out the window :-(

---

### Post by tednumber8 on 2009-01-04
**iwconfig**

>  iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**ifconfig**

> eth0      Link encap:Ethernet  HWaddr 00:16:17:a6:15:8e  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fea6:158e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49172679 (49.1 MB)  TX bytes:5757197 (5.7 MB)
          Interrupt:23 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:980308 (980.3 KB)  TX bytes:980308 (980.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:60:b3:c9:76:88  
          inet6 addr: fe80::260:b3ff:fec9:7688/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:155783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144154984 (144.1 MB)  TX bytes:129237484 (129.2 MB)



**iwlistscan**
> 
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 02:18:DE:01:83:56
                    ESSID:"linuxserver"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:1F:33:80:09:40
                    ESSID:"SKY05101"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1E:74:63:8D:03
                    ESSID:"MarkeyMark101"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.



I want to connect windows to ubuntu via the wlan0(Sitecom Wireless Adapter Wl-125. 

So that ubuntu can act as the only connection point for windows to access the internet.

Can anyone solve this?

I will pay the first person to solve this £5 via paypal :)

---

### Post by Iowan on 2009-01-04
My machine (still on Gutsy) has network settings under System>Administration>Network - in addition to the "Manual network configuration" icon in upper right corner.

---

### Post by tednumber8 on 2009-01-04
First person to solve this mystery for me gets £5 via paypal. Please help me out

---

### Post by Iowan on 2009-01-04
> **tednumber8 said:**
> I've found these forums to be highly populated with people that dont know how to work or fix stuff, so in interest of that could someone please point me to where I can actually get someone that can help me set this bloody server up.


thank youYou will find that these forums are highly populated with people who have problems, and people who are volunteering their time trying to help solve those problems.  I can point you toward help pages (like [this]("https://help.ubuntu.com/8.04/serverguide/C/index.html") one), or (maybe) offer suggestions for specific questions.

---

### Post by Iowan on 2009-01-04
See if the file /etc/dbus-1/event.d/25NetworkManager exists - perhaps the new version of NM has it elsewhere (or numbered differently).

---

### Post by tednumber8 on 2009-01-05
does anyone know?

---

### Post by superprash2003 on 2009-01-05
you could use this for internet connection sharing [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. you could avoid the firestarter error by using static ip instead of DHCP

---

### Post by tednumber8 on 2009-01-05
eth0 - connects to router
wlan0 - installed and working perfectly

I want to share my internet connection via wlan0 to my windows desktop.

Problem is firestarter will not let it happen because "device wlan0 is not ready"

what is the solution and just to help I'll post ifconfig and iwconfig in half hour. Half an hour because I'm not at my home server right now. 

thank you everyone and I hope someone can help.

ETA: Outputs

> iwconfig wlan0
wlan0 IEEE 802.11g ESSID:off/any 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Bit Rate:2 Mb/s Tx-Power:32 dBm 
RTS thr:2347 B Fragment thr:2346 B 
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

> ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:17:a6:15:8e 
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::216:17ff:fea6:158e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:43132 errors:0 dropped:0 overruns:0 frame:0
TX packets:35888 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:49172679 (49.1 MB) TX bytes:5757197 (5.7 MB)
Interrupt:23 Base address:0xde00 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:19397 errors:0 dropped:0 overruns:0 frame:0
TX packets:19397 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:980308 (980.3 KB) TX bytes:980308 (980.3 KB)

wlan0 Link encap:Ethernet HWaddr 00:60:b3:c9:76:88 
inet6 addr: fe80::260:b3ff:fec9:7688/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:155783 errors:0 dropped:0 overruns:0 frame:0
TX packets:158407 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:144154984 (144.1 MB) TX bytes:129237484 (129.2 MB)


> iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wlan0 Scan completed :
Cell 01 - Address: 02:18E:01:83:56
ESSID:"linuxserver"
Protocol:IEEE 802.11g
Mode:Ad-Hoc
Frequency:2.462 GHz (Channel 11)
Quality:75/100 Signal level:-48 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=1
Cell 02 - Address: 00:1F:33:80:09:40
ESSID:"SKY05101"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:29/100 Signal level:-77 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=3
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 03 - Address: 00:1E:74:63:8D:03
ESSID:"MarkeyMark101"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:29/100 Signal level:-77 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=1
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK

pan0 Interface doesn't support scanning.



---

### Post by Copernicus1234 on 2009-01-05
I did some googling and it seems firestarter is a firewall that can do this. You can always try it.

---

### Post by tednumber8 on 2009-01-05
Yea but no matter what i've done or no matter how many guides I've followed firestarter **always** errors. "device wlan0 is not ready"

---

### Post by Tom--d on 2009-01-05
Why do you have Firestarter installed?

---

### Post by tednumber8 on 2009-01-05
> **Tom--d said:**
> Why do you have Firestarter installed?

I installed it under advice from other linux users, why not have it installed, is there something better?

---

### Post by tednumber8 on 2009-01-05
> Im about to purchase this  54Mbps Wireless PCI Network LAN Adapter 802.11g/b WP-RT2561T

[Link to Product on Ebay]("http://cgi.ebay.co.uk/Wireless-802-11g-54MB-PCI-Network-Card-MAC-LINUX-WIN_W0QQitemZ300284518335QQcmdZViewItemQQptZUK_Computing_Networking_SM?hash=item300284518335&_trksid=p3286.c0.m14&_trkparms=72%3A1301%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318")

I have a pc with these expansion slots

Two full-height PCI 2.3 slots, one full-height PCI Express x1 slot and one full-height PCI-Express x16 slot

Already connected is a graphics card(PCI?) and a ethernet network card.(PCI?)

[B]Will there be enough expansion slots to fit this also?

And just before I buy is this compatible with ubuntu?[/B]

(just recently downloaded so not sure what version this is but know I installed server then added gnome desktop)

---

### Post by cabbiinc on 2009-01-06
Would Firestarter help or hinder? Is it needed at all?

---

### Post by tednumber8 on 2009-01-06
Is it compatible?

---

### Post by tednumber8 on 2009-01-08
Will samaba automatically configure an internet connection share or just a fileshare?

IF not whats the best software or way to network together, as a file server and as a internet connection access point/server?

Based on networking windows and ubuntu together > ubuntu connected to net via eth0

---

### Post by tednumber8 on 2009-01-08
> root@server-station:/home/mark# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]



[B]Why does it fail, any explanation?

And Network manager > stop = no directory found[/B]

> oot@server-station:/home/mark# /etc/dbus-1/event.d/25NetworkManager stop
bash: /etc/dbus-1/event.d/25NetworkManager: No such file or directory


---

### Post by albinootje on 2009-01-08
Please post the output of this :
```

cat /etc/network/interfaces
lsb_release -a
uname -a

```

---

### Post by superprash2003 on 2009-01-08
samba client can mount both types of shares..

---

### Post by Iowan on 2009-01-08
It appears something is wrong (or corrupted) in your /etc/network/interfaces file (perhaps on line 1). Per **albinootje**'s suggestion, it would be helpful to see the contents of that file.

---

### Post by tednumber8 on 2009-01-09
**I for the life of me can not get this card to share internet connection.**

**iwlist scanning**

> mark@sky36908:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


**ifconfig**

> eth0      Link encap:Ethernet  HWaddr 00:16:17:a6:15:8e  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fea6:158e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3536784 (3.5 MB)  TX bytes:427813 (427.8 KB)
          Interrupt:23 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:618440 (618.4 KB)  TX bytes:618440 (618.4 KB



**iwconfig**

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


[B]
Has anyone out there had experience with this? I can't even find the windows drivers in non exe format as the ones in exe format cannot be extracted using cabextract. Mmmmm the wonderful world of linux lol[/B]

If you need any more outputs please let me know, I'm stuck but I'm sure someone there can help me out :D

---

### Post by tednumber8 on 2009-01-10
anyone know how I get the drivers for this, it seems to be working fine but not for networking, as in it's picking up wirless router but not allowing me to configure as networking device

---

### Post by tednumber8 on 2009-01-10
sorry but *bump*

---

### Post by tednumber8 on 2009-01-10
Im setting up internet connection share between Ubuntu and windows.

I've been looking through settings for my router and see that the box is checked - use router as DHCP server. Should this box still be checked if I'm going to use ubuntu as the server?

I'm a noob so go easy on me if what I say doesn't make sense :-)

ETA: also UPNP is switched on, is this necessary?

---

### Post by tednumber8 on 2009-01-10
I have ubuntu connected to internet via eth0

I want it to share internet connection via wla0

I've figured out to use firestarter but still don't understand how it works like if I configure it in firestarter, what SSID will it broadcast so my other machines can connect.

It's not as easy as all these tutorials say it is, never once have I seen a tutorial to confgiure the ICS over wirless, as I've most of it setup can you explain how I get my other pc's to connect to the firestarter ICS over wirless?

How do I configure this to work?

---

### Post by tednumber8 on 2009-01-10
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

This link explains sharing my ethernet connection through wireless however if fall at the first step and that is stopping network manager. 

No such file or directory. Is my best bet to get a copy on Feisty and scrap Intrepid because not yet have i managed to stop network manager to complete this process

---

### Post by tednumber8 on 2009-01-10
My two computers are no talking over wireless ad-hoc connection


Only problem is, the ICS still wont work because quite truly Firestarter still says wlan0 is not ready. Why they are both connected together right now. Im not sure for what purpose,all I know that finally something has happened... WAHEy

now whats next to egt the ICS up and running?

please someone reply. please

---

### Post by skern03 on 2009-01-10
> **tednumber8 said:**
> My two computers are no talking over wireless ad-hoc connection


Only problem is, the ICS still wont work because quite truly Firestarter still says wlan0 is not ready. Why they are both connected together right now. Im not sure for what purpose,all I know that finally something has happened... WAHEy

now whats next to egt the ICS up and running?

please someone reply. please

From your post, it's pretty hard to tell what you're trying to do and what you've got set up. It sounds like you have two PCs with wireless connectivity, and some point of presence like a wireless switch connected to the Internet.

Here's how I have my system set up:
Cable modem plugs into my LinkSys switch that has both wired and wireless connectivity. The switch is set up for DHCP. The address is 192.168.1.1, an internal-only IP address.

My house has Cat5 to some areas, so it's simple - set up DHCP, and the PCs connect, and lease IP addresses from the switch. Or I can set up hard-coded IP addresses.

Ditto for the laptops with wireless NICs. Either DHCP or hard-coded IP addresses.

There's no need in this setup for any Internet Connection Sharing (I assume that's what you meant by ICS).

If that's not what you have, and you're missing the wireless/wired router, RUN, don't walk, to your nearest PC store and purchase one. It will save you tons of grief (they're pretty inexpensive).

---

### Post by mikewhatever on 2009-01-11
What kind of thread title is that?!

I think it doesn't matter. When the box is checked, the router will hand out IP addresses dynamically, unless a computer asks for the static IP.

---

### Post by steeleyuk on 2009-01-11
UPnP allows applications to open and close ports automatically. So for example, when you BitTorrent client connects, it tells the router to open port 4531 (for example) and the router does it.

Before UPnP came around you had to go into the router config and manually tell the router to open that port. You might as well leave UPnP enabled, there aren't too many benefits to having it turned off.

---

### Post by tednumber8 on 2009-01-11
I really really want to share my ubuntu internet connection around the house to my xbox, laptop etc.

Only problem is I haven't seen a guide anywhere that works and when I use firestarter it doesn't work - "wlan0 is not ready"

Please someone explain this to me. Please!

I'll post whatever outputs you need to know, just someone that knows how own up to it and teach others so this incesent thread posting doesnt have to be endless!


Seriously this has been 2 weeks. Please don't make me give up. Help me, have some spirit. eveyone reading and ignoring :-(

---

### Post by tednumber8 on 2009-01-11
No No No, I don't want my other devices to connect through router, I want them to connect rhough ubuntu's wirless network card, afterall ubuntu is supposed to be used as a server and it seems very much that it ISN'T very easily setup to be a server.

Whats the point in a server if you're going to connect everything directly to a router?

---

### Post by tednumber8 on 2009-01-11
I want to share my ubuntu ethernet connection through wirless network card to other clients (xbox etc) but can't find a tutuorial, and no-one yet has give me any idea how to make it possible.

I've seen the firestarter tutorial but it doesn't make sense cos I never configure and SSID therefore it could never work and even if i do it without configuring SSID, firestarter always errors.

Someone somwhere knows how, why not share the secret then people wouldn't have to keep coming on here crying out for the answer.

PLEASE someone tell me it's possible and if so How is it possible?

---

### Post by skern03 on 2009-01-11
> **tednumber8 said:**
> No No No, I don't want my other devices to connect through router, I want them to connect rhough ubuntu's wirless network card, afterall ubuntu is supposed to be used as a server and it seems very much that it ISN'T very easily setup to be a server.

Whats the point in a server if you're going to connect everything directly to a router?

Your first post wasn't that specific. If you want to use Ubuntu as a server, then my suggestion is to download and install the server version of Ubuntu and post your questions on the Ubuntu Server forum.

---

### Post by tednumber8 on 2009-01-11
ubuntu server forum?

---

### Post by Cap'n Skyler on 2009-01-11
[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)
u should be able to get help there.

---

### Post by skern03 on 2009-01-11
> **tednumber8 said:**
> ubuntu server forum?

When you log into the Ubuntu formus:
[http://ubuntuforums.org/](http://ubuntuforums.org/)
you see a list of forums. The Server Platforms is just beneath the Networking & Wireless forum where you posted this thread.

The server download is on the Ubuntu home page:
[http://www.ubuntu.com/](http://www.ubuntu.com/)
There are two downloads, desktop and server. The server is on the right.

If you're not used to 'nix server admin, the server version can be a bit of a challenge. I'm a programmer, not an admin, and the Ubuntu server I have here regularly drives me crazy! :p

What are you trying to accomplish by funneling all Internet traffic through a single machine?

---

### Post by skern03 on 2009-01-11
> **tednumber8 said:**
> ...ICS still wont work because quite truly Firestarter still says wlan0 is not ready... now whats next to get the ICS up and running?

I just downloaded Firestarter to see what you meant, and found the Internet Connection Sharing tab. My suggestion is that you post a new thread, and in the Title, make it on-point to your issue. Maybe something like this:
> Internet Connection Sharing in Firestarter won't work with Wireless

I think I misdirected you to the server forum if this is truly your issue. Apologies.

---

### Post by Iowan on 2009-01-11
> **tednumber8 said:**
>  Should this box still be checked if I'm going to use ubuntu as the server? You will want only one DHCP server - EITHER the router OR the Ubuntu server - not both.

---

### Post by tednumber8 on 2009-01-11
I'm very new to ubuntu about 1 and a half weeks. I've spent these one and a half weeks trying to configure ubuntu to serve my other client devices as an internet access point.

Ubuntu is connected to the internet via ethernet and I should be able to share that connection to toher clients over wirless networking card.

eveyone says firestarter this and firestarter that but it's not that easy. firestarter ALWAYS errors. wlan0 is not ready - that is my wireless network card.

Has anyone got an idea of how I make this possible as over in networking and wirless no-one has gave me a suitbale solution and really I'm at my wits end.

People here do know how to do it otherwise they wouldn't use ubuntu.

Please help me

---

### Post by tednumber8 on 2009-01-11
bumped

---

### Post by handydan918 on 2009-01-11
I'd start by looking into that error...
> wlan0 is not ready

Why isn't it ready? What is the output of iwconfig? 
Yos may do better to post this in networking, and see if you can find an iptables guru to write you a ruleset for this.

---

### Post by tednumber8 on 2009-01-11
bump again

---

### Post by tednumber8 on 2009-01-11
[B]Network manager stop command is in title and below.

sudo /etc/dbus-1/event.d/25NetworkManager stop

This command does not work "no such file or directory"

How to stop it in intrepid.

Need to stop it to get on with a tutorial found here [/B]

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

### Post by ugm6hr on 2009-01-11
Closed.

[http://ubuntuforums.org/showthread.php?p=6533853#post6533853](http://ubuntuforums.org/showthread.php?p=6533853#post6533853)

---

### Post by Scarlath on 2009-01-11
I'm not awesome at these things but after doing some searching... I *think* it is "sudo /etc/init.d/NetworkManager stop" :)

---

