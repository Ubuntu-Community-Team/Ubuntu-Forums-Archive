---
title: "Annoying Flash Player Problem [Firefox 3.0]"
date: 2008-07-03
forum: Multimedia Software
---

### Post by houseonfire on 2008-07-03
[I'm running 8.04 (Hardy) )

For whatever reason whenever i try to view flash of any kind on Firefox its a gray box. 
But I type in:
```
$ sudo apt-get install flashplugin-nonfree
```
It outputs 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I then type in 
```
$ sudo update-flashplugin
```
And i get the output of:
```
sudo: update-flashplugin: command not found
```

After this, I restart firefox, and it works, but then if i restart firefox again, it stops working until i type that stuff back in again.
And when it does work, I have to reload the page multiple times before it actually loads and plays.

---

### Post by houseonfire on 2008-07-04
I really need help with this problem please.
Thanks.

---

### Post by opt1k. on 2008-07-04
try this one:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by houseonfire on 2008-07-04
I'm already up to date.
Thanks though.

---

### Post by gandaran on 2008-07-04
strange problem, could be due to some error in a configuration file, here's what you could try, first backup your hidden home .mozilla folder, then delete this same folder and start firefox, if the problem still remains you can replace .mozilla folder back again from the backup. 
have you, any other flash installed like swfdec or gnash installed?

---

### Post by houseonfire on 2008-07-04
This fixed it.
Thank you very much.

If anyone else has the problem I had, doing this will remove your addons/Greasemonkey scripts/bookmarks. So back those up before doing this..

---

