---
title: "Ubuntu, Flash, and Transparency Issues"
date: 2008-09-30
forum: Multimedia Software
---

### Post by LeonBlade on 2008-09-30
Hello everyone,

I'm sure you've seen this problem before and probably are experiencing it yourself or once have before.

Well, on the LittleBigPlanet News site, the header has transparency covering the top of the site on each page, but the transparency isn't clear, it's white.

Right now I can address this issue using a JavaScript bookmark I setup...
```
javascript:document.getElementById("FLASHCONTAINER").innerHTML="";void(0);
```

Now I really don't want to have to deal with this problem, if there is any way I can fix this transparency problem, or even how I can configure Firebug to automatically call this JavaScript on the site, that would be great.

Thanks, and hope to hear back soon,
--LeonBlade

---

### Post by Crafty Kisses on 2008-09-30
What are the results of this command?
```
java --version
```

---

### Post by LeonBlade on 2008-10-14
Sorry for the delayed response.
```
java --version
```
Didn't work, but...
```
java -version
```
...did, and here are my results:
```

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

---

