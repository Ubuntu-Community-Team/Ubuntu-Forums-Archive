---
title: "eth0 not recognized"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Dave In Sidney on 2006-06-04
I did a live upgrade from 5.10 to 6.06 and have multiple issues. AFter rebooting I can no longer access the net, mainly cause I can no longer access eth0. The networking dialogue doesn't even have an "add device" option! Suggestions?

---

### Post by tonyr on 2006-06-04
Sometimes the upgrade from 5.10 to 6.06 misses some things.

If you are comfortable with the command line in a terminal, try this.  Make sure your 
**/etc/apt/sources.lst** uses **dapper** instead of **breezy** everywhere, and then
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by Dave In Sidney on 2006-06-04
Would if I could, but I not only can't tget to the net, it seems that I can no longer see my CDROM (or the DVD wither)! The system seems hosed and I'm starting to wonder if there's a way back to 5.10.

---

### Post by tonyr on 2006-06-04
OK, so this is my one-stupid-day-a-week day.  I should have known that: 
no eth0 = no apt-get.   And I don't know if it's even possible to get back to 5.10.

You could try
```

sudo apt-get -f install

```

and/or

```

sudo dpkg --configure -a

```

just in case something in your update broke silently.

---

