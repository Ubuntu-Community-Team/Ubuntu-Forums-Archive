---
title: "Wired Internet Connection Freezes"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by pbeesley on 2012-09-07
Hi Guys, hoping someone can help me with this one because its doing my head in.

For the past week or so my internet connection has been freezing for about 30seconds to a minute every so often. 

A ping request running in the background right now shows no errors trying to get out, it just doesn't do anything while the network is frozen (I've been running a ping to google since I started the PC and in 385 ping requests it's frozen 8 times.

This computer is fine when using windows :S

Things I've tried: [LIST]
[*]A full reinstall (with a seperate /home that was left unformatted)
[*]Updating driver to use r8168 instead of r8169 (i've had no issue with this drive since 12.04)
[*]Leaving PC on for hours and then running a ping command. (no difference)
[/LIST]

What Information should I be giving you guys? :frown:

P.S the only thing that has changed since this was work is I put in another 8gb of ram (now 16gb total) and I put an LED light strip into my case

Thanks

---

### Post by pbeesley on 2012-09-07
Ok so I just tried using (and currently am) using a live cd. The connection is fine :S even using the dodgey r8169 drivers :S

Could something in my /home be screwing this up?

---

### Post by pbeesley on 2012-09-09
I created a new user to see if it was /home settings some home. No dice :(

Been running a ping tool for the last 20mins 79% successful 

Any ideas?

---

### Post by pbeesley on 2012-09-10
no one :(

---

### Post by iponeverything on 2012-09-10
in grub -- boot to an older kernel.

---

### Post by pbeesley on 2012-09-10
well i tried reinstalling the entire OS, did nothing to help

---

### Post by steeldriver on 2012-09-10
sometimes these odd connectivity glitches are MTU related - afaik there's really no systematic way to figure that out, but it may be worth just playing with the connection MTU to see if it makes any difference

[http://en.wikipedia.org/wiki/Black_hole_%28networking%29#PMTUD_black_holes](http://en.wikipedia.org/wiki/Black_hole_%28networking%29#PMTUD_black_holes)

---

### Post by pbeesley on 2012-09-27
I fixed this problem and here's the story of how.

Gather round children for this is the story of pbeesley the fool!

Once upon a time pbeesley had a PC and a virgin media superhub. For a while these devices lived happily together living accross the road from each other. Mr Superhub lived at 192.168.0.1 while Mr PC was speical and lived at the special address of 192.168.0.100.

Then one day Mr Superhub started being naughty and causing issues in the land of the local domain. A new router was purchased and one day Mr Netgear arrived and moved into Mr Superhub's old address of 192.168.0.1 while Mr Superhub was cast out and put into modem mode for his sins.

It was around this time that Mr PC got sick, but only when in ubuntu, while in windows mode is was as happy as a lamb. Everyone on the domain weeped for Mr PC, the domain master scoured the wider internet domain for a cure but alas non was found. Then one day it came to the domain master in the shower! Mr Superhub was squatting in Mr PC's address of 192.168.0.100!!! Mr PC quickly moved acrross the road to 192.168.0.199 and everyone lived happily every after.   

TLDR: Don't set the IP of your PC to the same address as your modem ](*,)

---

### Post by jizkid on 2012-10-14
Hello, 
I have the same problem. 
30 second-types of hesitations, where also the ping freezes.
The dual boot on windows works fine. 

upgrading ubuntu did not help. 

I used DHCP for receiving an IP-adress.
Now i finally changed my ip-address in a solid one. Let's see what happens now.

After testing... it seems a little faster but still seems to freeze also, no conclusion yet, but the conclusion seems to go to "not solved"

The irritating thing is that all computers on my internal network are working fine, only my "top-desktop" on Ubuntu has this freezing effect, and formerly this was no problem at all.

---

