---
title: "Can't use aptitude"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2010-10-04
I have always updated via terminal using aptitude.
Using a fresh install, I am getting this messege:

```
dougie@Dougie64Beta:~$ sudo aptitude update
[sudo] password for dougie: 
sudo: aptitude: command not found
```

Is this a change and I now need to use apt-get update?

---

### Post by drmartens on 2010-10-04
Maybe it was removed from the defaults, just install it with apt-get...

---

### Post by davrosuk on 2010-10-04
aptitude has been removed from the distro. Its deprecated and you need to use apt-get instead.

---

### Post by 23meg on 2010-10-04
> **davrosuk said:**
> aptitude has been removed from the distro. Its deprecated and you need to use apt-get instead.

That's not true; aptitude has simply been removed from the desktop variant by default, where you can still install and use it.

---

### Post by DougieFresh4U on 2010-10-04
> **davrosuk said:**
> aptitude has been removed from the distro. Its deprecated and you need to use apt-get instead.

I know that **aptitude** and **apt-get** have been discussed ad nauseam, and I had thought that aptitude was the better to use and please I do not want to have an **'apt-get <> aptitude'** debate here, just was kind of thrown off a bit when I couldn't use **aptitude**.

---

### Post by VMC on 2010-10-04
> **DougieFresh4U said:**
> I know that **aptitude** and **apt-get** have been discussed ad nauseam, and I had thought that aptitude was the better to use and please I do not want to have an **'apt-get <> aptitude'** debate here, just was kind of thrown off a bit when I couldn't use **aptitude**.

I felt the same way, but decided to learn apt-get, apt-cache and all its relatives, since its there now and Aptitude is not. I also preferred Aptitude, but in the end I just moved on. I also realize that its just an install away, may times I want to use APT without the need to install something else.

---

### Post by cariboo on 2010-10-04
I still install aptitude, it's more of a personal preference.

---

