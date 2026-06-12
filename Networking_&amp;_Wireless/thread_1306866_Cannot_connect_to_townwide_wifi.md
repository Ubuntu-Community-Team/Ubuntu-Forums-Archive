---
title: "Cannot connect to townwide wifi"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by awinterbreeze77 on 2009-10-30
Hi all, I've posted about this before, but no response, so having another go.
:KS:KS:KS
None of the linux machines in the small town that I live in can connect to the town's wifi network. Not one. We have one resident 'advanced' linux user and several newbies, but none of us has had success. I run Ubuntu, and the others run Mint, Arch, and Crunchbang (I think that's what it's called.) So, here's a general overview of the network:

Like I said, it's a townwide Wifi network. It uses Chillispot. On any windows or mac machine in town, you can connect to the network. Once you open your browser, you will be immediately relocated to the town's 'bumper page' wifitown.net ; Once you click 'Login' on that page, you are relocated to the Chillispot login page, which has fields for your username and password. You then login, and access the internet. :D

On a linux machine, one of two things happens. Either, the computer simply does not connect to the wireless network (even when it should, like if the signal is really strong); **or** it does connect, you get an IP address and all that jazz, but when you pull up your browser, nothing happens. :( You are unable to unload any pages. Any thoughts?

Thanks
Anthony :popcorn:

Here is info about the connection, if you need it:
[B]Active Connection Information
[/B]Interface: 802.11 WiFi (ath0)
Speed: 1 Mb/s
Driver: ath_pci

IP Address: 192.168.182.57
Broadcast Address: 192.168.182.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.182.1
Primary DNS: 12.106.247.131
Secondary DNS: 12.106.247.140
Hardware Address: 00:17:F2:3F:FC:F9


Edit: I've tried to make this post as graphically pleasing as possible in order to elicit a response.

---

### Post by Dark_Stang on 2009-10-30
I have a few questions here...
1. What IP address are you redirected to when you login with a windows machine? Ping that website if you're unsure.
2. Do you know the network is subnetted?
Edit: And I don't mean it's a /24, I mean do you know the physical topology of the network?
3. What type of radius authentication are we working with... LEAP? PEAP? 
4. Can you manually enter the information for the RADIUS server?

---

### Post by awinterbreeze77 on 2009-10-31
1. 192.168.182.1
2. I believe it *is* subnetted
3. Do not know about Radius, have never used it, and I asked around but could not get info on it.
4. Like I said, don't know about Radius :( How would I enter the Radius info directly?
 
I talked again with the 'advanced' linux user who said that he *thought* - well, he said he was 'almost certain' - that it's an ActiveX control affecting the certificate, or something like that. And he suggests trying to get the certificate information manually from a windows box. So I'm trying to do that, now...

---

### Post by Dark_Stang on 2009-10-31
So it uses ActiveX? That doesn't sound like Chillispot. Go ahead and run the following command and post the output for me. Replace wlan0 with your wireless card's name. If you don't know it run 'iwconfig' and it should be pretty obvious.
```
sudo iwlist wlan0 scan
```

More info: A radius server is used for authentication in large scale networks. We can try to manually create a network profile in networkmanager to work around the login page. We just need as much info as possible.

---

### Post by awinterbreeze77 on 2009-10-31
Cell 01 - Address: 00:22:B0:49:92:70

                    ESSID:"stelleE2"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=15/70  Signal level=-80 dBm  Noise level=-95 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:wme_ie=dd180050f2020101000103a4000027a4000042435e0062322f00

          Cell 02 - Address: 00:17:3F:04:79:7A

                    ESSID:"belkin54g"

                    Mode:Master

                    Frequency:2.462 GHz (Channel 11)

                    Quality=18/70  Signal level=-77 dBm  Noise level=-95 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

          Cell 03 - Address: 00:1C:F0:08:02:10

                    ESSID:"stelleM"

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm

                    Encryption key:off

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s

                              48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

                    Extra:wme_ie=dd180050f2020101000103a4000027a4000042435e0062322f00

---

### Post by Dark_Stang on 2009-10-31
> **awinterbreeze77 said:**
> Cell 01 - Address: 00:22:B0:49:92:70
ESSID:"stelleE2"
...
Cell 02 - Address: 00:17:3F:04:79:7A
ESSID:"belkin54g"
...
Cell 03 - Address: 00:1C:F0:08:02:10
ESSID:"stelleM"
...
Okay, so I'm going to assume the belkin54g is one of your neighbors who doesn't know how to secure their router. Now, are stelleE2 and stelleM two access points for your town wide network? If they are you have an absolutely terrible signal coming from them. Probably because they are on channel 6, which gets a lot of interference from cordless phones that may be in the area.

Is the town wide network supposed to be a hidden network? It is possible that your wireless card, or linux's drivers for it, can't scan for hidden networks. Do you know what Windows shows the network name to be?

Edit: Okay, so I have to go to work now. I won't be back until late tonight but I will respond when I get back.

---

### Post by awinterbreeze77 on 2009-10-31
Hey,

StelleE2 and StelleM are the townwide wifi networks... the signal is deceiving; despite being terribly weak, it connects just fine and has terrific download speeds. Admittedly, the signal is stronger in other parts of town, but the speed is still sufficient when the speed is suitable. [as a side note, I have taken the linux boxes to other parts of town where the signal is stronger, trying to use the wifi networks, to no avail.]


Windows shows the names the same, as StelleE2 and StelleM (and there are more, StelleN and StelleE1 and so on and so forth). 

And, going on a tangent: you're almost right on belkin54g, it is my unsecured network, but it isn't connected through the wifi network, it's connected to an old and defunct radio network. *That* used to work on the linux machine until they canceled the radio network a little ways back; I just haven't unhooked the router yet.

---

### Post by Dark_Stang on 2009-11-01
Okay, it shows encryption is off. But if it's using a secure login then there HAS to be some sort of encryption, so let's just try some random crap to break in here.

I am going to assume you are using gnome's network manager. If not, please reply so we can work it out.

Right click on the network manager and click edit connections.
Go to the wireless tab.
Delete any copies of the networks that we will be connecting to that you already have in there, then hit Add.
For the SSID put in "stelleE2" without the quotes. This is case sensitive.
Mode should be Infrastructure.
Leave BSSID and MAC address blank, at least for now.
MTU, leave it at automatic. The AP should tell your laptop that.
Now click on the Wireless Security tab.
Set the security "WPA & WPA2 Enterprise". Some options should appear.
Next we select the type of authentication. Let's try PEAP first. (Protected EAP)
Anonymous identity: Leave blank.
CA Certificate: Leave none.
PEAP Version: Automatic
Inner Authentication: This is a tough one, let's say MSCHAPv2 for now.
Username: Enter your username
Password: Enter your password
Hit Apply. See if it will connect with those credentials. 

If it doesn't, go back to the authentication and set it to LEAP and try that. If that still doesn't work, try to set it to Tunneled TLS. And if that still doesn't work, play with your inner authentication methods.

Post back with what you've found and what you've tried. This is really one of those situations where I wish I could just talk to the person who setup the network. Or, better yet, get a hold of a few of the routers or the server that handles authentication to take a look.

---

### Post by awinterbreeze77 on 2009-11-01
Ok, did what I could do the best of my ability. Using 8.04 instead of 9.10 so network manager didn't have the add feature and several the options you listed above were missing. Used 'Connect to other wireless network' to try the WPA2 Enterprise and Leap to no avail. Set the settings to what you wrote as best I could, but no luck. So, I'm working on updating my network manager.

Also, as of note, one of the key points that is probably central to this is, I don't have a login and password for the _network_, only with Chillispot. The network, as the person in our town who runs it always says, is unsecured. So of course I've tested my chillispot login and password, but it doesn't seem like that would have anything to do with connecting to the network.

As a side note, if you can immagine it, this network is very similar to one you might encounter in, say, Starbucks, or Barnes & Noble, or Panera Bread or something. Like, you don't need a login and password to connect to the network, but as soon as you login you are relocated to their bumper through which you have to pass in order to access the web at large. 

So anyways, updating manager, I'll keep on keeping on.

[-<

---

### Post by Dark_Stang on 2009-11-01
From what I've read up on chillispot there has to be a way to support authentication. This appears to be done through either WPA with the access point, or SSL/TLS with a server. My info is coming from here and appears to be a little dated.
[http://www.chillispot.info/features.html](http://www.chillispot.info/features.html)

Edit: Asked my Cisco professor who has a CCNP and is looking at getting his CCIE if he's ever heard of Chillispot... Nope...

---

### Post by awinterbreeze77 on 2009-11-06
well dude, i'm kind of at a loss. tried wicd and no go and no word on anything else. It may be a lost cause. I'll keep on pestering the local linux guy to see if he can come up with anything, and tlak to the town's network manager once more.

Thanks for all your help --- If you have any idea, let me know.

---

### Post by Dark_Stang on 2009-11-11
Whoever setup the network should have all the answers for you. Sorry I can't help much beyond this.

---

