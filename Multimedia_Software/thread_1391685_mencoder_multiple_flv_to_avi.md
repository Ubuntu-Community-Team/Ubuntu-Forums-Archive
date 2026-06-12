---
title: "mencoder multiple flv to avi"
date: 2010-01-27
forum: Multimedia Software
---

### Post by LintonHanes on 2010-01-27
I'm using mecoder to encoder multiple flv to avi, using

for file in *.flv; do mencoder -oac mp3lame -ovc lavc "$file" -o "$file".avi"; done

... and I'm getting *****.flv.avi and have to use gprename to get rid of the .flv (i've seen another nautilus-script that is doing the same thing also)

..can you please help me make this command work properly?

---

### Post by VertexPusher on 2010-01-27
```
for file in *.flv; do mencoder -oac mp3lame -ovc lavc "$file" -o "`echo $file | sed -e 's/\.flv$/\.avi/'`"; done
```

---

### Post by LintonHanes on 2010-01-27
That's great, thanx!

cd flvs/
for file in *.flv; do mencoder -oac mp3lame -ovc lavc "$file" -o [COLOR=DeepSkyBlue]**done/**[/COLOR]"`echo $file | sed -e 's/\.flv$/\.avi/'`"; done

moves them too, I'd better google sed huh?

---

### Post by andrew.46 on 2010-01-27
Hi Linton,

> **LintonHanes said:**
> 

```
for file in *.flv; do mencoder -oac mp3lame -ovc lavc "$file" -o "$file".avi"; done
```

... and I'm getting *****.flv.avi and have to use gprename to get rid of the .flv (i've seen another nautilus-script that is doing the same thing also)

An alternative is to use:

```

for f in *.flv
  do 
  mencoder -oac mp3lame -ovc lavc "$f" -o "${f%.flv}.avi"     
done

```

All the best,

Andrew

---

