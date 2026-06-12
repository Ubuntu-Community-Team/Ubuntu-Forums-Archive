---
title: "Cannot acess master user ATI Catalyst control center"
date: 2010-08-17
forum: Mythbuntu
---

### Post by HudsonHawk04 on 2010-08-17
I am using an ATI card in my mythbuntu box and the left side of my screen off by just a bit and to be honest it is beginning to be quite bothersome, the problem is I cannot access the administrative catalyst control center. it says 

"to make changes on this page, administrator acess is reguired. Re-Launch ATI catalyst control center (super-user) and enter the administrator password"

I have tried using nautilus but to no avail, am i missing something?


If I have posted this in the wrong section of the forum I am sorry, did not know if it is a mythbuntu or ubuntu problem.

---

### Post by Finlir on 2010-11-16
I don't know anything about Mythbuntu but i had the same problem in kubuntu, the solution was to type "kdesudo amdcccle" it the terminal. Ofcourse that will only work for kde..

---

### Post by LowSky on 2010-11-17
open a terminal type

```
sudo amdcccle
```

---

### Post by nickrout on 2010-11-17
No!

```
gksudo amdcccle
```

---

