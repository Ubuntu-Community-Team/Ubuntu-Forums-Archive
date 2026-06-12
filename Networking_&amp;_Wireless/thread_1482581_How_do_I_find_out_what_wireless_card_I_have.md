---
title: "How do I find out what wireless card I have?"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by thejakeman on 2010-05-13
I'm seriously stuck here. All I know is that I have a Dell Inspiron laptop purchased about a year and 5 months ago.
Thanks in advance!

---

### Post by howefield on 2010-05-13
Try the terminal command 

```
lspci
```

Does that show you anything ?

---

### Post by mikewhatever on 2010-05-13
No sweat,
```
lspci | grep -i network
```
If the card is recognized, it should show in the output.

---

