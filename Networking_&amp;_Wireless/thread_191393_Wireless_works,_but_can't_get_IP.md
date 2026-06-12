---
title: "Wireless works, but can't get IP"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by luc1fersflowers on 2006-06-07
Hello all, I'm new to this whole game and I feel as though I'm making a simple mistake(or something). Anyway, I have a Dell Inspirion 6000 with an IPW2915 internal network card. Everything works great, except I can't seem to aquire an ip address from my router. My router shows up when I scan for networks via "iwlist eth1 scanning", yet when i try to "dhclient eth1" it ends up timing out. I've also tried to give my card a static IP and then procede to ping the router, and that just times out too. Any ideas?

Thanks much to all the random acts of kindness out there, it's really driven me to swtich to linux, knowing that the community is so well integrated and supportive!

---

### Post by xtacocorex on 2006-06-07
Are you posting from a wired Linux connection?

Does your router have a WEP key? 

What commands were you performing to try and get the wireless card working?

If I have this info, I may be able to help you better.

EDIT: I'm assuming the following doesn't work:
```

sudo iwconfig eth1 essid <ROUTERNAME>
sudo ifconfig eth1 up
sudo dhclient eth1

```

---

### Post by luc1fersflowers on 2006-06-07
I just tried what you said, and it didn't work. it just says "No DHCPOFFERS recieved. No working leases in persistent database - sleeping."

---

### Post by xtacocorex on 2006-06-07
I wanted to you answer the questions.

I have my wireless working. If you get me the answers to my first reply, I might be able to formulate a fix.

The code I put up is what I would normally do and I wanted to know if that is what you did, so I'm glad you said that that didn't work.

If you are on a wired linux connection, you can download wifi-radar and use it to configure the interface.

```
sudo apt-get install wifi-radar
```

To run it:
```
sudo wifi-radar
```

It will bring up a list of WAP's and if you click on yours and then connect, it'll ask to create a profile, do so and it should connect. This will also start up during the boot process to make sure you have internet when you log in.

EDIT: You must have changed your post after I read it, but it might be something with the router config. Try wifi-radar and see if that gets it to work

---

### Post by Nyati on 2006-06-07
Hi

I am not connected to a wired linux connection on the machine that I'm trying to get my wireless working, and I was wondering if you could shed some light on my problem?

I have an IBM T30 with a built-in AIRONET Wireless Communications Cisco Aironet Wireless 802.11b device.

when I type: lspci

I get:

CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
Network Controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

When I tried to set up my wireless connection, my network was recognised which tells me that the in-built device must be working, but I can't connect to the internet?

Now when I go back to System>Administration>Networking the wireless connections don't appear anymore???

Can you help?

---

### Post by luc1fersflowers on 2006-06-07
[QUOTE=xtacocorex]Are you posting from a wired Linux connection?

Does your router have a WEP key? 

What commands were you performing to try and get the wireless card working?

If I have this info, I may be able to help you better.

EDIT: I'm assuming the following doesn't work:
```

sudo iwconfig eth1 essid <ROUTERNAME>
sudo ifconfig eth1 up
sudo dhclient eth1

```[/QUOTE]

I am running under a wired network.
My router does have a WEP key.
I'm not sure what all commands I've tried, being new to linux the commands don't stick in my head, but for the past two days i've been searching the forums and trying everything that i can come across within my ablity to understand and complete instructions competently.

---

### Post by luc1fersflowers on 2006-06-07
[QUOTE=xtacocorex]I wanted to you answer the questions.

I have my wireless working. If you get me the answers to my first reply, I might be able to formulate a fix.

The code I put up is what I would normally do and I wanted to know if that is what you did, so I'm glad you said that that didn't work.

If you are on a wired linux connection, you can download wifi-radar and use it to configure the interface.

```
sudo apt-get install wifi-radar
```

To run it:
```
sudo wifi-radar
```

It will bring up a list of WAP's and if you click on yours and then connect, it'll ask to create a profile, do so and it should connect. This will also start up during the boot process to make sure you have internet when you log in.

EDIT: You must have changed your post after I read it, but it might be something with the router config. Try wifi-radar and see if that gets it to work[/QUOTE]


I just installed and ran wifi-radar here are the results.

luc1fersflowers@luc1fersflowers:~$ sudo wifi-radar
Stale pid file.  Removing
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:ce:c4:76:ab
Sending on   LPF/eth1/00:13:ce:c4:76:ab
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13


Now it is just idling with the DHCP handshake, normaly it would run through a few more intervals and then quit. ](*,)  idk what to do!

---

### Post by xtacocorex on 2006-06-07
Try:
```

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```

This will shut down the network stuff and then start it again. 

When you make your WEP did, did you do hex or ascii? There is an option for the WEP key in wifi-radar for the type of key.

The command line version:
```

sudo iwconfig eth1 essid <ROUTERNAME> key <HEXKEYHERE>
sudo ifconfig eth1 up
sudo dhclient eth1

```

If the key is ascii:
```

sudo iwconfig eth1 essid <ROUTERNAME> key s:<ASCIIKEYHERE>
sudo ifconfig eth1 up
sudo dhclient eth1

```

---

### Post by luc1fersflowers on 2006-06-07
Results:
luc1fersflowers@luc1fersflowers:~$ sudo iwconfig eth1 essid claude key s:**********
luc1fersflowers@luc1fersflowers:~$ sudo ifconfig eth1 up
luc1fersflowers@luc1fersflowers:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:ce:c4:76:ab
Sending on   LPF/eth1/00:13:ce:c4:76:ab
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
luc1fersflowers@luc1fersflowers:~$ sudo iwconfig eth1 essid claude key **********
luc1fersflowers@luc1fersflowers:~$ sudo ifconfig eth1 up luc1fersflowers@luc1fersflowers:~$ sudo dhclient eth1 Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:ce:c4:76:ab
Sending on   LPF/eth1/00:13:ce:c4:76:ab
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by xtacocorex on 2006-06-07
After seeing that output, I think the problem is with the router. 

How long does the connection stay up if you do:
```

sudo iwconfig eth1 essid claude key ***
sudo ifconfig eth1 192.168.*.* up

```

Replace the IP with one in your IP range, probably not 0.1 or 0.254-0.255.

---

### Post by twotonz on 2006-06-09
Hallo,
actually, I was trying to fix the same problem with no connection, but using another thread. Hope it is ok, just to but in here, but I think I can save you lot here a bit of time. Regarding a problem with the router, I think you can rule that out. The reasons behind my opionon is that here at home, I have 2 Computers, both with simular mainboard, grafic, etc. Nr. 1 has a wlan with a ti acx chip, and works a dream. Computer nr.2 has a wlan with rt2500 chip, and is really boring, just occasionly I manage to connect, and then only for a few minutes. Sometimes the card lights up like a christmas tree, and other times it's as dead as a doo-doo. Tried stopping & starting the network, rebooting, manually configuring in the consule, running scripts to automatically find avail. AP's, standing on my head, etc. In the kernel log there is a mention of the card...
"Driver using old /proc/net/wireless support, please fix driver!"

#luc1fersflowers,
perhaps you could also have a look at the kernel log (menu-system-ksystemLog, under kde menu-system-controlcenter-systemprotocol under gnome, rough translation, I have everything here in german) , and find the point when x is starting, there somewhere, if present, you should see the above mentioned.

I am afraid I cannot offer any solutions, just figured you were going in the wrong direction, & if you are getting simular kernel messages regarding the driver, then at least we know where the problem lies

---

### Post by SharpBlade on 2006-06-09
Hi luc1fersflowers.  Sorry I can not be of much help.  I am currently experiencing exactly the same problems as you with a Realtek 8185 wireless NIC: I opened a thread yesterday in this forum to try to get some inputs to get around the issue.

My ADSL router can see my wireless card (plugged into a destop computer running Dapper) as being "associated" whereas it sees my working wireless (Windows laptop) as being "authorized".
I have the same DHCP errors as you:
[B]No DHCPOFFERS received.
No working leases in persistent database - sleeping.
...[/B]
and I did configure my Realtek 8185 with a static IP address but to no avail.
Just to be sure I also disabled the encryption.

I am going to track this thread and hopefully somebody wil have a great idea to help both of us!

---

### Post by jawrat on 2006-06-09
i had a similar problem which resolved itself when i simply rebooted the router.  must have been a caching issue or something.  

one other thing to watch out for is mac address restrictions on your router.  i have mine configured this way....and i had to manually add the wireless card's mac address to the list.

keep at it, you'll get it.

---

### Post by SharpBlade on 2006-06-09
I rebooted the router but this did not get rid of the problem.
I have no IP filtering enabled on my router.
This is really starting to kill me...

---

### Post by SharpBlade on 2006-06-10
I eventually got my Realtek 8185 working :D 

Call me stupid...the problem was that I did not save my ADSL router configuration and it was still configured to use WPA encryption when I was assuming there was no encryption.... possibly of some help for luc1fersflowers  	R.

---

### Post by v3n0m on 2006-06-10
hmm, I have exactly the same problem as the topicstarter, wlan card found, accesspoint found, but no IP...

I have a texas instruments ACX 111 chipset (usrobotics 5416 wireless turbo pci card), which should work with ubuntu dapper (at least, the 5410 card should, according to the compatibility list, which is the same card, only for pcmcia slots)

I tried the suggestions in this thread, but the problem still occurs.

unfortunately I don't have the possibility to connect to the internet via a wired connection, so I don't have internet at the ubuntu distro at the moment.

the router is configured without ip filtering, and with a wepkey, which is correctly filled in, in ubuntu.

anyone got a clue how to solve this?

thanks in advance :)

---

### Post by DerGuteMoritz on 2006-06-10
Same problem here, no DHCP fails for me running a minipci card by Toshiba (at least it says so) in my IBM T30 using the orinoco driver. This seems to be a Dapper related issue, no?

---

### Post by v3n0m on 2006-06-10
I guess I know why the problem occurs: it tries to get a DHCP handshake from the adress 255.255.255.255, and my router is on 192.168.2.1, but how the heck do you change the 255.255.255.255 adress in ubuntu :S

I don't know if it is a dapper-only problem, since I wasn't able to use my wlan-card at all in breezy.

btw, haven't used linux much, only few days, without my wlan-card, there is so much I can't do, so I hope somebody finds a fix which solves this problem for everybody :D

---

### Post by SharpBlade on 2006-06-10
v3n0m, the address 255.255.255.255 is a broadcast address that is listened to by all the TCP/IP hosts.  So, this is why it is used for the DHCP handshake and I think what you see is perfectly normal.

---

### Post by v3n0m on 2006-06-10
aah, thanks :)
never knew that, that explains the strange IP.
always thought that the dhcp broadcast should be sent to the router...

but not too strange I'm wrong here, since I'm a complete n00b on linux distro's, and in windows it was just installing the drivers, and good to go.

but who cares, IF it works, linux, and especially ubuntu, is a very nice alternative for windows.

V3N0M

---

### Post by Adam B. on 2006-06-10
Same exact problem with a new install of dapper and the texas instruments ACX 111 chipset.  It see's the card, see the access point in iwconfig, but fails to get an IP address via dhcp.  :(

---

### Post by LoclynGrey on 2006-06-10
I have the same problem with 6.06 & Dlink Airplus 650+. (Texas Instruments)
Had no luck with ndiswrapper, even though the correct driver is loaded.  Downloaded wifi-radar, which can see access point but cannot resolve DHCP. I've set the access point to open access, under the same wifi Dlink card in windows xp it connects with no issues.

---

### Post by ComplexNumber on 2006-06-10
[quote=LoclynGrey]I have the same problem with 6.06 & Dlink Airplus 650+. (Texas Instruments)
Had no luck with ndiswrapper, even though the correct driver is loaded.  Downloaded wifi-radar, which can see access point but cannot resolve DHCP. I've set the access point to open access, under the same wifi Dlink card in windows xp it connects with no issues.[/quote]
what do you mean by "it can't resolve DHCP"?

---

### Post by LoclynGrey on 2006-06-10
Sorry should really say it cannot get a IP address from the router.

---

### Post by Joehome on 2006-06-10
I have this same issue, but with a twist. I also have tried a Xircom realport WIRED card adn got the same error I get with the Dlink wireless and Linksys wireless card. Could this possibly be something with the PCMCIA aspect of this os? All 3 of these cards worked fine in Breezy. Any help is appreciated.
-Joe

---

### Post by twotonz on 2006-06-11
Hallo,
I seem to get the impression, that more & more people are having network problems under dapper. I have been nosying around all the threads, that seem to be connected with this, & to be quiet honest, find no common denominator. 
I - Various people are all experiencing very simular problems
II - It does not seem to be connected with any one driver/chipset
III - Many people had thier cards working at some point (mine included)
IV - Problem occurs running Gnome or Kde
V - In many cases the cards are recognised, but cannot connect
VI - A lot of people running the same cards are having little/no problems

Or am I wrong? The only thing that I can think of at the moment, we all have a "non-standard" packet installed, that is somehow messing things up abit.

Love & Peace
anthony

---

### Post by barrmulio on 2006-06-11
just subscribed to this because i have the same issue over at [http://www.ubuntuforums.org/showthread.php?t=188998](http://www.ubuntuforums.org/showthread.php?t=188998)

even on a fresh vanilla ubuntu desktop install i still can't grab an ip 
tried with and without wep, i get the "No working leases in persistent database - sleeping"

I'm on a Dlink dwl-g120 card on eth2, with a dlink 624 router.  One a wired connection, i have no issues (eth0 is wired to the same router).  The power led it on, the link one never blinks at all, and my router never sees an attempt to connect.

---

### Post by Tom^ on 2006-06-11
Same problem - different cards and router. I really really hate this. I'm thinking of changing distro to see if it helps.

---

### Post by twotonz on 2006-06-13
#Tom, (& all others having problems)
Before you give up, try.....
[http://www.ubuntuforums.org/showthread.php?t=188192&page=3](http://www.ubuntuforums.org/showthread.php?t=188192&page=3)

and look for the post from Ariel on page 4.

Following his instructions, and then typing "sudo modprobe ndiswrapper" did the trick, and took me about 10 mins to complete, give it a go!

Love & Peace
anthony

---

### Post by v3n0m on 2006-06-13
thanks for the tip, but unfortunately I can't connect to the internet at all (just can't connect the wire, not a ubuntu problem), so wireless is the only option for me.

ndiswrapper seems to solve most problems, but I just don't get why the usr 5410 card is in the compatibility list if the 5416 doesn't work after 5 days trying (5410 & 5416 are the same, only difference is the interface. cardbus VS. pci)

I've been trying a bit this morning, and I found out, that the accesspoint it accidentally connected to, wasn't an accesspoint, but my own pc :confused: 
on managed mode, the wlan card doesn't find a single accesspoint, while there are at least 2 close enough to be found by my windows installation.

both of them are protected (wep key), but even when I fill in the wepkey, doesn't matter how (network administration OR via terminal IWCONFIG), no effect.

it does save the key, I see that via iwlist wlan0 key, but I can't see the accesspoints.

any ideas?

---

### Post by twotonz on 2006-06-13
hi v3n0m,
oh-oh, it's not gonna be easy, but lets have a go, (feeling on form, now I have Internet again!). Your problem I can fully understand, wireless is also my only option. Sooooo lets start......
We have to look at this thing a bit logically
1-Card is being recognised, but a few questions are open, what driver is the kernel using? (sudo lshw) You have mentioned ndiswrapper, is the native driver "blacklisted"? Is ndiswrapper properly working? (lsmod).
2- To give a better view of exactly whats happening, and as it is a bit difficult when one is not sitting in front of the computer concerned, how about posting a bit of info, for example the output from ifconfig, iwconfig, & interfaces for a start. (I use an usb stick, or did use :-b ). I can then at least compare to mine, or perhaps someone else will get a "brain-storm".
3- A bit more basic, but try "sudo dhclient ra0" (if your interface is called ra0). Are the lights on the card lighting up? (Perhaps changing the settings from static to dhcp first).
4- Have you ever had an internet connection with your card under linux?

This is all I can think of at the moment, in order to try and point you in the right direction.

Love & Peace (to all)
anthony

---

### Post by v3n0m on 2006-06-13
thanks for your time :)

yes, I mentioned ndiswrapper, but haven't installed it, since I can't without internet connection I guess.....

my card is recognized like it should, it uses the acx-pci driver (which should be fine, it uses the acx-111 chipset).

I'll copy the outputs of the commands you mentioned to a usbstick, and post them here later today, I'm in windows right now.

the settings are set to dhcp as far as I know, they were set to dhcp in the network-administration app, and after doing IFUP wlan0, I see it is trying to get a dhcp handshake, but it doesn't seem to find an accesspoint.

and the card didn't ever work in linux, since I only use linux for a few days, and ATM only from a livecd, if the wlan card works, I might switch over to ubuntu / other distro, or make a dualboot, but I can't seem to find out why it doesn't find AP's :S

however, thanks a lot :)

---

### Post by twotonz on 2006-06-13
Hi V3n0m,
That's great! I have an acx111 in my other computer, and had little problems with it for weeks (apart from having to set the gateway by every boot, but that hangs with the fact that I have a nic aswell). I shall dig out all the stuff that I collected about this chip, and then I guess, we just have to compare the configs on my working computer, with your not-working (yet!) one.

anthony

---

### Post by v3n0m on 2006-06-13
that's very good news :D
do you also have a 5416 card from usrobotics (wireless turbo pci)?

it's very strange that it doesn't spot accesspoints on my pc, while my windows installation (on the same pc) finds 2 or sometimes 3...

will take a look at the iwconfig & ifconfig outputs in a few hours :)

thanks

---

### Post by twotonz on 2006-06-13
Hallo again,
I just have to pop out for an hour, but shall check this thread when I get back, do not panik, I will not leave you alone :D .
I do not have a USRobitics, I think my card is a lesser known one from Sitecom (really cheap), but it doesn't matter, it's the chip on the card that's important.
As regards to you finding AP's in Windoze, that does not surprise me, at least we know the card is working! It's all pointing to troubles with the driver, but we shall see.

anthony

---

### Post by v3n0m on 2006-06-13
ok, I copied the output from the commands, here it comes.
I only set the wepkey, essid, and the channel to my own settings, nothing else changed (besides the blanking of the wepkey, so you only see **'s)

here it is:

----------
ifconfig
---------
> 
eth0    Link encap:Ethernet  HWaddr 00:13:8F:41:6F:91
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2740 (2.6 KiB)  TX bytes:2740 (2.6 KiB)

wlan0  Link encap:Ethernet  HWaddr 00:C0:49:E2:BD:42
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0xe000

----------
iwconfig
---------
> 
lo          no wireless extensions.

eth0      no wireless extensions.

wlan0   IEEE 802.11b+/g+  ESSID:"wlan"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr: off
          Encryption key:****-****-**   Security mode: open
          Power Management: off
          Link Quality=41/100  Signal level=17/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

----------
interfaces file
----------
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

========================
I guess the sit0 thing, is the firewire connection of my soundcard.
if somebody has got a clue why it doesn't find AP's, please tell me.

thanks for your time twotonz :D

---

### Post by twotonz on 2006-06-13
Hi V3n0m,
Ok, that looks fine, I think the "fix" is not going to be so difficult after all. I quote from another post, from the days way back before i had my wlan going. Appartently, the kernel gets a bit confused about which driver to use, you just have to give it a pointer........

> Append the line
options acx firmware_ver=1.2.1.34

to /etc/modprobe.d/options

that's it! Restart the computer, and you should have wlan. Let me know if it works

Love & Peace
anthony

*****EDIT
me & my edit's. It may also be a good idea, to disable the nic's, in order to use the wlan, (just go to network settings, you can enable again when u need them), oh, and check that the router address is correct, & it is not using the route-address from the nic.

---

### Post by zupermanz on 2006-06-13
I dint know if this helps but i've solved my problems installing dhcpcd;
sudo dhcpcd eth1
and you have an ip...

---

### Post by v3n0m on 2006-06-14
[QUOTE=twotonz]Hi V3n0m,
Ok, that looks fine, I think the "fix" is not going to be so difficult after all. I quote from another post, from the days way back before i had my wlan going. Appartently, the kernel gets a bit confused about which driver to use, you just have to give it a pointer........



that's it! Restart the computer, and you should have wlan. Let me know if it works

Love & Peace
anthony

*****EDIT
me & my edit's. It may also be a good idea, to disable the nic's, in order to use the wlan, (just go to network settings, you can enable again when u need them), oh, and check that the router address is correct, & it is not using the route-address from the nic.[/QUOTE]

sounds good twotonz :)
will try that, but ATM I can't restart ubuntu, since it isn't installed yet.

I'll take a small disk, and install it, if I can get this to work, it would be a major improvement.

thanks for your idea, will open the pc in a moment, and attach the other drive.

will let you hear as soon as possible :)

V3N0M

---

### Post by v3n0m on 2006-06-14
sorry for the doublepost, but if you can read this, I'm online in linux :D:D:D

thanks so much for helping me, I've been looking for a long time, and you come up with the working solution :D

thank you so much :)

after adding the line you suggested, a simple iwlist wlan0 scan
gave me a list of networks, which previously gave me "no scan results"

well, I have a lot to learn about linux....

---

### Post by twotonz on 2006-06-14
Hello,
Wicked! Glad that I could help, but like I said, I was just quoting from another post, so not really my idea, we are proberly on the same level with understanding linux, so I'm learning too. 
Anyways, I wish you much fun, I have allways found surfing internet on a linux box so much more pleasurable as with windoze!

Love & Peace
anthony

---

### Post by v3n0m on 2006-06-14
well. I'm using windows for many years now, and I like it quite well, but I'm always open for trying something new, and I tried linux before, but never had the wlan card working, so the linux distro couldn't be updated, software couldn't be installed.....

And I like expirimenting with other OSes, and maybe I'll make the switch someday.

---

### Post by twotonz on 2006-06-14
Hi V3n0m,
OK, point taken ;-) , I too like 98% of the people here have also used windows (correct spelling this time) for many years, & to be quite honest, when WfW came out, I thought it was the best thing since sliced bread (or perhaps, since bread). Without MS most of us wouldn't even own a computer, but still, although I'm gratefull to Bill's money & marketing expertise, I am very pleased that Linus exists, and for the person that he is. When only more things on this planet would run along the same lines.............

Love & Peace
anthony (I'm not in love, just an old hippie)

---

### Post by william_nbg on 2006-06-25
[QUOTE=twotonz]Hi V3n0m,
Ok, that looks fine, I think the "fix" is not going to be so difficult after all. I quote from another post, from the days way back before i had my wlan going. Appartently, the kernel gets a bit confused about which driver to use, you just have to give it a pointer........



that's it! Restart the computer, and you should have wlan. Let me know if it works

Love & Peace
anthony

*****EDIT
me & my edit's. It may also be a good idea, to disable the nic's, in order to use the wlan, (just go to network settings, you can enable again when u need them), oh, and check that the router address is correct, & it is not using the route-address from the nic.[/QUOTE]


Thank you!!!

I upgrading my wifes computer to Dapper today and after losing her wlan (Dlink acx 111) and trying everything I know (never enough) I found this thread. Your simple solution worked great. 

Was it simply that it wasn't pointing to the new acx drivers??

---

### Post by twotonz on 2006-07-03
#William,
yep :D 

Love & Peace
anthony

---

### Post by neoresin on 2006-07-04
hey guys
i've been attempting to get an ip for a couple of days now, and this seems to be the same sort of problem i'm having, ie, getting ndiswrapper (and at one point, the bcm43xx driver, but not at the same time) working, but unable to acquire an ip using dhclient. i'm relatively new to linux (and ubuntu/kubuntu [i've got kubuntu 6.06, but that shouldn't make too much a difference, i don't think... i could be wrong though... heh]) but have gotten ndiswrapper working on SuSE 10.0 before. ANYway, i'm still stuck at this point. would any of you (perhaps twotonz?) have any recommendations? perhaps including the pointer for the drivers using ndiswrapper in the /etc/modprobe.d/options file for the bcm drivers? would you happen to know what to enter for the broadcom drivers? any help would be amazing. thanks a bunch!

brian

---

### Post by Bayleo on 2006-07-04
Hey Neo, check out this thread...

[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless)

---

### Post by neoresin on 2006-07-05
hey guy thanks for the reply

unfortunately, while the sticky was quite good, it still didn't address the problem of the dhclient not receiving any offers. i'm having the same problem that one of the other guys on this thread is having (i believe) where (sudo) dhclient eth1 gives me:
```
root@kubuntu:/etc/modprobe.d# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:4b:91:36:f3
Sending on   LPF/eth1/00:90:4b:91:36:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
and i've tried this both under ndiswrapper AND with the bcm43xx driver. BUT it only happens with the wireless connection, which leads me to believe it has to do with the wireless driver. BUT i've used this driver under SuSE 10.0 and gotten ndiswrapper to work. perhaps it has something to do with dhclient. what do the SuSE people use for dhcp? ... hmmm... *does some investigating...* ok so i don't know where i can find that. all it says on distrowatch is that they both use dhcp. so be it. personally i'm all out of ideas. thanks for your help (and perhaps any additional help anybody would want to throw at me)!

brian

---

### Post by twotonz on 2006-07-09
Hi Brian,
Just a few things I would like to throw in here. For one, ndiswrapper, is in my opinion a last resort, personally I have just don't like it. If you do use  it, you have to make sure the drivers are sitting on your harddrive, and try around with other drivers apart from the winxp ones (eg. win2000). A friend had the bcm chip in his laptop, unfortuantly for you, it worked pretty much "out of the box" so we didn't do any fiddling around with it. (Although then we were useing "breezy").
Another thing, normally I have here many active ap's, the last couple of days though, I just couldn't get an ip, today no problems, the only thing that has changed here is the weather! (last couple of days we had storms in Berlin).

Love & Peace
anthony

---

