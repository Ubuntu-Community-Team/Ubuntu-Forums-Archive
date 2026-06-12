---
title: "Retroactive Desktop Role question"
date: 2007-11-02
forum: Mythbuntu
---

### Post by dwarrenku on 2007-11-02
So I have MythTV 7.10 installed and am using it also as a ubuntu desktop.  My question is, is it possible for me to run MythTV as an application without harming the other things for the desktop.

I really just want to turn on my computer and run MythTV alone, so all processing power and ram can go to MythTV and nothing else.  But the catch is, if I need to use something else in ubuntu, it would be nice to restart and have it there.

Any ideas?

---

### Post by superm1 on 2007-11-02
> **dwarrenku said:**
> So I have MythTV 7.10 installed and am using it also as a ubuntu desktop.  My question is, is it possible for me to run MythTV as an application without harming the other things for the desktop.

I really just want to turn on my computer and run MythTV alone, so all processing power and ram can go to MythTV and nothing else.  But the catch is, if I need to use something else in ubuntu, it would be nice to restart and have it there.

Any ideas?
I don't see any problems here.  What's your issue?

---

### Post by Eil on 2007-11-03
No, it sounds like dwarrenku wants to do the same thing that I want to, which is use my Mythbuntu machine like a set-top box. The problem is that Mythbuntu (and to a greater extent, MythTV) both assume that I want to watch TV from a laptop or computer workstation. Neither really integrates very well with a home theatre set up, although MythTV can be coerced into it with some effort and probably Mythbuntu can as well, hence this thread.

In order to make my Mythbuntu box a true set-top box, these are the requirements that Mythbuntu doesn't address to my knowledge:

1) Boot quickly and directly into MythTV.
2) Turn off machine via remote

Regarding #1, although Mythbuntu does boot MythTV directly, it takes awhile plus loads XFCE. This isn't very efficient. A set-top box needs to boot and give you an interface ASAP. I know XFCE is fairly lightweight but it's still a full desktop environment and it still takes a while to load and it still shows up on my TV screen where I have no intention or capability of using it.

I've started MythTV in the past automatically through a funky inittab + mingetty + xinitrc + ratpoison gyration, but Ubuntu doesn't even have inittab or mingetty so I'm not sure if it can be done like this.

It would also be nice if some of the more non-essential services (like Apache and Samba) were somehow started a few seconds after MythTV.

Regarding #2, I'm shocked and amazed that MythTV has been around for years and years at the point and still doesn't have a button in the GUI that says "turn off this machine please". :)

---

### Post by dwarrenku on 2007-11-03
> **superm1 said:**
> I don't see any problems here.  What's your issue?

Basically it goes like this.  

Right now, in the Mythbuntu control center, under MythTV configuration, I have "Ubuntu Desktop" checked under Desktop role.  This was default because I installed gutsy before installing mythbuntu.

If I uncheck the "Ubuntu Desktop" box, and restart, I assume that my system will then be devoted to MythTV alone, and no other applications.

Will I be able to later check it again and resume my Ubuntu back to its nice little desktop like self, where I can run other applications other than MythTV?

That's my question.

---

### Post by superm1 on 2007-11-04
> **dwarrenku said:**
> Basically it goes like this.  

Right now, in the Mythbuntu control center, under MythTV configuration, I have "Ubuntu Desktop" checked under Desktop role.  This was default because I installed gutsy before installing mythbuntu.

If I uncheck the "Ubuntu Desktop" box, and restart, I assume that my system will then be devoted to MythTV alone, and no other applications.

Will I be able to later check it again and resume my Ubuntu back to its nice little desktop like self, where I can run other applications other than MythTV?

That's my question.
Well because of corner cases like you, unchecking that box will only remove the *-desktop metapackage.  So in the case of an ubuntu desktop role, it will remove the ubuntu-desktop meta package.  All of the other stuff (Gnome, OOo, evolution, pidgin, ekiga, etc will still remain)

---

### Post by superm1 on 2007-11-04
> **Eil said:**
> No, it sounds like dwarrenku wants to do the same thing that I want to, which is use my Mythbuntu machine like a set-top box. The problem is that Mythbuntu (and to a greater extent, MythTV) both assume that I want to watch TV from a laptop or computer workstation. Neither really integrates very well with a home theatre set up, although MythTV can be coerced into it with some effort and probably Mythbuntu can as well, hence this thread.

In order to make my Mythbuntu box a true set-top box, these are the requirements that Mythbuntu doesn't address to my knowledge:

1) Boot quickly and directly into MythTV.
2) Turn off machine via remote

Regarding #1, although Mythbuntu does boot MythTV directly, it takes awhile plus loads XFCE. This isn't very efficient. A set-top box needs to boot and give you an interface ASAP. I know XFCE is fairly lightweight but it's still a full desktop environment and it still takes a while to load and it still shows up on my TV screen where I have no intention or capability of using it.

I've started MythTV in the past automatically through a funky inittab + mingetty + xinitrc + ratpoison gyration, but Ubuntu doesn't even have inittab or mingetty so I'm not sure if it can be done like this.

It would also be nice if some of the more non-essential services (like Apache and Samba) were somehow started a few seconds after MythTV.

Regarding #2, I'm shocked and amazed that MythTV has been around for years and years at the point and still doesn't have a button in the GUI that says "turn off this machine please". :)
Heres the thing:
With a product like this you have to keep a balance between usability and streamlining.  This is the reason we chose Xfce in the first place.  Our old method was using an even more lightweight window manager, and restarting the session if myth got closed out, etc.  

To the point of delaying apache, you are treading in that exact same territory.  If you let apache start after the GUI, you will have a lagging GUI when you first arrive to it.  Try playing a hidef show while apache is just getting started, it's going to be very choppy and provide a suboptimal reaction as opposed to telling the user "your good to go *now*".

At another question, have you actually done any speed tests & memory tests comparing starting Xfce/gdm versus starting a lightweight window manager and relying on a method to automatically start X and log in?  I'd be interested to see the actual speed differences.  When we switched from openbox to Xfce, it was literally a 3-5 second difference from what we got with openbox on my machine.  The real bottleneck comes down to be mythfrontend starting rather than the environment it is running in.

Someone proposed this all earlier back in our cycle:[https://blueprints.launchpad.net/mythbuntu/+spec/start-fe-from-init](https://blueprints.launchpad.net/mythbuntu/+spec/start-fe-from-init)
last time around.  I'd be open to including such an option (but not by default), but first off upstart needs to really be used properly by all of the starting scripts (myth, lirc, networking, mysql, apache, etc).

For #2, you can already do this on FE only machines, but it isn't fully configured for you since it's a security risk in the method that it has to be implemented.  There is also a spec for this written though: [https://blueprints.edge.launchpad.net/mythbuntu/+spec/off-button](https://blueprints.edge.launchpad.net/mythbuntu/+spec/off-button)

Now after all that long rant out here, if you really want to see #1 or #2 happen, the best thing I would recommend is to come join us in #ubuntu-mythtv-dev, and help implement it.  We've already got a very full plate of other specifications to work on this cycle, so I suspect they will be low priority otherwise.

---

### Post by dwarrenku on 2007-11-04
Thanks superm1 you answered my question perfectly.

Being a TiVo user for 5 years and now switching to MythTV with just a spare (8 year old) tv tuner card makes me wonder why I didn't save the ~$14 per month and do this earlier.

Thanks

---

