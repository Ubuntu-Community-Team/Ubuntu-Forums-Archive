---
title: "RDesktop and the Dual Monitor Dilemma"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by mister_doctor on 2009-11-04
I haven't found a thread for this yet, so I'm starting one.

I have a standard dual monitor set up between my laptop and a 2nd monitor. Since I use Linux at home but Windows at work, I use rdesktop (thru tsclient frontend) to connect to the office.

When I run rdesktop in fullscreen mode, it spans across both screens. Normal behaviour for the M$ tsclient is to occupy only one screen. I am looking for a way to replicate this with rdesktop.

My current workaround is to set rdesktop to display at a resolution just slightly smaller then the external monitor.

Is there a better solution then this? I'm comfortable with doing near-anything on Linux other then re-compiling from source, but I'd be willing to experiment if it means that I get what I want.

Thanks in advance.

---

### Post by danieldcl on 2009-11-06
I had the same problem.
The solution I have found is using the option -D "hide window manager decorations".

I open a terminal window in the second monitor and type:
rdesktop -g 1024x768 -D myserverIP

---

