---
title: "Gummi - installing new packages"
date: 2015-08-05
forum: Multimedia Software
---

### Post by dawicz on 2015-08-05
Hello everyone,

short question: how to install new packages on Gummi (ver. 0.6.5)?


many many many thanks for any help

---

### Post by howefield on 2015-08-05
Hello and welcome to the forums, if you are asking how to install version 0.6.5, you would probably be best with a ppa, I think the latest version in the Ubuntu repositories is 0.6.3

[https://launchpad.net/~gummi/+archive/ubuntu/gummi](https://launchpad.net/~gummi/+archive/ubuntu/gummi)  

If you are asking something else, please give more detail.

---

### Post by dawicz on 2015-08-05
thanks for the answer. I'd like to make a graph in my article, that's why I need a tikz package. I did actualize my ppa, but I'm still experiencing some difficulties. But leave them, I just want to know what to do with downloaded package files - paste them in Gummi directory or what?

---

### Post by Vladlenin5000 on 2015-08-05
If you added the PPA then just do
```
sudo apt-get update
sudo apt-get upgrade
```
and the app is automatically updated. Whether or not the new version does what you want is another issue.

---

