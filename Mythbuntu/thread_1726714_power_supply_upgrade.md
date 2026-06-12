---
title: "power supply upgrade"
date: 2011-04-11
forum: Mythbuntu
---

### Post by rudy1094 on 2011-04-11
It looks like to make this project work, I'm going to need to upgrade my power supply. How do I find out which power supplies will work on my PC? Will any power supply that fits in my case work? It's a dell Optiplex GX520 mini tower with a 230w power supply.

---

### Post by klc5555 on 2011-04-12
> **rudy1094 said:**
> It looks like to make this project work, I'm going to need to upgrade my power supply. How do I find out which power supplies will work on my PC? Will any power supply that fits in my case work? It's a dell Optiplex GX520 mini tower with a 230w power supply.

Looking at the specs here: [http://support.dell.com/support/edocs/systems/opgx520/en/ug/mtpwrspl.htm#wp1109155](http://support.dell.com/support/edocs/systems/opgx520/en/ug/mtpwrspl.htm#wp1109155)
it appears to be a fairly standard modern ATX power supply, albeit a skimpy one. 24 pin motherboard connector, 4 pin CPU supply, and just a few of the usual peripheral connectors, SATA, molex, etc. 

In theory, just about any ATX power supply of the desired wattage (500, 600, etc.) ought to fit, and, depending on the location of the fans on the new supply, may do a better job of venting the case than the current one. One concern in moving up to much higher wattage might end up being system heat, since from the online docs it doesn't appear that your Dell case is vented all that well.

Now while I suspect that just about any modern ATX power supply should be a drop-in replacement, be aware that Dell has in the past demonstrated a tendency to equip their machines with parts which are almost, but not quite, of standard dimensions. Measure your present power supply and compare these dimensions with the ones included in the online product description of your potential new power supply, so you'll know whether your proposed new supply will fit the case easily. Under normal circumstances, changing a power supply is maybe a half-hour to 45-minute procedure.

Good luck.

---

### Post by dibuntux on 2011-04-12
Why the upgrade? Too noisy? Get one with a 12 cm fan with auto regulation. I have Corsair and is almost completely silent. Be aware that other fans in tha case can be more noisy than the one in the PSU.
Besides dimensions, take a look at what you need for power:

[http://www.thermaltake.outervision.com/](http://www.thermaltake.outervision.com/)

---

### Post by xinix on 2011-04-15
I'm quite happy with my recent upgrade to a Seasonic x650.  It has a quiet fan and it only kicks in when it's temps go up.

---

### Post by deconstrained on 2011-04-15
Whatever you do, use this calculator to estimate wattage, not Newegg's. 
[http://extreme.outervision.com/psucalculatorlite.jsp](http://extreme.outervision.com/psucalculatorlite.jsp)
The one at Newegg inflates and stretches the necessary wattages way beyond ballpark figures for ordinary components so that you'll pay more money for a higher-end power supply.

Also, on a personal note, I recently shelled out a buttload of cash for a really nice fanless SeaSonic power supply, and...my computer now makes half as much noise and consumes 20% less power.

---

### Post by rudy1094 on 2011-04-15
Thanks for the input. I'm looking for a new power supply because I need a new video card that has VDPAU capabilities. The video card I'm looking at suggests a power supply of at least 300w. I'm still shopping around for the power supply I will buy.

---

### Post by rudy1094 on 2011-04-19
I bought a Thermaltake TR2 430W power supply.
[http://thermaltakeusa.com/Product.aspx?C=1247&ID=1541](http://thermaltakeusa.com/Product.aspx?C=1247&ID=1541)

I installed it in my Dell Optiplex gx520 and it wouldn't power on. The power button blinked an orange light, but it wouldn't power on. I installed the power supply in my Dell Dimension 2350 and it worked fine. I'm not sure why it didn't work in the Optiplex, but it worked in the Dimension. Any thoughts/suggestions?

---

### Post by klc5555 on 2011-04-20
> **rudy1094 said:**
> I bought a Thermaltake TR2 430W power supply.
[http://thermaltakeusa.com/Product.aspx?C=1247&ID=1541](http://thermaltakeusa.com/Product.aspx?C=1247&ID=1541)

I installed it in my Dell Optiplex gx520 and it wouldn't power on. The power button blinked an orange light, but it wouldn't power on. I installed the power supply in my Dell Dimension 2350 and it worked fine. I'm not sure why it didn't work in the Optiplex, but it worked in the Dimension. Any thoughts/suggestions?

Last time I had that happen to the extent that not even the fans would spin I had neglected to plug in the 4-pin CPU auxiliary supply next to the CPU. So make sure the 24-pin motherboard connector is seated properly so it "clicks", and check the 4-pin CPU auxiliary. 

Admittedly, some CPUs don't require the 4-pin, even when the motherboard has a socket for it, and some of these CPUs (I have one) fail to boot properly when the unneeded 4-pin supply is actually provided, but I doubt this latter case would be the situation in a Dell-designed machine as opposed to a box that a hobbyist would tend to throw together out of whatever parts are at hand.

---

### Post by LowSky on 2011-04-21
The best brands out there. Corsair, Seasonic, Antec, Silverstone. and a few other but im used to working with these.

best advice is dont skimp on the power supply. this is your pc's lifeblood take goood care of it.

newegg is a great source for reviews. but be wary of the negatives. supposedly people with negative experiences will respond about 4 to 1 in positive experience. best rule of thumb is if the negative reviews are over 20% then look elsewhere.

---

