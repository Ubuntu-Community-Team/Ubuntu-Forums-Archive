---
title: "update manager"
date: 2010-10-14
forum: Multimedia Software
---

### Post by heracles on 2010-10-14
Update manager has stopped working under Maverick. Is it best to format disk and reload the system anew or does anybody know of a fix?

---

### Post by garvinrick4 on 2010-10-14
> **heracles said:**
> Update manager has stopped working under Maverick. Is it best to format disk and reload the system anew or does anybody know of a fix?
There is an update out for that if you have not got it yet, maybe will help. Open a terminal and copy and paste; See if it is there as an upgrade.
```
sudo apt-get update && sudo apt-get dist-upgrade
```
If not use;
```
sudo apt-get remove update-manager
```
```
sudo apt-get remove update-manager-core
```
```
sudo apt-get clean
```
```
sudo apt-get install update-manager update-manager-core
```

That will remove it and clean out cache of packages and go out and fetch a new one from repository.

---

### Post by heracles on 2010-10-15
Thank you for such precise instructions. After following them it seems the update has worked .

---

