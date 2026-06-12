---
title: "iptables not clearing MASQUERADE"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-05-29
If I add a rule to iptables:
```

iptables -t nat -A POSTROUTING -o eth4 -j MASQUERADE

```

it does not get removed when I try to clear all the rules:

```

iptables -Z
iptables -F
iptables -X

```

How do I clear POSTROUTING?

---

### Post by JKyleOKC on 2011-05-29
Have you tried ```
iptables -t nat -F
```If you don't specify the table, it defaults to "filter" only.

---

### Post by Lars Noodén on 2011-05-29
That did it.  Thanks.

(PS. Which painting is your avatar from?)

---

### Post by JKyleOKC on 2011-05-29
That's no painting; it's a freeze frame from a video of me at the keyboard, that a friend made some 15 years ago while we were developing a video-over-cellphone application for use by storm chasers at a local TV station. I liked it so much that I've used it as my avatar ever since.

---

### Post by Lars Noodén on 2011-05-29
Very cool provenance.

---

