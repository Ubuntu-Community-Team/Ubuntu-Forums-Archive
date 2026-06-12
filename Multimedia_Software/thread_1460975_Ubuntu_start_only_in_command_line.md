---
title: "Ubuntu start only in command line"
date: 2010-04-23
forum: Multimedia Software
---

### Post by a.sopco on 2010-04-23
Hello!

Ubuntu 9.10 (Karmic Koala) 64 bit
laptop Asus f5n vidio: GeForce 7000M

I try to remove piton2.6, but system freeze, 
after these ubuntu  show massage (after reboot)

&quot;Ubuntu is running in low-grahics mode      
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself&quot;

I press &quot;ok&quot;

and give me next list of options

&quot;run ubuntu in low-graphics mode for just one session&quot; -- system freeze 

&quot;regonfigure graphics&quot; -- no result

I try  to reinstall graphic driver &quot;nvidia-glx-185&quot; -- no result

](*,)help!

I attach fail log to help find error

---

### Post by wojox on 2010-04-24
Try running:

```
sudo nvidia-xconfig
```

This will back up your old file and create a new one.

---

### Post by a.sopco on 2010-04-25
thanks Wojox,   it works perfectly

---

### Post by wojox on 2010-04-25
Your welcome :)

---

