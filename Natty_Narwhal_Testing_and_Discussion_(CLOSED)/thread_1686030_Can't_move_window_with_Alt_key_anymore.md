---
title: "Can't move window with Alt key anymore"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by durand on 2011-02-11
Hi,

I can't seem to move windows with the alt key pressed, and then using the left mouse button anymore. This was the case in unity and in pure compiz. I'm not sure what setting was changed by unity but it's really annoying. I also can't resize windows with alt + middle click and drag like in maverick. What's really strange is that I can drag windows that are not focussed but as soon as they are selected, I can't.

Does anyone know how to fix it?

Thanks!

EDIT: Making windows transparent by scrolling with alt has the same problem :(

---

### Post by coffeecat on 2011-02-11
Both alt + left mouse button to move a window, and alt + middle-click to drag are working for me in Unity/compiz fully updated within the last hour or so. Have a look in ccsm, Windows Management to see if you have 'Move Window' ticked, and Initiate Window Move set for '<Alt>Button1'.

---

### Post by cariboo on 2011-02-11
Here are some of the keyboard short cuts so far:

[https://wiki.ubuntu.com/Unity/KeyboardShortcuts]("https://wiki.ubuntu.com/Unity/KeyboardShortcuts")

---

### Post by durand on 2011-02-11
Hmmmph. I must have alt keys bound to something else. It's really weird though. I just can't do stuff to a window when selected. Even when focussed, it works but if I click directly in the window, alt doesn't work. I might try running a new user account and see if the same problem occurs there. Thanks for you help.

---

### Post by rburkartjo on 2011-02-12
car tks for posting the link for unity shortcut key was really going nuts trying to figure out cause i lot of the keys combos that worked in mav no longer work

---

### Post by Jay Car on 2011-02-12
> **durand said:**
> Hi,

I can't seem to move windows with the alt key pressed, and then using the left mouse button anymore. This was the case in unity and in pure compiz. I'm not sure what setting was changed by unity but it's really annoying. I also can't resize windows with alt + middle click and drag like in maverick. What's really strange is that I can drag windows that are not focussed but as soon as they are selected, I can't.

Does anyone know how to fix it?

Thanks!

EDIT: Making windows transparent by scrolling with alt has the same problem :(

Argh, this is also (one of many crazy things) happening to my Natty install. It only seemed to start a couple of days ago, but I had been making settings changes and (like always) figured it was caused by something I'd done. But after several hours of reading and trying to undo some of the changes I had made, it only got worse. The only thing that helped me to keep a sense of humour about the whole mess, was remembering a comment (or sig used by someone here on the forums) that said (roughly): "If it ain't broke, you haven't tweaked it enough."  

Well, I now believe I've tweaked it enough, 'cuz it's definitely broke. :D

coffeecat & cariboo907, as always, you are gems. I've stayed the course, this far, due largely to you two and many others that comment here (quackers too!). In spite of my many dilemmas, I am learning new things (in small steps) and finding it to be fun (mostly). :) 

I've decided that it's time I learn about making bug reports, so by the next testing cycle I can be more helpful. This time I've not been much help, because I'm pretty clueless about some of the messes I've made of poor Natty (and some of them have been pretty spectacular!), and Launchpad looks a little intimidating to me right now. Also, when I was a kid (and always underfoot), my mom used to tell me that, sometimes, the best way to help is to just stay out of the way...so, I've tried stay out of the way and not to be too noisy here. 

Hopefully the things I'm learning now will help me to be noisier next time.

:)

---

### Post by durand on 2011-02-12
Kinda why I was posting here first, to see if anyone else has the same problem. Why the heck did they have to change the tried and tested keyboard shortcuts in Unity, I really don't know.

---

### Post by cariboo on 2011-02-12
The key bindings you used to use are tied to gnome-panel, and seeing as Unity doesn't use gnome-panel, the key bindings will no longer work.

---

### Post by coffeecat on 2011-02-12
> **cariboo907 said:**
> The key bindings you used to use are tied to gnome-panel, and seeing as Unity doesn't use gnome-panel, the key bindings will no longer work.

Are Alt+left-click and alt+middle-click tied to gnome panel? Because they're both still working for me in Natty Unity despite some further updates. (Including some Plymouth updates which have - ahem - disrupted Plymouth.)

---

### Post by durand on 2011-02-12
> **coffeecat said:**
> Are Alt+left-click and alt+middle-click tied to gnome panel? Because they're both still working for me in Natty Unity despite some further updates. (Including some Plymouth updates which have - ahem - disrupted Plymouth.)

Damn, just discovered that alt-right is another thing that works like the alt-middle and alt-left.

---

### Post by mc4man on 2011-02-12
> **durand said:**
> Hi,

I can't seem to move windows with the alt key pressed, and then using the left mouse button anymore. This was the case in unity and in pure compiz. I'm not sure what setting was changed by unity but it's really annoying. I also can't resize windows with alt + middle click and drag like in maverick. (

Those 2 should still work fine in a Desktop > unity login (Alt+l.click to move, Alt+middle click to resize), they do here, noting the middle click is with a 3 button mouse.

If you set up and login to a new user do they work?

---

### Post by durand on 2011-02-13
Yeah, they work in a new user. I really can't see what setting was changed though. If I install unity and those apps, I can't use alt at all :/

---

### Post by funkyhat on 2011-02-24
I have reported this bug here [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/724454](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/724454)

Feel free to mark it as "affects me too"

---

