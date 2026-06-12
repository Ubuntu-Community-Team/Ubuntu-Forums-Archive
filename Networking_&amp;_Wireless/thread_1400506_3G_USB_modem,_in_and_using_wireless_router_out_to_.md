---
title: "3G USB modem, in and using wireless router out to lappy, Wii ect"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by hairy one on 2010-02-07
3G USB modem, in and using wireless router out (via ethernet) to lappy, Wii ect, this is my ambishion is there any one that could help?

We don't have a phone line just mobile phone and mobile internet because it is mobile!

I have a wireless router only but need wireless to improve my standing within the house because I am seen as a net hog!

I did come across a Virgin wireless modem but it is soooo painfully slow (tested it against the USB dongle modem 3-4kb same test 1 min later 280-300kb's USB.) The wife could make herself a cuppa just waiting for the facebook login page to load!

Would it need to pass on the connection bcause the USB is fully setup? then wireless is setup or would it be required to have a 3rd security setting ect in between?
It would be good to use a low spec computer because I have a few. Headless too, maybe?

Any takers for this one please?

Cheers in advance
hairy

---

### Post by spegru on 2010-02-07
You do realise a wireless router needs a phone line to connect to the internet dont you?
On the other hand maybe you are trying to share your 3G signal using the wireless router?
It may be possible but you can do it without the router, just your own pc.
In fact you can also get a 3G mobile dongle that also does wifi (from 3 in the UK) - it's made by Huawei).That's probably the easiest.

As far as performance is concerned it depends so much on 3G coverage. Do you really get 3G or is it dropping back to GPRS?
You need to get the dongle into a good position, probably upstairs near a window is best.

---

### Post by hairy one on 2010-02-07
thanks for your responce

Here is my 3G Virgin modem (Australia) 169e hewie

[ATTACH]146312[/ATTACH]


here is my portable wireless router NOT modem

[ATTACH]146313[/ATTACH]

LAN and WLAN connection only. It's size is smaller than a pack of 25 smokes or large box of matches and  got it for a very good price, so how to combine all of these items for a working internet connection?

P.S got it working off a Virgin modem to router connecion on windows 7 and shared the connection with our Mac but, windows sucks and the modem is soooo slow that the wife could make a cuppa before her facebook logon page had loaded on the MacBook.

So yes it works but I am a novice I click here and there but feel I am getting no where.

Cheers hairy

P.S USB modem teated against the modem. USB 280-300 kb, modem 3-4kb with same download within mins of each test

---

### Post by spegru on 2010-02-08
I see. You have a wifi router that is designed to work with a 3g dongle. I recognise both of those, made by Huawei - and the dongle is the same as mine. 

Are you sure you did a fair comparison with device positioning being the same or that it was not a temporary problem?.

It is possible that some setup thing in the router is pushing the dongle onto GPRS instead of 3G. However, I've never handled one of those - maybe there is an internal setup web page or whatever that you need to fiddle with. Also did you try the performance test in windows?

---

### Post by regstraton on 2010-02-08
Hi 

I believe the realm you want to enter is "Internet Connection Sharing", there is an article on the help pages here:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I regularly share my HSDPA (Mobile Broadband/3G/whatever) connection out on WiFi from my Eee PC and you could easily do it on Ethernet too.

_How to share my HSDPA internet connection with WiFi in a few minutes:_
[LIST=1]
[*] Connect to the Internet with HSDPA.
[*] Install Firestarter:  ```
$ sudo apt-get install firestarter
```
[*] Click on the NetworkManager Applet -> "Create New Wireless Network" and do so.
[*] Run  ```
$ ifconfig
```  in a terminal to see the device names, usually HSDPA will be a 'ppp?' and WiFi will be a 'ra?' or an 'eth?', etc.
[*] Run firestarter
[*] On 'Preferences' -> 'Firewall' -> 'Network Settings' enable 'Internet Connection Sharing'. Choosing your device names. Leave 'DHCP for Local Network' OFF
[*] Right click on the NetworkManager Applet -> 'Connection Information'.
Get the DNS from the HSDPA connection (eg: 10.206.65.68 ) and the IP from the WiFi connection (eg 10.42.43.1). Then dish out the following to you eager internet users:
 - WiFi Network Name
 - WiFi Password
 - DNS: 10.206.65.68
 - Gateway: 10.42.43.1
 - Subnet Mask: 255.255.255.0
 - IP Address: 10.42.43.X - where you allocate a new X per connection starting a 2.
[/LIST]
That's it.

If you want to avoid step 7) then you will need to install a DHCP server:  ```
$ sudo apt-get install dhcp3-server
```  and then you can select DHCP ON in step 6). But first you will need to configure the DHCP server, which is a bit more involved and requires permanent network configuration changes (I believe - though I hope some day to discover differently) so it is more suited to a permanently committed machine.


_Enabling/Disabling Shared WiFi:_
So far the only way I know to get the shared WiFi network to start is to select 'Connect automatically' in Right click NetworkManager Applet -> 'Edit Connections'.
And to get it to stop: deselect the 'Connect automatically' in 'Edit Connections' ... and then restart the Network Manager: ```
$ sudo /etc/init.d/NetworkManager restart
```

---

### Post by mikecanada on 2010-02-08
Don,t buy a Huawei E182E as it won,t work with Ubuntu,the Sierra Wireless 597 will however but it is much slower.

---

### Post by spegru on 2010-02-09
I see the E182E is brand new and not in Europe yet. However since all the other Huawei dongles work with Ubuntu I'd be surprised if it was not possible. Heck it's even possible to get the ZTE ones working with a bit of effort! What happens and what do you get with an lsusb command?

BTW registration's set of notes on internet connection sharing looks great. I will have to try that. Hairy can also try that instead of his matchbox to see if the performance is any better.

---

### Post by alexfish on 2010-02-09
> **mikecanada said:**
> Don,t buy a Huawei E182E as it won,t work with Ubuntu,the Sierra Wireless 597 will however but it is much slower.

hi

this device has good specifications , according to info it should work with windows,mac and Linux 

[http://www.huaweidevice.com/worldwide/productFeatures.do?pinfoId=2210&treeId=](http://www.huaweidevice.com/worldwide/productFeatures.do?pinfoId=2210&treeId=)

 so I would not give up on it / handy for this sort of work , from reading first post

---

### Post by hairy one on 2010-03-24
Hi back again after some away time due to self harm issues (hitting my head against the wall). This constant setting up and failing with both Ubuntu and Win$ has got to me. It is new'ish tec for a nomad and all these issues just to share a single connection! If I could I would help write a program but I spend my time working in the disability field and computers are my escape into another reality.

I bought a new 3g usb wireless modem to try to rectify the problem, but I out smarted myself. The modem is a low cost unit, specs suggest it will work but I am connected by Virgin and I must not connect with "CHAP".

You guest it this is the only function I am unable to do in the settings, I have another router!!!!!!!!!!!!! For those looking for a 3G connection I would look else where. The Indian I spoke to on their help line nearly hung up on and constantly spoke over me but that is another story.

regstraton thank you for your input I have one question I was wondering if I ask you (or anyone else) please!

Network manager.

When I connect to the 3G modem all is well [ATTACH]151367[/ATTACH]


Then I connect I connect eth0 and I get [ATTACH]151368[/ATTACH]

and I am unable to have any Internet activity at all at this time. Any ideas please?

cheers for now.
hairy

---

