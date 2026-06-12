---
title: "vnstat PHP Frontend Start date offset help"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by davidm84 on 2009-11-30
Hey everyone.

Sorry if this is in the wrong section. Couldn't find any obvious place to put this.

So what I'd like to do is monitor my bandwidth. I'm using a Ubuntu 9.10 "Desktop" box, connected to a E220 (Wireless Broadband) and the NIC connected to a Switch/WAP. So it's all working fine with vnstat and the PHP Frontend to view bandwidth. 

All is good and dandy, but the vnstat PHP Frontend only counts WHOLE hours, WHOLE days and WHOLE months (i.e. 1st till 31st). My ISP has us on a offbeat period (i.e. 26th till 25th of the next month). 

What I'd like to find out is has anyone found a bandwidth monitor or changed one that will offset the month start date with an interface like the PHP Frontend. I tried to do this by editing the PHP Frontend but just got lost (almost but didn't work).

I currently use [iiQuota]("http://www.southfreo.com/iiquota/Home.html") to check the usage via my IPhone (wanting Android!!!!) but would like something that uses local stats to find what my system says, not what they "think". I trust them but not that much. Errors do happen.

Thanks for your time:popcorn:

---

### Post by vinodhkumarsampath on 2011-10-30
Works good for me, my Internet plan has free download from 2am to 8am  and remaining time limited usage of 1GB / month. I tried changing the  source code to suit my preference so not to include data transfer during  2am to 8am, but failed. could anyone help me sorting out the issue pl..:(
vinodh kumar sampath

---

