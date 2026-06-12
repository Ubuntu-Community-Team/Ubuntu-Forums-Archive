---
title: "Is there a way to scale the dash in 11.04 to below default size?"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DogMatix on 2011-04-20
Is there a way to scale the dash in 11.04 to below default size?

Initially I was using 11.04 on my netbook with a 10" screen and the dash takes up the entire screen by default and does not collapse when search results do not use up the whole of the dash. However, I now have 11.04 installed on a Desktop with a 24" screen and I love the fact that the dash only occupies part of the screen, can be scaled to larger sizes and collapses to smaller size when the whole dash is not being used.

What I was wondering is:

[LIST]
[*]is the dash supposed to collapse on smaller screen sizes (i.e. 10") and I'm experiencing some kind of bug with my netbook install?;

[*]is it possible to scale the dash to below the default size when the dash occupies the entire screen?;
[/LIST]

---

### Post by Shmantiv_Radio on 2011-04-20
How is it taking up the whole screen a problem? 

Doesn't bother me in the slightest.

---

### Post by DogMatix on 2011-04-20
It would be nice to have it occupy a smaller amount of screen real estate. Also it would be nice to be able to reduce the size of it on my desktop too.
I guess its just a personal preference but I wondered if it was possible.

---

### Post by mc4man on 2011-04-20
There are 3 settings available, the default is likely automatic
> ~$ gsettings range  com.canonical.Unity form-factor
enum
'Automatic'
'Desktop'
'Netbook'

You could try Desktop and see how that works out
(Desktop will produce a size dependent on screen size/resolution?, not sure how that actually happens
```
gsettings set  com.canonical.Unity form-factor Desktop
```

---

### Post by wojox on 2011-04-20
> **mc4man said:**
> There are 3 settings available, the default is likely automatic

You could try Desktop and see how that works out
(Desktop will produce a size dependent on screen size/resolution?, not sure how that actually happens
```
gsettings set  com.canonical.Unity form-factor Desktop
```

You can also install:

```
sudo apt-get update; sudo apt-get install dconf-tools
```

For a GUI enviorment. Alt+F2 dconf-editor after it's installed.

---

### Post by DogMatix on 2011-04-20
Excellent thanks. The dash now collapses as it does on my Desktop. I still can't scale it smaller but having it collapse is a big improvement.

EDIT: Just noticed that the icons in dash are now off centre and the search bar disappears off the right hand side of the screen when set to desktop

---

