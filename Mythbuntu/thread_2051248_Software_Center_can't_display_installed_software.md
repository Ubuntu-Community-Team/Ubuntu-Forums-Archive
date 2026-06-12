---
title: "Software Center can't display installed software"
date: 2012-09-01
forum: Mythbuntu
---

### Post by philled on 2012-09-01
When I run Synaptic on my Mythbuntu 12.04 machine it works fine. But when I run Software Center and click the Installed icon the little logo spins around and around for ever and never displays anything.

It's able to display software when I click the All Software button, but it never displays anything on clicking the Installed icon. 

I've run these commands:
```
$ sudo rm /var/lib/apt/lists/* -vf
$ sudo apt-get clean all
$ sudo apt-get update
```And I've tried reinstalling Software Center but nothing makes it work. Any ideas why it's misbehaving like this?

---

