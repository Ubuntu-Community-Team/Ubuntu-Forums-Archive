---
title: "Recent update-manager change"
date: 2010-07-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-07-10
The new update-manager shows the package's description and name with a focus on the description. What sounds like a good idea in theory looks like an UX nightmare in reality to me:

[img]http://img.xrmb2.net/images/884686.png[/img]

Instead of not knowing what a certain package does (which is OK for me), I now have to feel even more dumb, because I don't understand what those descriptions say. What's a "kernel module"? What's a "shared library"? What are "header files"? Plus: some descriptions just suck.

IMO the change is causing more questions about a package update than it closes. #-o

**--- EDIT ---**

At least you can revert the change via a gconf key. Set '/apps/update-manager/summary_before_name' to false with gconf-editor and everything's back to normal. :)

---

### Post by dino99 on 2010-07-10
and this report: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/602980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/602980)

---

### Post by kyleabaker on 2010-07-10
> **MacUntu said:**
> IMO the change is causing more questions about a package update than it closes. #-o

I agree. I don't understand why they aren't making the update manager dead-simple by only showing "check for updates" and "install updates" buttons, something like this quick mockup.

[IMG]http://img23.imageshack.us/img23/2975/screenshotts.png[/IMG]

---

### Post by Mr. Picklesworth on 2010-07-11
I actually kind of like it. There's movement afoot to make package summaries and descriptions less geeky, so hopefully that will cure the problem you see.

---

### Post by Old Marcus on 2010-07-12
YEah, descriptions on 95% of packages in the repos are very terse and assume you know what they're talking about. When you don't, it's pretty rubbish. Synaptic is a wonderful tool, but what's the point if you don't know what half the apps do?

---

### Post by psyke83 on 2010-07-12
> **kyleabaker said:**
> I agree. I don't understand why they aren't making the update manager dead-simple by only showing "check for updates" and "install updates" buttons, something like this quick mockup.

[IMG]http://img23.imageshack.us/img23/2975/screenshotts.png[/IMG]

That would cause many problems during the development cycle (when users are expected to check that dependencies are satisfied before proceeding), and would encourage bad user habits. Check the sticky on Partial Upgrades for more information.

---

### Post by kyleabaker on 2010-07-12
> **psyke83 said:**
> That would cause many problems during the development cycle (when users are expected to check that dependencies are satisfied before proceeding), and would encourage bad user habits. Check the sticky on Partial Upgrades for more information.

That's true, but if the update-manager had the ability to start up in the state that it was last in, details shown or details hidden, then this wouldn't be a problem and would make the update manager less intimidating to new users when its released. When update alerts appear in Windows or Mac, they hide this information by default and you click to view more details. They must do this for a reason.

Show details in my example screenhot was intended to expand the view to the current style so that packages and information can be displayed for each update.

---

### Post by ranch hand on 2010-07-12
> **kyleabaker said:**
> That's true, but if the update-manager had the ability to start up in the state that it was last in, details shown or details hidden, then this wouldn't be a problem and would make the update manager less intimidating to new users when its released. When update alerts appear in Windows or Mac, they hide this information by default and you click to view more details. They must do this for a reason.

Show details in my example screenhot was intended to expand the view to the current style so that packages and information can be displayed for each update.
Yes they do, they assume you are to silly to understand or research what you don't understand.

We do not need to lower Linux in general or Ubuntu specifically to the lowest common user species.

---

### Post by orlox on 2010-07-13
My usability problem now, its that it's much harder to quickly check the entire package list (even when they're ordered alphabetically by package name). I wouldn't mind it that much if the package names where differentiated in any clear way, like being in bold or anything...

---

### Post by Slug71 on 2010-07-13
Do not want.

---

### Post by cszikszoy on 2010-07-14
Google is your friend.  Things like "Kernel" and "Module" are fundamental ideas and definitions.  I don't think we need to dilute the descriptions so much that they become completely meaningless.

---

### Post by MacUntu on 2010-07-14
> **cszikszoy said:**
> I don't think we need to dilute the descriptions so much that they become completely meaningless.

They **are** completely meaningless to the masses of computer users.

---

