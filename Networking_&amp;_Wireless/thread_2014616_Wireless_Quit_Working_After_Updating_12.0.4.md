---
title: "Wireless Quit Working After Updating 12.0.4"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by GaryH on 2012-07-02
Conditions:
Lenovo S10-3 notebook
Wireless broke after doing an update to 12.04

Symptom:
[LIST=1]
[*]In the drop down which appears after clicking the network icon, it is observed that:
*Wireless Networks* is dimmed
*wireless is disabled by a hardware switch* is dimmed
[*]I observed that the restricted broadcom driver wasn't activated
[*]I observed that activation of the driver failed and was referred to jockey.log
[*]After doing another update on 12.0.4, I got the driver to activate
[/LIST]

Workaround:
[LIST]
[*]Use Ethernet
[/LIST]

I googled for a fix a bit but couldn't find one. Does anybody have a fix?

Peace,
Gary

---

### Post by GaryH on 2012-07-02
entering "rfkill unblock all" at the Linux command prompt followed by a reboot solved it for me. :KS

---

