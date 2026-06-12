---
title: "Intel ProSet Wireless 3945 &amp; 9.04 Problem fixed"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Amber_Man on 2009-06-14
I have a Dell XPS 1210 notebook with and Intel pro-set wireless 3945 adapter.  After recently upgrading to Ubuntu 9.04 my network connection kept randomly disconnecting and sometimes I was unable to reconnect at all.

I was unable to find a fix anywhere, I even un-installed network manager and tried using wicd to only experience the same problem.

To fix the problem I uninstalled network manager and installed (via synaptic) two packages "connman" and "connman gnome"

Problem solved.

---

### Post by guitodd on 2009-06-15
I'm having the same issue with my Dell e1505n and the 3945 card.  I've read hundreds of post and followed Intels bug reports through to no solid solid solutions.  Seems to be many variations of the same issue.  

I'm going to try this when I get home!!  I'm hopeful since you are on a Dell too.  Thanks!!!

---

### Post by guitodd on 2009-06-18
Ok.. I don't appear to have the connman packages in Synaptic.  I did a search and tried adding the repo links.. but synaptic looks for an APT line and won't take the address.  I'm a bit of a noob here.

How would I add the repo?

---

