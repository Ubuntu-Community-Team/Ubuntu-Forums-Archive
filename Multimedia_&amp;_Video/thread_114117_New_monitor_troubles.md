---
title: "New monitor troubles"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by adam.mech09 on 2006-01-07
Hi

Just bought myself a new LCD monitor as a christmas present to myself.  Previously i had been running a CRT (samsung, i think) and everything was working properly, no problems at all.  After plugging in my new monitor and booting, i got as far as the login screen.  After inputting my username and password, a box popps up saying:

"Your preferred session type
GDM_failsafe.XTERM.desktop is not installed on this computer.
Do you wish tom make Default System session the sefault for future sessions?"

three options: just log in, make default, cancel.  

when i click on just log in, my monitor dies, displaying a box saying "Input not supported"

I have read on a few other posts of the same difficulty, but all of those are during install.  This setup has been working for me for the last four months on the crt.

Thanks for the help

---

### Post by adam.mech09 on 2006-01-11
fixed it...needed to change my xorg.conf file

booted up using a 5.10 live cd and copied down the xorg.conf file from there, seemed the differences were small but very monitor specific.  I couldnt determine what exactly had to do with it being an LCD versus a CRT, but making the appropriate changes fixed everything.

---

