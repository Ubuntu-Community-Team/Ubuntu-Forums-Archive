---
title: "GIMP Crash"
date: 2020-08-13
forum: Multimedia Software
---

### Post by candylovergirl on 2020-08-13
Hello,

GIMP is crashing do I have to install it again?

Thanks
Camelia

---

### Post by CelticWarrior on 2020-08-13
No, you don't.
Reinstalling stuff sometimes is necessary for many reasons but that's typically something you would do in Windows. 

First of all check your graphics and drivers. If you have Nvidia without the Nvidia (proprietary) drivers that is enough to cause issues.

---

### Post by candylovergirl on 2020-08-13
> **CelticWarrior said:**
> No, you don't.
Reinstalling stuff sometimes is necessary for many reasons but that's typically something you would do in Windows. 

First of all check your graphics and drivers. If you have Nvidia without the Nvidia (proprietary) drivers that is enough to cause issues.

Thank you, my Nvidia has (proprietary) drivers 

What other options do I have to avoid GIMP crashing?

Thanks 
Camelia

---

### Post by CelticWarrior on 2020-08-13
Run in Terminal: Just type gimp and enter.

It will show errors, some are normal and can be disregarded but one of them should show what's wrong. Post the results here so we can have a look.

---

### Post by SeijiSensei on 2020-08-13
How much memory do you have?  How big are the graphics you are trying to edit?  You could be running out of memory.

If you are using a recent version of Ubuntu, you won't have any swap enabled.  Follow these step to create a swapfile that is at least as big as your total memory.  I'm assuming a 4GB system here:
```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=4194304
sudo mkswap /swapfile
sudo swapon /swapfile

```
To have swap activated automatically at boot:
```
echo '/swapfile swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

The "count" parameter determines the size of the swapfile.  In this case to get a 4 GB swapfile I'm using 4 X 1048576 = 4194304.  Adjust as needed.

The command "free" will show you the size of your memory and of swap.  On my system with 16 GB of physical memory I have a relatively small 2 GB swapfile that is hardly used.

```

              total        used        free      shared  buff/cache   available
Mem:       16333200     3898848      458184      235920    11976168    11862356
Swap:       2097148       51980     2045168

```

I've used GIMP for years and can't recall the last time it crashed.  But I've typically had systems with at least 6 GB of physical memory and swap enabled.

If this is the machine you're using
[https://ubuntuforums.org/showthread.php?t=2448755](https://ubuntuforums.org/showthread.php?t=2448755)
you're probably running out of memory.

---

### Post by candylovergirl on 2020-08-14
> **SeijiSensei said:**
> How much memory do you have?  How big are the graphics you are trying to edit?  You could be running out of memory.

If you are using a recent version of Ubuntu, you won't have any swap enabled.  Follow these step to create a swapfile that is at least as big as your total memory.  I'm assuming a 4GB system here:
```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=4194304
sudo mkswap /swapfile
sudo swapon /swapfile

```
To have swap activated automatically at boot:
```
echo '/swapfile swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

The "count" parameter determines the size of the swapfile.  In this case to get a 4 GB swapfile I'm using 4 X 1048576 = 4194304.  Adjust as needed.

The command "free" will show you the size of your memory and of swap.  On my system with 16 GB of physical memory I have a relatively small 2 GB swapfile that is hardly used.

```

              total        used        free      shared  buff/cache   available
Mem:       16333200     3898848      458184      235920    11976168    11862356
Swap:       2097148       51980     2045168

```

I've used GIMP for years and can't recall the last time it crashed.  But I've typically had systems with at least 6 GB of physical memory and swap enabled.

If this is the machine you're using
[https://ubuntuforums.org/showthread.php?t=2448755](https://ubuntuforums.org/showthread.php?t=2448755)
you're probably running out of memory.

Hello,

Yes, the link about the computer is the model I have
I am using a the latest version of Ubuntu,
I have swap enabled thanks to your code ;)
And I had upgraded this PC to 8 GB but reads it reads 7.8 GB :shock:

I will continue using the swap enabled to see if that was the problem

Thanks
Camelia

---

### Post by CelticWarrior on 2020-08-14
> [COLOR=#000000]I had upgraded this PC to 8 GB but reads it reads 7.8 GB [/COLOR]:shock:

Perfectly normal. There's always system and video reserved memory.

---

### Post by candylovergirl on 2020-08-14
> **CelticWarrior said:**
> Perfectly normal. There's always system and video reserved memory.

Oh! I did not know that

Thank you

Camelia

---

### Post by candylovergirl on 2020-08-22
> **SeijiSensei said:**
> How much memory do you have?  How big are the graphics you are trying to edit?  You could be running out of memory.

If you are using a recent version of Ubuntu, you won't have any swap enabled.  Follow these step to create a swapfile that is at least as big as your total memory.  I'm assuming a 4GB system here:
```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=4194304
sudo mkswap /swapfile
sudo swapon /swapfile

```
To have swap activated automatically at boot:
```
echo '/swapfile swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

The "count" parameter determines the size of the swapfile.  In this case to get a 4 GB swapfile I'm using 4 X 1048576 = 4194304.  Adjust as needed.

The command "free" will show you the size of your memory and of swap.  On my system with 16 GB of physical memory I have a relatively small 2 GB swapfile that is hardly used.

```

              total        used        free      shared  buff/cache   available
Mem:       16333200     3898848      458184      235920    11976168    11862356
Swap:       2097148       51980     2045168

```

I've used GIMP for years and can't recall the last time it crashed.  But I've typically had systems with at least 6 GB of physical memory and swap enabled.

If this is the machine you're using
[https://ubuntuforums.org/showthread.php?t=2448755](https://ubuntuforums.org/showthread.php?t=2448755)
you're probably running out of memory.

Thank you, but if i have 8GB is OK the count=8388608 to create a swapfile?

```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=8388608
sudo mkswap /swapfile
sudo swapon /swapfile

```

Any change here for 8GB?

To have swap activated automatically at boot:
```
echo '/swapfile swap swap defaults 0 0' | sudo tee -a /etc/fstab
```

I did not understand this part, how can I see "free"?

The command "free" will show you the size of your memory and of swap.   On my system with 16 GB of physical memory I have a relatively small 2  GB swapfile that is hardly used.

```

              total        used        free      shared  buff/cache   available
Mem:       16333200     3898848      458184      235920    11976168    11862356
Swap:       2097148       51980     2045168

```

Thanks
Camelia

---

### Post by SeijiSensei on 2020-08-22
> **candylovergirl said:**
> Thank you, but if i have 8GB is OK the count=8388608 to create a swapfile?
Yes, use that number.
> I did not understand this part, how can I see "free"?
Open a terminal and type "free" at a command prompt. It's a command that comes on every Ubuntu (and probably every Linux) system.

How big are the images you're editing when GIMP crashes? Give us the horizontal and vertical lengths in pixels.

---

