---
title: "Why can't i install compiz-fusion-plugins-extra?"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-09-03
When i check the compiz ppa i see that everything is succsefully built but when i try to install compiz-fusion-plugins-extra i get this:

compiz-fusion-plugins-extra:
 Depends: compiz-core-abiversion-20091102

Thanks in advance.

---

### Post by mc4man on 2010-09-03
You may wish to link which ppa you're using, I'd take a guess that maybe the ...extra package is for lucid, not maverick.

---

### Post by ktp on 2010-09-03
> **aviramof said:**
> When i check the compiz ppa i see that everything is succsefully built but when i try to install compiz-fusion-plugins-extra i get this:

compiz-fusion-plugins-extra:
 Depends: compiz-core-abiversion-20091102

Thanks in advance.

which ppa?

---

### Post by aviramof on 2010-09-04
I wasn't aware that there is more then one ppa for compiz for maverick
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

---

### Post by ronacc on 2010-09-04
if you use the filter on that page and set it to maverick , you will see only 2 packages apply to maverick .

```
 	1:0.9.0-0ubuntu1~ppawithoutdecoration1
        0.9.0-0ubuntu1~ppa4 
```

---

### Post by karmila on 2010-09-04
> **ronacc said:**
> if you use the filter on that page and set it to maverick , you will see only 2 packages apply to maverick .

```
     1:0.9.0-0ubuntu1~ppawithoutdecoration1
        0.9.0-0ubuntu1~ppa4 
```

So, is it possible new compiz (0.9.0) do not support extra-plugins yet?

---

### Post by plun on 2010-09-04
> **aviramof said:**
> When i check the compiz ppa i see that everything is succsefully built but when i try to install compiz-fusion-plugins-extra i get this:

compiz-fusion-plugins-extra:
 Depends: compiz-core-abiversion-20091102

Thanks in advance.

Well, I have no idea why you are using a PPA for something which already is within Mavericks repo.... ???

---

### Post by aviramof on 2010-09-04
Because what in maverick repo is 0.8.4 or 0.8.6 not 0.9.0

---

### Post by plun on 2010-09-04
> **aviramof said:**
> Because what in maverick repo is 0.8.4 or 0.8.6 not 0.9.0

Ok......

I am using the Soreau script for building 0.9.

```
git clone git://anongit.compiz.org/users/soreau/scripts && ./scripts/build_compiz++

```

There are several bugs with 0.9 and with the script 0.9 will be installed as a parallel install.... much better then to use a broken ppa...;)

---

### Post by smoosh on 2010-09-29
Sooo, used that script to install Compiz 0.9, but when I try to start it using: ```
PREFIX=/opt/compiz; killall gtk-window-decorator; killall kde4-window-decorator; killall emerald; $PREFIX/bin/gtk-window-decorator & LD_LIBRARY_PATH=$PREFIX/lib/ $PREFIX/bin/compiz --replace ccp & disown
```

I get no windows decorations.

Any ideas?

---

