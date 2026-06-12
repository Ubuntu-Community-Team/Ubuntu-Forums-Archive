---
title: "Downloaded .debs and software centre"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-03-06
Anyone else getting problems with the software thinking downloaded .deb packages are bad and not letting you install?

---

### Post by mc4man on 2011-03-06
known issue for quite some time - 
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/702217](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/702217)

There will also be some issues w/ .debs that don't pass the new lintian ck. 'feature' in aptdaemon
While there is some value in it it will currently fail on things it shouldn't like packages installing anywhere but /usr

Atm that can be addressed if need be by removing lintian

edit: bug on lintian
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377)

---

### Post by ronacc on 2011-03-06
or use dpkg

---

### Post by Wobblybob on 2011-03-06
yes and have used the terminal command

sudo dpkg -i debname.deb

to install my deb..

---

### Post by Harry33 on 2011-03-06
> **Wobblybob said:**
> yes and have used the terminal command
sudo dpkg -i debname.deb
to install my deb..

This works well if all the dependencies are installed before this.
If you know you are missing one of them, you can of course install them together with dpkg, like this
```
sudo dpkg -i debname1.deb debname2.deb

```

---

### Post by mc4man on 2011-03-06
While i guess the topic was software center  - for single .debs you can just simply install gdebi
gdebi can also be made the default handler for .deb's and will install any missing dependant packages if needed
(or present error message if they're not available

---

