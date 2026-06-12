---
title: "Using 2 PCs to run parallel (passwordless ssh without IP)"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by maysmech on 2011-02-18
:KS Dear experts,

I want use two computer to run OpenFOAM or Fluent software.

These two computers are connected via a cross cable.

I have access to another by "ssh maysam@192.168.1.1" OR "ssh 192.168.1.1"

The problem is i should have access to another PC by "ssh maysam-desktop" command which can run parallel. maysam-desktop is name of anothe PC and maysam is name of its user.

Any help will be appreciated.
Regards.

---

### Post by cjhabs on 2011-02-18
> **maysmech said:**
> :KS Dear experts,

I want use two computer to run OpenFOAM or Fluent software.

These two computers are connected via a cross cable.

I have access to another by "ssh maysam@192.168.1.1" OR "ssh 192.168.1.1"

The problem is i should have access to another PC by "ssh maysam-desktop" command which can run parallel. maysam-desktop is name of anothe PC and maysam is name of its user.

Any help will be appreciated.
Regards.

I am not sure I understand - if you are saying that you want to access the other PC by name rather than IP address then edit the /etc/hosts file and add an entry for the pc there.

---

