---
title: "Freeze when X starts (nvidia etc)"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by netcat on 2006-09-01
I've recently started to use Ubuntu, and I have big problems with the nvidia drivers. Everytime X starts I get a blinking cursor for a few seconds, than it stops blinking and everything freezes. I can still reach the computer via SSH thought.
I have a Geforce 4 MX.
Xorg config is attached.

---

### Post by gsdefender on 2006-09-01
Try appending

```

irqpoll pci=routeirq

```

to the 

```

# kopt

```

line in /boot/grub/menu.lst, then do

```

sudo /sbin/update-grub; sudo /sbin/reboot

```

I've got a GeForce FX Go 5650, and have solved my troubles (exactly the same as yours) by doing that.

---

### Post by netcat on 2006-09-01
Didn't work. :/ Unless I did something wrong here:
```
# kopt=root=/dev/hdc1 ro irqpoll pci=routeirq
```

Attached the Xorg log file if anyone can get something useful from it.

---

