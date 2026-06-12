---
title: "Need Natty?"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Edho on 2011-04-23
My computer is cheap,  graphic card on board.

Ubuntu 10.10 runs good.
Of coarse no 3D or fancy things... don't need it.

Is there a advantage installing Natty when it is released?

---

### Post by buzzmandt on 2011-04-23
i bet 10.04 would run good too, or 9.10 for that matter. or maybe even 8.04 lts..... so why are you running 10.10??

go for 11.04 or not for the same reason. 

test first with live cd, if it works good you decide

---

### Post by Script Warlock on 2011-04-23
if this can benefit you why not.. read the features 
[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

---

### Post by KegHead on 2011-04-23
Hi!

I'm using 11.04/classic on an el cheapo atom based desktop.

It runs fast and smooth.

Reason I update?

I like to stay on the bleeding edge of technology.

KegHead

---

### Post by JRV on 2011-04-23
Since you do not have 3D you will need to install Unity2d or it will default to the old desktop.

To install Unity 2D, type the following commands in a terminal:
```

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d

```
This will install all of the necessary dependencies to run Unity 2D, including a "Unity 2D" session that you'll need to login with.

Then do the following:
 * log out
 * log back in and choose the "Unity 2D" session in the drop-down menu at the bottom of the login screen
 * you will then be running Unity 2D

---

### Post by VMC on 2011-04-23
> **Edho said:**
> My computer is _**cheap,  graphic card on board**_.

Ubuntu 10.10 runs good.
Of coarse no 3D or fancy things... don't need it.

Is there a advantage installing Natty when it is released?

What is the output of this from Terminal:

```
lspci|grep VGA
```

---

### Post by Edho on 2011-04-24
Thank You all for helping me.

Output is...

VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)

---

