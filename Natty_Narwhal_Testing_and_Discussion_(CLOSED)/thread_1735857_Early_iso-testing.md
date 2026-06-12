---
title: "Early iso-testing"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-04-21
Wow, one week to go and already some super early iso-testing:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

---

### Post by mc4man on 2011-04-23
As far as the live cd (try me), do find it odd that the log out option has been removed from the power button dropdown (unless it's been returned yesterday

The loading of some add. drivers like the nouveaua 3d for nvidia can only be done thru a a log out/in
(still can be done thru keyboard combos

---

### Post by kansasnoob on 2011-04-23
> **mc4man said:**
> As far as the live cd (try me), do find it odd that the log out option has been removed from the power button dropdown (unless it's been returned yesterday

The loading of some add. drivers like the nouveaua 3d for nvidia can only be done thru a a log out/in
(still can be done thru keyboard combos

I agree, one of the designers requested it be removed:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/750140](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/750140)

---

### Post by mc4man on 2011-04-23
So is there a "switch from ubuntu" option - don't see here but iso is from thur. night

---

### Post by kansasnoob on 2011-04-23
> **mc4man said:**
> So is there a "switch from ubuntu" option - don't see here but iso is from thur. night

I think it disappeared on the most recent build, but I don't see the change mentioned in any of the changelogs.

I'm also subscribed to that bug and the newer one and haven't seen a notice of any change.

---

### Post by mc4man on 2011-04-23
Such silliness - all because a dev who you'd think would know the live session user is ubuntu, (it only shows that it in the panel),  and that there was/is no password set...
I'm going to reopen the orig. just to see

The other related 'mistake;, (applies to installs also) is that a restart is not required for the mesa 3d drivers, only restarting x, (log out/in
And that may apply to other non video add. drivers

---

### Post by kansasnoob on 2011-04-23
> **mc4man said:**
> Such silliness - all because a dev who you'd think would know the live session user is ubuntu, (it only shows that it in the panel),  and that there was/is no password set...
I'm going to reopen the orig. just to see

The other related 'mistake;, (applies to installs also) is that a restart is not required for the mesa 3d drivers, only restarting x, (log out/in
And that may apply to other non video add. drivers

I had hoped that my comments there would prompt Matthew Paul Thomas to say, "Hey Evan, sorry I wasted your time, let's revert that". 

But that didn't happen, all I got was a, "I said I had no way to log in again, because I had no way of telling what the password was. It didn't even occur to me that just pressing Enter would work."

Rather than asking me to start a new bug report why didn't he just suck it up and say, "oops"? I guess designers never have oops moments like us humans :)

---

