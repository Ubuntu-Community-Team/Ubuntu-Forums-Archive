---
title: "Finding out which Video card I Have"
date: 2009-10-22
forum: Multimedia Software
---

### Post by joelw135 on 2009-10-22
Is there a way to find out what video card is installed on my PC, without opening it up?

---

### Post by SteveDee on 2009-10-23
The gui applications "sysinfo" and "Device Manager" will return information on your graphics interface.

---

### Post by howefield on 2009-10-23
Or open a terminal - Applications > Accessories > Terminal and type

```
lspci | grep VGA
```

---

### Post by sahabcse on 2009-10-23
run the below command in terminal 


#sudo lshw

---

