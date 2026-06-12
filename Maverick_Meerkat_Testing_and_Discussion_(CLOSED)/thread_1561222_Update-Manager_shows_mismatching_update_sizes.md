---
title: "Update-Manager shows mismatching update sizes"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-08-26
Is anyone else seeing update sizes that differ like the one below? Notice its 12mb initially, but then it becomes 13mb when the download begins.

[IMG]http://a.imageshack.us/img825/6694/screenshotfi.png[/IMG]

There appears to either be a rounding error going on or missing download information prior to starting the download.

---

### Post by ranch hand on 2010-08-26
No, because while some do use UM on stable OS', it is just not suitable at all for unstable OS'.

Use something, anything, else and you will not have these problems.

---

### Post by kyleabaker on 2010-08-26
> **ranch hand said:**
> No, because while some do use UM on stable OS', it is just not suitable at all for unstable OS'.

Use something, anything, else and you will not have these problems.

That wasn't very helpful. [IMG]http://a.imageshack.us/img820/7002/norris.gif[/IMG]

I use Update Manager, Synaptic and Apt-Get randomly. It shouldn't matter if I use Update Manager at this point because any bugs that are found need to be reported for the average joe when he starts using it. Telling me to simply use something else isn't really helping anyone if there is a legit bug here.

I like to get things sorted out rather than simply changing my application "block list" and imagine there wasn't something off. ;)

---

### Post by mc4man on 2010-08-26
> it is just not suitable at all for unstable OS'.

There is nothing wrong with using the update manager at all.

Using the um and also synaptic when needed it's virtually impossible to mess things up, with the obvious exception of issues caused by packages themselves. (bugged packages, poor interaction w/ other packages ect.

The only exception would be if one accepted the **pop up** for a 'partial upgrade', which I would never do.

I've **never** had any problems this way and have always been updated as soon  and as easily  any other method.

---

### Post by coffeecat on 2010-08-26
> **kyleabaker said:**
> There appears to either be a rounding error going on or missing download information prior to starting the download.

I can confirm this. When I first opened UM it gave me the usual partial upgrade message, but after a metadata refresh with the check button this went away and it reported 72.0MB to download. But when I went ahead with the update it reported that it was downloading 76.5MB.

---

### Post by kyleabaker on 2010-08-26
Thanks guys! I searched through the known bugs and its been filed already as of a month ago.

If you're seeing this bug as well, you should add your me-too:
[https://bugs.launchpad.net/update-manager/+bug/610820](https://bugs.launchpad.net/update-manager/+bug/610820)

---

### Post by PaulW2U on 2010-08-26
I've seen this so I've added a "me too".

---

### Post by 23meg on 2010-08-26
> **ranch hand said:**
> No, because while some do use UM on stable OS', it is just not suitable at all for unstable OS'.

Use something, anything, else and you will not have these problems.

Almost all people using stable releases will use Update Manager, and it needs to be tested. Recommending people not to use it during testing is not a good way to help with that.

There's nothing making Update Manager less suitable for use on the development branch, other than the "Partial Upgrade" phenomenon, which is simply differently worded in other package managers and should be understood by testers in any case. 

Please don't advise against certain software or practices without offering technical substantiation as to why they should be avoided.

---

