---
title: "Cannot get Advent Powerline adapters to work with Ubuntu"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by BolinMDT on 2012-12-17
Hi all

I've just bought a new cheap system and installed 12.04 on it. As it's a desktop and used in a different part of the house I bought a pair of Advent Powerline 200Mbps adapters (model APWL2012).

I have also tested the adapters with my old laptop running 8.04, with pretty much the same results.

The adapters have some lights on - according to the manual they are connected and working correctly and all is well there.

On 12.04 there is no internet connection. The network icon at the top seems to have recognised a wired connection. A pop up message keeps appearing saying that the wired connection is disconnected.

On 8.04 there is no internet connection. The network icon at the top looks the same as when the computer is connected to a working wired connection (2 black screens).

So it appears to be related to running Ubuntu but I cannot see what to do. The instructions with the adapters don't help and they came with a 'resource CD' which needs Windows to run.

Any ideas?

Thanks, Bolin.

---

### Post by synapsys on 2012-12-18
If the wired connection is sending out a proper signal, Ubuntu shouldn't have a problem with it. Do you have anything else running a Windows OS that you can use for testing? I read the description for the APWL-2012, and it mentions something about 128 bit AES encryption. I wonder if this is only between the two power outlets, or if you need some Windows client to make this work. Can you plug the Ubuntu box directly into the ethernet port on the router? If so, does it work?

---

### Post by BolinMDT on 2012-12-18
Hi synapsys, thanks for the reply.

I don't have a Windows machine to test with them, the only option would be to take them to a friend/relative to test.

The 'quick start' instructions make no mention of needing to install the 'resource' software, so in theory it should work straight off.... puzzling:confused:

My laptop sunning 8.04 is currently plugged straight into the router and has always been fine. It's not practical for me to set up the desktop next to the router, and as the symptoms are pretty much the same for both systems it should be a common problem between the two.

---

### Post by Grenage on 2012-12-18
homeplug/powerline adapters are generally designed to work together, with the connection being transparent to the devices connected to them.  My suspicion would be the units themselves, especially given the brand and the many complaints I have heard.

Try returning them for an alternate brand, or just an alternate set.  I've got a couple of netgear units, and they've been quite flawless.  Some units have software (installed on the client PC) encryption, while others are hardware - and much better.  Either way, try another set.

---

### Post by BolinMDT on 2012-12-19
Well I tested them at a friend's house on Windows XP, pretty much the same result - his computer detected the network connection but the internet didn't work.

He has the same ISP as me and suggested that was the cause, although I doubt it personally.

Has anybody any more ideas? I want to have another crack at this before giving up and returning them.

---

### Post by Grenage on 2012-12-19
> **BolinMDT said:**
> He has the same ISP as me and suggested that was the cause, although I doubt it personally.

You would indeed be correct in doubting that as a cause; you'll want to return them.  If there's an option to 're-pair' or reset the units via a button, you can try that.

---

### Post by haqking on 2012-12-19
have you set them up ?

some have different modes and need to be setup with the buttons on the front or through a web interface.

Depends on the model though, I take it you have followed the instructions for your model ?

---

### Post by BolinMDT on 2012-12-19
Thanks to everybody for their help - I have now solved this and feel a bit silly. I'll explain.

The instructions said to check that the 3 yellow lights were on (power, connection to other unit and ethernet to computer/router).

And they looked all to be on. When viewed from an angle, which is what I was doing due to the location of the sockets being behind furniture etc.

However, when viewed directly straight-on, it looked like the middle light on both (connection to other unit) was slightly dimmer than the other 2. Actually, the middle light wasn't on at all but the light from the other 2 LED's was spilling out and making it look like it was illuminated when viewed from an angle#-o

So they just needed to be paired.... now working.

So now I can get on and use my new machine with 12.04 - yay:D

Thanks again all and apologies for my lack of attention to detail - although I think the designers of these should take some blame for allowing light to spill out through a indicator that is supposed to be showing as off!

---

### Post by philinux on 2012-12-19
> **BolinMDT said:**
> 

So they just needed to be paired.... now working.



Mine are solwise and there is no pairing involved they just work. However the one in the lounge which also has a wireless facility was set to 192.168.1.1 which was the same as the router. Bad default eh. I had to change that to get wireless to work.

---

### Post by BolinMDT on 2012-12-19
The quick start instructions with mine said that once plugged in and all 3 lights are on then they will work, if not then they need to be paired.

But it looked like all 3 lights were on both so I hadn't tried to pair them as they already appeared to be paired!

---

