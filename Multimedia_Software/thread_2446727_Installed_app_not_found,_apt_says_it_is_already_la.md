---
title: "Installed app not found, apt says it is already latest version"
date: 2020-07-05
forum: Multimedia Software
---

### Post by porphyry52 on 2020-07-05
Could someone kindly explain the following result

```
/media/q/256GB/mobi $ sudo apt install foliate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
foliate is already the newest version (2.4.0).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
/media/q/256GB/mobi $ foliate
foliate: command not found
/media/q/256GB/mobi $ 
```

I have the same result with another ebook reader, bookworm. With both I installed from their respective ppas, both installs appeared normal, neither command can be found, but apt declares both to be up-to-date.

---

### Post by deadflowr on 2020-07-05
foliate isn't a command that is used for the app at hand,
for some reason or another..

The PPA does ship with a launcher for it, can you try that? 
Does it show up in the dash/menu listing for apps when you search for it?

FTR, the command that shows to run it from the launchers desktop file is
```
com.github.johnfactotum.Foliate %U
```
Which is ...
different.

---

### Post by porphyry52 on 2020-07-06
> **deadflowr said:**
> foliate isn't a command that is used for the app at hand,
for some reason or another..

The PPA does ship with a launcher for it, can you try that? 
Does it show up in the[B] dash/menu listing for apps when you search for it?
[/B]
FTR, the command that shows to run it from the launchers desktop file is
```
com.github.johnfactotum.Foliate %U
```
Which is ...
different.

Thank you, yes, there it is in the Office Menu, as is Bookworm too. The only time I ever use Menus is when I'm looking for some exotic system tool, but now I have another reason.

---

