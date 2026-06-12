---
title: "can't update"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dinamic1 on 2011-03-22
i'm on 11.04 and partial update freezes [http://i.imgur.com/NBkjC.png](http://i.imgur.com/NBkjC.png)
:(

---

### Post by cariboo on 2011-03-22
I'd suggest you read the [sticky]("http://ubuntuforums.org/showthread.php?t=1641400") about partial upgrades.

To solve your problem, you can install aptitude and use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

or Use Synaptic. which will show you which packages are the problem.

---

### Post by dinamic1 on 2011-03-22
> **cariboo907 said:**
> I'd suggest you read the [sticky]("http://ubuntuforums.org/showthread.php?t=1641400") about partial upgrades.

To solve your problem, you can install aptitude and use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```or Use Synaptic. which will show you which packages are the problem.
  
thanks, i've managed to update from terminal ):P

---

