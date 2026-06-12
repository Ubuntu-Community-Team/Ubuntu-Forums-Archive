---
title: "Need to connect to my university wireless network"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by Alnico on 2009-03-05
Hi!

I'm using Intrepid Ibex and I need to connect to my University wireless network. I tried reading various forum threads but no luck so far. My university does not support Linux anymore... their help system is dated.

I can connect in Vista but not Ubuntu.

This is the information to connect in Vista:
* [http://wireless.curtin.edu.au/downloads/Vista%20Student.pdf](http://wireless.curtin.edu.au/downloads/Vista%20Student.pdf)

This is to connect in Linux (but it does not work when I tried)
* [http://wireless.curtin.edu.au/downloads/remotecampuses.pdf](http://wireless.curtin.edu.au/downloads/remotecampuses.pdf)

Desperately looking for a solution.

Regards,

---

### Post by mark bower on 2009-03-06
it can be nothing more than your wireless adapter.  mine worked under XP, but would not work with Ubuntu 8.10.  get a Belkin F5D7050 (Best Buy, Fry's Electronics etc).  it works out of the box with native linux drivers, no ndiswrapper.  others report success with this adapter and that is why i purchased and am using it.

mark bower

---

### Post by Alnico on 2010-01-06
Curtin Wireless Settings in Ubuntu:

Found the solution:
[LIST]
[*]Turn on your wireless setting.
[*]Under the **Authentication** menu, select **Protected EAP**
[*]In **CA certificate**, select **Entrust.netSecureServerCertificationAuthority.cer**.
[*]Under **PEAP version**, select **Automatic**.
[*]Under **Inner Authentication**, select **MSCHAPv2**.
[*]Under **Username**, enter your Curtin student ID.
[*]Under **Password**, enter your Oasis password.
[/LIST]

It may take a while to connect.

---

### Post by mrmagoo1077 on 2010-01-14
I have a very similar problem, and followed these instructions with my schools certificate but it still wont connect (not the adapter part)

---

