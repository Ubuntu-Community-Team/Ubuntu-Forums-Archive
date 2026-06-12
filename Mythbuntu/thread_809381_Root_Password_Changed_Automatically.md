---
title: "Root Password Changed Automatically ?"
date: 2008-05-27
forum: Mythbuntu
---

### Post by stevecartermo on 2008-05-27
I have a MYTHBUNTU 8.04 box. It has been running for about a week. I tried to run the control centre today and it asked me for my password. I entered it and apparently my password has been changed, so I can no longer access the control centre.

It worked before I changed a setting in MYTHWEB. Originally [I] could view asx streams from within my network but not from work. So I think I changed a setting dealing with HTTP in MYTHWEB. Now I get the older MYTHWEB interface and I can't view ASX streams from anywhere.

I also installed some updates in the interim through the automatic update service.

The real problem is that my password has been changed.

Any ideas ?

Thanks[/I]

---

### Post by stevecartermo on 2008-05-27
UPDATE

I added '?RESET_TMPL=true' to the end of my MYTHWEB host name and the ASX streams are back !!!

But I still cannot access the MYTHBUNTU CONTROL CENTRE with my previous password. It seems like one of the updates has changed my root password. Is there a BACKDOOR I can use to get back into the control centre ?

Thanks

---

### Post by superm1 on 2008-05-28
If your user password has been changed (and not by you), then I think you have bigger worries.  No packaging updates would have done this.

Boot up into recovery mode, and choose the root console.

Type:

```
passwd USERNAME
```

where USERNAME is your normal login name.  This will allow you to reset that password.

Make sure that you have performed all the security updates (there is an SSH vulnerability floating around).  Also make sure that you check all your logs for possible intrusions.

---

### Post by stevecartermo on 2008-05-28
Thanks for the tip

I checked the logs and someone was ssh'ing into my box,  they were trying various first names, my user name and password WERE the same ... so someone was having some fun with me ... Too much time on their hands I guess.

---

### Post by laga on 2008-05-29
Time for a reinstall? ;)

---

### Post by stevecartermo on 2008-05-29
I didn't see any new users created. Do you think a reinstall is necessary ?

---

### Post by superm1 on 2008-05-29
> **stevecartermo said:**
> I didn't see any new users created. Do you think a reinstall is necessary ?
Well unless you can replay every command that they did; i would say a reinstall should be done.

Otherwise: you have no idea what backdoor hacks that they could have dropped in place.

---

