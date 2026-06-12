---
title: "Network Manager Icon"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gdonwallace on 2011-03-31
So I upgraded to 11.04 alpha 3 a few days ago.  Been messing around with it and all the system crashes, but its alpha so no real issue there.

The one thing I have seen and that is bothering me is he Network Manager Icon on the upper panel is not there any more.  I have an icon but its just a black square (kinda looks like a monitor).  There is nothing there indicating connection strength or that NM is making a connection.  I cant tell if I am actually connected to any wifi network, unless I see a temp on the lower panel next to the clock.

Anyone else have this issue or know how to fix it.  And it only started after an apt-get update / upgrade I did last week.

---

### Post by Harry33 on 2011-03-31
> **gdonwallace said:**
> So I upgraded to 11.04 alpha 3 a few days ago.  Been messing around with it and all the system crashes, but its alpha so no real issue there.

The one thing I have seen and that is bothering me is he Network Manager Icon on the upper panel is not there any more.  I have an icon but its just a black square (kinda looks like a monitor).  There is nothing there indicating connection strength or that NM is making a connection.  I cant tell if I am actually connected to any wifi network, unless I see a temp on the lower panel next to the clock.

Anyone else have this issue or know how to fix it.  And it only started after an apt-get update / upgrade I did last week.

Actually Natty is beta-1 now.

Nm-applet icon issue is well known.
The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741387](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741387)

You can get your icon back by downgrading the package
libappindicator1_0.3.0-0ubuntu1
to the previous version
libappindicator1_0.2.99-0ubuntu1

Here:
[https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1](https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1)

---

### Post by gdonwallace on 2011-03-31
I posted before the email came out that Natty hit beta.

I will try to downgrade and see if that helps.

---

