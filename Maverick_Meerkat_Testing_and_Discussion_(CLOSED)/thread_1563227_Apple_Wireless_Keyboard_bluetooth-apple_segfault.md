---
title: "Apple Wireless Keyboard bluetooth-apple segfault"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Maletor on 2010-08-28
Running gnome bluetooth results in a success. However, all does not seem well.

No difference when adding hid_apple to /etc/modules

```
maletor@denmark:~$ dmesg | grep -i bluetooth
...
bluetooth-apple[1867]: segfault at 38 ip 00007fdc041128ee sp 00007fff05d50b50 error 4 in libdbusmenu-glib.so.1.0.14[7fdc0410e000+10000]
```

---

### Post by xerosis on 2010-09-03
Not sure if it's related but only a handful of keys are working on mine in Maverick.

---

### Post by Twiggy794 on 2010-09-03
> **xerosis said:**
> Not sure if it's related but only a handful of keys are working on mine in Maverick.

What did you do to pair yours? I can get it to pair, sort of, but once it's paired it never works.  Watching in the Bluetooth Preferences screen it flickers with the connected state but never stays on.  Magic mouse works fine.

Edit: I'm on a fresh install btw.  They both worked great in Lucid.

---

### Post by xerosis on 2010-09-04
To pair I go through the usual routine, but once finished, disconnect the keyboard from Ubuntu, then press the power on the keyboard, that always worked for me.

---

### Post by Twiggy794 on 2010-09-04
> **xerosis said:**
> To pair I go through the usual routine, but once finished, disconnect the keyboard from Ubuntu, then press the power on the keyboard, that always worked for me.

I've done that a couple times, but whenever it picks it back up it asks me to enter a pin for the device.](*,)

---

### Post by Maletor on 2010-09-09
This is still a bug for me. If there is no relavant bug report already and others are still having issues there should definitely be one.

---

### Post by Maletor on 2010-09-14
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/630001](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/630001)

Please mark this bug as affecting you if that is the case.

---

