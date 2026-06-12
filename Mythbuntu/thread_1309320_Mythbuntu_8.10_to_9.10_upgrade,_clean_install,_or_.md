---
title: "Mythbuntu 8.10 to 9.10: upgrade, clean install, or don't bother?"
date: 2009-11-01
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-11-01
I have a Mythbuntu 8.10 box, which mostly works.

I didn't bother upgrading to 9.04, but I don't like to get too many versions behind, so I'm tempted to upgrade to 9.10.

I see that the updates manager gives me an option to upgrade to 9.04, but not 9.10. Is that because it's not possible to upgrade from 8.10 to 9.10? 

In any case, is it better to upgrade or do a clean install? I'm rather wary of doing a clean install, because I have spent a great many hours fiddling about with the system to get it to work (reading many posts on this forum I suspect I'm not alone in finding that a great many features of Mythbuntu don't work by default and a lot of fiddling is required), and I suspect I'd have to do all that again after a clean install.

However, if people who are more knowledgeable than me (that's probably most of you!) tell me that clean install is a lot easier in the long run, I shall listen.

Also, is there any compelling reason to upgrade at all? As I said earlier, my system mostly works, and having spent so long getting it that way, I'm a little reluctant to do anything that may mean some things stop working. The one thing I've never been able to get working is the remote control, and I have to control everything via a wireless keyboard. It would be nice if I could get the remote control working, so if remote control support is somehow improved in 9.10 compared with 8.10, that would be reason enough to upgrade.

Many thanks for any thoughts or suggestions.
NM

---

### Post by AJ1000 on 2009-11-01
I found clean install is the best. The ext4 and speed improvements are really good. The upgrade keeps ext3 and the old grub. Otherwise don't bother as I felt my system was pretty much the same when I did an upgrade.

Yes, it is still fiddly.

---

### Post by superm1 on 2009-11-01
In your scenario, clean install is probably the easier route otherwise you have to dist-upgrade from 8.10 to 9.04 and then to 9.10.

I'd recommend doing it on another hard drive in case there are problems that you might have with 9.10 so you dont have to start all over with 8.10.

Something worth mentioning is that lirc_i2c remotes aren't working in 9.10.

Anything else that you guys are finding that is still "fiddly", *please* file bugs.  [http://launchpad.net/mythbuntu](http://launchpad.net/mythbuntu)

If they're not reported in the tracker, it's quite possible that no one is aware of them! :)

---

### Post by AJ1000 on 2009-11-01
Yes, I have reported a couple of bugs.

---

### Post by NautiusMaximus on 2009-11-01
> **superm1 said:**
> 

Anything else that you guys are finding that is still "fiddly", *please* file bugs.  [http://launchpad.net/mythbuntu](http://launchpad.net/mythbuntu)

If they're not reported in the tracker, it's quite possible that no one is aware of them! :)

It's tricky for someone relatively inexperienced in the ways of Linux, such as myself, to know what's appropriate to file as a bug and what isn't. I've found load of things that don't work they way I think they ought to work, but it's difficult to know whether that's because they really are bugs or just because I don't know what I'm doing (which for the most part, I don't).

Would a good rule of thumb be that if after googling my problem and posting about it here, it's still not solved, then it's probably worth filing as a bug?

---

### Post by cabbage on 2009-11-01
> Something worth mentioning is that lirc_i2c remotes aren't working in 9.10.


Would this apply to a remote plugged into a Hauppauge Nova-T 500?

This would be a bit of a show stopper for me. Maybe this should be listed under "known issues" on the mythbuntu site?


Regards...

---

### Post by murchball on 2009-11-02
FWIW I just upgraded my backend from 8.04. No problems whatsoever, but I did make sure that I had a database backup before I started. I also used Clonezilla to make an image of my system partition, just in case.

---

### Post by Fire_Chief on 2009-11-20
> **murchball said:**
> FWIW I just upgraded my backend from 8.04. No problems whatsoever, but I did make sure that I had a database backup before I started. I also used Clonezilla to make an image of my system partition, just in case.

Did you do this through the dist-upgrade process (8.04 -> 8.10 -> 9.04 -> 9.10)? Or did you use another method to get to 9.10 faster?

---

### Post by murchball on 2009-11-20
Exactly, one-by-one. It probably took four or five hours.

---

