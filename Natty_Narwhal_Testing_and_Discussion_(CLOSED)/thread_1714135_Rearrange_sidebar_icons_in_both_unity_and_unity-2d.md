---
title: "Rearrange sidebar icons in both unity and unity-2d?"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-25
Sorry if I used the wrong search words but I didn't find an answer to this. As I've been testing unity and unity-2d a bit more I know I can remove and add icons/launchers but I don't know how to rearrange the existing ones.

I do know that I can actually remove and add in a certain order to achieve that goal but is there an easier way? I'm thinking maybe there's a way in regular unity using the compiz-config tool but I'm not seeing it, and I have no idea where "settings" are stored for unity-2d :confused:

Thanks in advance.

---

### Post by lucazade on 2011-03-25
> **kansasnoob said:**
> Sorry if I used the wrong search words but I didn't find an answer to this. As I've been testing unity and unity-2d a bit more I know I can remove and add icons/launchers but I don't know how to rearrange the existing ones.

I do know that I can actually remove and add in a certain order to achieve that goal but is there an easier way? I'm thinking maybe there's a way in regular unity using the compiz-config tool but I'm not seeing it, and I have no idea where "settings" are stored for unity-2d :confused:

Thanks in advance.

In unity-2d keep a launcher clicked for a couple of seconds then move it up and down, in unity should be similar because they changed the behavior some releases ago.

---

### Post by webme on 2011-03-25
> **kansasnoob said:**
> Sorry if I used the wrong search words but I didn't find an answer to this. As I've been testing unity and unity-2d a bit more I know I can remove and add icons/launchers but I don't know how to rearrange the existing ones.

I do know that I can actually remove and add in a certain order to achieve that goal but is there an easier way? I'm thinking maybe there's a way in regular unity using the compiz-config tool but I'm not seeing it, and I have no idea where "settings" are stored for unity-2d :confused:

Thanks in advance.

There is an option in dconf-editor to put your favorite icons (by typing the name) and a button "Set to default" to set few favorite icons as default, but, in compiz config I don't think exist what you want (at least ATM).

---

### Post by cariboo on 2011-03-25
I'm not fully up-to-date, as I haven't rebooted since the last update, this is for Unity 3D, click and hold the icon you want to move, move to the desktop, then drag it to where you want in the panel.

---

### Post by mc4man on 2011-03-25
In 3d now you can just left click (hold) and move up or down directly in the launcher (or pull out and place, either way.

Never used 2d - as of a month or so ago (date of page), it seemed you could only do so in gconf-editor - screenshot here (use a up or down in the launcher's 'edit' key
[http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html)

Edit: if 2d has/uses dconf-editor as shown above then once you get the key in edit mode you could use cut and paste to rearrange (or retype

---

### Post by VMC on 2011-03-25
> **mc4man said:**
> In 3d now you can just left click (hold) and move up or down directly in the launcher (or pull out and place, either way.

Never used 2d - as of a month or so ago (date of page), it seemed you could only do so in gconf-editor - screenshot here (use a up or down in the launcher's 'edit' key
[http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html)

Edit: if 2d has/uses dconf-editor as shown above then once you get the key in edit mode you could use cut and paste to rearrange (or retype
Yes, I found that out by accident. At first I needed to drag it outside the holder and then up or down and back in again. The latest addition I can just move it up or down and their is a white line telling me where I'm going.

---

### Post by kansasnoob on 2011-03-25
Cool, I'm gonna' give this a closer look tomorrow. Chances are I was just being impatient.

There is absolutely the insane expectation that all clicks should work as they have since Gutsy ;)

---

### Post by cariboo on 2011-03-25
This isn't pointed at anyone in particular, but I'm amazed how many people expect Unity to be finished after only a little over 5 months of development.

Unity is still getting better everyday, and I'm personally amazed how far it's come in that time. I can't wait to see what's in store for us after UDS-O in May.

---

### Post by rbrick49 on 2011-03-25
> **cariboo907 said:**
> This isn't pointed at anyone in particular, but I'm amazed how many people expect Unity to be finished after only a little over 5 months of development.

Unity is still getting better everyday, and I'm personally amazed how far it's come in that time. I can't wait to see what's in store for us after UDS-O in May.
yes cariboo but unity wont even work on my computer due to ati lack of support for open source

---

### Post by cariboo on 2011-03-25
There are quite a few people using Unity 3D running ATI cards, and as was said in an other thread, it looks like new ATI drivers will be out soon.

---

### Post by kansasnoob on 2011-03-27
> **mc4man said:**
> In 3d now you can just left click (hold) and move up or down directly in the launcher (or pull out and place, either way.

Never used 2d - as of a month or so ago (date of page), it seemed you could only do so in gconf-editor - screenshot here (use a up or down in the launcher's 'edit' key
[http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html)

Edit: if 2d has/uses dconf-editor as shown above then once you get the key in edit mode you could use cut and paste to rearrange (or retype

That's the most helpful thing I've seen in quite a while. Many, many thanks :D

---

### Post by rburkartjo on 2011-03-27
tks for the info on rearranging the icons. on my computer it applies only to the icons that you add the default ones cant be moved

---

### Post by dmegg on 2011-04-20
> **cariboo907 said:**
> This isn't pointed at anyone in particular, but I'm amazed how many people expect Unity to be finished after only a little over 5 months of development.

That's fair -- it's not fair to expect a mature, production-quality app after only 5 months -- but then why is it already the default in Natty?

---

### Post by lucazade on 2011-04-20
> **dmegg said:**
> That's fair -- it's not fair to expect a mature, production-quality app after only 5 months -- but then why is it already the default in Natty?

Because f/oss software usually doesn't mature inside a software house, only in the hands of developers and unreleased for a long time (like for proprietary software).
It is released often and early to get feedbacks, bug reports and code contributions from a community of testers, developers and early adopters.
It is included in Natty also because it is not a LTS release so there is no reason to keep everything as stable as possible.. is the correct release and time to push something unstable but with good perspectives in order to have a stable and feature rich release for the next LTS.
(something it could be difficult achived if this software is not pushed to masses, at least for small/medium company and for f/oss software)

---

### Post by dmegg on 2011-04-20
> **lucazade said:**
> Because f/oss software usually doesn't mature inside a software house, only in the hands of developers and unreleased for a long time (like for proprietary software).
It is released often and early to get feedbacks, bug reports and code contributions from a community of testers, developers and early adopters.
It is included in Natty also because it is not a LTS release so there is no reason to keep everything as stable as possible.. is the correct release and time to push something unstable but with good perspectives in order to have a stable and feature rich release for the next LTS.
(something it could be difficult achived if this software is not pushed to masses, at least for small/medium company and for f/oss software)

I agree with the spirit of your statement - I've been active as a FOSS developer and project maintainer for over 20 years, and have always released early and often - but you're confusing "released" with "default".  

Should Unity be released and included in Natty for people to play with?  Of course!  Should Unity be the automatic default for new Ubuntu users before it's mature and stable?  Nope.

---

### Post by lucazade on 2011-04-20
> **dmegg said:**
> I agree with the spirit of your statement - I've been active as a FOSS developer and project maintainer for over 20 years, and have always released early and often - but you're confusing "released" with "default".  

Should Unity be released and included in Natty for people to play with?  Of course!  Should Unity be the automatic default for new Ubuntu users before it's mature and stable?  Nope.

No confusion, I would say a different point of view..
Let me try to explain better with some examples... Ubuntu decided to ship grub2 as default bootloader some release ago and it was not mature, same applied for plymouth, for pulseaudio, for other user space applications (empathy) and without providing a fallback in default installation.
Now these applications are pretty solid (erm, enough solid)!
In natty we have both a mature stack (gnome-panel and friends) and unity, this seems to me resonable, it is a first time without a out-out decision.

edit: anyway we're going OT! :)

---

