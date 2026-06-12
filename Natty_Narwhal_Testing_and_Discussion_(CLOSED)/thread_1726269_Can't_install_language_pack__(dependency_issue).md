---
title: "Can't install language pack  (dependency issue)"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vaskark on 2011-04-10
I'm receiving an error message when trying to install* language-pack-gnome-en* in synaptic:

```
Depends: language-pack-gnome-en-base but it is not going to be installed
Depends: language-pack-en-base but it is not going to be installed
```Is there any way around this? Those 2 packages were removed by my mistake, and now there are several apps that won't work without them (ccsm, for example).

Thanks.

---

### Post by 5149.5 on 2011-04-10
There are probably a few of us in this state. I have been staying reasonably up to date and here is the output of my last upgrade:

```
The following packages have been kept back:
  language-pack-en-base language-pack-gnome-en-base
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded
```

The next cycle or two will take care of those.

---

### Post by Harry33 on 2011-04-11
> **vaskark said:**
> I'm receiving an error message when trying to install* language-pack-gnome-en* in synaptic:
```
Depends: language-pack-gnome-en-base but it is not going to be installed
Depends: language-pack-en-base but it is not going to be installed
```Is there any way around this? Those 2 packages were removed by my mistake, and now there are several apps that won't work without them (ccsm, for example).
Thanks.

Just do not upgrade yet.
Two new packages are still missing from updates.
That is why apt offers to remove the old ones.
You see those two packages you are trying to install depend on those two missing packages.
So just wait.

---

### Post by haustier on 2011-04-11
Is there any workaround for this? I now have a system without a system locale. Great...

---

### Post by dino99 on 2011-04-11
several possible choices:
- reinstall
- wait for additional packages upload
- continue to break your system with partial upgrades

---

### Post by Harry33 on 2011-04-11
> **dino99 said:**
> several possible choices:
- reinstall
- wait for additional packages upload
- continue to break your system with partial upgrades

+ 1
Exactly, why people go and deliberately remove important packages in order to get a partial upgrade installed.

---

### Post by 23dornot23d on 2011-04-11
[B]Ok had to put these back again ...... 

(dist-upgrade removed then for me but I do like to try things out  - why did it want to remove them who knows ?)

sudo apt-get update
sudo install aptitude
sudo aptitude update

 [/B]**sudo **[B]aptitude install language-support-uk
 sudo dpkg-reconfigure locales


worked for me today ..... you have to choose the language you want though .....
[/B]

---

### Post by ukbeast on 2011-04-11
I feel like a newb.

Just wait till they send more update?
 This is not a fault with my system?
What is a partial upgrade?

Sorry with my questions, this is the 1st time I had this problem.

Now Synaptic Package Manager freezes.

---

### Post by Harry33 on 2011-04-11
> **ukbeast said:**
> I feel like a newb.
...
What is a partial upgrade?
Sorry with my questions, this is the 1st time I had this problem.
Now Synaptic Package Manager freezes.

Here is more info "partial upgrade":
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by lucazade on 2011-04-11
new language packages are available in repos.

---

### Post by ukbeast on 2011-04-11
Thanks for the info Harry.

Just ran sudo apt-get update,(again) now the problems gone,
thanks Ubuntu :)

---

### Post by Harry33 on 2011-04-11
> **ukbeast said:**
> Thanks for the info Harry.

Just ran sudo apt-get update,(again) now the problems gone,
thanks Ubuntu :)

You are welcome.
Now you can mark this thread as "Solved".

---

