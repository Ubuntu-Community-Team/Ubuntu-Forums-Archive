---
title: "Install TV Tuner PCI Card Philips 7130 w/FM"
date: 2009-01-15
forum: Multimedia Software
---

### Post by kjhughes23 on 2009-01-15
I need help installing the tv tuner vard. It was in the pc when I intalled Ubuntu but i could never get it working, I am new to Ubuntu and I have no clue as to how to get it working

Any help (ideas / websites) is greatly appreciated!!

---

### Post by John Jason Jordan on 2009-01-15
> **kjhughes23 said:**
> I need help installing the tv tuner vard. It was in the pc when I intalled Ubuntu but i could never get it working, I am new to Ubuntu and I have no clue as to how to get it working

Any help (ideas / websites) is greatly appreciated!!

Start by going to mythtv.com. Once you get there you will find links to many other sites dedicated to TV on Linux. Pay particular attention to their list of supported cards. And they also have lots of how-to's.

---

### Post by cariboo on 2009-01-15
You will have to find out what the card number is. Have a look [here]("http://http://gentoo-wiki.com/HARDWARE_saa7134),") to see if your card is listed. When you find the card number create a text file that looks like this:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=X
```

Where X is your card number. Once you have created the file copy it to /etc/modprobe.d:

```
sudo cp <filename> /etc/modprobe.d/
```

Once you have done the above, you need to remove the modules:

```
sudo rmmod saa7134_alsa
```

and

```
sudo rmmod saa7134
```

then insert the module:

```
sudo modprobe saa7134
```

Of course you can just reboot to do the same thing. Once you have done the above, hook up your cable and open Tvtime and watch TV.

Jim

---

### Post by kjhughes23 on 2009-01-16
Thanks but the link is bad for me, can you type out the address

---

### Post by John Jason Jordan on 2009-01-16
> **kjhughes23 said:**
> Thanks but the link is bad for me, can you type out the address

Sorry, it's an .org, not a .com:

[http://www.mythtv.org/]("http://www.mythtv.org/")

---

