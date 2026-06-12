---
title: "Connecting to the internet via an Airport Extreme"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by rishabh on 2009-04-13
This is my networking setup:

Ubuntu PC -> DLink USB wireless adapter -> Apple Airport Express (Password protected) -> modem -> internet.

Ubuntu gives out of the box driver support for the Dlink USB adapter. 
Network manager detects the Airport wireless network and the signal strength.

However, since the Airport's wireless is encrypted, I need a passphrase to connect (which is 8 characters long). 
Network manager refuses to connect using the passphrase I give it. 
It works fine on Vista using the software DLink provides.

Is this normal or am I doing something wrong? How do I make it connect?

---

### Post by ulfj on 2009-04-13
I have no problem connecting to the airport extreme routers,but configuring them was another story,I got frustrated and used windows to do that.

---

### Post by rishabh on 2009-04-13
ulfj,

The Airport seems to be configured properly, as it works with Vista perfectly. 
I think I might be choosing the wrong setting, or confusing WEP with WPA or something like that. 

Could it also be something to do with what is mentioned here?:  [http://www.symphonious.net/2005/12/13/80211b-ubuntu-linux-airport-and-you/](http://www.symphonious.net/2005/12/13/80211b-ubuntu-linux-airport-and-you/) 

The problem is that it would be a little difficult to gain access to the Mac through which I could run the Airport Admin Utility.

---

### Post by ulfj on 2009-04-13
Kind of funny I just recived a call from the building that I set up the routers in and a couple of people are having the same problem as you are,I will see if I can solve this in the morning tommorrow and will post the solution to the problem then.From the link you posted that may well be your solution,

---

### Post by rishabh on 2009-04-14
The problem is that it's hard for me to access the Airport Admin Utility. 
Is there any way to generate the hex key from my passphrase as Ubuntu would understand it? 
Some software, perhaps?
Or maybe if the algorithm is known, I could work it out myself?

---

### Post by cyberurchin on 2009-04-14
Hi!

Have you tried connecting to the internet with Windows (which apparently works) and then connecting with Linux WITHOUT turning off/rebooting the DSL router and the Airport Extreme?

c.

---

### Post by rishabh on 2009-04-14
cyberurchin,
Yes, that's what I've been trying. 
Doesn't work :(

---

### Post by heimi on 2009-04-18
I have the same problem. I can connect to my Airport Extreme Base station with several Windows maschines. I can also connect with my Ubuntu 08.10 Installation but not with the current release candidate of Ubuntu 09.04. 
The Base station is found, but when I try to connect using my WPA Key it cannot connect and prompts me for the password again (which is then displayed as a hex value).
When I connect to another router, the connection runs fine. So the problem is related to the Airport Extreme Station.

---

### Post by phubai on 2009-04-18
Well, I just connected to mine, so I'm not sure we can isolate it to an Airport Extreme issue at all. I am using WPA2 on the Airport Extreme and am not hiding the SSID as an FYI.

I was connected via my old Netopia, but thought I'd try the Airport just to be sure there wasn't a problem. I'm not saying there isn't, but at least for me and my configuration as mentioned above, it's working fine on 9.04.

---

### Post by heimi on 2009-04-19
Thanx for that information. 

I swiched to another Router (there's a FON Router running here too) and I have no problem to connect with a WPA2 Key to the FON Router with the same beta 09.04 installation. So at least for me it seems to be related to the base station.

---

### Post by notessensei on 2009-07-26
I also have problems with my Airport Extreme. I can connect to public wifi, to the corporate wifi (that is using LEAP/WPA2), but not to the airport. I tried WICD and it worked nicely except when using WICD something overwrites my resolv.conf when I use VPN, so I switched back to network-manager.
So there must be some configuration switch to make Ubuntu play nicely with the airport.

---

