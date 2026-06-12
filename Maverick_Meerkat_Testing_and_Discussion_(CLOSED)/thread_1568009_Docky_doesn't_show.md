---
title: "Docky doesn't show"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-09-04
Okay so when my sister turned on the computer, Docky wouldn't show. 

It was on Intellihide and now it's not showing no more. 

How can I fix this? 

Thanks!

---

### Post by cariboo on 2010-09-04
Remove the docky directory from ~/.local/share to ssee if that solves the problem, you'll probably have to start it from the menu to get it showing again.

**Note** You'll lose your customizations when you remove the directory.

---

### Post by TheNerdAL on 2010-09-06
> **cariboo907 said:**
> Remove the docky directory from ~/.local/share to ssee if that solves the problem, you'll probably have to start it from the menu to get it showing again.

**Note** You'll lose your customizations when you remove the directory.

Did that and it's just like a frozen Docky and  you can't do anything with it.

---

### Post by kaldor on 2010-09-06
Try a different dock. If it happens with cairo-dock, then it might be a driver issue.

---

### Post by TheNerdAL on 2010-09-06
> **kaldor said:**
> Try a different dock. If it happens with cairo-dock, then it might be a driver issue.

Tried AWN and it worked okay. (I accidentally opened it.)

---

### Post by Nickedynick on 2010-09-06
I've just had a series of random freezes with Docky too. It was fine this morning, seems really unstable now and I don't recall there being any updates to it...

---

### Post by karmila on 2010-09-06
Before turn off my computer there was notification saying that docky won't work because compiz/some feature don't work.

But after nvidia driver upgrade to 256.53 the notification no longer show up.

---

### Post by cariboo on 2010-09-06
@TheNerdAL, did you create a bug, and if so could you please post the bug#.

---

### Post by TheNerdAL on 2010-09-06
> **cariboo907 said:**
> @TheNerdAL, did you create a bug, and if so could you please post the bug#.

How do you create a  bug?

---

### Post by 23meg on 2010-09-06
> **TheNerdAL said:**
> How do you create a  bug?

[https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs)

---

### Post by cariboo on 2010-09-06
Make sure you have a [Launchpad]("https://launchpad.net/") account, the press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

in this case you would use docky for <packagename>. If you are going to running a testing version, you might as well join the fun. 

I submitted a bug about docky a couple of weeks ago, and the dev got right on the problem right away. If you have the weather docklet enabled, the next time weather conditions are smoky where you live, there will be am icon showing it.

---

### Post by TheNerdAL on 2010-09-06
> **cariboo907 said:**
> Make sure you have a [Launchpad]("https://launchpad.net/") account, the press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

in this case you would use docky for <packagename>. If you are going to running a testing version, you might as well join the fun. 

I submitted a bug about docky a couple of weeks ago, and the dev got right on the problem right away. If you have the weather docklet enabled, the next time weather conditions are smoky where you live, there will be am icon showing it.

Reported: [https://bugs.launchpad.net/docky/+bug/628372](https://bugs.launchpad.net/docky/+bug/628372)

And thanks! :D Now I know how to report bugs.

---

