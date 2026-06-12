---
title: "Cinelerra install on Kubuntu 8.10"
date: 2008-12-30
forum: Multimedia Software
---

### Post by Ole Juul on 2008-12-30
Has anybody done this? I found no specifics with Google, and the Cinelerra site has (apparently) broken instructions, so I may be on a wild goose chase! :) There are 5 packages in Adept Manager, all labeled "Virtual meta package for cinelerra", and each one says "BREAK (install)". Can anyone point me to some instructions?

---

### Post by SuperSonic4 on 2008-12-30
Source: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

Method 1:
From konsole: ```
sudo nano /etc/apt/sources.list
``` and add
```
deb http://akirad.cinelerra.org akirad-intrepid main
``` to the end[/code]. Press ctrl+x to exit pressing y to save
```
sudo apt-get update
```. Now you can either look for an upgrade in adept-updater or do ```
sudo apt-get install cinelerra
``` 

Method 2:

Download this deb: [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and run it by single clicking

---

### Post by Ole Juul on 2008-12-30
Thanks, but that is exactly the problem. That information that cinelerra provides does not work for me. The repositories have been updated and I cannot install using Adept. This is on a fresh install made for the purpose (with upgrades/updates).

I just tried your alternate suggestion of downloading the deb. The result is that cinelerra no longer shows up in Adept, and there is no sign of cinelerra anywhere else that I know to look. What now?

---

### Post by Ole Juul on 2008-12-30
SOLVED:

The problem here was that the installation was actually 8.04 and not 8.10. The cinelerra repositories are different for those.

I had, mistakenly, assumed that installing 8.04 and doing a complete upgrade would land me at 8.10 - it doesn't. :)

I discovered the problem by learning how to find the version number, which is to type:

```
$ cat /etc/issue
```

---

