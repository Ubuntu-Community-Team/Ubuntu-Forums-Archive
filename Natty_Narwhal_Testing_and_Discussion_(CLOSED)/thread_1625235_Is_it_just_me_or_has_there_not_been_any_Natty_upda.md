---
title: "Is it just me or has there not been any Natty updates recently?"
date: 2010-11-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-11-18
I haven't been getting any updates in the past few days, plus when I open terminal and update sources, it runs through a few of them and then says:

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.lzma  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.lzma  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Can anyone help me?

---

### Post by chrisccoulson on 2010-11-18
Those warnings are expected, as there is no natty pocket for the extras repository yet

---

### Post by cariboo on 2010-11-18
I had the same problem on one system, I changed the repositories to maverick, and still no luck.  I Disabled the extras repositories completely and the updates came flooding in.

---

### Post by Quackers on 2010-11-19
I've had zillions of updates in the last 2 days!

---

### Post by go7Ul1ai on 2010-11-19
> **cariboo907 said:**
> I had the same problem on one system, I changed the repositories to maverick, and still no luck.  I Disabled the extras repositories completely and the updates came flooding in.

Thank you, just disabled the extras repositories and I now have updates again.. yay :)

---

### Post by chrisccoulson on 2010-11-19
> **lee.jarratt said:**
> Thank you, just disabled the extras repositories and I now have updates again.. yay :)

Hmmmm, that sounds like a bug. I don't think a missing repository should do that, and I don't think it used to (but, perhaps I'm wrong)

---

### Post by dino99 on 2010-11-19
vote for bug , not expected

---

### Post by kaldor on 2010-11-20
Confirmed here.

---

### Post by Anduu on 2010-11-21
My laptop install wouldn't let me upgrade to Natty untill I removed the extras

---

### Post by fluteflute on 2010-11-21
Same problem (and fix) here - very odd! Not sure what to file this bug against though.

---

### Post by NCLI on 2010-11-21
> **fluteflute said:**
> Same problem (and fix) here - very odd! Not sure what to file this bug against though.
I would say apt-get. The developers can always correct it, just getting the bug filed will be a major step towards getting it fixed.

---

### Post by karmila on 2010-11-21
> **fluteflute said:**
> Same problem (and fix) here - very odd! Not sure what to file this bug against though.

The same here...

---

### Post by fluteflute on 2010-11-21
> **chrisccoulson said:**
> Hmmmm, that sounds like a bug. I don't think a missing repository should do that, and I don't think it used to (but, perhaps I'm wrong)
Bug reported at [http://bugs.launchpad.net/ubuntu/+source/apt/+bug/678196](http://bugs.launchpad.net/ubuntu/+source/apt/+bug/678196)

---

### Post by paul_in_london on 2010-11-21
I was wondering what was going on too.

As well as disabling the extras repo I had to switch to the main server.

---

### Post by plun on 2010-11-21
> **paul_in_london said:**
> I was wondering what was going on too.

As well as disabling the extras repo I had to switch to the main server.

This page can be used for locating archive trouble.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by paul_in_london on 2010-11-21
> **plun said:**
> This page can be used for locating archive trouble.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Thanks plun.

---

### Post by jfernyhough on 2010-11-21
All updates stopped coming through for me sometime last week; to fix it I deleted /var/lib/apt and /var/lib/aptitude . I don't know which one fixed things, but it was probably a stale lock or similar.

If you do this you may have to recreate some subdirectories, but that's pretty trivial as it will throw up an error saying what directories it expects to be there.

---

