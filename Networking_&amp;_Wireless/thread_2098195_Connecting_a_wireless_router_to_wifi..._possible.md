---
title: "Connecting a wireless router to wifi... possible?"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by lykwydchykyn on 2012-12-25
I should probably know this, but somewhere between holiday stress and having a one-month old daughter has blown my brain power.

So here's my question:

I have a wireless network in my house, but I want to set up some non-wireless systems in a part of the house where I can't feasibly run cable.

I have a spare wireless router, a Netgear WGT624 v2.  AFAICT I can't put DD-WRT on it or anything like that.

I'm wondering if I can connect the wireless on the Netgear to my WIFI network as an uplink, and then use the wired ports on it to connect devices to the network.  It seems like it should be possible, but maybe I'm not searching for the right terminology for this setup.

Anyone have any insight?

---

### Post by chadk5utc on 2012-12-25
I dont know if off the shelf equipment will do what you want but I do this with Ubiquiti NanoStationM2HP and PicoStationM2HP devices which allow both interfaces to be fully configured in multiple modes. These are commercial Linux WISP AP/Routers. I have one of them installed remotely in the horse barn with security system so I can monitor them from the house about 800feet.

---

### Post by Cheesemill on 2012-12-26
You need to set up the router as a wireless bridge. Some will let you do this via the routers web interface but after a quick google it seems like this isn't the case with the WGT624.

Instead you have to telnet into the routers command line interface and make the appropriate adjustments, there's an article here that describes the process:
[http://www.beatjunkie.de/Router_eng.htm](http://www.beatjunkie.de/Router_eng.htm)

The only problem that I can see is the the application used to enable the CLI is a Windows executable (telnetEnable.exe) but you should be able to run this through Wine (or from a Windows machine if you have one).

---

### Post by fyfe54 on 2012-12-26
I had a similar situation.  The wireless router is in the basement at the front of house and I needed (better) internet access for streaming netflix on the second floor at the back of the house.  I used a pair of Powerlink adapters with a cable from the wireless router to the Powerlink downstairs.  Upstairs, there is a cable from the Powerlink to another wireless router.  The  streaming device (Blueray player) is hard wired.  The upstairs router greatly improved the wireless signal up there too, but you may not be able to do wireless with the WGT624v2.

---

### Post by kurt18947 on 2012-12-26
Or buy a wireless bridge if you don't have a wireless router you can repurpose.  Or use powerline networking as fyfe54 suggested.  Or there's another option if you have coax running where you need it.  Verizon FiOS uses MoCA as an ethernet transport (If that's the proper term - it may not be).  People have bought used Verizon FiOS routers - there's one for sale on my local Craigslist for $15 - and repurposed them.  That eliminates some potential problems with powerline networking but MoCA can be a little fussy about what kind of splitters and how many are daisy chained.

---

### Post by lykwydchykyn on 2012-12-27
> **Cheesemill said:**
> You need to set up the router as a wireless bridge. Some will let you do this via the routers web interface but after a quick google it seems like this isn't the case with the WGT624.

Instead you have to telnet into the routers command line interface and make the appropriate adjustments, there's an article here that describes the process:
[http://www.beatjunkie.de/Router_eng.htm](http://www.beatjunkie.de/Router_eng.htm)

The only problem that I can see is the the application used to enable the CLI is a Windows executable (telnetEnable.exe) but you should be able to run this through Wine (or from a Windows machine if you have one).

I think I compiled this once and tried to enable telnet on the device.  I can't remember if I ever got in or not, but I'll give it another go.

---

