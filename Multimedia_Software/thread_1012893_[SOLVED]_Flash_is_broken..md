---
title: "[SOLVED] Flash is broken."
date: 2008-12-16
forum: Multimedia Software
---

### Post by Cadeyrn on 2008-12-16
So, I installed the newest version of Flash into my web browsers through Add/Remove Programs, and yet when I go into Tools>Add-ons>Plugins, Flash isn't listed as an installed plugin. Plus, when I go to a site that has Flash, the Flash doesn't play, and then when I click the Install Missing Plugins button, or get Linux Flash off the Adobe site, both downloads say Firefox already has flash installed. What the crap???

---

### Post by securitynut on 2008-12-16
I too am having the same problem with flash. I've gotten it from adobe's site, synaptic, and firefox (install missing plugins), all with no success. It says its installed but when i try to play a youtube vid it says that i still need flash.

---

### Post by wolfen69 on 2008-12-16
did you restart firefox?

---

### Post by wolfen69 on 2008-12-16
if restarting firefox isn't the issue, (i had to ask) let's start over from scratch. go to system>administration>synaptic package manager and completely remove flash. then go to applications>accessories>terminal and type in:```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb for ubuntu and click to install. restart firefox if open.

---

### Post by Cadeyrn on 2008-12-16
Thanks. it works!

---

### Post by binbin on 2008-12-16
Wolfen69,

Thank you so much! This problem has been bothering me for weeks. And it's completely resolved.

This place rock!!!:guitar:

---

### Post by pandamoniumcomputers on 2008-12-18
Hey Wolfen good looking out man this flash issue has been a pain for quite some time.

---

