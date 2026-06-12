---
title: "Netgear WG111v3, Connected but no internet"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by kyle99 on 2009-03-25
I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827)

At the end, I managed to connect to the router, but there's no internet. It works when using a different adapter, but that router is old and slow, so I wanna use the netgear one. I'm using 9.04 beta, but this problem affected me when I used 8.10 aswell. Any help?

~Thanks

:guitar::guitar:

---

### Post by kyle99 on 2009-03-25
Bump

---

### Post by kyle99 on 2009-03-25
Bump

---

### Post by kyle99 on 2009-03-26
Bump

---

### Post by kyle99 on 2009-03-26
Bump

---

### Post by kyle99 on 2009-03-26
Bump

---

### Post by kyle99 on 2009-03-27
Bump

---

### Post by kyle99 on 2009-03-27
Bump

---

### Post by kyle99 on 2009-03-27
Bump

---

### Post by sailthesea on 2009-03-27
Mine works (just) but the netgear really doesn't hack it with Ubuntu I've been looking for a way to improve it for ages Try your older equipment and do some upgrades that seems to help a bit I can't remember exactly what made the most difference but if I do I'll let you know!
 You're not the only one having this problem Believe me:(

---

### Post by Rehdon on 2009-04-25
Hi all,
to my great surprise now the Netgear WG111v3 USB adapter works out of the box with Ubuntu 9.04! Before this Ubuntu release I had to use ndiswrapper, no more.

There's a big "but" somewhere, though, because the network connection seems to be slower for some applications (f.i. for the MMORPG I'm currently playing). I thought this might be related to IPv6, but it seems that it was regularly enabled under 8.10.

Any ideas? Anybody tried using ndiswrapper under 9.04?

Rehdon

---

### Post by matbroadbent on 2009-04-25
....yes, without any success at all. :(  

Intrepid was quite happy with my WG111v3 + Wicd combination.  Now Jaunty has come along and spoiled the party.  

It'll be really ironic if NDISWRAPPER is no longer required, and is actually causing the problem, instead of being the one thing that brings my wireless connection to life.

Further to the original post: if you're connected wirelessly to your router, and still have no internet connection, performing a DHCP release/renew on the router itself usually fixes it for me.

---

### Post by matbroadbent on 2009-04-27
Confirmed: Jaunty works with the WG111 v3 out of the box here.  (Evidence = just try the Live CD!)

After spending a day and a half faffing* about trying to get Intrepid's botched-but-working-config back resembling a Jaunty clean install, I'm happy to report that I'm now connected wirelessly without NDISWrapper or Wicd.  

It'll be interesting to see if the connection holds up when under heavy use....




(*a highly technical undertaking)

---

### Post by wolfestine on 2009-04-28
I don't know about you guys, but it's not working for me. I mean I do get connected to my router, but strangely enough I can't ping it. And yes, I am using final release of Jaunty all right. The thing is, I can send about 2-5 pings before it starts failing. Also the lights on my wg111v3 stays on, rather than blinking like it should, but that's 'cause no data is being transferred. The driver that is being used is one rtl8187. I am a newbie, and would be grateful for your help. Also, am I thread-jacking? should I start my own thread? 'cause it seems that I am the only one here having problems with the final release.

---

### Post by Rehdon on 2009-04-29
No, I'm having problems too, and the light is not blinking, you're right.

Rehdon

---

### Post by mcds2 on 2009-04-29
i can't get my adapter to work and i am using the same one the difference is that mine is the pci version and i am using the wubi installer for ubuntu 9.04! coulde someone help me get it working!

---

### Post by matbroadbent on 2009-04-30
The "light not blinking" might be a red herring.  As reported above, mine's working fine and - you're all correct - the light just doesn't seem to blink with this rtl8187 driver.

On inspection I can't ping my default gateway either.  Then again, that might be down to Firestarter stopping that sort of traffic.

All I can suggest is try a full blown LiveCD environment.  (Not much help, I know, sorry.)  The theory here is that LiveCD is about as clean an Ubuntu environment as you're ever likely to get.  If wireless doesn't work here I'd be thinking hardware; if it works here and then not in your installed Ubuntu environment, then I'd be thinking config/software.

In times of desperation, historically, I've abandoned Gnome Network Manager and gone with Wicd.  Unfortunately for me it's been found wanting in Jaunty this time, but you might have some success.

---

### Post by WhiteWhale76 on 2009-05-07
I upgraded from Ibex to Jaunty, the WG111v3 quit working. Status shows connected to router but no internet, same sob story. Should I battle on or just hook up the ethernet cable :confused::confused::confused:
 
WW

---

### Post by dushy7 on 2009-07-08
I bought a Thinkpad t400 recently. With it I took the Thinkpad b/g/n wireless card expecting that would be a atheros make. Unfortunately it was a realtek 8172 part. After a lot of searching on the internet I found that there are no linux drivers for that card (even ndiswrapper doesn't work). 

So I got a wg111v3 netgear usb adapter from radio shack. I am using Ubuntu 9.04. Like you all said, when I plugged it in I was connected, but I could not ping to router and there was no internet. 

I was initially 15ft away from my router. As I started taking the usb adapter closer to the router, the signal started getting better and the internet started working. So I moved my router within 5 feet range of my desk and the adapter has no problems now. Full signal/speed. No connection drops in about 7 hours now. 

The only thing that I am worried about is the warmness of the adapter exterior. The surface of the adapter get extremely hot after prolonged usage. Is that normal? 

Anyway I am glad the wireless is working somehow. But I hope Realtek 8172 will be supported in the future at least.:p

---

