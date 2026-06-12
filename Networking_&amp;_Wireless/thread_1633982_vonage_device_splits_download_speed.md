---
title: "vonage device splits download speed"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by mystmaiden on 2010-11-29
I have vonage phone service and two computers - currently using the vonage device which is essentially acts as a router with 2 phone ports. The trouble is, the vonage device splits the download speed among the two computers and the phone even when the second computer and the phone are plugged in but not actually being used.  Is there such a thing as a router with phone ports that does Not do this? My searches have come up with some solutions - all of which seem more complicated than needful. 

thanks,

mystmaiden

---

### Post by iponeverything on 2010-11-29
Put a switch between the wall and voyage router.

---

### Post by mystmaiden on 2010-11-30
iponeverything wrote: > Put a switch between the wall and voyage router.

sounds simple enough, but could you please explain a bit - exactly what kind of switch, etc?

---

### Post by cybergnome on 2010-11-30
Well, you really didn't say how your computers are connected to the single port in the Vonage router.  You could be using a hub, which differs from a switch in that all of the ports receive all of the packets, resulting in collisions that reduce the DTR.  That's why the switch is better.  The packets go to the proper port, rather than to all of them.  The switch BTW, is what I use with mine.

FWIW, you only get a certain amount of bandwidth over your connection.  That's determined by your ISP.  It is shared for all of the protocols you use that are ACTIVELY
being used, http, voip, etc.  So you're download rate MAY degrade with more activity, but it shouldn't be affected where there is no competing activity.  I'm not sure how you could determine that anyway.

Fluctuations, or rather reductions in DTR that are not activity related and not associated with increased load on the internet outside, implicate your modem, possibly the Vonage router, and possibly your internet connection (from the provider to your house).

Lastly, you should be aware that you don't have to use the Vonage router as a router or gateway.  You can configure another device(s) as gateway and router, and connect and configure the Vonage device to that router for Voip only.

My setup is as yours, and works ok with two computers.

---

### Post by mystmaiden on 2010-12-01
cybergnome wrote:>  FWIW, you only get a certain amount of bandwidth over your connection. That's determined by your ISP. It is shared for all of the protocols you use that are ACTIVELY being used, http, voip, etc. So you're download rate MAY degrade with more activity, but it shouldn't be affected where there is no competing activity. I'm not sure how you could determine that anyway.



Our vonage device has four ethernet ports, and 2 phone ports. I have each computer hooked up to an ethernet port and the phone in its respective spot (wired connections). How I determined it was splitting the signal was by checking speedtest.net when neither the phone nor the other computer were in use and finding that the speed was roughly a third of what I pay for. When I called suddenlink to see why, they asked about my set up and told me it was the vonage device. Afterward I hooked the main computer directly to the modem and sure enough my download speed was three times as fast as with the vonage device.

and:
> Lastly, you should be aware that you don't have to use the Vonage router as a router or gateway. You can configure another device(s) as gateway and router, and connect and configure the Vonage device to that router for Voip only.

How would you hook up both a router and a vonage device?

---

