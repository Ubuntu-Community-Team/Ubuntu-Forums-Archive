---
title: "Problem Installing Lynx"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by niewski on 2011-02-01
I'm running Ubuntu Server 10.10 through VMware Workstation and when I use "sudo apt-get install lynx" I get an error saying "Package 'lynx' has no installation candidate"

Does anyone know how I can fix this?

---

### Post by wojox on 2011-02-01
Try:

```
sudo apt-get update && sudo apt-get install lynx-cur
```

---

### Post by niewski on 2011-02-01
When I do the update I get an error saying "Some index files have failed to download, they have been ignored, or old ones used instead."
I tried the "apt-get install lynx-cur" anyway and it couldn't find the package.
I checked my connection by pinging google.com and everything seemed fine.

---

### Post by wojox on 2011-02-01
What do your sources list look like?

```
cat /etc/apt/sources.list
```

---

### Post by wojox on 2011-02-01
w3m is installed by default you know.

```
w3m -v http://www.google.com
```

---

### Post by niewski on 2011-02-01
Okay so I tried going to google using w3m and I couldn't load the page, so I guess my problem is different than what I originally thought.

---

