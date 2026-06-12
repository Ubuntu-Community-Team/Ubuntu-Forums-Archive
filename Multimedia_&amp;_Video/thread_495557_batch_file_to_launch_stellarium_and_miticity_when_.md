---
title: "batch file to launch stellarium and miticity when compiz is running"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by koshari on 2007-07-08
ok so stellarium doesnt play well with compiz.

so i are attempting to write a little script that switches the desktop manager back to metacity and then executed stellaruin when compiz is running, 

i started with this basic script that is touch and go, works sometimes and not others,

```
#! /bin/bash
metacity --replace
stellarium
fi
```

i think i need something like 

```
if desktop=compiz
metacity --replace
stellarium
else
stellarium
fi
```

sometimes the batch will change compiz to metacity but doesnt open stellaruium and site in the process running list as sleeping, and then if you select compiz back it leunches stellarium causing havoc.

does anyone know how i can use the if condition to see if compiz is running so satisfy the following conditions?

---

