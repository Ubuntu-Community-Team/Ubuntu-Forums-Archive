---
title: "updates doesn't load completely,what should i do?"
date: 2011-04-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sina_RJ on 2011-04-28
i was beta 1 and update frequently,and each time i did that there were about 23 MB download for updating lists,now when i do that there is about 23KB of download,this means the other lists are finished and I'm on final release or my lists are crashed?

---

### Post by Eestlane on 2011-04-28
Try sudo apt-get dist-upgrade

---

### Post by Sina_RJ on 2011-04-28
> **Eestlane said:**
> Try sudo apt-get dist-upgrade

nothing happened,just like befor it says there are no updates!!!
but it can't be!
i updated last night so there should be some updates for me to go on final release version!

---

### Post by macroshaft on 2011-04-28
> **Sina_RJ said:**
> nothing happened,just like befor it says there are no updates!!!
but it can't be!
i updated last night so there should be some updates for me to go on final release version!

Should there? I got no updates today.
The devs will have spent the last 24 hours getting everything ready for release, if they did any updates today it would throw all that off so you're probably up to date.

---

### Post by Harry33 on 2011-04-28
> **Sina_RJ said:**
> nothing happened,just like befor it says there are no updates!!!
but it can't be!
i updated last night so there should be some updates for me to go on final release version!

The latest updates were these (from natty-proposed):
- file-roller 2.32.2-0ubuntu0.1
- glib-networking 2.28.6.1-0ubuntu1
- unity 3.8.12-0ubuntu1
- nux 0.9.48-0ubuntu1
- bamf 0.2.90-0ubuntu3

Check that you have the natty-proposed repository enabled (from software-properties-gtk or from Synaptic).

---

### Post by KegHead on 2011-04-28
Hi!

I use:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Rerstart.

Works everytime for me.

KegHead

---

