---
title: "Dual Ethernet Card, Network Feedthrough?"
date: 2008-04-15
forum: Mythbuntu
---

### Post by poke4christ on 2008-04-15
I'm running a network cable from my router to my new mythtv box.  I'm using a HDHomerun, so that has to connect to the network too.  My antenna is in the attic (needed for good reception) and we are using a prexisting coax feed to run from the attic to the living room TV.  Because of this, I need to have the HDHomerun in the living room as well as the Mythbox.  Therefore, I need two connections in the living room from the network.

I don't want to feed two cables, so I've been considering the best solution.  I've had a hard time finding cheap spliters online plus the shipping is annoying.  Radioshack has one, but it's 27 bucks (rip off).  One idea I've had is installing an additional network card on my mythbox and running it to the HDHomerun(they are cheap and can be included in my current newegg order).  Will this be transparent to the network?  Will it require some work to make it happen?  Can you think of a better solution?

Really, I just want the cheapest/easiest solution to this problem.  I'll make my own if the components are cheap enough and readily available.

---

### Post by murchball on 2008-04-15
I'm not sure what sort of a splitter you are talking about. It sounds like your best bet is to put an ethernet switch. Newegg has some for $10.

---

### Post by poke4christ on 2008-04-15
Well, I know a little bit about newtorking.  With ethernet, there is no inteligent switching neccessary on a single small network.  All traffic goes to all locations.  Therefore, you just need a split in the cable (the wires).  Since newegg has a cheap switch, I might just do that and get a couple 99 cent wires.

---

### Post by poke4christ on 2008-04-15
The other thing was I wanted something clean.  Having a whole additional switch back there that requires power is a little cumbersome and uneccesary.  However, I don't know if I can avoid it and keep a decent price.

---

### Post by Trollslayer on 2008-04-15
> **poke4christ said:**
> Well, I know a little bit about newtorking.  With ethernet, there is no inteligent switching neccessary on a single small network.  All traffic goes to all locations.  Therefore, you just need a split in the cable (the wires).  Since newegg has a cheap switch, I might just do that and get a couple 99 cent wires.

That was on 10BaseT from a long time ago, Ethernet runs on Cat5/6 which consists of four twisted pairs.
If you can get a cheap switch then that is the reccomended route. Second choice would be a second network card but that is slower.

---

### Post by volkswagner on 2008-04-15
> **poke4christ said:**
> I'm running a network cable from my router to my new mythtv box.  I'm using a HDHomerun, so that has to connect to the network too.  My antenna is in the attic (needed for good reception) and we are using a prexisting coax feed to run from the attic to the living room TV.  Because of this, I need to have the HDHomerun in the living room as well as the Mythbox.  Therefore, I need two connections in the living room from the network.

I don't want to feed two cables, so I've been considering the best solution.  I've had a hard time finding cheap spliters online plus the shipping is annoying.  Radioshack has one, but it's 27 bucks (rip off).  One idea I've had is installing an additional network card on my mythbox and running it to the HDHomerun(they are cheap and can be included in my current newegg order).  Will this be transparent to the network?  Will it require some work to make it happen?  Can you think of a better solution?

Really, I just want the cheapest/easiest solution to this problem.  I'll make my own if the components are cheap enough and readily available.

I think the cheapest and easiest would be add a switch.   No additional drivers, configuration, etc.

I think the most functional would be to do what you said you don't want to do.  I would pull two ethernet cables to the living room from you "network closet".  You have not said why you only want one.  Unless I misunderstood and the cable is actually existing.

I know you cheap and simple.  I think you should consider future proof and upgrades.  

Scenario 1: You currently have gigabit switch in you network closet, yet your mythbox only has 10/100.  Purchasing a gigabit card for your mythbox may be in the future.  This would allow you to use your current card for the HDhomerun.  You may need a crossover cable when connecting directly to an NIC.

Scenario 2:  Your Network is only 10/100 but you happen to have a gigabit NIC in your mythbox.  If you add a network switch in the living room, you may not want a cheapo for possible network upgrades to gigabit.

Scenario 3: Both the mythbox and network are all 10/100.  Now what?

In any of the above scenarios, pulling two cat5/6 cables will work well.

If you are terminating Cat5 and have some parts lying around you may consider this.  TX/RX takes two pair on the network.  If you want to make your own splitter try this.  Don't parallel the cables as a telephone splitter would.  You can use two pair for the HD homerun, and two pair for the mythbox.  I am sure to get flamed here.  Can you say degredation, crosstalk, yada yada.  But, hey if it works without loss in bandwidth, keep it.  No ugly switch.

Hey Cat5 is cheaper than coax.  Run two cables.  :)

---

### Post by volkswagner on 2008-04-15
Scratch my 2 pr. Idea.  That would be the aforementioned 10baseT

---

### Post by poke4christ on 2008-04-16
My network setup/situation is this.  I just moved in with a guy who had a basic wireless router.  He has no prexisting wiring through the house.  I ran a cable from his room to mine (just accros the hall) and set up my wireless router as a basic switch/hub on the network.  So now, I'm going to run a cable from my room to the living room for the mythbox.  As I said, both the Tuner and the Mythbox need to be in the living room.

Concerning the 10/100, I know about this, but I haven't looked into it that much.  Are all cheap wireless routers 10/100 for ethernet?  I would assume.  I know that most NIC nowadays are gigabit.  I'm not going to worry about it right now though because 10/100 is plenty fast for any purpose I might have now.  Also, it's cheap enough that it wouldn't really affect future upgrades, so that isn't a consideration.

If I bought a switch (which I probably will) why is power necessary?  Is it just for boosting the signal to 4 cables?  That's what I would assume considering that there is no inteligent routing going on.  I forget what the difference is between a switch and a hub.  As I said, I was kinda wanting it clean and easy.

As for running two cables vs one, that was more just for my roomate.  Though it will be mostly out of sight, I know that he doesn't really like running the cables, so I was just trying to minimize it.

[This]("http://www.radioshack.com/product/index.jsp?productId=2268439&cp=&sr=1&origkw=ethernet+splitter&kw=ethernet+splitter&parentPage=search") is actually exactly what I was wanting, but it's just not the cheapest option.  Why newegg doesn't have this I don't know.  Anyway, this is a lot of talk for such a simple problem and I'm probably just going to buy the switch and a couple 1 foot cables to go along with it.  Thanks for the help guys.

edit:  Conserning the switch, I believe that it's function is that it would isolate traffic among it's components from the rest of the network.  Is this correct?  If so, talk between my mythbox and HDHomerun wouldn't go to the rest of the network.  If I'm remembering right, that is how a switch is different from a hub.  This isn't a concern for me and my small network, but it's good to understand the function behind the technology.

---

### Post by poke4christ on 2008-04-16
Okay, I got what I'm gonna do figured out.  It's hard to splice your own since it's hard to find the right female adapters for cheap.  However, newegg has female to female couplers for 2 bucks.  Also, my work has the male adapters and crimpers I would need.  So, I'm just gonna use those and splice my own like volkswagner mentioned.  Thanks for the help guys.

---

### Post by Trollslayer on 2008-04-16
> **poke4christ said:**
> 
eedit:  Conserning the switch, I believe that it's function is that it would isolate traffic among it's components from the rest of the network.  Is this correct?  If so, talk between my mythbox and HDHomerun wouldn't go to the rest of the network.  If I'm remembering right, that is how a switch is different from a hub.  This isn't a concern for me and my small network, but it's good to understand the function behind the technology.

An ethernet switch learns where traffic has to go so when it knows only uses the required routes. In practice this means two PCs can communicate without blocking another two.
It doesn't block anything, just optimises and regenerates the packets so effects from multiple cables don't start building up.

---

### Post by volkswagner on 2008-04-16
> **poke4christ said:**
> Okay, I got what I'm gonna do figured out.  It's hard to splice your own since it's hard to find the right female adapters for cheap.  However, newegg has female to female couplers for 2 bucks.  Also, my work has the male adapters and crimpers I would need.  So, I'm just gonna use those and splice my own like volkswagner mentioned.  Thanks for the help guys.


Please be aware of my second post.  The speed may only be 10mbs vs. 100mbs, with only two pair.  I am not sure on this.  I just know older networks only used two pair.  I have in a pinch used one cat5 to terminate two voice and one lan.  The lan was only for internet so the speed was not an issue.  

You may want to try your own splitter.  If you have access to RJ45 jacks at work do the following.  Terminate at the router with standard male RJ45.  Use two wall jacks for the living room.  When terminating the first lan jack, leave the slack long enough to terminate the second jack.  This will give you two females, which you can terminate in an wiremold box if you want to keep it neat and secure.  You can try to keep the twists between jacks for "optimal performance".  May even try both and let us know what worked best.

---

### Post by poke4christ on 2008-04-16
Good to know.  I'll see what type of speed I get.  The only thing this should really affect is the streaming between my HDHomerun and my Mythbox.  I'm not sure what type of speed it needs, however I do know that the HDHomerun works fine over wifi so it shouldn't be too bad on speed requirements.  If my performance is fine for HD I'm sure it will be fine for anything else.  I should get my components in and it put together by monday night.  I'll update everyone then.

Zach

---

