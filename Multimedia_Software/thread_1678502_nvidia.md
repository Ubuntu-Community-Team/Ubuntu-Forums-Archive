---
title: "nvidia"
date: 2011-01-30
forum: Multimedia Software
---

### Post by usafmom04 on 2011-01-30
i do not know what video card is in my laptop how do i find out? 
I installed the update 11.0 and now I can not get a picture. Not sure if it is the video card or not. please help!

---

### Post by realzippy on 2011-01-30
[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

mind that 11.04 is testing...

---

### Post by BicyclerBoy on 2011-01-30
Maybe natty forum

AFAIK
Release ubuntu 11.04 natty uses Xorg 2.0 which breaks closed source video drivers.

---

### Post by lidex on 2011-01-30
> **usafmom04 said:**
> i do not know what video card is in my laptop how do i find out? 


Using a Terminal="Applications->Accessories->Terminal"
```
lspci -nn | grep VGA
```

---

### Post by usafmom04 on 2011-01-30
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
```
lspci -nn | grep VGA
```



thanks guys.  i went back to 10.10 till the kninks get worked out of 11

---

