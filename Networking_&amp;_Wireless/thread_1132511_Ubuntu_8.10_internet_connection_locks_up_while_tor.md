---
title: "Ubuntu 8.10 internet connection locks up while torrenting"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by Christen on 2009-04-21
Hey all, I seem to be having a strange problem. When I'm downloading a torrent (Client does not matter, I have tested with multiple clients) after a longer period of time my Internet connection completely shuts down and I am unable to do anything. This never happened when I used Windows. Does anyone know a fix for this?

Thank you in advance.

---

### Post by linuxuser21 on 2009-04-21
What kind of connection are you using?  Ex. Dial-up, DSL, ect.

---

### Post by Christen on 2009-04-21
I'm using a wireless DSL connection

---

### Post by acimmarusti on 2009-04-22
There have been some problems with wireless networks in ubuntu that cause crashes. I had that problem. I solved it by using this:

```

sudo apt-get install linux-backports-modules-intrepid

```

---

### Post by Christen on 2009-04-22
> **acimmarusti said:**
> There have been some problems with wireless networks in ubuntu that cause crashes. I had that problem. I solved it by using this:

```

sudo apt-get install linux-backports-modules-intrepid

```

Thanks for the tip. I installed that, lets see how it goes.

---

### Post by Christen on 2009-04-22
After I installed that it didn't work. It still locked up my Internet connection. Any other suggestions?

---

