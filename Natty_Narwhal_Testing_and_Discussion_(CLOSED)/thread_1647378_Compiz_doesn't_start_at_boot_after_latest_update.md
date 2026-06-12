---
title: "Compiz doesn't start at boot after latest update"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-17
Since the compiz updates yesterday compiz is not starting at boot.
I am going into Places > / > usr > bin and double clicking on compiz diamond.
That fixes it :-)

Anyone else seeing this?

---

### Post by Amroozy on 2010-12-17
go to compiz config settings manager ccsm and make sure that ubuntu unity plugin is checked ...

---

### Post by Quackers on 2010-12-17
Thanks, but the Unity plugin in ccsm is still checked. It's definitely compiz that won't start without a push :-)

---

### Post by chrismine on 2010-12-17
I have always started compiz from System -> Preferences - Startup Applications with command - compiz --replace.

---

### Post by Quackers on 2010-12-17
With no Unity and with ctrl+alt+t not starting a terminal and alt+F2 doing nothing, it's difficult to run compiz --replace :-)
Without cairo-dock I would be struggling.

---

### Post by Amroozy on 2010-12-17
right click on the desktop make new folder find your way to usr/shared/applications 
you can do anything from there

---

### Post by Quackers on 2010-12-17
As I have said, I have cairo-dock so I can get to the point of starting compiz manually. My concern is that it is not starting by itself as it was before yesterday.

---

### Post by mc4man on 2010-12-17
yesterdays compiz update removed a patch from the 0ubuntu2 ver. (000_workaround_gconfbackend_init_hang.patch:

I think that was possibly a mistake, the effect was immediate when trying to use the Desktop login.

orig. somewhat  unconfirmed bug that lead to patch removal
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461)

new on 0ubunu4
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691403](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691403)

Edit: noting again that this will not most likely not effect the classic login

---

### Post by Quackers on 2010-12-17
Thanks for the info mc4man.
I just installed 2.6.37-10 and it's behaving the same way.
I'll await an update :-)

---

### Post by Quackers on 2010-12-17
Recent compiz updates solved this - for the moment :-)

---

