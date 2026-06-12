---
title: "How to upgrade from Beta to RC ?"
date: 2007-10-12
forum: Mythbuntu
---

### Post by idanag on 2007-10-12
HOw do I upgrade with APT from Beta to RC ?

could you write the console line ?

I installed the 64 Beta ISO.

10x

Idan

---

### Post by rsambuca on 2007-10-12
If you have been keeping up-to-date via the update manager, you automatically have the latest version, the Release Candidate.  To do it via the command line, just enter

sudo apt-get update
sudo apt-get upgrade

---

### Post by superm1 on 2007-10-12
You may possibly run into issues with network manager upgrading between the two - lots of instances of it running.

If so

```
rm ~/.cache -rf
```

And log out/ in

---

