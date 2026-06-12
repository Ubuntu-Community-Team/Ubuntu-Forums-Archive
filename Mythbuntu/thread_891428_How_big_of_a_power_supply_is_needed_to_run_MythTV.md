---
title: "How big of a power supply is needed to run MythTV?"
date: 2008-08-16
forum: Mythbuntu
---

### Post by bglaze1 on 2008-08-16
I am thinking of purchasing a barebones deal to get started with my MythTV system.  There is a wide difference when it comes to power supplies (on the systems I am looking at).  They range from something like this:
Ultra LS600 Lifetime Series 600W Power Supply - $70
to something like this:
Power Up Mid-T case w/450w PSU - $40

My question is how much power would I need to run my MythTV box if I intend to capture dual HD streams?  
Would both of these be sufficient for my needs?

---

### Post by ian dobson on 2008-08-16
Hi,

We need to know what hardware your going to be using (CPU, Ram, Graphic card, How many Harddisks) etc. before we can say anything about the PSU you'll need.

Regards
Ian Dobson

---

### Post by bglaze1 on 2008-08-16
One system I cam considering is this:
XFX GeForce 8200 Motherboard
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
XFX GeForce 8500 GT USC 512MB PCIe 
1TB Seagate Barracuda HD

or possibly this (cheaper version):
Asus M2N-MX SE Plus Motherboard 
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
onboard GeForce 6100
1TB Seagate Barracuda HD

How would that do?
Those are two options that I am considering (one is the higher end of my budget, the other a cheaper version).
The recommended power supply is obviously the 600W with the more expensive one, and the 450W with the cheaper one.  

Would a 450W power supply work with either of these systems? Or would I need more power for the more expensive system?  

If I wanted to be able to expand in the future, would I need to use the 600W or would the 450W power supply have room to grow still?

Thanks, let me know if you need more information.

---

### Post by mrand on 2008-08-16
> **bglaze1 said:**
> One system I cam considering is this:
XFX GeForce 8200 Motherboard
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
XFX GeForce 8500 GT USC 512MB PCIe 
1TB Seagate Barracuda HD

or possibly this (cheaper version):
Asus M2N-MX SE Plus Motherboard 
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
onboard GeForce 6100
1TB Seagate Barracuda HD

How would that do?
Those are two options that I am considering (one is the higher end of my budget, the other a cheaper version).
The recommended power supply is obviously the 600W with the more expensive one, and the 450W with the cheaper one.  

Would a 450W power supply work with either of these systems? Or would I need more power for the more expensive system?  

If I wanted to be able to expand in the future, would I need to use the 600W or would the 450W power supply have room to grow still?

Thanks, let me know if you need more information.Howdy,

It should be possible to find approximate power numbers for each of your components.  I haven't done that, but I believe it is a rare system that needs more than 300 Watts, much less 450 Watts.  Power supply efficiency isn't as good when you buy too much power supply.  If your system is going to be on a fair amount of time, strongly consider a 80+ efficiency one.  They aren't much more expensive, and frequently on sale.  

Modern hard drives are 10-12 Watts a piece. I don't know the power consumption of the GeForce 8500, but that might be worth checking - I don't think it is one of the high power consumption cards, but you should check.  I do know that you can't use it for hardware acceleration because XvMC isn't available on the newer GeForce cards, so either you need a fast CPU if you want to do high-def sooner than later, or you need a different card.

Hope that helps,

[INDENT]   Marc[/INDENT]

---

### Post by newlinux on 2008-08-16
I have 7 desktops (most run 24/7), a few with multiple tuners, multiple hard drives, PCIx video cards, 4 sticks of RAM, etc. - All my PSUs are 250-450W. Just a reference point. Every system is different,

---

### Post by brian mcgee on 2008-08-16
> **bglaze1 said:**
> One system I cam considering is this:
XFX GeForce 8200 Motherboard
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
XFX GeForce 8500 GT USC 512MB PCIe 
1TB Seagate Barracuda HD

or possibly this (cheaper version):
Asus M2N-MX SE Plus Motherboard 
AMD A64 X2 5000+ 2.60GHz Black Edition Retail 
Crucial 2048MB PC5400 DDR2 667MHz Memory
onboard GeForce 6100
1TB Seagate Barracuda HD

The 450W PSU will still leave you room to grow. I bet neither system you spec'd out would consume more than 200 watts peak (250 tops). Most people go crazy with PSU purchases. You should be more concerned with quality, features (e.g. Active PFC), noise, efficiency, etc...

For what you mentioned, I'd recommend something in the SeaSonic S12 II SS series. I've installed 3 SeaSonic S12 II SS-380 PSUs, and they should be plenty for you. If you're concerned, maybe pick up one of their 500W units. Honestly, you need less than you think.

For an HTPC, you want quiet and efficient, and those SeaSonics are both.

---

### Post by brian mcgee on 2008-08-24
Another thought. If you're interested in knowing the power consumption of a machine (or anything else with a plug), pick up a Kill A Watt. The power consumption will vary based on load, clock speed etc, so don't consider readings as the max possible consumption.

(I'm **not** affiliated with Kill A Watt, it's just a product I've used and liked)

Have you looked at the AMD 4850e? Better power efficiency, but similar price.

---

### Post by pnauta on 2008-08-25
It sort of amazes me that this question comes up.  I can appreciate that HD streams will eat up some serious CPU cycles, but the first spec I used to choose my components was: how LITTLE power will the system use? So I ended up choosing a system which will use 80W max, using amongst others a AMD BE 2350 CPU.  The point is not only to have a green system, but also cooling in a living room situation and when you have to cool 450W to 600W, believe me it will be one noisy system.  Also, my HTPC and TV are in a closed cabinet, so heat is the last thing I want to generate.

I was faced with choosing a PSU which would be efficient at low power consumption, and settled for a Sharkoon which at least should convert 80% of the input into output.

Hope this will make you consider what's important for you.  It's maybe OK to choose a big monster of a PSU, but make sure it is efficient, because it will in itself generate a lot of heat depending on it's specs.

---

