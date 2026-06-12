---
title: "Script name in inetref"
date: 2014-08-06
forum: Mythbuntu
---

### Post by jack35 on 2014-08-06
MythTV is not displaying Cover art, Fan art or Banners in recorded programs. I think the problem is with the way inetref is being populated in the recorded table.

```

[FONT=fixedsys][SIZE=2]mysql> select title,subtitle,inetref from recorded where inetref regexp "......py_";
+---------------+--------------------------------------------------+-----------------+
| title         | subtitle                                         | inetref         |
+---------------+--------------------------------------------------+-----------------+
| Peter Gunn    | Kill From Nowhere                                | ttvdb.py_76506  |
| Peter Gunn    | Vendetta                                         | ttvdb.py_76506  |
| NOVA          | Australia's First 4 Billion Years: Monsters      | ttvdb.py_76119  |
| NOVA          | Australia's First 4 Billion Years: Life Explodes | ttvdb.py_76119  |
| Star Trek     | That Which Survives                              | ttvdb.py_77526  |
| The Blacklist | Mako Tanida                                      | ttvdb.py_266189 |
| The Blacklist | Ivan                                             | ttvdb.py_266189 |
| Frontline     | Losing Iraq                                      | ttvdb.py_80646  |
| Peter Gunn    | Bullet for a Badge                               | ttvdb.py_76506  |
| Frontline     | Separate and Unequal                             | ttvdb.py_80646  |
+---------------+--------------------------------------------------+-----------------+
10 rows in set (0.00 sec)
[/SIZE][/FONT]
```

Has anyone else seen this?

Thanks,

Jack

---

### Post by tgm4883 on 2014-08-07
> **jack35 said:**
> MythTV is not displaying Cover art, Fan art or Banners in recorded programs. I think the problem is with the way inetref is being populated in the recorded table.

```

[FONT=fixedsys][SIZE=2]mysql> select title,subtitle,inetref from recorded where inetref regexp "......py_";
+---------------+--------------------------------------------------+-----------------+
| title         | subtitle                                         | inetref         |
+---------------+--------------------------------------------------+-----------------+
| Peter Gunn    | Kill From Nowhere                                | ttvdb.py_76506  |
| Peter Gunn    | Vendetta                                         | ttvdb.py_76506  |
| NOVA          | Australia's First 4 Billion Years: Monsters      | ttvdb.py_76119  |
| NOVA          | Australia's First 4 Billion Years: Life Explodes | ttvdb.py_76119  |
| Star Trek     | That Which Survives                              | ttvdb.py_77526  |
| The Blacklist | Mako Tanida                                      | ttvdb.py_266189 |
| The Blacklist | Ivan                                             | ttvdb.py_266189 |
| Frontline     | Losing Iraq                                      | ttvdb.py_80646  |
| Peter Gunn    | Bullet for a Badge                               | ttvdb.py_76506  |
| Frontline     | Separate and Unequal                             | ttvdb.py_80646  |
+---------------+--------------------------------------------------+-----------------+
10 rows in set (0.00 sec)
[/SIZE][/FONT]
```

Has anyone else seen this?

Thanks,

Jack

That is actually how it is done now, to avoid grabbing artwork from the wrong grabber (which in the past has done some pretty bad things).

---

### Post by jack35 on 2014-08-08
Okay, thanks...

---

