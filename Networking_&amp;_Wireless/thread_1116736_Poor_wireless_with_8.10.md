---
title: "Poor wireless with 8.10"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by lloydsharons on 2009-04-05
Love 8.10 except wireless reception which is mediocer at best.  My Belkin pcma card f5d7010 version 3001 worked well with 7,10 but gives variable signal strength on 8.10.  I downloaded a new ralink driver but now need to know how to install it. Help would be appreciated.

---

### Post by chessnerd on 2009-04-05
What type of file is the driver? I recently installed a .run driver online and it wouldn't work so I had to convert it to an executable for it to work. If this is the case, try this command:
```
chmod +x (the path for the driver i.e. /home/lloydsharons/ralinkdriver.run)
```
After that you should be able to run the program.
If this isn't the case, I'm not the best guy to ask (I just started using Linux two weeks ago).

---

