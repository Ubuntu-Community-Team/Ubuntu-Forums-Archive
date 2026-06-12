---
title: "gksudo nautilus errors"
date: 2010-08-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-08-01
I am getting the following errors when starting nautilus as root. Nautilus starts fine but get about 20 of the errors listed below. Anyone else seeing this?

```

bill@billsim-1010-32:~$ gksudo nautilus
Initializing nautilus-gdu extension

(nautilus:2248): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:2248): GLib-GObject-WARNING **: invalid (NULL) pointer instance


```

Bill

---

### Post by ronacc on 2010-08-01
yes its been doing that for a while , doesn't seem to cause any problem for me .

---

### Post by draki on 2010-08-03
Me too - but as mentioned doesn't *seem *to be doing any harm

---

### Post by endotherm on 2010-08-03
well the nautilus-GDU extension is for showing the properties of a disk
[https://fedoraproject.org/w/index.php?title=Image:Nautilus-gdu.png&diff=0&oldid=prev](https://fedoraproject.org/w/index.php?title=Image:Nautilus-gdu.png&diff=0&oldid=prev)
so is not a huge loss if it continues to fail. 
several people with simmialr issues suggested deleting config files out of your home (.gvfs/metadata, .gconf/nautilus, etc) but there didn't seem to be any rhyme or reason to their methodology so I am loathe to suggest it.

---

### Post by garvinrick4 on 2010-08-04
I seem to remember reading more than once it is a bug that is at a low importance level since it is harmless. When I find where I saved it I will post.

---

