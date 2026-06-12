---
title: "Internet connection was faster on Windows..."
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by the_fury on 2008-12-09
I switched to Ubuntu only a month ago, so I'm still somewhat wet around the ears. 

On Windows, my router would boost my wireless signal to an average of 270 mbps, a max of 300 mbps. 

When I ran Ubuntu for the first time, I checked "connection information" and was disappointed to find a measly 54 mbps. 

What's going on? Can Ubuntu not handle higher speeds or what? If you can shed some light on this, it'd be appreciated.

NOTE: I've tried various tweaks (disabling ipv6, etc.) so please keep this in mind as you answer the question. I am merely asking why it will not use my obviously faster connection.

---

### Post by spiderbatdad on 2008-12-09
how is your performance affected? My wireless "speed" according to network monitor is 11 mbps. As I type this, I am downloading a file from the internet at 540KB/s.
Try a speed test online. [http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by the_fury on 2008-12-10
My Network Connections box shows "54 mbps" and I can't get above a 24 mbps download on BitTorrent.

My speed test results: [http://www.speedtest.net/result/370791739.png](http://www.speedtest.net/result/370791739.png)

---

### Post by superprash2003 on 2008-12-11
54mbps is probably the speed between your pc and your wifi router.. this would be useful for LAN transfers.. but your actual internet download speed seems to be 24mbps.. you could verify the actual speed with your ISP..

---

### Post by rickyjones on 2008-12-11
> **the_fury said:**
> I switched to Ubuntu only a month ago, so I'm still somewhat wet around the ears. 

On Windows, my router would boost my wireless signal to an average of 270 mbps, a max of 300 mbps. 

When I ran Ubuntu for the first time, I checked "connection information" and was disappointed to find a measly 54 mbps. 

What's going on? Can Ubuntu not handle higher speeds or what? If you can shed some light on this, it'd be appreciated.

NOTE: I've tried various tweaks (disabling ipv6, etc.) so please keep this in mind as you answer the question. I am merely asking why it will not use my obviously faster connection.

What kind of wireless hardware are you using? It is quite possible that the Windows device drivers allowed some extra speed by taking advantage of a proprietary portion of the hardware. For example, the Dlink brand of wireless gear has it's own Super G rated at 108mbps. In order to use it all the products must be dlink and have the same family of hardware. It's also positive that only the Windows device drivers will enable this function.

Just a thought.

-Richard

---

### Post by the_fury on 2009-03-28
> **superprash2003 said:**
> 54mbps is probably the speed between your pc and your wifi router.. this would be useful for LAN transfers.. but your actual internet download speed seems to be 24mbps.. you could verify the actual speed with your ISP..

I'm not sure how to verify that... I have Comcast if anyone knows......

---

### Post by the_fury on 2009-03-28
> **rickyjones said:**
> What kind of wireless hardware are you using? It is quite possible that the Windows device drivers allowed some extra speed by taking advantage of a proprietary portion of the hardware. For example, the Dlink brand of wireless gear has it's own Super G rated at 108mbps. In order to use it all the products must be dlink and have the same family of hardware. It's also positive that only the Windows device drivers will enable this function.

Just a thought.

-Richard

I'm using my laptop's standard wireless adapter... an Intel wireless pro adapter.. I don't know exactly, but the wireless router was ADVERTISED at 300 mbps. And in Windows, it used to say at least 270 mbps. I know it's possible for network-manager to display 100mbps (I had an ethernet connection once), so why doesn't it display that here?

---

### Post by the_fury on 2009-03-30
bump

---

### Post by the_fury on 2009-04-01
bump

---

### Post by Mze on 2009-04-01
Checking your [internet speed]("http://www.dslreports.com/speedtest")

---

### Post by freonchill on 2009-04-01
you are mixing several monikers here

internet - comcast 5,10,50mbps (thats your "rated" down speed)
e.g. you can get 50mbps download speed (note, this is in BITS; e.g. 50mbps / 8 = 6.25mb/s (megabytes)
typically upload speed over residential ISP is much slower (probably 768,1,1.5mbps (once again, in BITS, so 1.5 / 8 = 0.1875mb/s or 192kilobytes/s)

wired lan - 10/100/1000baseT; is the "theoretical speed" you will NEVER get 100mbps over 100baseT, typically 3/4 to 1/2 that
e.g. 100baseT = 100 /8 = 12.5 - 6.25 megabytes

wireless lan - B = 11mbps, G = 54mbps, N = 54 to 300mbps; this is the "theoretical speed" you will never get 54mbps through-out over G wireless, it might show 54mbps as your connection rate, just as 100baseT you will see when connected over wired. other caveat with wireless is that RF is not perfect (what wireless travels over) so you can have a wireless G router and a wireless G wireless card and only have 27mbps or 11mbps due to signal strength.

54 /2 /8 = 3.375megabytes MAX

so, you say that you used to get 270 to 300mbps wireless
then you probably had wireless N. if you are only getting 54mbps now. the driver in linux for your wireless card does NOT support N, so it is falling back on wireless G for service, so you get 54mbps rather than 270-300mbps.

you said that your connection is 54mbps (wireless signal) and getting 24mbps on torrents

torrents have an option for max speed. lets just assume you have standard comcast internet service, 5mbps / 8 = .625 * 1024 (to get to kilobytes) = 640 kilobytes (now, comcast has {speed boost, which could, for the first 5-10mb during traditional downloads allow you to have twice your connection speed) so you could peak out at 1280 kilobytes (or 1.28megabytes) but its doubtful for torrents that that is possible.

so if your torrent program is showing your speed in bits, then it might be showing 5mbps (megaBITS) MAX, there is no way you can get 26mbps.

what exactly is your hardware
assuming linksys/rca/motorola modem

some retail wireless N router, perhaps even MIMO (hense the 300mbps connection speed) your wireless card

if a intel wireless card (that was able to do 300mbps before, must be an N card (4965AGN or 5100/5300)

any of the intel wireless N card have to have 2.6.24 or higher kernel.

---

### Post by linxuser14 on 2009-08-03
I've noticed this slow down effect also. My laptop has intel pro wireless and has gotten around 200 while in windows compared to less than 100 in linux. I've just recently tried linux virtual machine running in windows host, and the virtual player shows multiple connections to the windows host with a speed approaching 300. I've never seen it go that fast with my current router connection. I imagine the connect between guest and host is all internal but I'm curious that its faster than windows native connect speed. But linux native, really is slow enough that I'm thinking of using the virtual linux. I'm gonna try a windows' guest on windows' host and see if it increases more.

:confused:

edit - add

I'm using XP and hardy 8.04.

addt'l edit speed result
I've never got a result like this, I've managed net adapters in virtual machine (5 of them, bridged, vmnet0, ... vmnet3) I'm wowed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123513&stc=1&d=1249348426[/IMG]

edit - OK I see. result(Kb/s) / 8 = KB/s .

The following is null - in figuring it out the speed result actually comes up the same as for native windows. Linux native is still slow, while virtual linux guest running in windows host is faster.
Heres the virtual XP result, shows same as native speed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123589&stc=1&d=1249404035[/IMG]

***Note: NIX my false conclusion above: I was self-'deluded',,,, ***

(The only true conclusion was that native linux was 1/3 of windows' connection speed,
virtual linux and virtual XP running in XP host show near to the same speed result
as native windows) - (Also virtuals linux/XP connect at 1/3 of speed of windows'
host, when run under linux host)

---

