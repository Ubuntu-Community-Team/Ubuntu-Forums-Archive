---
title: "update-manager -d and do-release-upgrade -d fail to find natty"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by amp_man on 2011-04-14
As the title says, I've got a week old install of Maverick that I'm trying to upgrade to Natty, but neither update-manager -d nor do-release-upgrade -d seem to find the new release. Neither has any errors, just doesn't find the new release.

```
Oz@TinMan:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found
```

---

### Post by dino99 on 2011-04-14
dont use these commands till final release, instead open synaptic sources.list to change repo from maverick to natty, and of course deactivate all third parties before updating/upgrading

---

### Post by amp_man on 2011-04-14
> **dino99 said:**
> dont use these commands till final release, instead open synaptic sources.list to change repo from maverick to natty, and of course deactivate all third parties before updating/upgrading

Huh? It shows up fine on my laptop, also running 10.10, but was formerly running 10.04.

EDIT: ok, never mind, it's working on the test system now as well.

---

### Post by coffeecat on 2011-04-14
I updated a Maverick installation to Natty a few days ago with:

```
sudo apt-get update
update-manager -d -c
```I'm not sure whether you need to do the apt-get update first, but try it anyway. The -c option shouldn't really be necessary for upgrading to Natty at the moment, but...

---

### Post by Arand on 2011-04-14
```
sudo do-release-upgrade -d
update-manager -d
``` Either are indeed the _correct_ methods of upgrading to a development release, whereas editing the sources.list is not recommended for ubuntu.

- arand

---

