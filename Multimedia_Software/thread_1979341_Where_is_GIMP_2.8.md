---
title: "Where is GIMP 2.8?"
date: 2012-05-13
forum: Multimedia Software
---

### Post by annadaprasad on 2012-05-13
GIMP 2.[SIZE=4]8[/SIZE] was released on 2012-05-03

And I am still in version 2.[SIZE=4]6[/SIZE]. Why?



Ubuntu Software Center has 2.6. Can you believe it?

The version is out in the wild and I am not able to get hands on it.

---

### Post by zombifier25 on 2012-05-13
Was that a cry for help? :D
Anywho, Ubuntu does not include GIMP 2.8 because it was released after Ubuntu's feature freeze. Type these commands in the terminal to get GIMP 2.8:

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by PaulW2U on 2012-05-13
See [http://ubuntuforums.org/showthread.php?t=1975348](http://ubuntuforums.org/showthread.php?t=1975348).

I doubt you'll see 2.8 in the main repositories until Ubuntu 12.10 is released. That's the way it seems to work with new software versions.

---

### Post by Rodney9 on 2012-05-13
> **zombifier25 said:**
> Was that a cry for help? :D
Anywho, Ubuntu does not include GIMP 2.8 because it was released after Ubuntu's feature freeze. Type these commands in the terminal to get GIMP 2.8:

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

That mucked up my Gimp install, I used --- ```
sudo apt-get purge Gimp*

sudo add-apt-repository ppa:otto-kesselgulasch/gimp

sudo apt-get update

sudo apt-get install gimp
```

The purge is needed first.

Rodney

---

### Post by zombifier25 on 2012-05-14
> **Rodney9 said:**
> That mucked up my Gimp install, I used --- ```
sudo apt-get purge Gimp*

sudo add-apt-repository ppa:otto-kesselgulasch/gimp

sudo apt-get update

sudo apt-get install gimp
```

The purge is needed first.

Rodney

I didn't need to purge. Then again, my machine is different than yours.

---

### Post by annadaprasad on 2012-05-15
> **zombifier25 said:**
> I didn't need to purge. Then again, my machine is different than yours.


Which one will work on my machine??? I think its i386 or something like that.

---

### Post by Yellow Pasque on 2012-05-15
You run the 4 commands (in order) and that will automatically install the appropriate version.

---

