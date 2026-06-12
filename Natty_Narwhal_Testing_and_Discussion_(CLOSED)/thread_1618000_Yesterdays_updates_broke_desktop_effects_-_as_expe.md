---
title: "Yesterdays updates broke desktop effects - as expected"
date: 2010-11-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-10
I ran Update Manager last night and there were several updates available (mostly for Compiz and Gnome) and was offered a Partial Upgrade. So I went to Synaptic and had a mooch around. It seemed to me that the only major problem would be the removal of Compiz Fusion extras plugin so I went ahead and installed the updates. A few failed and I installed them again afterwards. This left one which I installed on its own. 
I even dared to reboot :-). Everything came back and the only thing missing is desktop effects, which I can not now enable. No biggy.
I viewed Framli's post and looked at the linked ppa but as I couldn't see a replacement for the Fusion extras package I'm not sure whether to get the packages or not :confused:.
I'll have a think :-)

---

### Post by Quackers on 2010-11-10
An update
I've just run the most recent updates and there is no change. Desktop effects can not be enabled. I have checked that the Nvidia driver is still installed and it is ok.
One other thing I have noticed is that System > Admin > Additional Drivers does not run any more. It does not even appear to start.

---

### Post by caryb on 2010-11-10
Not sure if the same problem for me, I lost my desktop & effects in Kubuntu. I can alt+f2 to get my apps to run. I have installed xfce window manager to get by.

Cary

---

### Post by dino99 on 2010-11-10
all the previous compiz installed packages and their dependencies need to be removed/purged, then you can install compiz

---

### Post by Quackers on 2010-11-10
> **dino99 said:**
> all the previous compiz installed packages and their dependencies need to be removed/purged, then you can install compiz

Aha! Thank you dino99, I sort of suspected that but, wasn't sure. I'll give it a try.

BTW, it wasn't a complaint! It was just an observation :-)

---

### Post by Quackers on 2010-11-10
Oh dear
I added the ppa from the link in Framli's post and now Software Sources won't start either :-).
In Synaptic if I click on repositories it says that the repositories have changed and I should click on reload. After clicking on reload it says the same thing again :-) I think something is broken :-)
Firefox keeps crashing. Can't enable desktop effects. Update manager stopped working :-) It's a bit of a mess at the moment. It's a laugh :-)

Cairo Dock is still working though :-)

---

### Post by dino99 on 2010-11-10
might work now as gtk2 have been reverted back

---

### Post by Quackers on 2010-11-10
> **dino99 said:**
> might work now as gtk2 have been reverted back

I did a sudo apt-get update which reported duplicate sources, but I couldn't see any.
Then I did an apt-get upgrade and the gtk2 update appeared.
so UM is back and synaptic doesn't give duplicate source errors now. I couldn't see any anyway :confused:

Thanks dino99.

Now I'll see if things are still crashing and try that compiz ppa again :-) It's all go!

---

### Post by Starks on 2010-11-10
The water effect and desktop cube works. Wobbly windows doesn't.

---

### Post by Quackers on 2010-11-10
I'm still getting "unable to enable desktop effects". It's looking for an available driver but I already have the Nvidia 260 driver installed. Odd.

---

### Post by lucazade on 2010-11-10
> **Quackers said:**
> I'm still getting "unable to enable desktop effects". It's looking for an available driver but I already have the Nvidia 260 driver installed. Odd.

Have you tried "compiz --replace" from terminal?
It works for me on Nvidia 250gts.

---

### Post by Starks on 2010-11-10
Gotta do compiz --replace to enable.

---

### Post by Benjamin_Lebsanft on 2010-11-10
The top and bottom area (1px) are insensitive to clicks here, maybe compiz related?

---

### Post by Quackers on 2010-11-10
I tried compiz --replace before but it had no effect. However I've since done a couple of mods and I tried it again.
I now have wobbly windows etc but if I go to System > Preferences > Appearance I can't enable desktop effects!
Thanks

---

### Post by Quackers on 2010-11-10
I rebooted to let things settle a bit - and they did :-)
Now I don't have wobbly windows any more, lol. And I still can't enable desktop effects :-) It's all good fun

---

### Post by jfernyhough on 2010-11-10
Has anyone else found that after an ALT-TAB existing window content doesn't update? I can still click on title bars to move and close, but window content is not updated. I've found I can fix this by disabling/enabling "Copy to texture" in CCSM, but it happens no matter if this is enabled or not which makes me think it's nothing to do with this setting at all!

If I open a new window this works as normal - it's all a bit weird!

--edit
Typical, after posting I disable Mipmap in Static Application Switcher. Fixed. Probably an issue with fglrx.

---

### Post by Arrowstar on 2010-11-10
So today I grabbed the Natty compiz package(s) on my 11.04 testing install.  I still note that I get a message in the Visual Effects tab in "Appearance" that states that "Mutter is running, can't enable visual effects" or some such thing.  And (I believe as expected) if I attempt to "compiz --replace" with Unity running, things go downhill quickly.

Is this all normal behavior at the moment?

---

### Post by cariboo on 2010-11-10
> **Arrowstar said:**
> So today I grabbed the Natty compiz package(s) on my 11.04 testing install.  I still note that I get a message in the Visual Effects tab in "Appearance" that states that "Mutter is running, can't enable visual effects" or some such thing.  And (I believe as expected) if I attempt to "compiz --replace" with Unity running, things go downhill quickly.

Is this all normal behavior at the moment?

You're getting ahead of things, Unity hasn't been rebuilt to take advantage of compiz yet.

I'd give it a couple of weeks before we see the newer version of Unity

Why is everyone in such a hurry? Natty won't be released until April.

---

### Post by Quackers on 2010-11-10
Such a hurry for what? You lost me.

---

### Post by cariboo on 2010-11-11
Check out the Unity Desktop and Wayland threads in the Cafe, there are quite a few people that seem to think that because announcements have been made, the software was ready to use.

---

### Post by Arrowstar on 2010-11-11
Oh I'm fully aware it's not ready to use.  I just like hanging out on the bleeding edge (or at least being prepared for said bleeding edge when it arrives!).  It's rather exciting. :D

---

### Post by ranch hand on 2010-11-11
> **cariboo907 said:**
> Check out the Unity Desktop and Wayland threads in the Cafe, there are quite a few people that seem to think that because announcements have been made, the software was ready to use.
Good Gods man don't abuse yourself by going over there.  That is just more abuse than anyone in their right mind can take.

Those folks are insane.

Stay here where people are just nuts.

---

### Post by woodbj on 2010-11-11
Is it just me or did the new updates make the theme/windows look a lot nicer

---

### Post by Quackers on 2010-11-11
I like it :-) :-)

---

### Post by coffeecat on 2010-11-11
Yes, I've had some - um - fun with updates over the last couple of days. Last night I was still getting compiz with this Radeon HD4350/open-source driver setup but compiz was seriously affecting the usability of the desktop. This morning the Visual Effects tab in Appearance was telling me that compiz was off, but the windows were still wobbling. :? Managed to switch it off properly eventually.

Somewhat OT, but I see that we're going through one of our periodic python [s]breakages[/s] transitions. I let this morning's updates remove a few bells and whistles I like to have all of which depend on python-gnome2, which depends on python-somethingorother which conflicts with.... at which point I lost the plot.

> **ranch hand said:**
> Those folks are insane.

Stay here where people are just nuts.

:lol:

---

### Post by Quackers on 2010-11-11
Yes, for a couple of hours yesterday my Natty installation was almost unusable. I returned to maverick for a while. When I returned there were more updates available (although UM would run, it wouldn't show the last screen where updates were available, it just went zombie. It's still doing it) but the updates made it more usable again. 
Desktop effects can sometimes be enabled and at other times can't, and yet wobbly windows still work :-)
Obviously things will get worse before they get better and this is expected. It's all a learning curve for me. If it crashes and burns it's not the end of the world :-)
I realise that testing is really for more experienced users than me, but I'll see what happens and hopefully learn a bit.

---

### Post by hugmenot on 2010-11-11
> **Benjamin_Lebsanft said:**
> The top and bottom area (1px) are insensitive to clicks here, maybe compiz related?

This is the relevant bug: [http://pad.lv/638974](http://pad.lv/638974)

The workaround of disabling edge switching in the Wall plugin doesn’t work for me. Confirm/disconfirm?

---

### Post by Baul on 2010-11-12
Yelp - it has all gone abit hazelnut whirl like!!!

---

