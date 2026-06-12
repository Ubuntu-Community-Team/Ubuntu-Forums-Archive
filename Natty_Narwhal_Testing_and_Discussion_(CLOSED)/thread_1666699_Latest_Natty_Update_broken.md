---
title: "Latest Natty Update broken"
date: 2011-01-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-01-14
Latest update gives me

> The following packages have unmet dependencies.
 unity : Depends: compiz-core-abiversion-20101111 but it is not installable
E: Broken packages
which means that either compiz will not run or 'ubuntu-desktop unity' will not install.

---

### Post by kyleabaker on 2011-01-14
ugly messages, glad I waited. :/

Thanks for the notice!

---

### Post by frederik.nnaji on 2011-01-14
> **Peter09 said:**
> Latest update gives me


which means that either compiz will not run or 'ubuntu-desktop unity' will not install.

yeah, this hurts.

a workaround, anyone?

---

### Post by jfernyhough on 2011-01-14
You just have to be patient and wait (I know it's hard ;)) This kind of thing happens regularly as packages are updated and dependencies are broken.

---

### Post by jfernyhough on 2011-01-14
--double post, weird timeouts when submitting form data...

---

### Post by cariboo on 2011-01-14
When it looks like important packages will be removed, I always us aptitude:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by jerrylamos on 2011-01-14
> **frederik.nnaji said:**
> yeah, this hurts.

a workaround, anyone?
Frederick, 

There's a new login option for "classic no effects".  This doesn't use Compiz.  That presumes you can get to login...

I've seen some command lines that allow changing the login option from say the recovery mode boot prompt, but I don't know which thread that is in.

Jerry

---

