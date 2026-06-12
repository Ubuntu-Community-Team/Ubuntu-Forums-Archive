---
title: "Unable to join wireless in Jaunty"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by pramathesh on 2009-05-27
Hi guys recently formatted my IBM T40p to Jaunty. But as of now I'm not able to join the w/l n/w at home which happens to be WPA2 secure. If I disable security it has no issues to join the same. It worked fine on 8.10. Any help?

---

### Post by pramathesh on 2009-05-27
:o

---

### Post by pramathesh on 2009-05-28
bump........

---

### Post by t0mppa on 2009-05-28
Please don't bump your thread on an hourly basis. People on these forums come from all over the globe and being on different timezones, they're online at different times of the day for you. Also, none of us sit here constantly monitoring the stream of new posts, since we don't get payed to do this.

And to further your cause, post the output of the following commands from the terminal, so that people know what wireless card, chipset & drivers you have and then can better help you with your problem: ```
lspci
lshw -C network
```

For instance, some older Windows drivers used with NDISWrapper simply don't know how to handle WPA2, since it wasn't around when they were created.

Also, [here]("http://ubuntuforums.org/showthread.php?t=571188")'s a thread where you can try different approaches on the encryptions manually, to limit the problem to just WPA2 for instance or to prove that none of the encryption options work, and kevdog tends to give devoted support to each individuals issues.

---

