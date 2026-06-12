---
title: "Trouble with my sound please help"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by adn258 on 2008-01-23
Okay I have Ubuntu 7.10 and I have it on an HP Pavilion dv6000 and my sound device is

Intel Corporation 82801H (ICH8 Family) 

Some place a person before told me how to fix this and it WORKED but I had to delete and reinstall unbutu so now that's not working anymore the fix was some command for installing something and it had something in it  like backport or something install backport does anyone know?

---

### Post by balaknair on 2008-01-23
In System menu> Admistration> Software Sources--> Updates> enable Backports(Unsupported updates)

Then in a terminal(Applications menu> Accessories> Terminal)
uname -r

This will tell you what Linux kernel you use
In terminal
sudo apt-get install linux-backports-modules-generic

If you use the i386 kernel replace *generic* in the above command with *i386*

---

### Post by adn258 on 2008-01-23
> **adn258 said:**
> Okay I have Ubuntu 7.10 and I have it on an HP Pavilion dv6000 and my sound device is

Intel Corporation 82801H (ICH8 Family) 

Some place a person before told me how to fix this and it WORKED but I had to delete and reinstall unbutu so now that's not working anymore the fix was some command for installing something and it had something in it  like backport or something install backport does anyone know?

thanks that worked dude

---

