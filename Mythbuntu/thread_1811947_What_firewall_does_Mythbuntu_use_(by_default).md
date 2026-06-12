---
title: "What firewall does Mythbuntu use (by default)?"
date: 2011-07-25
forum: Mythbuntu
---

### Post by bs27975 on 2011-07-25
I have a computer on order - I expect to run Kubuntu LTS + Mythbuntu on it. [If you wish to debate the wisdom of that, start a different thread, please.]

In prep for this computer, I'm going to read up on firewalls (again).

What firewall does Mythbuntu use by default?

If the answer is 'none', that's fine. If so, then what is the usual underlying / default firewall of k/ubuntu? Again, an answer of none is fine.

If the answer is 'iptables', remind me please ... are there not things like shorewall, which sit on top of iptables (or, rather, provide a 'gui' interface to iptables)? Are there others? Are there favourites?

Also, anyone have (probably not Mythbuntu) links to setting up such firewalls / best practices, etc.?

Thanks very kindly.

---

### Post by nickrout on 2011-07-25
by default none.

mythtv is not designed to be secure. It is not designed to front onto the internet. put it behind a firewall machine rather than running a firewall on it.

---

### Post by bs27975 on 2011-07-25
> **nickrout said:**
> by default none.

And on an underlying k/ubuntu?

> **nickrout said:**
> mythtv is not designed to be secure. It is not designed to front onto the internet. put it behind a firewall machine rather than running a firewall on it.

Can you speak to why not run a firewall on it?
(I presume the easiest way to answer that is by pointing me towards links that discuss it, rather than rehashing it here.)

[Part of where I'm coming from: (i) I do not need YAMTM - Yet Another Machine To Maintain; (ii) No reasonably / cheaply priced router exists [aside from OpenWRT] with the flexibility I'm looking for, such as the port redirecting or access lists my PIX 501 has; (iii) there seems to be some synergy by having the app and firewall on one box, instead of trying to coordinate two boxes.]

---

