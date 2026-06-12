---
title: "about Banshee"
date: 2008-07-03
forum: Multimedia Software
---

### Post by wsamh on 2008-07-03
Does anyone know how to install banshee 1.0. I don't get the instructions that is gives in the website.

---

### Post by ibutho on 2008-07-03
According to the instructions, you have to add the lines below to your /etc/apt/sources.list file.
```

deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
```
After that you can install banshee using the packaging tools e.g. Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install banshee
```

---

### Post by kpkeerthi on 2008-07-03
1. Open terminal from Applications -> Accessories -> Terminal
2. Edit your apt sources file:
```
gksudo gedit /etc/apt/sources.list
```
3. Paste the below lines to the end of the file
```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
```
4. Save and Exit
5. Run the below commands at the command prompt
```
sudo aptitude update && sudo aptitude upgrade
```
5. Now, run this command
```
sudo aptitude install banshee-1
```

Have fun!

---

### Post by wsamh on 2008-07-03
Thank you, you guys.

---

