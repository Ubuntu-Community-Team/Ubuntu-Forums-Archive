---
title: "starting irexec stops lircd, help"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Blackie_Chan on 2007-04-26
I followed the instructions to install lirc using [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy). 

```

neo@matrix:/etc# ps aux | grep lirc
root     25033  0.0  0.0   2880   508 ?        Ss   22:03   0:00 /usr/sbin/lircd
root     25037  0.0  0.1   2884   756 pts/0    R+   22:03   0:00 grep lirc

```

I created my .lircrc, and ran irexec. 

But after running irexec, lirc dies
```

neo@matrix:/etc# ps aux | grep lirc
root     25037  0.0  0.1   2884   756 pts/0    R+   22:03   0:00 grep lirc
neo@matrix:/etc# ps aux | grep irexec
neo    25182  0.0  0.1   2880   760 pts/1    S+   22:14   0:00 grep irexec

```

Can someone suggest a way to get irexec running? Am I missing something?

Thanks in advance.

---

### Post by Blackie_Chan on 2007-05-05
I got the problem fixed now. 

After googling, I found out that modules: lirc_atiusb and ati_remote do not work together. So I just found the ati_remote module, and renamed it so that it doesn't get loaded at startup.

```
user@ubuntu:~$ find /lib/modules/* -name ati_remote*
```

After rebooting, I was able to run irexec.

---

