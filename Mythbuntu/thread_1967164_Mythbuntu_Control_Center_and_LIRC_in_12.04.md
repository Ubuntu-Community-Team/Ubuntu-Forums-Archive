---
title: "Mythbuntu Control Center and LIRC in 12.04"
date: 2012-04-27
forum: Mythbuntu
---

### Post by thatguruguy on 2012-04-27
The Mythbuntu Control Center wants to reconfigure my LIRC settings, as root.  Since I use a homebrew serial receiver, I really don't want it to.  However, there is no apparent way for me to change its mind.

Since the only way to enable the mythtv repository is through the MCC (as of 12.04), I am faced with a bit of a quandary.  I really want to enable the repository, but don't want MCC to mess with my LIRC settings.

Any input would be appreciated.  The ability to use MCC in a way that makes sense would be appreciated even more.

---

### Post by tgm4883 on 2012-04-27
> **thatguruguy said:**
> The Mythbuntu Control Center wants to reconfigure my LIRC settings, as root.  Since I use a homebrew serial receiver, I really don't want it to.  However, there is no apparent way for me to change its mind.

Since the only way to enable the mythtv repository is through the MCC (as of 12.04), I am faced with a bit of a quandary.  I really want to enable the repository, but don't want MCC to mess with my LIRC settings.

Any input would be appreciated.  The ability to use MCC in a way that makes sense would be appreciated even more.

I seem to recall a bug about that, must not have gotten fixed before release. I'll poke the developer on that. 

In the meantime, you can add the updates repo manually via the command line by doing (assuming you want MythTV 0.25 updates)

```
apt-add-repository ppa:mythbuntu/0.25
```

---

### Post by thatguruguy on 2012-04-27
> **tgm4883 said:**
> I seem to recall a bug about that, must not have gotten fixed before release. I'll poke the developer on that. 

In the meantime, you can add the updates repo manually via the command line by doing (assuming you want MythTV 0.25 updates)

```
apt-add-repository ppa:mythbuntu/0.25
```

Thanks!

---

### Post by tgm4883 on 2012-04-27
> **thatguruguy said:**
> Thanks!

Out of curiosity, is the LIRC tab of MCC set to anything (like custom)?

---

### Post by thatguruguy on 2012-05-01
I apologize for not having responded to you earlier.

Here's a screen shot:
[IMG]http://img641.imageshack.us/img641/412/mcclircscreenshot.jpg[/IMG]

It would be useful to either be able to "uncheck" any buttons, or have an option that read something like "Make no changes".

FWIW, this is running on a box which has been upgraded from 11.10.

---

### Post by chicobiker on 2012-05-05
You might try checking "No additional remote suppoet" at the top.  That will uncheck your current setting.

---

### Post by thatguruguy on 2012-05-07
> **chicobiker said:**
> You might try checking "No additional remote suppoet" at the top.  That will uncheck your current setting.

... and it removes LIRC from my system.  Which is not an ideal solution, all things considered.

---

### Post by anonymousdog on 2012-05-08
> **thatguruguy said:**
> ... and it removes LIRC from my system.  Which is not an ideal solution, all things considered.
I also have noted on test PCs that there seems to be no option that equates to "no change" in MCC.

---

### Post by thatguruguy on 2012-05-08
> **anonymousdog said:**
> I also have noted on test PCs that there seems to be no option that equates to "no change" in MCC.

Indeed. And that's a problem.

---

### Post by foxbuntu on 2012-05-09
Thanks for the detailed reports. I have been looking into the code and replicated the situation that causes this. The fix however is more complicated than it first seemed and I am working on a solution to not break other things.

---

### Post by thatguruguy on 2012-05-09
> **foxbuntu said:**
> Thanks for the detailed reports. I have been looking into the code and replicated the situation that causes this. The fix however is more complicated than it first seemed and I am working on a solution to not break other things.

Thanks!  That is great to hear.

---

### Post by anonymousdog on 2012-05-09
> **foxbuntu said:**
> The fix however is more complicated than it first seemed...
Thanks for your work, fox.  Ain't that "the way" of all things computer?

---

### Post by thatguruguy on 2012-10-05
I was wondering if there's been any progress on this issue.

---

