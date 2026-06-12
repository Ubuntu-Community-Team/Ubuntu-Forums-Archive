---
title: "FreeNX default key still works after generating custom key"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by midden on 2011-03-25
I installed freenx on my desktop and decided to set up a custom key following this tutorial: [https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

```
sudo dpkg-reconfigure freenx-server
```

Here I chose 'Create new custom keys' and SSH. After copying the client.id_dsa.key file to my laptop, I was able to log in no problem. However, I decided to check and used another computer (running qtnx as a client) to attempt a login with the default key.

It still worked.

Have I missed something in the fine print here? If not, is there a way to fix this behavior?

Thanks for your help.
midden

---

### Post by midden on 2011-04-05
I have now tried re-setting the key a couple of times and still have the same problem. Any thoughts, or should I move this to another forum?

---

