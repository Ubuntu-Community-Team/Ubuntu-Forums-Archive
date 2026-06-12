---
title: "Shared home folders - how realistic?"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by jonny on 2006-05-30
How practical is it to share a home folder between clients (I plan to use NFS on 4-5 PCs)?  I really want the convenience, but I'm worried about:

 - Mucked up toolbars and desktop due to differing screen resolutions on different clients
 - Menu items for programs that don't exist on a given desktop
 - Conflicts between configuration files where not all clients have the same software version
 - Laptop issues when the network's not available

Does anyone have any experience, good or bad?

---

### Post by Sef on 2006-05-30
Are some the machines Windows machines or are all GNU-Linux ones?  NFS is for GNU-Linux. (just checking)

---

### Post by jonny on 2006-05-30
[QUOTE=Sef]Are some the machines Windows machines or are all GNU-Linux ones?  NFS is for GNU-Linux. (just checking)[/QUOTE]One dual boots Windows for the kids' games but anything productive is always done in Ubuntu - it's just so much more pleasant to use.

I got Samba working before fiddling with NFS but it seemed like a second rate option - slow and cumbersome to configure

---

### Post by scooper on 2006-06-02
Personally, I would take a more selective approach.  Sharing the entire home directory is counting on luck.  There's transient state in there that may or may not be dependent on machine state.  It depends on the app, i.e. no guarantees are possible.  And if you ever somehow have both machines running and are logged in, then all bets are off.  If it works it may just be by coincidence.

I would consider taking a more careful and selective approach.  One possibility is to have separate home directories with soft links to shared subdirectories for applications that you become comfortable work fine in a shared environment.  There's a lot of stuff for which there would be no benefit in sharing anyway.  Yes, this is more work, but there may not be as many things you care about sharing as you may think.

HTH,
Steve

---

### Post by Iowan on 2006-06-02
[QUOTE=scooper]Yes, this is more work, but there may not be as many things you care about sharing as you may think.
[/QUOTE] Don't think of it as more work - think of it as [COLOR="DarkOrchid"]an educational opportunity[/COLOR] ;)

---

### Post by jonny on 2006-06-04
[QUOTE=scooper]Personally, I would take a more selective approach.  Sharing the entire home directory is counting on luck.  There's transient state in there that may or may not be dependent on machine state.  It depends on the app, i.e. no guarantees are possible.  And if you ever somehow have both machines running and are logged in, then all bets are off.  If it works it may just be by coincidence.

I would consider taking a more careful and selective approach.  One possibility is to have separate home directories with soft links to shared subdirectories for applications that you become comfortable work fine in a shared environment.  There's a lot of stuff for which there would be no benefit in sharing anyway.  Yes, this is more work, but there may not be as many things you care about sharing as you may think.

HTH,
Steve[/QUOTE]
Thanks for that advice.  I did recklessly try mounting a home folder as an NFS share and the results weren't too pretty - lots of error messages about missing icons, unsupported panel applets and the like.

I guess that the way forward is to share the Documents and Desktop folders for each user instead.  That'll give 99% of the benefits without any of the pain.

---

