---
title: "Galaxy Screensaver locks up system"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by wkulecz on 2006-09-30
Fresh install of 6.06.1 from "alternate" CD on raid 1 array.  Istalled all the updates offered upon initial boot up.

Playing with the screeensavers, choosing "galaxy" locked the system up hard.  Rest button only way to recover.

Problem repeatable.

How to remove galaxy from the list?

Anyone else have this problem with "galaxy" or any other screensaver modules?

--wally.

---

### Post by fatsheep on 2006-09-30
I have no problems with Galaxy.  Do you have the propriety drivers for your graphics card installed?

---

### Post by wkulecz on 2006-09-30
No its a stock install.

I'd set up six Ubuntu system (configured one, cloned five more) week before last using the proprietary drivers and it had a lockup while letting "random" screensaver run.  Ultimately these systems needed to have all blanking and screensavers disabled for their intended use, so I disabled screensavers and got on with setting things up.  The first system has run continuously for over a week with no issues (very heavy network usage application)

I do plan to install the nvidia drivers here, but based on past experience if it fixes "galaxy" I suspect it breaks something else.

I don't (won't) put much effort into fixing "eye candy" problems as I rather quickly disable any of this crap at the slightest hint of trouble.

--wally.

---

### Post by fatsheep on 2006-09-30
There are many different ways to install the nvidia drivers but I think the easiest is through Automatix (check the link in my signature).  All you need to do is scroll down to the "Nvidia driver" item, check it's box, and hit "OK" and it will install.  You shouldn't have any more problems with screensavers after that.

---

### Post by wkulecz on 2006-09-30
You missed what I's said.  I had, as far as I can tell the same lockup on a differnet system that had the nvidia proprietary driver installed.  Since it was on "random" and was locked up when I came in the next day I wasn't able to tell which was the one that locked up. After disabling the screensavers system uptime is well over a week now.

This one is repeatable, all I have to do is choose "galaxy" in the preview window and after a little drawing in the prepiew box it locks up.

I do intend to install the nividia drivers tomorrow.

--wally.

---

### Post by fatsheep on 2006-09-30
Ok tell me if you still have problems with Galaxy after the propriety drivers install.

---

### Post by wkulecz on 2006-09-30
Will do.  FYI this is GeForce 7300LE, 128MB, PCI-express; other systems were GeForce 5500, 128MB, ACP. 

--wally.

---

### Post by wkulecz on 2006-10-01
You were correct, after installing the nvidia glx drivers the lockup problem with galaxy screensaver is gone.  It'll be intresting to see if I now observe the lockup I saw on the other system on this one with random screensaver.

--wally.

---

### Post by fatsheep on 2006-10-01
Glad to hear it.  :)

---

