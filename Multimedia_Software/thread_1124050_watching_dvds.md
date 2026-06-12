---
title: "watching dvds"
date: 2009-04-12
forum: Multimedia Software
---

### Post by zeag on 2009-04-12
I'm trying to watch a movie and a it says "it could not read from source"
What should i do

---

### Post by linuxuser21 on 2009-04-13
Have you looked at the [Restricted Formats Documentation]("https://help.ubuntu.com/community/RestrictedFormats")?

---

### Post by wolfen69 on 2009-04-13
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```
then 
```
sudo apt-get install libdvdcss2
```

---

