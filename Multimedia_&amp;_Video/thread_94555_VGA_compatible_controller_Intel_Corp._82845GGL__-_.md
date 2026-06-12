---
title: "VGA compatible controller: Intel Corp. 82845G/GL  - HOWTO ?"
date: 2005-11-24
forum: Multimedia &amp; Video
---

### Post by Husio on 2005-11-24
Hi,
I have *Intel 82845G/GL Integrated Graphics Device *, and can't install drivers to it. I whant to play ET but I don't have direct rendering. 

Could someone help me with it? Some sollution...

For more detalis (a few prints from console) please visit [http://husio.homelinux.com/Home/Linux/linux1.html]("http://husio.homelinux.com/Home/Linux/linux1.html")
Site maybe sometimes disabled, becouse it's on my home-server ;)

---

### Post by ranf on 2005-11-24
[QUOTE=Husio]
I have *Intel 82845G/GL Integrated Graphics Device *, and can't install drivers to it. I whant to play ET but I don't have direct rendering. 

Could someone help me with it? Some sollution...

For more detalis (a few prints from console) please visit [http://husio.homelinux.com/Home/Linux/linux1.html]("http://husio.homelinux.com/Home/Linux/linux1.html")
Site maybe sometimes disabled, becouse it's on my home-server ;)[/QUOTE]

make: *** /lib/modules/2.6.12-9-386/build: Nie ma takiego pliku ani katalogu. Stop.
Could you translate that error message? It's polish isn't it?

Have a look at /lib/modules/2.6.12-9-386/build with `ls -la'.

On my box it links to kernel headers:
```
ranf@schlepp:~ $ la /lib/modules/2.6.12-9-686/build
lrwxrwxrwx  1 root root 35 2005-10-20 18:42 /lib/modules/2.6.12-9-686/build -> /usr/src/linux-headers-2.6.12-9-686/

```

---

### Post by Husio on 2005-11-24
> make: *** /lib/modules/2.6.12-9-386/build: Nie ma takiego pliku ani katalogu. Stop.
Could you translate that error message? It's polish isn't it?

Nie ma takiego pliku ani katalogu -- it means -- no such a dictionary/folder or whatever...   

Is there any other way to install Intel drivers? I've tryed to use apt, but can't find any driver. There's no easyer way ?

[Ye, polish, and I'm trying to write in eanglish ;-) ]

---

### Post by ranf on 2005-11-25
[QUOTE=Husio]
Is there any other way to install Intel drivers? I've tryed to use apt, but can't find any driver. There's no easyer way ?
[/QUOTE]
I don't know of other drivers. That doesn't mean there are none. I just don't know.

---

