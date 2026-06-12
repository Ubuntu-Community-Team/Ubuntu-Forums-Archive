---
title: "Lirc -&gt; Symlink to dev/lirc does not work"
date: 2009-12-08
forum: Multimedia Software
---

### Post by m.bluemle on 2009-12-08
Hi,
i have the problem, that Lirc only make a *dev/lirc0* but no *dev/lirc*. I have no issue in *irw *until i set a symbol link by 
```
ln -s /dev/lirc0 /dev/lirc 
```from *lirc0* to *lirc*. But this kind of solution is only a temp one. After the next booting I have to set the link again, to get an dev/lirc.
I found a solution for this problem in the net:

```
sudo echo KERNEL="lirc0", SYMLINK="lirc" >> /etc/udev/udev.rules
echo lirc_i2c | sudo tee -a /etc/modules 
```This does write me *KERNEL=lirc0, SYMLINK=lirc* in the udev.rules, but it doesn´t set the link after booting. I´am working on a 9.04 Mini Ubuntu System.
Can anyone help me? Why does the solution not work? How can i set this symbol link automatically after booting?

---

