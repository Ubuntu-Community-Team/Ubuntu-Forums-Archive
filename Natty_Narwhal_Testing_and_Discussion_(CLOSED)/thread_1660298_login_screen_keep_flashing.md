---
title: "login screen keep flashing"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Penguin360 on 2011-01-05
My login screen keeps flashing now after I ran a system update before Christmas, so I cannot log in now. Can someone help me?

Thanks,

---

### Post by Penguin360 on 2011-01-05
Am I the only one has this problem?

---

### Post by dino99 on 2011-01-05
make a cold boot, choose "recovery mode" then "repair packages" then "continue normal boot"

hope you can log then:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure compiz

---

### Post by wojox on 2011-01-05
Boot into recovery mode and run your updates.

---

### Post by Penguin360 on 2011-01-05
I cannot log into Recovery Mode because the login screen keeps flickering and there is no way for me to choose anything.

Finally, I logged in with Ctrl+Alt+F1, then run commands:
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

After the update was finished, I rebooted my pc normally, and everything was fine.

Thank you for your help.

---

### Post by cariboo on 2011-01-05
Just so you know for next time, you access recovery mode from the grub menu, just hold down the shift key after post to see the grub menu.

---

### Post by Penguin360 on 2011-01-05
> **cariboo907 said:**
> Just so you know for next time, you access recovery mode from the grub menu, just hold down the shift key after post to see the grub menu.

Somehow, I thought it was the Esc key. That explains why I could not access the recovery mode because I was holding down the wrong key.

Thank you so much.

---

### Post by cariboo on 2011-01-05
The behavior change when grub2 was installed by default back in Lucid.

---

