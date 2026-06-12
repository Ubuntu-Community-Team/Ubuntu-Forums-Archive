---
title: "Touchpad regression suddenly"
date: 2011-01-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaehny on 2011-01-08
Hi,
  I have been using NN since early December and it has been surprisingly stable (with classic desktop, Unity is unusable to me currently). With the last large group of updates late last week I have lost the touchpad edge scrolling that has worked since it was fixed with 10.10. I did have issue with this early last year too and had to do some poking. I vaguely remember it was related to ALPS touchpad then, but the software infrastructure underneath seems to have changed. I need a hint as to where to look again.

Sony Vaio VPCEB15FX 
Natty with updates as of 2PM, 8-JAN-11.

touchpad works fine except no edge scrolling in BasKet, Firefox, gedit. I have noticed that I lost my trash and my icons a couple times on restart - but a second restart fixed all that. I will try to dig up my old fix, but hope this is finally put to rest for good.

Otherwise, aside from log pauses now and again in Firefox I am shocked at how normal everything is...

UPDATED
OK I went back and created a psmouse.conf file in /etc/modprobe.d directory that has the following line in it:
options psmouse proto=imps

this effectively makes this a default device (as I recall) and gives me edge scrolling back, but it shouldn't be necessary.

---

