---
title: "I cant open Cinelerra"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Fionnzer on 2009-01-26
I installed cinelerra using [this guide]("http://cinelerra.org/getting_cinelerra.php#intrepid") from the deb
It seemed to install ok But I dont know how to open it 
Ive tried typing cinelerra into both terminal amd run but they just say command not found 
Any help woul be great 
Thanks :p

---

### Post by opscure on 2009-01-26
the deb you installed just put the repo into your sources.  
you may need to update your apt first 
```
sudo apt-get update
```
and then do a:
```
sudo apt-get install cinelerra
```
to install

---

### Post by Fionnzer on 2009-01-26
Thanks mate ;)

---

