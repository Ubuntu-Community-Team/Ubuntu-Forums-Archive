---
title: "Network Manager see no Blueman's connection"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by aneganov on 2010-02-26
After connecting my phone via bluetooth using Blueman and then activating Dialup connection in Blueman, it says "Now DUN is available in Network Manager" or something like this.
But, there is NOTHING about DUN connection in NM. What this thing is telling about?

Any ideas?

---

### Post by aneganov on 2010-02-28
Still have the problem.

Steps to reproduce:

1. I open Blueman, see my cellular phone there:

[ATTACH]148507[/ATTACH]

2. Select "Connect to: Dial-up Networking Gateway", after some time I see notification: **DUN connection on Motokisa will now be available  in Network Manager**:

[ATTACH]148505[/ATTACH]

3. I go in NM connections and see nothing related: 

[ATTACH]148506[/ATTACH]


So what do they mean - available?

---

### Post by aneganov on 2010-02-28
[https://bugs.edge.launchpad.net/blueman/+bug/529367](https://bugs.edge.launchpad.net/blueman/+bug/529367)

Reported a bug

---

### Post by walmis on 2010-02-28
I see you have "&#1084;&#1086;&#1073;&#1080;&#1083;&#1085;&#1099;&#1077; &#1096;&#1080;&#1088;&#1086;&#1082;&#1086;&#1087;&#1086;&#1083;&#1086;&#1089;&#1077;&#1085;&#1099;&#1077;", that most likely is your dun connection.

---

### Post by aneganov on 2010-02-28
> **walmis said:**
> I see you have "&#1084;&#1086;&#1073;&#1080;&#1083;&#1085;&#1099;&#1077; &#1096;&#1080;&#1088;&#1086;&#1082;&#1086;&#1087;&#1086;&#1083;&#1086;&#1089;&#1077;&#1085;&#1099;&#1077;", that most likely is your dun connection.

Yes, I tried looking in there, this is what it offers. 

"&#1052;&#1086;&#1073;&#1080;&#1083;&#1100;&#1085;&#1099;&#1077; &#1096;&#1080;&#1088;&#1086;&#1082;&#1086;&#1087;&#1086;&#1083;&#1086;&#1089;&#1085;&#1099;&#1077;" tab:

[ATTACH]148509[/ATTACH]

We see &#1041;&#1080;&#1083;&#1072;&#1081;&#1085; there, which is the name of most famous cellular provider here. 

Adding new connection brings this dialog:
[ATTACH]148510[/ATTACH]

In drop-down list, there are two options:

* any device
* GSM device

Selecting any of these and clicking Next brings list of countries... which I suppose is not the correct way. After selecting Russia (what else should I check?) a window with list of providers appears. Nothing about "Motokisa" - my phone and DUN connection provider.

---

### Post by aneganov on 2010-02-28
Omg I'm stupid. 
&#1041;&#1080;&#1083;&#1072;&#1081;&#1085; is the name of my DUN connection?! 
ROFL

**Walmis** - thank you!

---

