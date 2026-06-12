---
title: "Installed Nvidia latest driver"
date: 2010-07-09
forum: Multimedia Software
---

### Post by Tedel on 2010-07-09
Hello,

It was very painful for me, but I managed to update the Nvidia driver. I share this solution in case any other of you use two window or desktop managers.

1. Download the latest Nvidia driver from their site.
2. Update your Linux Kernel **and** its headers
3. Reboot
4. Log in in tty mode (control+alt f1)
5. Stop X server with ```
sudo service kdm stop
```
6. Navigate where you downloaded your driver and run it
7. Let it update the Xorg configuration file for you.

I have Xubuntu and I also downloaded Kubuntu, so the other threads which talk about this didn't help me in full. I had to mix "from here and from there" to get here.

---

### Post by Tedel on 2010-07-09
I have a question, though. How do I know I am using the correct driver?

---

