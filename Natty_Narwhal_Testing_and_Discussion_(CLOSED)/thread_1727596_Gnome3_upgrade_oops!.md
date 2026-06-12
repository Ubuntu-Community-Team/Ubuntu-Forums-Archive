---
title: "Gnome3 upgrade oops!"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sonja on 2011-04-12
I followed [these instructions]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1625-how-to-install-gnome3-in-ubuntu-1104-natty-via-ppa") to upgrade to Gnome3. I was already in Natty beta.

Now when I turn on my computer, I get [this error]("http://i.imgur.com/TSVxw.png").

Help? :)

---

### Post by Sonja on 2011-04-12
Great success!

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntugnometeam/gnome3

```

Or if you got into this mess via UbuntuTweak, you want: 

```

sudo ppa-purge ppa:gnome3-team/gnome3

```

---

### Post by Harry33 on 2011-04-13
> **Sonja said:**
> Great success!

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntugnometeam/gnome3

```

These Gnome3/Gnome-shell upgrades into Natty do have issues, meaning the Gnome3 PPA's are not ready yet.
These should be tested only into a testing setup machine, not into a production machine.

---

### Post by SCrid2000 on 2011-04-19
Thanks man. I had to do this too. 
:p upgraded back to 11.04 after I downgraded to 10.10 out of dislike of unity, then couldn't install the new gnome shell... grrr...

---

