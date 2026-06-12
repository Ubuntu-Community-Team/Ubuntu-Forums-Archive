---
title: "RealPlayer Install"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by DannyW on 2007-04-11
I've done some searching around, I've tried all the solutions, it seems simple, but I really can't see a way forward:

I'm trying to install RealPlayer as described in the wiki.

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

But on the last line keep getting:
> sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory


Here is my output:
```
danny@danny-desktop:~/Desktop$ ls -l
total 5680
-rwxr-xr-x 1 danny danny 5802563 2007-04-11 13:41 RealPlayer10GOLD.bin
danny@danny-desktop:~/Desktop$ sudo ./RealPlayer10GOLD.bin 
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
danny@danny-desktop:~/Desktop$ 
```

---

### Post by smbm on 2007-04-11
I've never quite worked this out but sometimes I've had to put sh instead of ./

IE:
```

sudo sh RealPlayer10GOLD.bin
```

It's worked for me before.

Hopefully it'll work for you.

Good luck

---

### Post by DannyW on 2007-04-12
I'm afraid not :(

```
danny@danny-desktop:~$ cd ~/Desktop
danny@danny-desktop:~/Desktop$ chmod 755 RealPlayer10GOLD.bin
danny@danny-desktop:~/Desktop$ ls -l
total 5680
-rwxr-xr-x 1 danny danny 5802563 2007-04-11 13:41 RealPlayer10GOLD.bin
danny@danny-desktop:~/Desktop$ sudo sh RealPlayer10GOLD.bin 
Password:
RealPlayer10GOLD.bin: 1: Syntax error: "(" unexpected
danny@danny-desktop:~/Desktop$ 
```

---

