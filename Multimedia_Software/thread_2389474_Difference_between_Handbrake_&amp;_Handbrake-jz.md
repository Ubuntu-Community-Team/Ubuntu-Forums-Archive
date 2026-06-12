---
title: "Difference between Handbrake &amp; Handbrake-jz"
date: 2018-04-17
forum: Multimedia Software
---

### Post by Joe_Linux on 2018-04-17
I have tried using the Google search engine to find the difference between Handbrake & Handbrake-jz (they are both available as downloads from Ubuntu Software) I have been unsuccessful so far. I am using Ubuntu 16.04. Thank you for any assistance.

---

### Post by deadflowr on 2018-04-17
One is a snap package.
And the other is not.
The software center, or whatever the name is, isn't very good at giving you useful information in 16.04.
Things have improved in the newest Ubuntu releases.

You can open a terminal and run these commands to see which version is which type of package 
```
snap find handbrake
```
and 
```
apt search handbrake
```

The major difference between them is that snap packages are designed to be easily updated to newer versions.
Where as the older apt style packages tend to be frozen at a certain version for the life of the particular release of Ubuntu you have.

---

### Post by Joe_Linux on 2018-04-19
Thanks

---

