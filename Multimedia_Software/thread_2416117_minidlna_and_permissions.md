---
title: "minidlna and permissions"
date: 2019-04-05
forum: Multimedia Software
---

### Post by manugutito on 2019-04-05
Hey all,

I have installed a minimal Ubuntu image in a Odroid XU4+Cloudshell and I'm trying to set up a minidlna server. The files to be shared are at /mnt/hdd, and belong to my user. I have added the user 'minidlna', which runs the server, to my user's group so that access to the files can be restricted to user and group alone. However, only 750 seems to work; as soon as the group (and thus, minidlna's user) loses execution permissions, I get the error

```
error: Media directory "V,/mnt/hdd/<...>" not accessible [Permission denied]
```

Is this normal or am I missing something? Why does minidlna need execute permissions? Is there a way to work with read only permissions?

Thanks a lot,

Manu

---

### Post by SeijiSensei on 2019-04-05
For directories, the execute permission determines whether the contents of the directory can be listed, which minidlna obviously must be able to do to build its index.

---

### Post by manugutito on 2019-04-06
I see! Thanks for your help!

---

