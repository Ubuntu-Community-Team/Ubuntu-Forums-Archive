---
title: "Linksys E1200 Wireless N Router"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2012-02-24
Bought a new Linksys E1200 Wireless N Router today. righy now I'm hard wired to the router and I have a good connection. Thats as far as I have gotten. The cd won't run under Wine. I can access the home page at [http://192.168.1.1/](http://192.168.1.1/). Theres a ton of stuff on there and I'm lost.

I assume that what I need is for my router and my adapter to have the same settings. So I also assume that I need to access the home page of my adapter (Lynksys wireless-g WMP45G) and determine its settings and then make both the router and the adapter have the same settings. How am I doing so far?

However, I am not able to access the adapter home page which should be something like 192.168.1.2 or something.
By the way, my old router address was 192.168.2.1. This new routers address is 192.168.1.1. Shouldn't they both have the same address?

Ok, guys. Thanks in advance for any help you can offer.

---

### Post by roelforg on 2012-02-24
May i note that the cd isn't needed?

IIRC most routers come w/o pass.
If you can find out what the SSID is, you could just connect and be done with it.

---

### Post by sofasurfer on 2012-02-25
I am completely lost.

When I installed my adapters a couple years ago I still was running Winblose next to ubuntu. So I was able to use the cd that came with the adapter. Ok, the cd is not needed, but know-how is, and I do not have know-how.
No cd and no know-how.

I am thinking that it would be best to buy a new adapter that is not only more compatable with the router but also a new adapter probably will be better supported by ubuntu. Correct? Any good ideas on completely compatable adapters that anyone can setup? USB is ok but I think cards are better. You tell me.

---

### Post by roelforg on 2012-02-25
> **sofasurfer said:**
> I am completely lost.

When I installed my adapters a couple years ago I still was running Winblose next to ubuntu. So I was able to use the cd that came with the adapter. Ok, the cd is not needed, but know-how is, and I do not have know-how.
No cd and no know-how.

I am thinking that it would be best to buy a new adapter that is not only more compatable with the router but also a new adapter probably will be better supported by ubuntu. Correct? Any good ideas on completely compatable adapters that anyone can setup? USB is ok but I think cards are better. You tell me.
Wait, what?
Your old dongle should be as compatible with your new router as with your last.
Just use NetworkManager to select the new network and go online.

---

### Post by agillator on 2012-02-25
Try this: disconnect your wired connection and reboot.  Network Manager should start up and start looking for a wireless connection. Wait a moment and then open Network Manager and see if your new router is listed as an available network SSID. I've forgotten what its name will be, but you should be able to identify it. If it does show up then go back and set up your wired connection again and set up the wireless connection information on the router, especially in wireless security select wpa/wpa2 and set up the passphrase. Keep a copy of the passphrase! Then you should be able to go back to Network Manager and set up a connection using the passphrase.  Let us know what happens and what you find.

---

### Post by sofasurfer on 2012-02-25
My wired connection that I made is named "linksys router wired". It works.
I disconnected the cable from the router and rebooted. In "network connections" my wired connection appears but that is all. Of course...how could a wireless connection appear if my adapter is not configured to it? Just thinking...
Ok, teach me more. Thank you for your help.

P.S. I just looked at the back of my usb adapter. It is dated 2007. You sure I shouldn't buy a new one?

---

### Post by oldfred on 2012-02-25
I just bought a new cheap N router. My 2006 Toshiba sees it just fine. I just used Firefox browser to connect and update its settings using wired Ethernet and its default address. Set a password on the router, I let Firefox remember the PW and bookmark it, in case I want to change or review settings.

The CD was for Windows only, so I downloaded a manual from the web site, but later found that searching the CD was a PDF copy of the manual that I could have used.

Basically you log in to the router. You want to change the name from the default, so you know its yours, you want to change to WPA2 and set a wireless password. On your PC then you will have to update to the new password.

My wife was not pleased with my first password as trying to type in the long complicated phase on her Kindle was not easy. So I made it a short less complicated phase and still hear complaints. :)

---

### Post by sofasurfer on 2012-02-25
I am including screenshots of my routers homepage. 
I just though of something. Shouldn't I remove my old adapter, restart the pc, reinstall the adapter and then start the pc again to get it to recognize the router?
I'm really counting on you guys:D

---

### Post by baumanno on 2012-02-25
sofasurfer,

what happens when you try to connect to your wireless network? does it ask you for user/password? if so, there might be a default combination in the instructions, something like 'admin / 123456'...
just trying to narrow this down!

cheers

EDIT:
sorry, misread your post, you're only finding your wired connection... i'll keep thinking

---

### Post by baumanno on 2012-02-25
Now, what about if, in the Wireless Settings --> Basic Wireless settings you switch to 'manual' instead of WPS?
Work your way through the menus and check for the commonplace stuff:
[LIST]
[*]Is the SSID broadcast or being hidden?
[*]Is Wireless function on
[*]etc...[/LIST]

Also, if you have the possibility, try checking with the WiFi-connection of a smartphone or other device whether that can pick up your wireless-signal. That would rule out an error regarding router-settings, at least...

---

### Post by sofasurfer on 2012-02-25
I'm at work so can't do much now.
I also want to add this...My routers webpage is at 192.168.1.1. My adapter should be at 192.168.1.2 or something like that, right? But when I try to access it I get a "page not found" or some similar message. Another clue that makes me wonder if my adapter is dead. Whatcha think?

---

### Post by agillator on 2012-02-25
Now you have me confused. First, if you disconnect your computer from the ethernet network, no wired networks should show in network manager. That's what we want for this test. If there are ANY wireless networks that network manager can see (and that broadcast their SSID) you should see the name(s) in network manager. You may not be able to connect for various reasons, but you should at least see the name. If not, and you know there are some you should see (like a neighbor's) then that could be a problem with the adapter or with network manager. Have you done anything to network manager since you installed your system? Do you have another computer or a friend with a laptop who can come to your place and see if s/he can see your wireless router? Has you wireless card worked in the past? Remember, seeing that the network (access point/router) is available is not the same as being able to get on to it. It just means that the access point is broadcasting its SSID. What we want is for your computer to see the SSID of your router/access point. Once we have that, then we can worry about ip addresses, passwords, and so on.

Let me add something just so we do not confuse each other: your adapter is the board in your computer or the usb device connected to your computer. I seriously doubt that it has a 'web page'. Your router/access point is the Linksys 1200 you are trying to get connected. It probably does have a web page. Somewhere in all that you also have a modem which connects to the telephone line, the cable tv network, or something that actually gives you the internet signal. It MAY or may not have a web page. We are not concerned about that . . . yet.

---

### Post by sofasurfer on 2012-02-26
Ok, this is crazy but I will try to sound a little smarter.
First off, when you refer to "network manager" are you talking about what is shown in the attachment? This is know to me as "network connections". I deleted the connection that was shown in it and rebooted. Nothing appeared in "network connections". So I clicked on "add connection", a connection called "wired connection 1" was created.

I restored factory defaults on the router. I restarted the pc and although I can connect to 192.168.1.1 and the "connected" icon appears, I can not access the internet. So, at this time I am connected directly through the modem.

---

### Post by baumanno on 2012-02-26
First off, what you have in the screenshot is indeed referred to as the network-manager.

Did I gather correctly that you can't get online via your new router? Are all connections established properly, i.e. is your modem connected to the WAN-port of your router? In case you have config-options on that modem, check if DHCP is on (DHCP auto-assigns IP-adresses to connected clients). 
Then, as has been suggested before, switch from "Wireless Protected Setup" to "Manual" on your Linksys and if possible check with some kind of external wifi-device that the signal broadcast from your router can be picked up (this could be another computer, laptop, smartphone, or even one of those webradio-gadgets). Then, check for other wireless connections around your location (neighbours') to see whether your wireless-adapter is functioning...

Oh, and report back what you get from that little bit of reconaissance-work :)

---

### Post by kurt18947 on 2012-02-26
Hi

I don't see anything in your screen shots but when you open the setup or wireless tab on your router, is there a button that says something like "enable wireless"? The few routers I've dealt with always had a way to turn on and turn off wireless.  They sometimes default to "off".

Edit:  I found the setup guide for your router.  You might log onto the router and the right-most tab may be labeled "status".  If so, click on that.  There should be a 'wireless' choice that will tell you about the router's wireless connection.  Has your wireless adapter worked with another router?  I assume it has.

---

### Post by sofasurfer on 2012-02-26
This is freaking insane.
Ok, here I go again. 
I finally got the router setup program off the cd and got it running. It searches for a network and finds none. So I bought a new adapter today. I ran the setup again and IT STILL FINDS NO NETWORK. I ran the manual but the whole manual is obsessed with the idea that I must have winblows. Well guess what...I DON'T!!!

I have tried many settings in the router setup page and nothing helps. Much of it is so confusing I do not even know what I did.

If I connect through my modem I can get online but I can not connect to the routers config page. 
If I connect through the router(wired) I can access the router config page but I can't get online.

I called Linksys and they have a problem with me having linux. I called Charter and they...well, their Charter.

This is insane. I should have basic connection with no trouble. 

I guess I'll be taking all this **** back tomorrow.

---

### Post by kurt18947 on 2012-02-27
Will the setup CD work with Linux?  Seems unlikely.  The only time I've used a setup CD it made my life more complicated than it needed to be.  You should be able to log onto the router's web interface using a wired connection, click on "status" and know if your wireless connection is live.  Are you certain your wireless adapter(s) are working?  Do your wireless adapters work with your old router?  Trying 2 new things at the same time may complicate your life.  If you have 2  items (router and wifi adapter) that must both function correctly in order to establish a connection and you change both, how do you know which one is the problem? Or is neither one functioning correctly?

As far as Linksys not supporting Linux,  that's par for the course (even though Linux made Linksys mucho $ with their WRT54G routers running -- guess what?).  That's also why I keep a windows installation around even though I hardly ever use it.  When talking to technical support trouble shooting a possible hardware or ISP problem,  it's just far simpler to let the tech support people use their scripts that usually start with:  "click on the start button......."

---

### Post by sofasurfer on 2012-02-27
:popcorn: Holy crap!! I got this thing going (wired connection through router). Not sure wgat I did right though. Tthink it may be that I changed from "wi-fi protected setup" to "manual" but that can't be it because that setting is under "wireless".

If anyone else is having trouble and wants to see my settings screenshots I have them.

Now my next step is to figure out how to install my new Netgear adapter.:lolflag:

---

### Post by sofasurfer on 2012-02-27
I just noticed that the only security modes on the router are "WPA2 Personnal" and "WPA2 Enterprise".

The modes available in Network Manager are "WPA & WPA2 Personal" and "WPA & WPA2 Enterprise".
Are these compatable?

---

### Post by kurt18947 on 2012-02-27
> **sofasurfer said:**
> :popcorn: Holy crap!! I got this thing going (wired connection through router). Not sure wgat I did right though. Tthink it may be that I changed from "wi-fi protected setup" to "manual" but that can't be it because that setting is under "wireless".

[COLOR=Blue]That is where I would expect to find WiFi setup.  If you're doing manual setup, don't use a personally identifiable SSID and use a strong password.  I've never used WPS but I think there's a security issue with it.[/COLOR]

If anyone else is having trouble and wants to see my settings screenshots I have them.

Now my next step is to figure out how to install my new Netgear adapter.:lolflag:

Netgear adapters can be easy or a real PITA.  A secret of the Linux WiFi world is that manufacturer is pretty much irrelevant, chipset matters more.  Chipsets vary from model to model and even within models.  For instance, an old TrendNet Wifi adapter version 2 used an SiS chipset whose support sucked.  Version 3 used a Realtek 8187B chipset which has been plug -n- play for a few years now.  A  first step with the Netgear adapter might be to post the output of this terminal command:
"lsusb"  That's a lower case "L".  If your new adapter is a PCI, the command would be "lspci" It'll look something like this:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**
Bus 004 Device 002: ID 047d:2048 Kensington 
Bus 004 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 005: ID 04f9:01f3 Brother Industries, Ltd 

```

This tells me I have an Atheros AR9271 chipset which is plug -n- play on distros 11.04 and more recent.  Once you know your chipset, you can plug that into the search box in the 'Networking and Wireless' forum and see if there are any 'solved' posting for your adapter or chipset.

---

### Post by sofasurfer on 2012-02-27
I ran lsusb yesterday. All it said was that it was a Netgear. I did some searching and I think it is a r8169. Anyway I am taking it back today. I may get another or maybe not. I checked Ebay and there are a couple that say they work with linux and they are cheap. I may go with one of those. Waiting to hear back from one of the sellers that I questioned about there product.
Check this out and give me your opinion. It may be helpful to others.
[http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=linux+wireless+adapter&_sacat=See-All-Categories](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=linux+wireless+adapter&_sacat=See-All-Categories)

---

### Post by kurt18947 on 2012-02-27
> **sofasurfer said:**
> I ran lsusb yesterday. All it said was that it was a Netgear. I did some searching and I think it is a r8169. Anyway I am taking it back today. I may get another or maybe not. I checked Ebay and there are a couple that say they work with linux and they are cheap. I may go with one of those. Waiting to hear back from one of the sellers that I questioned about there product.
Check this out and give me your opinion. It may be helpful to others.
[http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=linux+wireless+adapter&_sacat=See-All-Categories](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=linux+wireless+adapter&_sacat=See-All-Categories)

Be careful about cheap off-brand Ebay adapters that "work with Linux".  They may ..... if you have extraordinary skills and can tweak the source code then build the drivers. I've been down that road.  I'll recommend 3 that I've found to be "plug & play".  The machine I'm on now has the Netgear I referenced earlier, WNA-1100.  Staples stocks it and it's plug and play on 11.04 and higher.  It's an N150 as are a couple others I've mentioned.  I don't do large file transfers or other heavy network tasks over wireless so I don't find 150 Mb./sec a handicap.  If you want to go the Ebay route, you could look for a Dlink DWA-131.  It uses a Realtek rtl-8192SU chipset and like the Netgear has been plug & play since 11.04.  A twin to the Dlink is a Trendnet TEW-649UB. Local CompUSAs were selling these for $14.99 at one time.  

[http://www.staples.com/Netgear-Wireless-N-150-USB-Adapter/product_819059?catalogId=10051&fromUrl=home&currentUrl=&cmSearchKeyword=Netgear+wna1100&cmArea=SEARCH&langId=-1&storeId=10001&ddkey=http:StaplesSearch](http://www.staples.com/Netgear-Wireless-N-150-USB-Adapter/product_819059?catalogId=10051&fromUrl=home&currentUrl=&cmSearchKeyword=Netgear+wna1100&cmArea=SEARCH&langId=-1&storeId=10001&ddkey=http:StaplesSearch)

I bought a Dlink from this Ebay vendor $12.99 w/ free shipping.  Claims it's a manufacturer refurb, it looked and worked like new to me just no retail packaging.
[http://www.ebay.com/itm/D-Link-DWA-131-Wireless-N-WIFI-Nano-USB-Micro-Mini-Compact-Adapter-/370585118446?pt=LH_DefaultDomain_0&hash=item56489826ee](http://www.ebay.com/itm/D-Link-DWA-131-Wireless-N-WIFI-Nano-USB-Micro-Mini-Compact-Adapter-/370585118446?pt=LH_DefaultDomain_0&hash=item56489826ee)

---

### Post by sofasurfer on 2012-02-28
Any knowledge about using these items on 10.04?

---

### Post by kurt18947 on 2012-02-28
> **sofasurfer said:**
> Any knowledge about using these items on 10.04?

Yes.  They'll work but they all require work.

I used an installer from Source Forge to install the Netgear.  

```
http://sourceforge.net/projects/ath9k-htc/
```It's a 2 step process.  First you install the .deb file like any other .deb file.  Then, you look in (I think -- it's been a while and I have no gnome 2 installs left) applications -> system.  You'll see something like ath9k installer.  Run that, it may take several minutes then restart.  The adapter should be alive.

The rtl-8192SU adapter requires a firmware file.  I'll post a link to the bug:

```
http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html
```The bug talks report about 10.10 but I'm pretty sure it applies to 10.04 as well.  The essence is to download the file rtl8192sfw.bin and create a folder lib/firmware/RTL8192SU/  then put the rtl8192sfw.bin in the new folder.  It's possible that the newer versions of 10.04 will support these adapters without the tweaks but I haven't had a 10.04 install  for probably a year or more.

If you do get one of the above mentioned adapters, I'd plug it in and see if it works before doing the tweaks, maybe the latest iteration of 10.04 includes native support.  I'll mention one more adapter that has been plug -n- play for me since 9.x but it's a G speed adapter so might limit faster broadband connections.

[http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=trendnet+tew-424ub&_sacat=See-All-Categories](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=trendnet+tew-424ub&_sacat=See-All-Categories)

---

### Post by sofasurfer on 2012-02-29
I took my adapter back and stopped at Meijers and bought a Netgear WNA1100. I it does not work I will load up a 11.04 Ubuntu and try it on that. Trouble is I did try 11.04 when it came out and it would not work properly on my pc. O well, maybe it will work better this time.
To be sure about one thing...my router is a n300. Worst Buy salesman told me I need to match router and adapter to 150 or 300 or whatever. Or is my n300 router downward compatable to a 150 adapter?

---

### Post by kurt18947 on 2012-02-29
> **sofasurfer said:**
> I took my adapter back and stopped at Meijers and bought a Netgear WNA1100. I it does not work I will load up a 11.04 Ubuntu and try it on that. Trouble is I did try 11.04 when it came out and it would not work properly on my pc. O well, maybe it will work better this time.
To be sure about one thing...my router is a n300. Worst Buy salesman told me I need to match router and adapter to 150 or 300 or whatever. Or is my n300 router downward compatable to a 150 adapter?


I'm not positive but it should be.  I have an ActionTec Mi424 (something) because that's what comes from the ISP.  There *may* be a setting somewhere that forces the router to operate at one speed, there is on the Actiontec.  I'm not sure where you would find it if there is such a setting -- maybe under the wireless tab?  I would certainly hope that the default setting would be for maximum compatibility e.g. it would work with G, N150 and N300.  

I installed 11.04 when it became 'official'.  I found quite a few rough spots but they mostly smoothed out after a month or so.  If you can get your Netgear WNA1100 to work on 10.04 you might want to hold out 'til 12.04.  I've been running it since the first alpha release and even now when it's just at the beta release it's quite stable.  The thing to remember is that even though 12.04 defaults to Unity,  it's really easy to add other desktops/window managers.   You can install the Xfce or LXDE desktops and select one of those when you logon.  Or you could try Mint which is built on 11.10 but comes with Mate & Cinnamon as well as Gnome (shell).  There are many choices out there.

---

### Post by sofasurfer on 2012-03-01
On Ubuntu Documentation > Community Documentation > HardwareSupportComponentsWirelessNetworkCardsNetgear, located at... [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) ...there is a non-functioning link to a driver for the Netgear WNA1100 USB wireless adapter.
Anyone know where that driver can be found?

---

### Post by kurt18947 on 2012-03-01
> **sofasurfer said:**
> On Ubuntu Documentation > Community Documentation > HardwareSupportComponentsWirelessNetworkCardsNetgear, located at... [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) ...there is a non-functioning link to a driver for the Netgear WNA1100 USB wireless adapter.
Anyone know where that driver can be found?

Does the installer from source forge not work for you?  It's dead simple to use and worked great for me the times I used it.

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)
There may well be a link somewhere  to download, extract etc. etc. but why?  Unless the installer doesn't work for you.  The page says it was tested on 10.04.

---

### Post by sofasurfer on 2012-03-01
The link took me to a "not found" page. I found the installer on a different site. I installed it, went to the went to the system tools menu and ran it. I then inserted to adapter and rebooted. Not working. Maybe I have a setting wrong. I'll try to look at it after work tonight.

---

### Post by kurt18947 on 2012-03-01
Odd. I just clicked on the link and it took me where I expected.  The .deb file is called 
    [B]             [B][SIZE=3]GUI Program to install ath9k_htc (Atheros) and the author's handle is:
[/SIZE][/B][/B]

               **[SIZE=3][vagrale13]("http://sourceforge.net/users/vagrale13")[/SIZE]**[SIZE=3][]("http://sourceforge.net/users/vagrale13")[/SIZE]


If you weren't able to get to the source forge page, here is something from that page:



[LIST]
[*]The deb package ath9k_htc-installer.1.0.1-maverick-fixed.deb works only for Ubuntu Maverick NO in oldest version!
[*]Newer  deb package 1.0.2 adding newer changes of driver. Please use it on  Lucid and older version! Doesn' t work on Maverick and newer version.
[*]Newer  deb package 1.0.3 fixed "dpkg: error" and adding newer changes of  driver. Please remove first older version ath9k_htc-installer<1.0.2  and then install it. Use it on Lucid and older version! Doesn' t work on  Maverick and newer version.
[*]Newer deb package  1.0.4 adding newer changes of driver. Please use it on Lucid and older  version! Doesn' t work on Maverick and newer version.
[/LIST]
You could also try to find the page via a google search.  Something like "ath9k_htc+sourceforge" should do it.  I'm sure it's possible to install drivers the more conventional way.  I just found the installer so simple and to work so well.  Have you enabled back ports in 10.04?  That might get the current driver,  dunno.




**[SIZE=3][]("http://sourceforge.net/users/vagrale13")[/SIZE]**

---

### Post by sofasurfer on 2012-03-01
As I stated above, I did find the driver at a differant site. It also said it worked with 10.04 and older versions. I am at work so can not verify the version. Will double check and verify after work. Sounds like I'm just a simple mistake away from getting it running. 
Checked out thinkpenquin.com. As a last resort I can get a compatable adapter from them. They are said to offer a quarantee of compatability.

---

### Post by kurt18947 on 2012-03-02
The installer .deb is more than just the driver.  It includes the driver plus firmware/software/scripts/whatever to configure the adapter automatically.   It does appear that version matters, 1.0.4 is the most recent, .  Once 11.04 came out with native support I no longer needed the installer so don't have experience with the current version(s).

---

### Post by Sicadastra on 2012-04-06
> **roelforg said:**
> May i note that the cd isn't needed?

IIRC most routers come w/o pass.
If you can find out what the SSID is, you could just connect and be done with it.

Hi, I'd like to ask for clarification. If I use a Linksys E1200, does that mean I won't need to install the CD and I can set it up online (with that special ip address provided)? My laptop only has Ubuntu for OS and I'd rather not install the router's program on our Windows PC.

Thank you.

---

### Post by Vishal Agarwal on 2012-04-06
Linksys router configuration is very easy. U actually don't need any CD. Log in through WEB interface and configure it.

If your problem is not soled the pl come again.

---

