---
title: "Simple Task - Difficult"
date: 2013-07-06
forum: Multimedia Software
---

### Post by Geffers on 2013-07-06
Gee, for some reason a simple task of producing a CD image is proving difficult.

Brasero, doesn't seem to give me an .iso option, only .toc but on selecting that it tells me I must install manually toc2cue

OK, sudo apt-get install toc2cue says package CANNOT BE FOUND.

Never mind, I'll use command line dd.

Disk utility says it is /dev/sr0 so command sudo dd if=/dev/sd0 of=path gives me **Input/output error**

Give up, it's too warm out.

Geffers

---

### Post by DJ_Max on 2013-07-06
```
sudo apt-get install cue2toc cdrdao
```

---

### Post by Geffers on 2013-07-06
> **DJ_Max said:**
> ```
sudo apt-get install cue2toc cdrdao
```

Thank you but I am baffled, why did my attempt at cue2toc fail but both together are successful?

Geffers

---

### Post by DJ_Max on 2013-07-06
> **Geffers said:**
> Thank you but I am baffled, why did my attempt at cue2toc fail but both together are successful?

Geffers

No, you said you tried to install ***toc2cue***, when the package is actually ***cue2toc***. The error message is generic, this should actually be a bug report as it's asking you to install a package that doesn't exisit, because the name is different

Cdrao is a package you would have needed eventually.

---

### Post by gordintoronto on 2013-07-06
Two other packages you should look at: DVD Styler and Devede. Both produce an ISO.

---

