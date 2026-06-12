---
title: "Frostwire - needs JRE 1.5"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by geovino on 2007-11-01
I just installed Frostwire in my new Gutsy install. I've used it before in Feisty, but this time when I tried to open it from the menu it didn't open. Then I tried typing frostwire in the terminal. It said that I needed Java JRE 1.5 or newer. Where do you download this?

---

### Post by haldean on 2007-11-01
```
sudo apt-get install sun-java5-jre
``` should do the trick!

---

### Post by taurus on 2007-11-01
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by geovino on 2007-11-01
> **haldean said:**
> ```
sudo apt-get install sun-java5-jre
``` should do the trick!

Indeed! It's working now. :)

---

