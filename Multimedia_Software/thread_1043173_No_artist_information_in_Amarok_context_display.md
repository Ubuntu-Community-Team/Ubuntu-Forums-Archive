---
title: "No artist information in Amarok context display"
date: 2009-01-18
forum: Multimedia Software
---

### Post by bowens44 on 2009-01-18
I am running Ubunutu 8.10 32 bit. I installed amarok with synaptic. When I chose the context tab and artist, I get a list of a languages or nothing at all.

I have searched google etc but have not found a solution. 

Any help will be greatly appreciated. This is my favorite feature in amarok

---

### Post by Hopsakee on 2009-02-04
I've got no solution either and exactly the same problem. Only since a couple of weeks. Before I never had that problem. The only difference is, I'm using 64 instead of 32.

---

### Post by AlfyBoy on 2009-03-20
Same problem here, and I'm using a dell mini 9 8.04 default install.

---

### Post by AlfyBoy on 2009-03-22
I found a possible solution, install amarok 1.4.10 from  [here]("http://janitux.boaboa.org/etc/amarok_1.4.10-0ubuntu3_i386.deb")
[http://janitux.boaboa.org/etc/amarok_1.4.10-0ubuntu3_i386.deb](http://janitux.boaboa.org/etc/amarok_1.4.10-0ubuntu3_i386.deb)

And do 

```
echo amarok hold| sudo dpkg --set-selections 
```

In terminal to avoid future updates that might damage it again.

Thanks to alvaro_feria, form this Amarok Forum [http://amarok.kde.org/forum/index.php?topic=16356.0](http://amarok.kde.org/forum/index.php?topic=16356.0)

---

