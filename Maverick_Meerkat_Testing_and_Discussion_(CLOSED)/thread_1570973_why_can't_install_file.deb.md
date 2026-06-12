---
title: "why can't install file.deb"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tonjaa on 2010-09-08
i try to use ubuntu 10.10 BETA  64bit  kernel 2.6.35-20 - generic 
i download file dropbox 0.6.3 file .deb  normally when i ever install on ubuntu 10.04 it can
install easy but why when i try to install now it show folder insight and line at tool bar 
[COLOR=DarkRed]nautilus-dropbox_0.6.3_amd64.deb [read only]  [/COLOR]how i can install file .deb this ?

---

### Post by oldos2er on 2010-09-08
Looks like you opened it in File Roller (also called Archive Manager) instead of gdebi.

---

### Post by tonjaa on 2010-09-09
thank you for guide me and how i can install out of Archive manager ?

---

### Post by printfw on 2010-09-09
```
dpkg -i nautilus-dropbox_0.6.3_amd64.deb
```

---

### Post by nilarimogard on 2010-09-09
Gdebi was removed from Maverick. Run an upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```
And then .deb files should open in Ubuntu Software Center. Or use the command line way to install debs like printfw mentioned above.

---

### Post by tonjaa on 2010-09-09
after i update and upgrade now i can install it. thank you so much ;)

---

### Post by Joeb454 on 2010-09-09
*Thread moved to **Maverick Meerkat Testing and Discussion***.

---

### Post by oldos2er on 2010-09-09
> **nilarimogard said:**
> Gdebi was removed from Maverick. 

But isn't it still available in the repositories? gdebi can handle dependencies; dpkg can't.

---

### Post by mc4man on 2010-09-09
> But isn't it still available in the repositories
It's still there and can be used, either from cli or gui.
gdebi-gtk has been fixed and can be used if desired, though the software center is the now the current default for .debs (and works ok

---

### Post by Noz3001 on 2010-09-09
Deb files install via the Software Center in Maverick

---

