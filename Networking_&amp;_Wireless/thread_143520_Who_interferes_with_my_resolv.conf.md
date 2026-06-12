---
title: "Who interferes with my resolv.conf?"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by Alessandro Allegri on 2006-03-12
I installed Breezy today.
Everything works fine except one little thing:
every so often I have to rewrite (or sudo cp from a backup file) the resolv.conf because something interferes with it and changes it to a DNS address that does not work (probably I have accidentally entered it somewhere during the installation process, but who knows where it is stored now). Luckily I can realize when this happens because suddenly URL's do not work anymore, so I have to do the cp and lo and behold, everything's back to normal.
If there is anybody who can suggest where I should put my hands to clean this frustrating little mess, I'll appreciate it.
Bye,
A:A

---

### Post by mzilhao on 2006-03-12
hi,

i had that problem, it was driving me nuts. 
try removing the resolvconf package. i think that was what solved it for me...

Miguel

---

### Post by Alessandro Allegri on 2006-03-13
Thank you so much. You pointed out what I think was wrong.
Actually, and funnily enough, I did not have the resolvconf package loaded. I loaded it and, as far as I can see, the problem seems solved.
Let me see if it keeps that way... 
A:A

---

