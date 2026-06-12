---
title: "Improvements for Sept 15 Install Fest"
date: 2007-07-22
forum: Maryland Team - US
---

### Post by aboutblank on 2007-07-22
Well we had a grand time at our Install Fest at Loyola college, but we can definitely do better. Let's list some things we can improve on.


*Arranging the room. Set up stations where a person can just plop down and plug in. We should have tables already setup with power and ethernet. (We need more ethernet cables :-( - We should probably buy a box of 50 in bulk)

*Networking - We need to do NAT and where we can, do wired. 5-port switches at each table with long cables running back to one large switch connect to LAN should be sufficient. 

*People - 

[INDENT]1 Greeter/assigner - Stands at the door and assigns incoming people to *technicians*. This position is best suited for someone who doesn't have the technical knowledge to install with confidence, but wants to help.

Technicians - I think we should pair 1 Technician with 2 or 3 installees. These technicians will stay with their assigned people the whole time. They should wait for a *bouncer* to come around if they run into trouble.

Bouncer - These people have advanced technical know-how and will walk around to each technician and assist with any problems they are having.[/INDENT]

*CDs - Heh. As everyone that was there knows, we had a few problems with media. We need more alternate CDs. People need to be refreshed on the [installation requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"). CDs should be burnt in advance and tested with the "check cd for defects" option. It really slowed us down and will be unacceptable at the next one.

*Donation Box - Ohhh what about if we buy food for people? We could have the greeter tell people where food is allowed, and ask them to make a donation in a donation box set up by the food.

Overall I think it went pretty well. I'm looking forward to seeing the pictures.

---

### Post by rhoderickj on 2007-07-22
> **aboutblank said:**
> Arranging the room. Set up stations where a person can just plop down and plug in. We should have tables already setup with power and ethernet. (We need more ethernet cables :-( - We should probably buy a box of 50 in bulk)

Agreed. I also think it'd be nice to work out the station setup ahead of time so we know exactly how much hardware we're going to need. I think Todd said he has a big roll of CAT5, so maybe he wouldn't mind cutting and crimping a few 5ft patch cables.

> Networking - We need to do NAT and where we can, do wired. 5-port switches at each table with long cables running back to one large switch connect to LAN should be sufficient.

That sounds good. I'll pick up one or two switches before the next install fest. Will we need any more KVMs too?

> CDs - Heh. As everyone that was there knows, we had a few problems with media. We need more alternate CDs. People need to be refreshed on the [installation requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"). CDs should be burnt in advance and tested with the "check cd for defects" option. It really slowed us down and will be unacceptable at the next one.

Yes! I also think it'd be nice to label each CD with a batch number. For example, if 20 cds were burned from the same iso on the same burner, they'd be given a batch number and it'd be written on the CD. So if we have any more problems we know which batch is the culprit. 

> Donation Box - Ohhh what about if we buy food for people? We could have the greeter tell people where food is allowed, and ask them to make a donation in a donation box set up by the food.

Good idea. I think it'd be a bit naive to just leave an open pool of cash sitting out on a table though. We need to have a locking box that isn't going to walk off.

> Overall I think it went pretty well. I'm looking forward to seeing the pictures.

I'm ready to upload these as soon as Chuck gets me FTP access to the ubuntu-maryland server.

---

### Post by parma1 on 2007-07-23
For those of us who couldn't make it on Saturday, can we get a 35-words-or-less synopsis of what happened? How many showed up, how long was everyone there, how many successful (and unsuccessful installs), etc.

---

### Post by aboutblank on 2007-07-23
Parma1: Sure why not. I can't guarentee 35 words or less.

We had about 15 technicians and maybe 20 people show up? Most were there for 2 hours. We had quite a few successful installations. We failed on a few (grub error 18, bad hardware). Overall, we learned quite a few things, including how badly we need alternate CDs.

---

### Post by parma1 on 2007-07-23
Wow. 20 people -- I'm shocked (and pleased). Apparently our hand-wringing on Thursday nite was overly conservative.

---

### Post by rhoderickj on 2007-07-23
> **parma1 said:**
> Wow. 20 people -- I'm shocked (and pleased). Apparently our hand-wringing on Thursday nite was overly conservative.

Yeah, I think everyone was quite pleased with the turnout, especially considering that we did very little advertising. I think we also learned a bit about the demographics of those who are CURRENTLY attending install fests, as most of the attendees were already Linux-aware but had troublesome hardware and wanted assistance. I think that after the presentations team gets started, we'll also be able to bring a slightly different crowd.

As soon as Chuck gets me FTP access to the server I'll upload some photos. They'll help to give you an idea of how things went. 

-- Josh

---

### Post by phr0ze on 2007-07-23
A lot of time was waisted too. Many machines remained idle for a while because the tech was busy wrestling a difficult box. Here is what I suggest.

1. I will bring about 10-20 alternate disks burned and checked.
2. I will bring about 10-20 live CDs for installers (I don't know what happened but these seemed to get lost)
3. Definately have a host who can greet people, give them an official material, sticker and CD on their way out, manage the food.
4. If we are going to do some sort of Apt proxy, have it ready so time can be spent setting up other stuff.
5. KVMs, We need more 4 port KVMs.
6. Laptops should go to a separate station which just has power and lan.
7. Hardware Labels - definately label everything we bring. If possible, label the guest's equipment too.
8. Prioritize the install process. The tech should flip the KVM and make sure all machines are doing something. If there are 2 difficult machines in a bunch, the tech should work with the machine that has been there the longest.
9. If we have enough help, have someone who assists with plugging in new machines, removing machines, working general network issues, finding supplies, and most importantly does research on the internet for difficult issues.

Per station we need 4-5 port switch, 4 port KVM, 1 Keyboard, 1 Mouse, 1 Monitor with cables, 5 network cables, 4 PC Power Cables, 1 DVI-VGA, 8 outlets. 

Thoughts?

John

---

### Post by rhoderickj on 2007-07-23
All excellent suggestions, and I second them. 

> 5. KVMs, We need more 4 port KVMs.

Why 4-port? Wouldn't that mean each technician is working on 4 systems at once? That seems like a heavy load to me, especially if just one of the systems is particularly troublesome. 

> 7. Hardware Labels - definately label everything we bring. If possible, label the guest's equipment too.

I was just thinking about this today actually. I think I have a whole bunch of unused thin mailing-style labels so, if you like, I can print a bunch of labels for us. For cables, we can just wrap the label around so that it sticks to itself. As for guests' equipment, we might be better off using small sticky labels. Hopefully though, if we're more organized next time, we'll be able to tell quite easily whose equipment we're working with. 

> Per station we need 4-5 port switch, 4 port KVM, 1 Keyboard, 1 Mouse, 1 Monitor with cables, 5 network cables, 4 PC Power Cables, 1 DVI-VGA, 8 outlets. 

So you're planning for each station to have 4 PCs? I was thinking that two would be a handful. And you're going to need two ports on the switch just to daisy chain them, so if you have a 4  or 5 port switch that only leaves 2 or 3 ports respectively. Personally, I vote for each station being setup for two PCs: 1 4-port switch, 1 2-port KVM, 1 keyboard, 1 mouse, 1 monitor, 2 network cables, 2 power cables, etc.

The main reason we ran out of support last time was because of the CDs. I think that if we don't have CD problems next time, we'll be able to move PCs much more quickly and 2 PCs per station would be sufficient.

---

### Post by phr0ze on 2007-07-24
> **rhoderickj said:**
> Why 4-port? Wouldn't that mean each technician is working on 4 systems at once? That seems like a heavy load to me, especially if just one of the systems is particularly troublesome. 
Yes and no, the problem last time with the 4 port KVM was that there were too many people switching in and out of stations (due to lack of planning) that no one was checking other machines. Near the end though we started getting it down. Most of the machines were so slow at the install that a 2 port KVM station could become bogged down by slow processes. Obviously we have some 2 port KVMs and we will end up with some 2 port stations, but maybe the greeter can determine if the guest is bringing a difficult machine and direct it to a 2 port station. 
> 
I was just thinking about this today actually. I think I have a whole bunch of unused thin mailing-style labels so, if you like, I can print a bunch of labels for us. For cables, we can just wrap the label around so that it sticks to itself. As for guests' equipment, we might be better off using small sticky labels. Hopefully though, if we're more organized next time, we'll be able to tell quite easily whose equipment we're working with. 

I had labels with me and I did exactly that with my stuff. It helped for most of it. Some stuff near the end was hooked up in a rush and I didn't get time to label it.

> 
So you're planning for each station to have 4 PCs? I was thinking that two would be a handful. And you're going to need two ports on the switch just to daisy chain them, so if you have a 4  or 5 port switch that only leaves 2 or 3 ports respectively. Personally, I vote for each station being setup for two PCs: 1 4-port switch, 1 2-port KVM, 1 keyboard, 1 mouse, 1 monitor, 2 network cables, 2 power cables, etc.

This requires a lot more monitors which is was a problem for us. 3 of our monitors were from the school. and one of them was from a guest. We had no idea that any of those would be there, and if they weren't we would have been in serious trouble.  We were also low on keyboards and mice too, but much better than we were on monitors.  I also don't recommend daisy chaining switches. I recommend a central switch which other switches come off of. Also I specifically stated a 4-5 port switch because I was actually thinking most of my switches are part of a router with a WAN port, so in that case 4 ports is enough. If you don't have a WAN port then you need a 5 port switch.


> 
The main reason we ran out of support last time was because of the CDs. I think that if we don't have CD problems next time, we'll be able to move PCs much more quickly and 2 PCs per station would be sufficient.

---

### Post by rhoderickj on 2007-07-24
> **phr0ze said:**
> Yes and no, the problem last time with the 4 port KVM was that there were too many people switching in and out of stations (due to lack of planning) that no one was checking other machines. Near the end though we started getting it down. Most of the machines were so slow at the install that a 2 port KVM station could become bogged down by slow processes. Obviously we have some 2 port KVMs and we will end up with some 2 port stations, but maybe the greeter can determine if the guest is bringing a difficult machine and direct it to a 2 port station.

Good point. 

> This requires a lot more monitors which is was a problem for us. 3 of our monitors were from the school. and one of them was from a guest. We had no idea that any of those would be there, and if they weren't we would have been in serious trouble.  We were also low on keyboards and mice too, but much better than we were on monitors.  I also don't recommend daisy chaining switches. I recommend a central switch which other switches come off of. Also I specifically stated a 4-5 port switch because I was actually thinking most of my switches are part of a router with a WAN port, so in that case 4 ports is enough. If you don't have a WAN port then you need a 5 port switch.

Okay, that makes sense. Maybe we can find some used monitors somewhere. I'll have to check out the local Goodwill. They usually have a few lying around. I'm also going to pick up at least one switch and a KVM before the next install fest and I hope others will do the same.

---

### Post by aboutblank on 2007-07-24
I just got twenty 20' ethernet cables. I'll have those in a large tub at the next install fest. Techs can bring in 5 or so, write down what they brought, and dump it in the community pool of ethernet cables. We'll set up all the stations, and if we need more cables, we can just grab one from the tub. I might be able to handle all the network cables myself, we'll have to see how many I get. In any case, don't buy a bulk pack.

---

### Post by phr0ze on 2007-07-25
> **aboutblank said:**
> I just got twenty 20' ethernet cables. I'll have those in a large tub at the next install fest. Techs can bring in 5 or so, write down what they brought, and dump it in the community pool of ethernet cables. We'll set up all the stations, and if we need more cables, we can just grab one from the tub. I might be able to handle all the network cables myself, we'll have to see how many I get. In any case, don't buy a bulk pack.

I already have a bulk pack. My friend just didn't return it to me on time. I will bring it just in case.

---

### Post by aboutblank on 2007-07-26
> **phr0ze said:**
> I already have a bulk pack. My friend just didn't return it to me on time. I will bring it just in case.

D'oh!

Okay, well that works just fine. One thing I'd like to briefly mention is that I would *love* to have another install fest at Loyola after the SFD one. The power situation is great as well as the room setup. 

But as far as the SFD one, a few of us are going to need to meet there on a weekend to check out the location and make sure we'll be set. Do we have enough space? Power? Tables? Chairs? Can someone give me the address please?

---

### Post by rhoderickj on 2007-07-26
> **aboutblank said:**
> Okay, well that works just fine. One thing I'd like to briefly mention is that I would *love* to have another install fest at Loyola after the SFD one. The power situation is great as well as the room setup. 

I totally agree with you on this. I think the Loyola campus is awesome. The setup was excellent and the room itself was roomy and had a great view! :)

> But as far as the SFD one, a few of us are going to need to meet there on a weekend to check out the location and make sure we'll be set. Do we have enough space? Power? Tables? Chairs? Can someone give me the address please?

It's at the Howard County Libary's East Columbia branch. I put the address and stuff on the wiki. Just follow the link for the event page. By the way, I think all of the hardware listings from now on should go on the generic install fest page, as the hardware listing applies to all install fests. Unless anyone has any objections to this, I'll just migrate your list from the last one to the install fest page, so we can add to it as we go along.

---

### Post by ChuckFrain on 2007-07-29
In case anyone is insterested, CompUSA has [NetGear 5 port switches]("http://tinyurl.com/33tofs") on sale for $9.99 after a $25 eRebate thru 8/4. 

I've had no problems with their erebate system in the past.

---

