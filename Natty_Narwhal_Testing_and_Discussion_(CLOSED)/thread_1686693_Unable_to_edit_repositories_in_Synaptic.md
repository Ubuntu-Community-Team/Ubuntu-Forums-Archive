---
title: "Unable to edit repositories in Synaptic"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dearingj on 2011-02-12
Has anyone else had this problem? I open Synaptic, open the Settings menu, and choose Repositories. A new window is opened, but it is blank.

I've also noticed - and this may or may not be related - that Update Manager's Settings button is grayed out.

I'm running Lubuntu Natty (Ubuntu, upgraded from Maverick, with the lubuntu-core package installed).

---

### Post by Harry33 on 2011-02-13
> **dearingj said:**
> Has anyone else had this problem? I open Synaptic, open the Settings menu, and choose Repositories. A new window is opened, but it is blank.

I've also noticed - and this may or may not be related - that Update Manager's Settings button is grayed out.

I'm running Lubuntu Natty (Ubuntu, upgraded from Maverick, with the lubuntu-core package installed).

Problems with software sources (repositories management) rise up every now and then.
However, atm there should not be one around.
First check, that the package software-properties-gtk is installed (and also perhaps try reinstalling it).

And try to start the applications from terminal too:
```

sudo software-properties-gtk

```

---

### Post by dearingj on 2011-02-13
For some reason I had software-properties-kde installed instead of software-properties-gtk installed. Installing -gtk and removing -kde solved the problem. Thanks for the tip :)

---

