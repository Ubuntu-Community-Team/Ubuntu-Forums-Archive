---
title: "Console volume meter?"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by jcollins on 2007-12-23
Does anyone know of a console volume meter? It would be great if I could turn the current volume output into an integer, or something I could work with in a shell script.

---

### Post by mali2297 on 2007-12-23
To get information about PCM, use
```

amixer get PCM

```

If you want to extract the volume level (in %), you can pipe the output to grep and sed.
```

amixer get PCM | grep Left: | sed -e s/".*[0-9].\["// -e s/"%.*"//

```

---

### Post by jcollins on 2008-01-16
Many thanks for the reply but I was looking for something that would meter the volume, like with a live update of a song volume when playing. Is that possible?

---

