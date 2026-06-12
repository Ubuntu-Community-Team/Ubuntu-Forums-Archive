---
title: "append ssh keys to additional remote machines"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by crowhill on 2010-12-04
hi there!

i want to set up passphrase-less ssh login to multiple remote machines from my laptop.

i've done it for the first remote machine by typing

```
ssh-keygen -t dsa
```

(pressing "enter" for "no password") then

```
ssh-copy-id -i ~/.ssh/id_dsa.pub user@remote_1
```

now, if i want to repeat this to enable phassword-less ssh'ing to an additional remote_2 machine, **how would i go about it?** i tried to simply repeat the above but it asks me whether i want to overwrite the file id_dsa, which i used to create the key for the remote_1 machine. i type "no" and can't make any progress.

**how can i set this up?**

also, i read somewhere that simply pressing "enter" for "no password" is a bad idea. one should instead use something called an ssh agent. **how does it work? how could i achieve my setting using the ssh agent?**

thank you so much,
cheers,
crowhill.

---

### Post by crowhill on 2010-12-04
figured it out myself!

just copy the file to remote_2 as well :)

---

