---
title: "Cannot install Handbrake"
date: 2019-04-04
forum: Multimedia Software
---

### Post by elastigirl2 on 2019-04-04
Hello, 

I am very non-tech-savvy so please give me very straightforward instructions.... I am hitting a wall when trying to install Handbrake on Ubuntu. It is telling me to run manually "dpkg-configure-a".
When I try to do that in the terminal, it's not accepted. Can you please help? I don't know how else to manually run this. Thanks a lot!

Barbara

---

### Post by jeremy31 on 2019-04-04
Isn't it ```
sudo dpkg --configure -a
```

---

### Post by Autodave on 2019-04-04
As jeremy31 said: you must use sudo.  It will then ask for your password: enter it.  Realize that as you enter your password, it will NOT be displayed on your screen!  Just enter it and then hit the ENTER key.

---

