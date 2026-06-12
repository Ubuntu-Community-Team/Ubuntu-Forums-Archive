---
title: "Medibuntu on 8.04"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by maldek on 2008-03-24
I just installed the latest 8.04 beta .iso and got everything up and customized how I like it then remembered medibuntu doesn't usually have anything for beta releases until they're finalized.  How do I go about watching DVDs on 8.04?

---

### Post by overdrank on 2008-03-24
> **maldek said:**
> I just installed the latest 8.04 beta .iso and got everything up and customized how I like it then remembered medibuntu doesn't usually have anything for beta releases until they're finalized.  How do I go about watching DVDs on 8.04?

Hi and I just wen to 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and installed the deb manually and off I went
example
```


wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb
sudo dpkg -i w64codecs_20061203-0medibuntu2_amd64.deb


```

---

### Post by maldek on 2008-03-24
Ah, I've always gone the route of installing the repository.  I learned something today. Thanks!

---

