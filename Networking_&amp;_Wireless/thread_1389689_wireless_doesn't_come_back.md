---
title: "wireless doesn't come back"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Bigneil on 2010-01-24
on my laptop and on my desktop computers, if there is a prolonged break in the wireless ,ie: if the wireless hub is switched of over night but desktop computer stays on, in the morning when i switch the hub back on i have to restart ubuntu to get the wireless to work again. or on the laptop if it is put to sleep for any length of time, same thing happens. 

when clicking on the wireless icon in the upper right hand tray the options for wireless are greyed out. i don't know how to resolve this

---

### Post by garvinrick4 on 2010-01-24
> **Bigneil said:**
> on my laptop and on my desktop computers, if there is a prolonged break in the wireless ,ie: if the wireless hub is switched of over night but desktop computer stays on, in the morning when i switch the hub back on i have to restart ubuntu to get the wireless to work again. or on the laptop if it is put to sleep for any length of time, same thing happens. 

when clicking on the wireless icon in the upper right hand tray the options for wireless are greyed out. i don't know how to resolve this

Look in etc/resolv.conf  when I am on line it has my isp in there. So if I go to another isp in another location it changes to the one I am using then. If you turn off your router you are losing
your info and the router must do its thing before you get back online. Same when you are using Live CD and in chroot to a OS there is no info in etc/resolv.conf and must give the info in your Live CD etc/resolv.conf to get online. Leave router on would solve your issue everything runs through router.

---

### Post by Bigneil on 2010-01-24
thanks for your reply. i didn't understand much of what you said :( 

i used the switching of the wireless hub off, as an example, usually computer and hub are switched off at night. The more annoying issue is the laptop that when suspended for any length of time has to then be restarted to get wireless back on.  there must be a simpler solution?

---

### Post by garvinrick4 on 2010-01-25
> **Bigneil said:**
> thanks for your reply. i didn't understand much of what you said :( 

i used the switching of the wireless hub off, as an example, usually computer and hub are switched off at night. The more annoying issue is the laptop that when suspended for any length of time has to then be restarted to get wireless back on.  there must be a simpler solution?

There should be an applet in the notification area in upper right with sound and battery applet
that you should click on to pick your wireless connection that is yours. Choose it enter password
if it asks and a connection is made. 

If not right click on upper panel select Add to Panel go to Notification area select to add and it will install in upper right corner to the left of your log-in name. 

Can understand turning Machine off but why Router. Accomplishes nothing.

---

