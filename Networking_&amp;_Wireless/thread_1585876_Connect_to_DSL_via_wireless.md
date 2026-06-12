---
title: "Connect to DSL via wireless"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by nlsthzn on 2010-10-01
Greetings all,

I just took the plunge again and purged Windows 7 from my desktop computer and replaced it with the Lucid Lynx :D

Now my problem is I was using "Internet Connection Sharing" in Windows 7 to let my laptop and netbook connect to the Internet via wireless.  Now I don't have the option of sharing my Internet connection anymore as Ubuntu would require me to have two network interface devices to do this, thus I am trying to make my laptop and netbook connect to the DSL modem via the wireless AP (which is possible in Windows as my wife is doing it right now on her laptop).

How do I go about getting my laptop (running Lucid Lynx) and netbook (Lucid Lynx Netbook Remix) to connect to the DSL modem via a wireless connection?  (Google was not much help :()


Thanks
Neil

---

### Post by dmizer on 2010-10-01
First, determine what wireless card you have in your laptop. Something like the following can be used:
```
lshw -C network
```
For pci wireless cards (anything but USB):
```
lspci
```
For USB wireless cards
```
lsusb
```
Then, check this list for instructions: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Or, do a forum search via google using your wireless card's information like so: [http://www.google.com/#sclient=psy&hl=en&q=linksys+wireless+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=c6affe93747c32d0](http://www.google.com/#sclient=psy&hl=en&q=linksys+wireless+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=c6affe93747c32d0)

---

### Post by CharlesA on 2010-10-01
Why not just use a wireless router, it would be much less work to set up.

---

### Post by dmizer on 2010-10-01
> **CharlesA said:**
> Why not just use a wireless router, it would be much less work to set up.

Since the DSL modem is able to host a wireless connection, the DSL modem is a modem/router combination and a dedicated router would most probably be redundant.

---

### Post by nlsthzn on 2010-10-01
> **dmizer said:**
> First, determine what wireless card you have in your laptop. Something like the following can be used:
```
lshw -C network
```For pci wireless cards (anything but USB):
```
lspci
```For USB wireless cards
```
lsusb
```Then, check this list for instructions: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Or, do a forum search via google using your wireless card's information like so: [http://www.google.com/#sclient=psy&hl=en&q=linksys+wireless+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=c6affe93747c32d0](http://www.google.com/#sclient=psy&hl=en&q=linksys+wireless+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=c6affe93747c32d0)

Thanks for the fast reply... I will go now and check out these links and report back :KS

> **CharlesA said:**
> Why not just use a wireless router, it would be much less work to set up.

Trying to make do with what I got :)

> **dmizer said:**
> Since the DSL modem is able to host a wireless connection, the DSL modem is a modem/router combination and a dedicated router would most probably be redundant.

Maybe should clarify here a bit, my DSL modem does not have wireless built in, it is connected to a switch (which has ethernet lines running to basically every room in the house, so I also connected a dlink wireless AP to one of the points to give me wireless access to the network.

(I actually tried switching to Linux on my desktop a few months ago but couldn't get Internet Connection Sharing enabled on Linux so now I am trying a different "solution")

---

### Post by CharlesA on 2010-10-01
> **dmizer said:**
> Since the DSL modem is able to host a wireless connection, the DSL modem is a modem/router combination and a dedicated router would most probably be redundant.

D'oh! I misread the OP.

Sounds like the wireless card isn't being detected, so run the commands that dmizer posted and that should get you to a place to start.

---

### Post by grahammechanical on 2010-10-01
I really do not know what I am talking about but, if your laptop and netbook have wireless built in then they should connect to your wireless AP if it is in range.

Do you see the network icon? What information does that give you when you right and left click?
code

```
nm-tool
``` in a terminal and see if your wireless device is connected and if any wireless networks (the wireless AP in your case) are in range.

Regards.

 > you should be able to configure connection sharing by right clicking on  your network icon (in the notifications toolbar), and select "edit  connections". Select the wired adaptor (eth0), and click "edit". Click  on "IPv4 settings" and change the method to "Shared to other computers".  Click "apply". Enjoy shared internet.  The same would apply to a wireless connection (I think).

---

### Post by nlsthzn on 2010-10-01
Seems there is a bit of confusion here... let me try and clarify a bit...

Both my laptop and netbook's wireless cards work in Ubuntu, when I was running Windows 7 on my desktop machine I had Internet Connection Sharing enabled on it so that my laptop and netbook simply had to connect to the network wirelessly and then they would be able to connect to the Internet via my desktop machine.

Now I have installed Ubuntu on my desktop machine and as it only has one network card installed I can't share the Internet connection like I did in Windows, which means every machine on the network has to connect to the DSL router inividually (with the required username and password).

My wife's laptop running Windows is able to do this, it connects to the wireless AP, sends the username and password and is connected to the Internet, however I do not know how to get my laptop and netbook to do the same :/

I can set up a wireless network or a DSL network but it seems I can't set up DSL via wireless (hope that explains a bit better)...

Maybe there is another way of doing this, I am not sure?

---

### Post by nlsthzn on 2010-10-01
> **grahammechanical said:**
> I really do not know what I am talking about but, if your laptop and netbook have wireless built in then they should connect to your wireless AP if it is in range.

Do you see the network icon? What information does that give you when you right and left click?
code

```
nm-tool
``` in a terminal and see if your wireless device is connected and if any wireless networks (the wireless AP in your case) are in range.

Regards.

   The same would apply to a wireless connection (I think).

On my desktop system it is connecting directly to the DSL modem, "Auto eth0" is showing as not connected, and if I connect with it my connection to the DSL router is lost :/

---

### Post by dmizer on 2010-10-01
> **nlsthzn said:**
> Seems there is a bit of confusion here... let me try and clarify a bit...

Both my laptop and netbook's wireless cards work in Ubuntu, when I was running Windows 7 on my desktop machine I had Internet Connection Sharing enabled on it so that my laptop and netbook simply had to connect to the network wirelessly and then they would be able to connect to the Internet via my desktop machine.

Now I have installed Ubuntu on my desktop machine and as it only has one network card installed I can't share the Internet connection like I did in Windows, which means every machine on the network has to connect to the DSL router inividually (with the required username and password).

My wife's laptop running Windows is able to do this, it connects to the wireless AP, sends the username and password and is connected to the Internet, however I do not know how to get my laptop and netbook to do the same :/

I can set up a wireless network or a DSL network but it seems I can't set up DSL via wireless (hope that explains a bit better)...

Maybe there is another way of doing this, I am not sure?

I'm confused now too. I assumed you were simply having problems getting your wireless card to work. Now it seems apparent that this is not the case.

Perhaps a picture of what you want to do might help?

Edit:
Here's an example from my network
```

Fiber terminal --LAN cable-- eth0 (server) eth1 --LAN cable-- wireless hub ~~~ laptops.

```

---

### Post by nlsthzn on 2010-10-01
[[IMG]http://img522.imageshack.us/img522/4979/diagram1s.jpg[/IMG]]("http://img522.imageshack.us/i/diagram1s.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is my current network... I used to have "Internet Connection Sharing" enabled on the desktop so the laptops would simply connect to the wireless AP and have net access... now I Ubuntu installed and thus when they connect to the AP no net access (I have no way of configuring the "modem" to keep the password/username, every machine has to login separately...)

---

### Post by dmizer on 2010-10-01
Ah ha! I think I understand now. What you need is indeed a router. This can be done with Ubuntu, but it would really help if you had two wired network adapters on the desktop computer. Then you can put Ubuntu between the DSL modem and the hub.

However, it would probably cause you far less headache if you simply purchased a wired router (wired only routers are really cheap) to put between the DSL modem and the hub. It would also provide you far more stable network security.

---

### Post by nlsthzn on 2010-10-01
> **dmizer said:**
> Ah ha! I think I understand now. What you need is indeed a router. This can be done with Ubuntu, but it would really help if you had two wired network adapters on the desktop computer. Then you can put Ubuntu between the DSL modem and the hub.

So there is no way for the laptops running Ubuntu to log into the DSL modem via wireless like is possible in Windows?

---

### Post by dmizer on 2010-10-01
Yes there is. However, that network configuration is far from ideal and less than secure. This means that each computer on your network must have a local software firewall. This also means that only one computer can be online at any given time.

With a router, you have a hardware firewall which is more reliable than a software firewall. These days, it's really not advisable to have a computer directly connected to the internet. Also with a router, you don't have to worry about entering connection details every time.

To connect to your DSL, all you have to do is right click on the networking applet in your toolbar, and select "Edit connections". Then click on the DSL tab and fill in the information.

---

### Post by nlsthzn on 2010-10-01
> **dmizer said:**
> Yes there is. However, that network configuration is far from ideal and less than secure. This means that each computer on your network must have a local software firewall. This also means that only one computer can be online at any given time.

With a router, you have a hardware firewall which is more reliable than a software firewall. These days, it's really not advisable to have a computer directly connected to the internet. Also with a router, you don't have to worry about entering connection details every time.

To connect to your DSL, all you have to do is right click on the networking applet in your toolbar, and select "Edit connections". Then click on the DSL tab and fill in the information.

> Yes there is. However, that network configuration is far from ideal and  less than secure. This means that each computer on your network must  have a local software firewall. This also means that only one computer  can be online at any given time.

Actually the reason I set up Internet Connection Sharing in the beggining was because only one PC can connect at a time... or so it seemed... I have now successfully had my desktop, wife's laptop and even X-Box 360 connecting at the same time (don't know how)...

> To connect to your DSL, all you have to do is right click on the  networking applet in your toolbar, and select "Edit connections". Then  click on the DSL tab and fill in the information.

Sure, this worked well on the desktop to set up the DSL connection, but does not work on the laptop/netbook... Under the wireless tab is my wireless connection and under the DSL is the DSL connection but only the wireless connections are available, can't choose to connect via DSL (I guess because there is no wired network connected)...

---

### Post by dmizer on 2010-10-01
Here is your best option without having to purchase a router (I still **_HIGHLY_** suggest purchasing a router):

Put the Ubuntu desktop between the modem and the hub, and configure it for connection sharing. Then all the wireless computers will get internet through the Ubuntu desktop and none of them will have to sign on to DSL manually. The only limitation here is that you will need two network adapters on the Ubuntu desktop.

---

### Post by nlsthzn on 2010-10-01
> **dmizer said:**
> Here is your best option without having to purchase a router (I still **_HIGHLY_** suggest purchasing a router):

Put the Ubuntu desktop between the modem and the hub, and configure it for connection sharing. Then all the wireless computers will get internet through the Ubuntu desktop and none of them will have to sign on to DSL manually. The only limitation here is that you will need two network adapters on the Ubuntu desktop.

Oh well... sucks when Windows outshines GNU/Linux in something like networking :(

---

### Post by dmizer on 2010-10-01
> **nlsthzn said:**
> Oh well... sucks when Windows outshines GNU/Linux in something like networking :(

By no means am I saying it can't be done. What I'm trying to do here is suggest to you a far better, safer, more secure, and easier way.

---

### Post by nlsthzn on 2010-10-01
> **dmizer said:**
> By no means am I saying it can't be done. What I'm trying to do here is suggest to you a far better, safer, more secure, and easier way.

Having to purchase additional hardware != Easier (Unfortunately...)

HOWEVER thanks for the input it is appreciated!


Neil

---

### Post by dmizer on 2010-10-01
> **nlsthzn said:**
> Having to purchase additional hardware != Easier (Unfortunately...)

HOWEVER thanks for the input it is appreciated!


Neil

Do you not have two network cards on your desktop? If not, that could be a cheaper solution than a router.

By "easier", this is what I mean. Here's how to connect to ADSL via Wireless: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) (you'll have to specify the wireless interface in the provider file).

That's a little old so it may have to be tweaked to fit your situation. There may be another way with Network-manager, but I am not aware of it.

Here's the bug on your issue: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/232172](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/232172) you may want to add yourself to the bug by clicking on the "This bug affects 5 people. Does this bug affect you?" link.

---

### Post by CharlesA on 2010-10-01
> **dmizer said:**
> By no means am I saying it can't be done. What I'm trying to do here is suggest to you a far better, safer, more secure, and easier way.

Agreed.

> **nlsthzn said:**
> Having to purchase additional hardware != Easier (Unfortunately...)

HOWEVER thanks for the input it is appreciated!


Neil

You'd have to stick another network card in the ubuntu pc for that to work.

It would look something like this:

Modem == Ubuntu PC == AP == Other machines

---

### Post by nlsthzn on 2010-10-01
Will get a second network card and then set-up Internet sharing... pretty sure I will need assistance so I will be back :D

---

### Post by dmizer on 2010-10-01
> **nlsthzn said:**
> Will get a second network card and then set-up Internet sharing... pretty sure I will need assistance so I will be back :D

It is pretty straight foreward. Here is a primer. [http://www.ge.ubuntuforums.org/showpost.php?p=9709154&postcount=2](http://www.ge.ubuntuforums.org/showpost.php?p=9709154&postcount=2)

---

### Post by nlsthzn on 2010-10-02
Just as a point of interest, just enabled "Internet Connection Sharing" on my wifes laptop (which only connects via wifi) and at least now all of my other devices; laptop, netbook, X-Box 360, iPod can all access the web...

---

### Post by dmizer on 2010-10-02
> **nlsthzn said:**
> Just as a point of interest, just enabled "Internet Connection Sharing" on my wifes laptop (which only connects via wifi) and at least now all of my other devices; laptop, netbook, X-Box 360, iPod can all access the web...

Despite the fact that it appears to work, this is far from ideal and is likely to cause problems in your network. Unless your wife's laptop is between the hub and the DSL modem, you will have problems because at any given time the IP lease from your wife's laptop could expire and any one of the other networked computers would grab an IP from your ISP, effectively disabling your wife's laptop.

For a stable and reliable network, you'll need some kind of [NAT]("http://en.wikipedia.org/wiki/Network_address_translation") between the hub and the modem. That NAT can come in the form of a hardware router, or it can come in the form of an ICS host with two network cards placed between the modem and the hub.

This is basic networking and is true in any network, if the client machines are Linux, Windows, or even MAC. It is also true in any network no matter what OS the ICS server is running.

---

### Post by nlsthzn on 2010-10-02
> **dmizer said:**
> Despite the fact that it appears to work, this is far from ideal and is likely to cause problems in your network. Unless your wife's laptop is between the hub and the DSL modem, you will have problems because at any given time the IP lease from your wife's laptop could expire and any one of the other networked computers would grab an IP from your ISP, effectively disabling your wife's laptop.

For a stable and reliable network, you'll need some kind of [NAT]("http://en.wikipedia.org/wiki/Network_address_translation") between the hub and the modem. That NAT can come in the form of a hardware router, or it can come in the form of an ICS host with two network cards placed between the modem and the hub.

This is basic networking and is true in any network, if the client machines are Linux, Windows, or even MAC. It is also true in any network no matter what OS the ICS server is running.

I'm not sure why this hasn't happened then because I was running the same basic setup with my desktop for a year and a half now and I don't recall having any such issues... but thanks for the heads up... once I get the extra network card I will do it right...

---

### Post by hunters1094 on 2010-10-02
> **nlsthzn said:**
> [[IMG]http://img522.imageshack.us/img522/4979/diagram1s.jpg[/IMG]]("http://img522.imageshack.us/i/diagram1s.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is my current network... I used to have "Internet Connection Sharing" enabled on the desktop so the laptops would simply connect to the wireless AP and have net access... now I Ubuntu installed and thus when they connect to the AP no net access (I have no way of configuring the "modem" to keep the password/username, every machine has to login separately...)

my network is like yours. and i spent 2 days in solving this problem.
i installed my Lucid Lynx yesterday.

1. i installed  Broadcom STA wireless driver.
2. i removed network manager, i also did not use wicd, i wanted to configure manually.
3. with Ubuntu 9.10, i configured easily.  

my interface :
> 
auto eth1
iface eth1 inet static
address 192.168.0.27
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
network 192.168.0.0

wpa-ssid "myssid"
wpa-psk "mykey"
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK


i did the first time, could not connect
i did more several times, and now i can connect to the internet via wireless. don't know why.


my iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



lshw -C network

> 
*-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:20:15:23
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.27 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f1ffc000-f1ffffff



can anyone show me why, i don't want to have this problem anymore. thanks.

---

### Post by nlsthzn on 2010-10-02
@hunters1094:
 
Do you have two network interface cards in the computer you are using to share the internet?

---

### Post by hunters1094 on 2010-10-02
> **nlsthzn said:**
> @hunters1094:
 
Do you have two network interface cards in the computer you are using to share the internet?

no, i use a real switch. it does not matter much. 

ifconfig 
> 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:b4:12:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f6fe0000-f7000000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:20:15:23  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe20:1523/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1635 errors:0 dropped:0 overruns:0 frame:553
          TX packets:1791 errors:46 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1650240 (1.6 MB)  TX bytes:254187 (254.1 KB)
          Interrupt:17 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:e8:b4:12:91  
          inet addr:169.254.8.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:f6fe0000-f7000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4229 (4.2 KB)  TX bytes:4229 (4.2 KB)


u can see that i'm using eth1 @-@

but i feel that my connection is slower than in Windows. trying to make it faster ^^

---

### Post by grahammechanical on 2010-10-02
My motherboard has wireless built-in. According to the user manual it can be set in Access Point Mode (this is what I think you are trying to achieve), Infrastructure Mode, Ad-hoc Mode.

When I go to Edit Connections and select my wireless connection and look at the wireless tab I see Mode but there only two options, Infrastructure Mode and Ad-hoc Mode. If I go to IPv4 tab I see Method. It is set to Automatic (DHCP) but it can be changed to either Link-local only or Shared to with other computers. May be either of these settings will help. May be they will stop something else working.

Regards.

---

