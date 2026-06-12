---
title: "wireless stopped &amp; no nm icon"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by vallvi on 2010-05-09
my wireless stopped conecting & Icant see the wireless icon anymore on the top bar. When I run nm-applet. it says:
** (nm-applet:1547): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

In my dual boot windows, the wireless finctions ok. 

any idea what I should do?

---

### Post by vallvi on 2010-05-09
[B]I'm getting no response at absolute beginner, so trying here:

wireless stopped & no nm icon[/B]             
                                                                my wireless  stopped conecting & Icant see the wireless icon anymore on the top  bar. When I run nm-applet. it says:
** (nm-applet:1547): WARNING **: <WARN>  constructor(): Couldn't  initialize the D-Bus manager.

In my dual boot windows, the wireless finctions ok. 

any idea what I should do?

---

### Post by vallvi on 2010-05-09
??

---

### Post by vallvi on 2010-05-10
bump?

---

### Post by vallvi on 2010-05-10
bump

---

### Post by wilee-nilee on 2010-05-10
Right click on the panel then add to then notification. If you removed this by accident you will not see ant network manager icons. AS far as no wireless you will have to more specific.

---

### Post by gradinaruvasile on 2010-05-10
> **vallvi said:**
> [B]I'm getting no response at absolute beginner, so trying here:

wireless stopped & no nm icon[/B]             
                                                                my wireless  stopped conecting & Icant see the wireless icon anymore on the top  bar. When I run nm-applet. it says:
** (nm-applet:1547): WARNING **: <WARN>  constructor(): Couldn't  initialize the D-Bus manager.

In my dual boot windows, the wireless finctions ok. 

any idea what I should do?


Reinstall network-manager is one option:

```
sudo apt-get install --reinstall network-manager-gnome
```

Other than that you can use Wicd to see if it works.

---

### Post by lisati on 2010-05-10
Threads merged. Please do not start multiple threads for the same question.

---

### Post by vallvi on 2010-05-11
hmm, I got myself in a mess, I think. I tried to reinstall the nework manager as suggested, but it didn't allow me. Then I uninstalled the network manager to install wicd, but I can't because I need internet for that.... 

Any suggestion what I do next? How do I get NM back? Or is the only option I have to clean install 10.04 again??

Any help would be appreciated. Thnx

---

### Post by vallvi on 2010-05-11
in case this helps: my wireles card is rt 2870. 

But actually, my basic question is: can I re-install an un-installed Network manager without access to Internet?

---

