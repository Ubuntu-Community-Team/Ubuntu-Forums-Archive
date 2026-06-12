---
title: "ToshSATELLITE A100 Wireless Setup?"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by Lindethiel on 2012-04-19
Am new to Ubuntu, obviously. Am trying to get this wireless running, according to most, it should work straight away, although I don't really know whether I need to grab some drivers or anything.

Here's some stats

**Make.** Toshiba Satellite A100

**Wireless.** Intel PRO/Wireless 3945ABG.

I went through the 'how to post a wireless problem thread guide,' but most of the commands seemed to result in nothing relevant in terminal, or, more likely, went over my head and I executed them wrong.

Would really appreciate your help!

---

### Post by kc1di on 2012-04-19
run the following command in a terminal and post the output:

```
dmesg | grep iwl
rfkill list
```
if the list you get say hardblock yes then look for a wireless button on the laptop.
and make sure it's turned on.

---

### Post by IWantFroyo on 2012-04-19
Also, plug in an ethernet cable and make sure you have no drivers to install (run Additional Drivers). If there's anything wireless related, install it.

---

