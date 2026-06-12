---
title: "change sound with two sound cards"
date: 2009-11-13
forum: Multimedia Software
---

### Post by davidtuti on 2009-11-13
Hi,

Recently I've installed Kubuntu Karmic, everything it's ok. Before I use the next command to change between the two cards:

asoundconf set-default-card Intel or asoundconf set-default-card Live


But now, If I execute this it says me:

asoundconf: command not found

Any help please?
Many thanks and sorry for my english!

---

### Post by markbuntu on 2009-11-13
Most likely asoundconf is not installed on your system. You can change the default sound card in System Settings.

---

### Post by davidtuti on 2009-11-13
> **markbuntu said:**
> Most likely asoundconf is not installed on your system. You can change the default sound card in System Settings.

Thanks, but I need to change the default card in a shell-script.
Any help?

---

### Post by markbuntu on 2009-11-13
You could get asoundconf from the repos.

---

### Post by davidtuti on 2009-11-14
> **markbuntu said:**
> You could get asoundconf from the repos.

In synaptic I only see "asoundconf-gtk". If I insall this, I have the same problem.
Any help? Please
Thanks.

---

