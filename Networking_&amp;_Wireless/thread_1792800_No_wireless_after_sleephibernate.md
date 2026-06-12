---
title: "No wireless after sleep/hibernate"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by derekreilly on 2011-06-28
Hi,

When I put Kubuntu into sleep or hibernate, most of the time when I come back, wireless is off and I cannot activate it again. The same thing happened with a previous Ubuntu installation.


I googled around and found a fix, editing  /etc/default/acpi-support. I needed to add networking to STOP_SERVICES so that my wireless will stop and restart when I come in and out of sleep or hibernate as per below, but it hasn't helped. Does anyone have any other ideas? Derek.

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

---

### Post by derekreilly on 2011-06-29
This morning the system woke up and wireless was available. How strange. :confused:

---

### Post by derekreilly on 2011-06-29
and now it doesn't work again, does anyone have any ideas?

---

### Post by brpylko on 2012-01-23
I have had a similar problem, I would run ```
service --status-all
``` from the terminal and add all of the networking services to the STOP_SERVICES list.

---

