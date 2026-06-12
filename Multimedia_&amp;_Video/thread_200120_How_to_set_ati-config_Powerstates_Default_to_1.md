---
title: "How to set ati-config Powerstates Default to 1?"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by Onyros on 2006-06-19
Hya, guys ;)

I finally found a way to minimize Dapper's battery consumption by using

```
aticonfig --set-powerstate=1
```

which puts the graphics card into a low voltage mode, and also makes my lappy cooler.

I checked this out with

```
aticonfig --list-powerstates
```

which gives me an output of

```
    core/mem      [flags]
-----------------
* 1: 105/120 MHz  [low voltage]
  2: 209/182 MHz  [low voltage]
  3: 358/331 MHz  [default state]
```

after I changed the Powerstate to 1.

My question is... how do I change the default state to #1? I'd rather enable good video acceleration when I need it, so I can keep the laptop cooler and battery consumption lower by default.

---

### Post by lodp on 2006-07-25
i've got the same problem. i think it would be enough to automatically execute > aticonfig --set-powerstate=1 on start-up -- i just couldn't figure out how to do that. i created a file with that content, made it executable, and placed it in /etc/init.d -- doesn't seem to work out, though. any help would be greatly appreciated.

btw, in another thread somebody said he placed the command in system > properties > sessions > start-programs. doesn't work for me, cause i'm running kubuntu.

---

### Post by ltmon on 2006-07-25
> **lodp said:**
> i've got the same problem. i think it would be enough to automatically execute  on start-up -- i just couldn't figure out how to do that. i created a file with that content, made it executable, and placed it in /etc/init.d -- doesn't seem to work out, though. any help would be greatly appreciated.

btw, in another thread somebody said he placed the command in system > properties > sessions > start-programs. doesn't work for me, cause i'm running kubuntu.

If you're running kubuntu the easiest way is to put it in an executable shell script in ~/.kde/Autostart/

L.

---

### Post by lodp on 2006-07-27
thanks for the tip -- works brilliantly..

---

