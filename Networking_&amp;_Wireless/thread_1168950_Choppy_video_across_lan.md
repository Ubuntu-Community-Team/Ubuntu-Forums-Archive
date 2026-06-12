---
title: "Choppy video across lan"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by mr_cardholder on 2009-05-24
Hi all,
I was wondering if someone could give me some advice on resolving this issue.

 I have set up a Kubuntu 9.04 server with the intent of sharing video across a wireless network using samba. I have everything setup and working, however the video is very choppy, loses frames and sometimes freezes altogether. The videos I have been testing with run just fine on both the server and clients so the problem must be in the network. 

The server is wired to a wireless router and the router sends the video to the clients across the wireless network. I have shut down all applications that use the internet on both the server and the clients but to no avail. I was hoping there might be some resolution other than replacing the equipment I currently have in place.

Thanks,
mr_cardholder

---

### Post by lisati on 2009-05-24
I don't know if this will help but one of my routers has a "WMM" mode on its advanced wireless settings that helps give priority to time-dependent data such as video and audio.

---

### Post by mr_cardholder on 2009-05-24
> **lisati said:**
> I don't know if this will help but one of my routers has a "WMM" mode on its advanced wireless settings that helps give priority to time-dependent data such as video and audio.

Thanks for that but unfortunately my router doesn't seem to have that option. It was only $25 after all.

---

### Post by Mars73 on 2009-05-24
> **mr_cardholder said:**
> Thanks for that but unfortunately my router doesn't seem to have that option. It was only $25 after all.

One of the things I use my Ubuntu machine for is sharing movies to my Xbox/XBMC downstairs with the help of Samba.
With previous versions it worked wonderful but with 9.04 I had the same problems. Choppy video and mostly after a while it stops.
Do you have ssid on disabled? After trying out 100 of different things/options I turned on the ssid broadcast today and all was fine.
Playback is smooth and no stops.

---

### Post by mr_cardholder on 2009-05-24
> **Mars73 said:**
> One of the things I use my Ubuntu machine for is sharing movies to my Xbox/XBMC downstairs with the help of Samba.
With previous versions it worked wonderful but with 9.04 I had the same problems. Choppy video and mostly after a while it stops.
Do you have ssid on disabled? After trying out 100 of different things/options I turned on the ssid broadcast today and all was fine.
Playback is smooth and no stops.

I assume you mean ssid broadcast on the router and yes, it is turned on. I turned it off just to experiment with what you said and same result, still choppy

---

### Post by mr_cardholder on 2009-05-24
Okay, after doing some further testing, I can say that the problem is definitely the wireless connection. When I wired my laptop to the router directly, the issues were gone. Also, my desktop has the same issue with the video streaming as the laptop so the laptop isn't the problem.

---

### Post by Kareeser on 2009-05-24
When you say the desktop has the same issue, do you mean that the wired desktop can't watch videos on the wireless laptop?

Reversing the connection doesn't mean the laptop isn't at fault... it does sound like either the wireless card on the laptop, or the transmitter on the router, is not powerful enough...

---

### Post by edvar on 2009-09-14
I have the exact same problem. I have jaunty running XBMC and a Macbook running Plex both connected wirelessly with Ubuntu sharing my media folder to Plex using samba. I also tried with VNC but at no avail.

At first I thought it was a problem with my router being at Wireless G one so I bought an Airport Extreme, connected it to my ADSL/Wireless router via ethernet and bought a Wireless N card to the Ubuntu box. So both Ubuntu and Mac are now connected at Wireless N speeds to the Airport Extreme and they go out to the internet via a wired connection to the router. Same problem. 

Then I thought the cause was the router or my apartment had too much radio interference. Well, a couple of week ago I moved to a new place and bought a brand new ADSL/Wireless router. Still same problem.


This is driving me crazy! Browsing the internet is fine but streaming video is still a nightmare in Jaunty!

---

