---
title: "[SOLVED] EnvyNG not present in synaptics manager"
date: 2008-10-03
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2008-10-03
Hello I'm trying install EnvyNG to get dual screen working on my laptop I'm have a Radeo XPRESS 200M 5955 (PCIE) graphics card.

When I go into the Synaptics Package Manager and search for EnvyNG or Envy all I get is a soundcard package. I have tried sudo aptitude installe and sudo apt-get install and updated the system through the update manager gui but they just say everything is upto date.

Any help (I'm a newbie)
Thanks

---

### Post by AmbiguousOutlier on 2008-10-03
Bump

---

### Post by AmbiguousOutlier on 2008-10-04
I tried 

```

sudo apt-get install envyng-gtk

```

which produced the error

```

E: Couldn't find package envyng-gtk

```

---

### Post by ggarenn on 2008-10-04
If it helps, when I run the command it works just fine...

---

### Post by Elfy on 2008-10-04
First - it's only in the hardy repos afaik, so if you're using an earlier version you need to go to the website - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

If you are using 8.04 then check your sources - System >Admin menu - software sources, make sure that the repos are enabled close and reload if necessary and try again.

---

### Post by AmbiguousOutlier on 2008-10-04
lol, thanks ggarenn

Thanks forestpixie your comment helped.

---

