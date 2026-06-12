---
title: "Crash course in Launchpad"
date: 2010-08-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by amauk on 2010-08-12
I know this is the maverick testing forum
but there isn't a forum for launchpad

Is there a crash course available for launchpad (or distributed version control systems in general?)

I've tried tracking the progress of bugs I've filed that have had fixes released, and it's a maze of branches and different things, that I can't seem to wrap my head around. I think there's some fundamental concept that I'm missing, cause I can't understand how the whole thing is coordinated

Just curious, as much as anything

---

### Post by taavikko on 2010-08-12
From [https://help.launchpad.net](https://help.launchpad.net)

Contact us: #launchpad and #launchpad-dev on Freenode, launchpad-users list or ask the sysadmins for help.

IRC is a good place to ask if in need of assistance.

---

### Post by Longinus00 on 2010-08-12
Launchpad isn't a DVCS(Distributed Version Control Systems), it's a project management/software hosting website kind of like sourceforge or google code. Launchpad does, however, host code using a DVCS called bazaar.

---

### Post by Mr. Picklesworth on 2010-08-12
Launchpad and Bzr's own documentation are actually quite excellent for getting started, in my experience.

Some points of interest:
[https://help.launchpad.net/Code/QuickStart](https://help.launchpad.net/Code/QuickStart)
[http://doc.bazaar.canonical.com/bzr.2.2/en/](http://doc.bazaar.canonical.com/bzr.2.2/en/)
[http://bazaar.canonical.com/en/](http://bazaar.canonical.com/en/)

The package bzr-explorer provides a really nice GUI for Bazaar, too ;)

---

### Post by 23meg on 2010-08-12
There's no web forum dedicated to Launchpad, but the main purpose of this forum is to provide testing assistance, and Launchpad is our most prominent tool, so if you have questions after studying some of the above, you can ask them here as well as in the [launchpad-users mailing list]("http://lists.ubuntu.com/mailman/listinfo/launchpad-users"), or #launchpad on [Freenode]("http://www.ubuntu.com/support/community/chat").

---

### Post by ubu newb on 2010-08-12
How does someone unsubscribe from launchpad?  I no longer want to receive bug reports.

---

### Post by 23meg on 2010-08-12
> **ubu newb said:**
> How does someone unsubscribe from launchpad?  I no longer want to receive bug reports.

Go to the page for the bug you want to unsubscribe from, and click the "Unsubscribe" link on the right. Or visit [https://bugs.launchpad.net/ubuntu/+bug/bugnumber/+subscribe](https://bugs.launchpad.net/ubuntu/+bug/bugnumber/+subscribe), replacing "bugnumber" with the actual number of the bug, and click "Continue". Or send mail to [email]bugnumber@bugs.launchpad.net[/email] , replacing "bugnumber" with the actual number of the bug, with the body text "unsubscribe".

---

### Post by ubu newb on 2010-08-12
> **23meg said:**
> Go to the page for the bug you want to unsubscribe from, and click the "Unsubscribe" link on the right. Or visit [https://bugs.launchpad.net/ubuntu/+bug/bugnumber/+subscribe](https://bugs.launchpad.net/ubuntu/+bug/bugnumber/+subscribe), replacing "bugnumber" with the actual number of the bug, and click "Continue". Or send mail to [EMAIL="bugnumber@bugs.launchpad.net"]bugnumber@bugs.launchpad.net[/EMAIL] , replacing "bugnumber" with the actual number of the bug, with the body text "unsubscribe".


If I understand you correctly, I have to unsubscribe to individual bugs.  Not what I want to do.   I don't want to receive any bug reports at all.

---

### Post by Mr. Picklesworth on 2010-08-12
> **ubu newb said:**
> If I understand you correctly, I have to unsubscribe to individual bugs.  Not what I want to do.   I don't want to receive any bug reports at all.

You're only subscribed to bug reports if you have explicitly done so or joined a team subscribed to said bug reports. It tells you at the bottom of each message you receive why you received it, so you can figure out how to deal with it. For example&#8230;

> --
Desktop icons are allowed to overlap
[https://bugs.launchpad.net/bugs/40872](https://bugs.launchpad.net/bugs/40872)
You received this bug notification because you are a direct subscriber
of the bug.

Or:

> --
memory leaks in liblaunchpad-integration
[https://bugs.launchpad.net/bugs/483610](https://bugs.launchpad.net/bugs/483610)
You received this bug notification because you are a member of Ubuntu
Desktop, which is the registrant for launchpad-integration.

---

### Post by ubu newb on 2010-08-13
Here's what I have at the bottom:

~/.bazaar created owned by root (when run under sudo)
[https://bugs.launchpad.net/bugs/376388](https://bugs.launchpad.net/bugs/376388)       <----------------------I have over 40 of these with different numbers
You received this bug notification because you are subscribed to bzr in
ubuntu.


How do I stop the bzr in ubuntu group?   Unsubscribing from each individual number will only stop that number not future bugs with different numbers.

---

### Post by 23meg on 2010-08-13
> **ubu newb said:**
> Here's what I have at the bottom:

~/.bazaar created owned by root (when run under sudo)
[https://bugs.launchpad.net/bugs/376388](https://bugs.launchpad.net/bugs/376388)       <----------------------I have over 40 of these with different numbers
You received this bug notification because you are subscribed to bzr in
ubuntu.


How do I stop the bzr in ubuntu group?   Unsubscribing from each individual number will only stop that number not future bugs with different numbers.

You've subscribed to receive notification about all bugs for the bzr package in Ubuntu. Go to [https://launchpad.net/ubuntu/+source/bzr](https://launchpad.net/ubuntu/+source/bzr) and click "Subscribe to bug mail" (yes, the wording is such even if you're already subscribed) on the right, and uncheck "I want to receive these notifications by e-mail".

For future reference: [https://help.launchpad.net/Bugs/Subscriptions](https://help.launchpad.net/Bugs/Subscriptions)

---

