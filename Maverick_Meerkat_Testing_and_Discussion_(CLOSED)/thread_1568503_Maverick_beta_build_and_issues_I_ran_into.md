---
title: "Maverick beta build and issues I ran into"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VastOne on 2010-09-05
For information to others who may encounter this, I wanted share these issues and fixes

I did a complete install of the beta on one of my main machines different than those of my test environment. 

I have a seperate /Home  partition.  I ran into to pulseaudio daemon failing to initialize and the only way to resolve was to remove ./pulse from my /Home partition and reinstall.

Compiz beta does not work with 10.10 beta but Compiz stable does.

gdebi is completely gone and without a clear message that it is.  I did install it via synaptic but it crashes 99% of the time using the gui. dpkg -i appname.deb is the only way I got several to work (Ranch Hand I hear ya, this should be the way for every deb!)

I do not have alt tab function any more to switch between apps

Edit - Alt tab was not working due to a Compiz issue, resolved.

Spent the better part of yesterday chasing these down but all in all, 10.10 beta is pretty stable.

---

### Post by mc4man on 2010-09-05
> gdebi is completely gone and without a clear message that it is
As mentioned elsewhere there is a new r. click option on .debs to install with software center that works fine and will install add. deps if needed and available
(can also be added to the browser pop up for .debs accessed, installed directly from  online

Whether gbebi-gtk displays details and or errors is now controlled by the setting in synaptic as to the 'automatically close....' progress pop up

(a rather strange 'fix' to non persistent checkbox in previous gdebi-gtk progress window

---

### Post by VastOne on 2010-09-05
> **mc4man said:**
> As mentioned elsewhere there is a new r. click option on .debs to install with software center that works fine and will install add. deps if needed and available
(can also be added to the browser pop up for .debs accessed, installed directly from  online

Whether gbebi-gtk displays details and or errors is now controlled by the setting in synaptic as to the 'automatically close....' progress pop up

(a rather strange 'fix' to non persistent checkbox in previous gdebi-gtk progress window

I found out about these after the fact.  What needs to happen eventually is when opening by dbl click, Software Center should be the choice to Open with by default. And yes it is a strange fix.

---

### Post by al090187 on 2010-09-12
I'm still having the Alt + Tab problems. How can I sort Compiz out?

Thanks.

---

### Post by VastOne on 2010-09-12
> **al090187 said:**
> I'm still having the Alt + Tab problems. How can I sort Compiz out?

Thanks.

For me it was Compiz Config Settings Manager - Window Management - and turned off Application Switcher

---

