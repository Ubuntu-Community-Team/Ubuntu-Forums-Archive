---
title: "wifi issue - &quot;no dhcpoffers received&quot;"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by annec on 2009-11-01
Hi!

I've been trying for some long hours to solve a wifi issue that appeared when upgrading to version 9.10 of Ubuntu. It was kind of working under previous version 9.04 (never was perfect, but I could access the internet most of the time...). Now it's decided not to work at all anymore.

So, here's the issue: 
- wifi began with some randomly disconnecting, say, every 10 minutes. 
- iwconfig stated "no access point"
- then it stopped recognizing networks, e.g. iwlist scan gives me "no scan results". 
- I tried several things (note that I'm no informatician, I'm more of a beginner with linux), including modifying file /etc/network/interfaces where I added 
```
auto wlan0 # (that's my wifi interface)
iface wlan0 inet dhcp
wireless-essid "my_network"  #(don't know if I should use the " " here...)
wireless-key my_key
```

I also tried: ```
 /etc/init.d/networking restart 
```

and I observed with iwevent that even when it did see my network (which it does randomly making me feel lucky), it switched within a second from "New Access Point/cell: [actual access point]" to "New Access Point/Cell: Not-Associated". 

Finally, 

 ```
 sudo ifconfig wlan0 up
sudo dhclient wlan0 
```
gives, after some bla:

 ```
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received
No working leases in persistent database - sleeping
```

A few more infos and clues include:
- I'm using network-manager ; wanted to change but then again: no internet on my linux machine
- I read something on a forum related to getting a static IP address, which I think might be a relevant idea
- oh, and of course: internet works perfectly fine on the mac os I'm using to send this post!

There. I hope I'm expressing myself ok and giving relevant infos. I really really hope you can give me some hints here, because I think I'm about to crack up! Thank you a LOT in advance.

---

### Post by rpras on 2009-11-02
I'm having the same problem on Karmic installed on a 60Mhz PowerPC iBook G3.  Airport card in the iBook (802.11b) did connect a few times to my Netgear 54g router.  However, I've had no connection -- the same "No DHCPOFFERS received" message keeps appearing -- I've tried Network Manager, wicd, and command line -- all give the same "error."

Tonight I also tried my D-Link DWA-160 802.11a/b/g/n USB wnic.  Same problem.

Both the Airport card and the DWA-160 work because I can see the available APs.  Signal strength is good.  The connection fails with "Cannot obtain an IP address" or some such.

Any help is greatly appreciated.

---

### Post by jamogon on 2009-11-02
I have the same problem, and not how to solve ...  
 8.04 In previous versions I had no problem

---

### Post by annec on 2009-11-02
OK, so what I did is: 

- I went through the options of Network Manager, tab "Wireless" and deleted what it had named "auto [my_network]". 
- Then I reconnected to the network. It asked me for my password. And worked!
- I used the internet connection to download wicd and replace network-manager with it. It automatically suppresses network-manager, so there is nothing to do. 
- I reconnected using wicd and it seems stable. 

I'll keep you informed...

---

### Post by annec on 2009-11-02
It has not stopped working since I installed wicd. So my advice: get rid of network-manager!

---

### Post by rpras on 2009-11-02
> **annec said:**
> OK, so what I did is: 

- I went through the options of Network Manager, tab "Wireless" and deleted what it had named "auto [my_network]". 
- Then I reconnected to the network. It asked me for my password. And worked!
- I used the internet connection to download wicd and replace network-manager with it. It automatically suppresses network-manager, so there is nothing to do. 
- I reconnected using wicd and it seems stable. 

I'll keep you informed...

Hmmm...  I have to try this...

> **annec said:**
> It has not stopped working since I installed wicd. So my advice: get rid of network-manager!

This is the behavior I saw with Jaunty and Karmic -- after first installing wicd (and getting rid of network manager in the process), the connection to my Netgear 54g router was rock solid -- until the next disconnect/reconnect cycle.  Have you tried disconnecting and reconnecting with success?

---

### Post by rpras on 2009-11-03
Ok, so tonight I tried another approach.  Since it is at the "dhclient eth1" (Airport card on my iBook G3) or "dhclient wlan0" (DLink DWA-160 USB on my iBook G3) stage that things fail, I tried compiling and using dhclient from ISC dhcp 3.1.3 release.  The dhcp version in Karmic I have installed on my iBook is version 3.1.2.  Just hoping that a later version would help.

No luck.  Still "No DHCPOFFERS received."  Next on my list of things to try is: downgrading wicd or network manager, downgrading the kernel, and building a new powerpc kernel.

---

### Post by rpras on 2009-11-07
My problems connecting to my wireless routers from my iBook G3 running Karmic continue.

Last night I was able to test if Airport would connect to an unencrypted network.  It worked -- DHCP and all.  So the good news is that I have narrowed down the problem to WPA.  Most probably wpa_supplicant is either misconfigured or not properly talking to the orinoco driver.

Investigation continues...

---

### Post by rpras on 2009-11-08
Finally -- got it working!!!  :D

Okay -- so this is what worked for me -- I'm no expert so please don't ask "why?"  I have Karmic on my 600MHz iBook G3 with an Airport card.  The modules "airport" and "orinoco" are loaded correctly on boot.

What I did this time was to **completely** remove wicd.  No network-manager either.  Plain vanilla ifconfig/iwconfig/wpa_supplicant/dhclient.  All from Karmic.

Then I followed the guide here: [COLOR=Blue]_[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)_[/COLOR]  (thanks Ubuntu Geek! =D>).  Purely command line stuff -- and it worked.  Conclusion: wicd and network-manager both seem to have problems with wpa_supplicant.  Not sure why.  The connection survived a reboot, so it seems to be here to stay.  Typing this on my iBook.  Yay!!

Here is my /etc/wpa_supplicant.conf:

```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="myap"
    scan_ssid=0
    proto=WPA
    key_mgmt=WPA-PSK
    psk=mypsk
    pairwise=TKIP
    group=TKIP
}
```Now, I used these lines in my /etc/network/interfaces file:

```

# Airport 2
auto eth2
iface eth2 inet dhcp

# WPA
wpa-ap-scan 1
pre-up sudo /sbin/wpa_supplicant -ieth2 -Dwext -c/etc/wpa_supplicant.conf
pre-up sleep 5
post-down sudo killall -q wpa_supplicant
```and checked if my wireless adapter was up and running after a reboot.  It was!  Great.  However, I still had to run 

```

sudo dhclient eth2
```after logging in to get an IP assigned from my AP.  Would be great if I could figure out how to get dhclient run at boot time also.  Any pointers would be great.  For now, I can live with it.

I love Ubuntu.

---

### Post by annec on 2009-11-15
Hi there,

Sorry I did not answer, I thought the issue was solved. 

OK so your solution works too. I remember indeed having a look at that wpa_supplicant thing. 

However, I am no expert either! 

My update is: since I installed wicd, **I have not had the smallest issue** with my connection. 

I hope one of the two solutions works for other people who have the same problem!

Cheers,

annec

---

