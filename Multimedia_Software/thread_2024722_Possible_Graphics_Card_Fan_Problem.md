---
title: "Possible Graphics Card Fan Problem"
date: 2012-07-14
forum: Multimedia Software
---

### Post by Shadius on 2012-07-14
Hey everybody! :) 

I have an NVIDIA GeForce 6200 graphics card and I've noticed that the fan hasn't come on not even once since I've installed it. I'm wondering if there's a way to check if there's something wrong with the fan on the graphics card. Before I installed the graphics card, I was trying to see if the fan spun easily and it didn't really spin. It seemed liked trying to spin a rusty fan, if that makes any sense. I don't really know how to describe it, but the fan didn't spin very fluid. So with all that explained, is there a way to diagnose and solve this?

---

### Post by QIII on 2012-07-14
Uh...

There's something wrong with the fan.

:)

Time to RMA it.

---

### Post by Shadius on 2012-07-14
> **QIII said:**
> Uh...

There's something wrong with the fan.

:)

Time to RMA it.

Unfortunately, I can't RMA it because it was given to me by a friend. Any tips on repairing it?

---

### Post by QIII on 2012-07-14
If the fan does not spin freely, I'm afraid it's probably not a user-level repair.

If I were to hazard a guess, I'd say one of two things:

The internals of the motor are damaged.

The fan is striking or dragging on some component on the card and has likely done damage.

Do you have a door you need to prop open from time to time? :(

---

### Post by Shadius on 2012-07-14
> **QIII said:**
> If the fan does not spin freely, I'm afraid it's probably not a user-level repair.

If I were to hazard a guess, I'd say one of two things:

The internals of the motor are damaged.

The fan is striking or dragging on some component on the card and has likely done damage.

Do you have a door you need to prop open from time to time? :(

Okay, if repairing it myself isn't an option, what risks can I expect with the fan not working on the graphics card?

---

### Post by QIII on 2012-07-14
How well does the smoke alarm in your house work?  :)

Graphics chips get hot.  Very hot.  Hotter than your CPU by far.  Would you run your CPU without a fan?

If you were an expert modder, you might see if you can find a passive heat sink (a long shot) or another damaged card -- exactly the same model -- that doesn't work but the fan spins and swap the fans, but that would probably be a lot of work and might cost you more than a new card. Even then, depending on the specs of the card, a passive heat sink might not be near enough to cool it.

I guess what I am trying to say here is that this is a job for your wallet.

---

### Post by Shadius on 2012-07-14
> **QIII said:**
> How well does the smoke alarm in your house work?  :)

Graphics chips get hot.  Very hot.  Hotter than your CPU by far.  Would you run your CPU without a fan?

If you were an expert modder, you might see if you can find a passive heat sink (a long shot) or another damaged card -- exactly the same model -- that doesn't work but the fan spins and swap the fans, but that would probably be a lot of work and might cost you more than a new card. Even then, depending on the specs of the card, a passive heat sink might not be near enough to cool it.

I guess what I am trying to say here is that this is a job for your wallet.

Well, that's not very good news. :( Anyway, thanks.

---

### Post by QIII on 2012-07-14
Sorry.  I really hate it when the best advice I can give is something that will cost someone some cash.

---

### Post by Shadius on 2012-07-14
> **QIII said:**
> Sorry.  I really hate it when the best advice I can give is something that will cost someone some cash.

Don't beat yourself up. You did help me diagnose that there was a problem with the fan and I'm thankful for that. :) It just sucks since I was happy to find out that it can run Ubuntu 3D.

---

### Post by prshah on 2012-07-14
> **Shadius said:**
> Any tips on repairing it?

Actually, it's pretty easy to repair the fan on most heatsinks.

Typically, over time, dust builds up within the body and vanes.

Usually, a few good long blasts from a vaccum cleaner (BLOW, NOT SUCK) will get the fan spinning smoothly. In the worst case, you can peel off the centre sticker, and put in a couple of drops of lubricating oil (I use hair oil if I don't have lube oil on hand), and then manually spin the vanes a couple of times. You can also put in the oil in the gap between the vanes and the body (at the centre).

Ideally, the fan should be able to turn smoothly, just by blowing on it.

Be careful not to touch the vaccumm cleaner nozzle to the blades; the blade will break off INSTANTLY.

Worst comes to worst, you can replace the fan entirely; there will probably be a couple of screws holding it to the heatsink. 

If you want to go the whole hog, you can also consider removing old thermal paste and putting fresh thermal paste/grease, if the heatsink can be removed easily.

---

### Post by Shadius on 2012-07-14
> **prshah said:**
> Actually, it's pretty easy to repair the fan on most heatsinks.

Typically, over time, dust builds up within the body and vanes.

Usually, a few good long blasts from a vaccum cleaner (BLOW, NOT SUCK) will get the fan spinning smoothly. In the worst case, you can peel off the centre sticker, and put in a couple of drops of lubricating oil (I use hair oil if I don't have lube oil on hand), and then manually spin the vanes a couple of times. You can also put in the oil in the gap between the vanes and the body (at the centre).

Ideally, the fan should be able to turn smoothly, just by blowing on it.

Be careful not to touch the vaccumm cleaner nozzle to the blades; the blade will break off INSTANTLY.

Worst comes to worst, you can replace the fan entirely; there will probably be a couple of screws holding it to the heatsink. 

If you want to go the whole hog, you can also consider removing old thermal paste and putting fresh thermal paste/grease, if the heatsink can be removed easily.

I might give it a try. Thank you.

---

### Post by MartyBuntu on 2012-07-14
The 6200 is easily cooled with a third-party, passive heatsink should you decide to go that route.

---

### Post by Shadius on 2012-07-14
> **MartyBuntu said:**
> The 6200 is easily cooled with a third-party, passive heatsink should you decide to go that route.

Could you point me in the right direction of where to obtain one?

---

### Post by QIII on 2012-07-14
Frozencpu.com might be a place to start.  They sell cooling accessories for more than just CPUs.

Directron.com is a great place for bits and parts if you are a modder.  I checked and they do have generic graphics card fans, but you would have to measure the diameter and height of the fan very carefully.

No disrespect to the others who have offered solutions, but...

If you decide to put a very TINY amount of oil in it, you do that on the back side of the fan so you have some disassembly to do.  DO NOT remove the sticker.  Use a syringe containing the oil to poke a very tiny hole in it and put some tape with good adhesive over it when done. You may have to probe carefully to find the hole.  Use sewing machine oil or hair clipper oil.  Nothing else.  And only a very small amount.

Blowing air is really a good way to clean radiator fins, but doesn't usually improve matters for the fan itself.  Even if you flip the fan over, the gap between the rotor housing and the stator housing is so small that the pressure from a blowing vacuum is ineffective.  Compressed air from a can may get in there, but might result in not much more than churning up dust inside the cavity.  Besides that, any dust on the bearings is not likely to be removed because it will be trapped in whatever oil is already there.

Newegg.com has new, passively cooled 6200s for US$45.

Some companies like Zalman have small GPU HSFs that are relatively the same size as the stock HSF.  Zalman is expensive.  Other manufacturers have them in the US$10 range.

In my life experience and 35 years with computers, I have found that doing things "on the cheap" is often expensive in the end.

---

### Post by Shadius on 2012-07-14
> **QIII said:**
> Frozencpu.com might be a place to start.  They sell cooling accessories for more than just CPUs.

Directron.com is a great place for bits and parts if you are a modder.  I checked and they do have generic graphics card fans, but you would have to measure the diameter and height of the fan very carefully.

No disrespect to the others who have offered solutions, but...

If you decide to put a very TINY amount of oil in it, you do that on the back side of the fan so you have some disassembly to do.  DO NOT remove the sticker.  Use a syringe containing the oil to poke a very tiny hole in it and put some tape with good adhesive over it when done. You may have to probe carefully to find the hole.  Use sewing machine oil or hair clipper oil.  Nothing else.  And only a very small amount.

Blowing air is really a good way to clean radiator fins, but doesn't usually improve matters for the fan itself.  Even if you flip the fan over, the gap between the rotor housing and the stator housing is so small that the pressure from a blowing vacuum is ineffective.  Compressed air from a can may get in there, but might result in not much more than churning up dust inside the cavity.  Besides that, any dust on the bearings is not likely to be removed because it will be trapped in whatever oil is already there.

Newegg.com has new, passively cooled 6200s for US$45.

Some companies like Zalman have small GPU HSFs that are relatively the same size as the stock HSF.  Zalman is expensive.  Other manufacturers have them in the US$10 range.

In my life experience and 35 years with computers, I have found that doing things "on the cheap" is often expensive in the end.

Thanks for your suggestions QIII. I will check out those sites and weigh my options. I have absolutely no experience in repairing a graphics card's fan so that might be a little difficult for me. I'll try the easiest and simplest things first. Thank you.

---

### Post by pme 72 on 2012-07-14
Would an auxillary PCI slot fan work? There is one in my case directed at a passively cooled Sapphire HD4550. It is a Titan EC-TTC-SC-03. Reading reviews on Newegg's site some owners have used it when their on board fan stopped working. Replacing the onboard fan would be a better solution but the Titan might be an alternative.

---

### Post by trueno sprinter ae86 on 2012-11-04
u can find rubish pcs around get a cpu fan and tie it with string to the card making sure it will stay and not hit somethink and then u have control though mb if its a 3 or 4 pin fan also this will be overkill in cooling witch is a +++ i would also get some thermal paste and put it on gpu just for extra cooling could look at differnt heat sink
the more cooler it is the better and longer it will run and the more u can push it

---

