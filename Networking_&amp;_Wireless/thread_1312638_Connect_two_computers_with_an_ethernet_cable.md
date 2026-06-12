---
title: "Connect two computers with an ethernet cable"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by nikhilbhardwaj on 2009-11-03
i just got a new laptop with windows7 on it
i've installed ubuntu 9.10 to dual boot with it

i have an old pc( 7 years old)
dual boot sabayon with windows XP

i was wondering if i could connect the two with an ethernet cable
both have ethernet slots

just plugging in the cable doesn't work
is it possible

i don't have any hub or switch
only one caT5 ethernet patch cable

---

### Post by arjuntank on 2009-11-03
yes you can. you need to configure the ip settings manually if dhcp isnt working, on both the pc. Are you trying to link sabayon and ubuntu together?

---

### Post by underquark on 2009-11-03
[Try here](http://www.technologysearchengine.org/search.htm?cx=006405419447330284711%3Arsfrabl83dk&cof=FORID%3A10&q=How+connect+two+PC%27s+using+Ethernet+cable&sa=Search&newwindow=1#1353).

Could you tell us why you want to connect them?  I.e is it just to transfer a few files or have you something more interesting in mind?

---

### Post by ArcaVex on 2009-11-03
Basically to connect two computers directly you need a cross-over ethernet cable.
To connect two computers together VIA a router/switch then you need a straight patch cable.

The reason the wires need to be crossed over is so the transmit/receive wires don't clash. (A router does this naturally)

Either re-wire if you have the tools and knowledge (which isn't hard)  or buy a crossover cable from somewhere

---

### Post by ratcheer on 2009-11-03
> **ArcaVex said:**
> What type of cable are you using?

Basically to connect two computers directly you need a cross-over ethernet cable.
To connect two computers together VIA a router/switch then you need a straight patch cable.

The reason the wires need to be crossed over is so the transmit/receive wires don't clash.

Absolutely correct. It is easier to use an ethernet switch, unless you are well-versed in making your own cables. Even if you find a pre-made crossover cable in a store, it is likely to cost 3 X as much as a normal cable.

Everyone needs an ethernet switch, anyway.

Tim

---

### Post by nikhilbhardwaj on 2009-11-04
> **ArcaVex said:**
> Basically to connect two computers directly you need a cross-over ethernet cable.
To connect two computers together VIA a router/switch then you need a straight patch cable.

The reason the wires need to be crossed over is so the transmit/receive wires don't clash. (A router does this naturally)

Either re-wire if you have the tools and knowledge (which isn't hard)  or buy a crossover cable from somewhere 

ok
so i've bought 5 metres of crossover cable


i plan to transfer files
and try a few two player games like fifa

---

### Post by arjuntank on 2009-11-04
> **nikhilbhardwaj said:**
> ok
so i've bought 5 metres of crossover cable


i plan to transfer files
and try a few two player games like fifa

just for the info here, cat5 that you already had, would have done the job.

---

### Post by nikhilbhardwaj on 2009-11-06
> **arjuntank said:**
> just for the info here, cat5 that you already had, would have done the job.

but people have said that i'd have required a hub or switch with that

i was able to transfer files using windows
using the network manager from the control panel

but haven't had any luck with the same in linux

---

### Post by arjuntank on 2009-11-06
> **nikhilbhardwaj said:**
> but people have said that i'd have required a hub or switch with that

i was able to transfer files using windows
using the network manager from the control panel

but haven't had any luck with the same in linux

a hub or a switch is truly required when you have many systems on the network. what i think is that, for your fifa sessions an enough length cat5 or crossover would work just fine. all, you need to do now is just connect any cable you have and see what happens. if it does'nt help, there could be many resons behind it so just follow this guide: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") and you are good to go :D

---

