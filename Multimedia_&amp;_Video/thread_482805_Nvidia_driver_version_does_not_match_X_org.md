---
title: "Nvidia driver version does not match X org"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by coderipper1983 on 2007-06-24
okay, so I used the package manager to install nvidia-glx-new for my 7600gt card. I went to the restricted drivers manager and activated the driver then rebooted the comp. On restart, I get an error message saying the nvidia driver version is 9755 but the x org version is something like 9631. I get the same error trying to yse the nvidia-glx drivers from the package manager. Im not sure what to do now. Thx.

[email]Coderipper1983@gmail.com[/email]
Newbie Ubuntu User

---

### Post by NilsE on 2007-06-24
Reboot in recovery mode or just get to a terminal if you can and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

To rebuild your xorg.conf

---

