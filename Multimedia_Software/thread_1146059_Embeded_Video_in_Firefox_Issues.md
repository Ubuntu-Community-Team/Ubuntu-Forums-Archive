---
title: "Embeded Video in Firefox Issues"
date: 2009-05-02
forum: Multimedia Software
---

### Post by risknothin on 2009-05-02
Since installing ubuntu 9.04 o have had issues playing emeded video. it appears that flash on sites like espn does not even load, on other sites there is a huge play icon but nothing happeneds

iv installed every plugin for firefox video that i can find but still has issues w/ some sites

---

### Post by xc3RnbFO8P on 2009-05-02
Try **Epiphany-Gecko** Browser in Synaptic Package Manager.

---

### Post by pastalavista on 2009-05-02
Are you running Ad Block PLus? Many sites won't let you watch video unless you allow them to run their ads. Disable it on those sites and reload the page, see if that does it

---

### Post by risknothin on 2009-05-02
I like firefox and it was working before i formated and updated to 9.04

i tried disabling ad-block completely and restarting firefox but it did not fix the issue

---

### Post by gandaran on 2009-05-02
> **risknothin said:**
> Since installing ubuntu 9.04 o have had issues playing emeded video. it appears that flash on sites like espn does not even load, on other sites there is a huge play icon but nothing happeneds

iv installed every plugin for firefox video that i can find but still has issues w/ some sites

the huge play icon is swfdec flash, remove this flash package (swfdec-mozilla) and keep only adobe flash installed.

---

### Post by risknothin on 2009-05-02
i disabled shockwave flash and installed adobe flash but that didnt help it seems to have done nothing as adobe flash is not listed in my firefox plugins

---

### Post by gandaran on 2009-05-02
> **risknothin said:**
> i disabled shockwave flash and installed adobe flash but that didnt help it seems to have done nothing as adobe flash is not listed in my firefox plugins
look don't disable shockwave flash, only make sure you don't have swfdec or gnash installed, these two open source flash packages if any installed won't let firefox use adobe flash, install only the **flashplugin-installer** (adobe flash) from apt-get or synaptic!

---

### Post by risknothin on 2009-05-02
That worked thank you for your help

---

