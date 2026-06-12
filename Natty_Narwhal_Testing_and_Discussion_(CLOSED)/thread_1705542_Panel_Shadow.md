---
title: "Panel Shadow?"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by BigCityCat on 2011-03-12
I know this is insignificant but the top panel looks like **** without a shadow under it. Are they going to add this? Probably no info on this because it isn't that important. Is there anyway to get that now?

Anyway I have just started testing unity on a separate partition. It's not bad with a few changes. Definitely like the re-sizable launcher, and setting the dash to netbook default with gconf editor.

---

### Post by MacUntu on 2011-03-12
According to Neil Patel it's planned, but a pretty low priority item.

---

### Post by BigCityCat on 2011-03-12
That is good to know. Thanks.

---

### Post by Finalfantasykid on 2011-03-12
I sure hope this gets done before the final release.  Even though it is a minor thing, it does significantly improve the look of the desktop IMO, especially when the panel is semi transparent.

---

### Post by montini on 2011-04-01
I really really hope so too. That is a big appearance bug in my oppinion.

---

### Post by Framli on 2011-04-01
It's here :)

---

### Post by montini on 2011-04-01
> **Framli said:**
> It's here :)

yup, sorry, just made update after the post - now it's fine :)

---

### Post by Quackers on 2011-04-01
Hmm, it doesn't look so good if the top panel is set as completely transparent! All I get now is a thin dark shadow a quarter of an inch from the top of my screen. Doesn't look too good, I can tell you :-)

See below

---

### Post by cariboo on 2011-04-01
I was going to suggest the same thing, the shadow doesn't work with a transparent panel.

---

### Post by mc4man on 2011-04-01
> **Quackers said:**
> Hmm, it doesn't look so good if the top panel is set as completely transparent! All I get now is a thin dark shadow a quarter of an inch from the top of my screen. Doesn't look too good, I can tell you :-)

See below
For whatever reason don't get the panel shadow here at all (2 day old, 2wk. old updated installs)
Will have to do a beta 1 fresh and see, do use a transparent panel (0), so that would be no good.

I'd file a bug on, maybe at some point it could be done as - if the panel is set to trans of 0 to disable the shadow

Atm it's a small addition to unity code so don't think it's user configurable, would be easy to remove completely in a rebuild if only way.

---

### Post by Quackers on 2011-04-01
> **mc4man said:**
> For whatever reason don't get the panel shadow here at all (2 day old, 2wk. old updated installs)
Will have to do a beta 1 fresh and see, do use a transparent panel (0), so that would be no good.

I'd file a bug on, maybe at some point it could be done as - if the panel is set to trans of 0 to disable the shadow

Atm it's a small addition to unity code so don't think it's user configurable, would be easy to remove completely in a rebuild if only way.
I only get the shadow in beta1, not in either alpha system. It sounds from earlier posts that this is intended behaviour.

---

### Post by mc4man on 2011-04-01
> **Quackers said:**
> I only get the shadow in beta1, not in either alpha system. It sounds from earlier posts that this is intended behaviour.

I'm making a beta 1 disk now - the change was in the new unity update today, 3.8.2-0ubuntu1,  so it will still be 'beta 1 + update'
Though as mentioned for some reason can't get it to happen in any pre-beta 1 updated installs, one is from 03/30

Edit: - if I set up a new user and login can see it clearly, one of those things that sometimes doesn't get 'done' in an existing user
Depending on background, tastes, ect. one may not like the shadow with a fully transparent panel

Now that I can see the shadow, looked for a report, didn't find one so filed semi-specific one
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682)

---

### Post by mc4man on 2011-04-08
possibly at some point shadow will be dropped if fully transparent or become a non source setting (bug got a little play.
If it really bothers and not inclined to rebuild unity (patch avail.), then the shadow depends on the compiz  .png plugin which one may or may not be using (used by the mt grab handles which is somewhat worthless unless hardware supports

Side note - if window title overlay is desired on scale then enable the scale addons and text plugins, a little 'off' but does work  - more suited to smaller screens

---

### Post by VinDSL on 2011-04-08
> **mc4man said:**
> If it really bothers and not inclined to rebuild unity (patch avail.), then the shadow depends on the compiz  .png plugin which one may or may not be using (used by the mt grab handles) which is somewhat worthless unless hardware supports [...]
Heh!  Thank you, thank you, thank you!  :D

I hated that drop shadow, much more than I loved MT Grab Handles.

It's a fair compromise...

---

