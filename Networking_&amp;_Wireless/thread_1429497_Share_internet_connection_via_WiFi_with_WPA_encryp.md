---
title: "Share internet connection via WiFi with WPA encryption?"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by PCman13 on 2010-03-14
Hello everybody,

A few weeks ago, I bought an iPod touch, and I wanted to use internet on it, without a router. I setted up an ad-hoc network on my laptop, via the tray icon. When I keep it unsecured, it works sometimes, but when I activate WPA encryption, it doesn't work anymore. 

I havn't got a router, and I'm not planning to buy one, because I don't need to use the connection very much.

I don't know what information is useful, so if I gave too less information, please tell me what information I need to place.

---

### Post by Nostalos on 2010-03-14
WPA and WPA2 do not work in ad-hoc mode.   It has to be unencrypted and i "think" WEP works.   If you have to have WPA you will need to look into settting up for Master mode.  Which is entirely dependant on which wireless card you have.  Unless you have a few specific cards its pretty much not going to happen.

---

### Post by Cabalbl4 on 2010-03-25
Yes, that's the case.
While ad-hoc WEP works fine for me, no luck with ad-hoc WPA. :cry:
This troubles me a bit, because WEP connections are not much secure.

---

### Post by captain_171 on 2010-03-25
You can set up a network card in ubuntu to work as infrastructure mode. Then you can use any encryption as you want and then you can use your Ubuntu PC as a router and share your internet connection.
Would you like more info on that?

---

### Post by Cabalbl4 on 2010-03-25
> **captain_171 said:**
> You can set up a network card in ubuntu to work as infrastructure mode. Then you can use any encryption as you want and then you can use your Ubuntu PC as a router and share your internet connection.
Would you like more info on that?
Hmm, I think this can be useful to try. 
Thanks in advice for info.

---

### Post by BishopPell on 2010-03-28
> **captain_171 said:**
> You can set up a network card in ubuntu to work as infrastructure mode. Then you can use any encryption as you want and then you can use your Ubuntu PC as a router and share your internet connection.
Would you like more info on that?

I am of the understanding that "infrastructure" mode is also called "master" mode.  So the same problem highlighted by previous user is that many wifi network cards will not work in master mode.   You get this error:

$ sudo iwconfig wlan0 mode master
[B]Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.[/B]

My Dell Latitude E6400 has a Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

It's certainly a pain that I cannot use WPA / WPA2 in adhoc mode.  Its frustrating that ubuntu does not tell me this, it appears to create the adhoc network with WPA security, but then I start seeing spurious networks with funny characters!

Anyway, I am now looking at possibility of configuring an OpenVPN for my adhoc wireless access point - something hopefully compatible with my Iphone 3GS!!!

---

### Post by BishopPell on 2010-03-28
Funny thing is, I could not get the iPhone to recognise my WEP wireless network when I used a passphrase.  I ended up using a 128bit key entered in hexidecimal in ubuntu.  I was then able to enter then ascii equivalent of the key in iPhone.  The same passphrase network worked on another laptop running fedora - go figure!

---

### Post by captain_171 on 2010-03-28
You are using sudo before that command right?
and also setting the SSID also?

take a peek at this this:
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Use master instead of adhoc.

---

### Post by PCman13 on 2010-03-30
> **captain_171 said:**
> You can set up a network card in ubuntu to work as infrastructure mode. Then you can use any encryption as you want and then you can use your Ubuntu PC as a router and share your internet connection.
Would you like more info on that?
Yes, I want information on that, because I want to use encyption. Does wep encryption work? I have an other question too, in some routers you can rescrict the MAC adresses. Can this also be done in ubuntu? If yes, please tell me how.

---

### Post by MrMistr on 2010-08-18
I just encountered the same problem.  

[LIST]
[*]The WiFi card in my laptop can not be used as master, but it supports AdHoc mode.
[*]At home the card connects to my Access Point using WPA2, which means the it knows how to handle it.
[/LIST]
I set up the adhoc mode via the network manager. It seems simple enough. I then activated it by connecting to a "hidden" network.

The "receiving" end was an XP laptop. The network showed up in the Wireless panel.

I can create a link between these two computers, if I use a) no encryption, or b) WEP encryption (which is just as bad). When I switch to WPA on the Ubuntu machine, it does not work.

I noticed however that the password entry in XP asked for a WEP password, even if the Ubuntu machine is set to WPA.

The reason seems to be, that the signal send by the Ubuntu machine does contain the information that an encryption is used, but does NOT specify WPA, if WPA is used.

On **another** Ubuntu machine I scanned for Wifi signals using

```

sudo iwlist scan

```This is the entry of an access point using with WPA2

```

          Cell 01 - Address: 00:26:4D:1A:7F:C6
                    ESSID:"Heimnetz"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/100  Signal level=-66 dBm  
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000002ecfd456932

```This is the entry for the adhoc unit (configured for WPA):

```

          Cell 02 - Address: 3A:69:14:44:F2:1E
                    ESSID:"tralala"
                    Mode:Ad-Hoc
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/100  Signal level=-56 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000010656387

```As you can see, there is no mentioning of WPA encryption. 

This might be the reason why XP is asking for an WEP key even though WPA is used.

May I ask you to make a similar scan? Perhaps this info is enough to make the powers that be to look for the bug in the right place.

---

