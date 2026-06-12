---
title: "Nova-T-500 remote mixing button codes"
date: 2009-11-08
forum: Mythbuntu
---

### Post by avelach on 2009-11-08
Hi all,

I've succesfully installed Mythbuntu 9.10 using a Hauppauge Nova-T-500 and everything seems to be running fine except for a strange remote controller (silver top, black bottom) behavior:

When I press some buttons and keep them hold down most of the keycodes are right but now and then they match other keycodes. For instance, pressing Volume Up button work right half of the time but then it spits some other button code (i.e. Skip Back). This happens mostly with a bunch of buttons and it is a very annoying behavior and can be seen using irw. I experiment the same behavior using two identical remotes I own.

I tried several well-known config files from MythTV and LinuxTV wikis and even wrote my own config using irrecord to no avail. I suspect it is related to some parameters like toggle_bit_mask or similar but I do not understand them well enough to know what could be wrong.

Any clues are welcome!

---

### Post by avelach on 2009-12-13
At last it was a faulty/wrong IR sensor wire. Full story:

[http://www.mythtvtalk.com/forum/installation-issues/12208-nova-t-500-remote-mixes-button-actions.html](http://www.mythtvtalk.com/forum/installation-issues/12208-nova-t-500-remote-mixes-button-actions.html)

---

