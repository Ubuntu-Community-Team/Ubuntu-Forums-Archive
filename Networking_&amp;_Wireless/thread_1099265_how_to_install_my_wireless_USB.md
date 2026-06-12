---
title: "how to install my wireless USB"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by lil_kid1333 on 2009-03-18
Hi I got a Wireless-G USB Adapter Model No.: WUSB54GC it came with a cd but it's exe :(

I was wondering how do I install it?

---

### Post by ugm6hr on 2009-03-18
Depends on the chipset.

If it doesn't just work, then you presumably have a new version (with an as yet unsupported chipset).

[http://start.ubuntuforums.org/showthread.php?p=6878480](http://start.ubuntuforums.org/showthread.php?p=6878480)

---

### Post by lil_kid1333 on 2009-03-18
Well can I try to install it anyways? how do I know what chipset it has...  ?

I think mine is an older version cause I googled it but a grey one came out and mine is black...

---

### Post by Steelfan555 on 2009-03-18
I have the same one, and on the cd there is a folder called drivers. Look in there for the .inf . If your doesnt have it, i can email it to you. :)

---

### Post by lil_kid1333 on 2009-03-18
Ok I found the autorun.inf

I went to a folder called x86 and found rt2870.inf could it be that one the one you talking about?

lol btw I like your signature it's funny and true

---

### Post by ugm6hr on 2009-03-18
If it is the original rt2870, then this should help:
[https://launchpad.net/~henrik-hw0/+archive/ppahttps://launchpad.net/~henrik-hw0/+archive/ppa](https://launchpad.net/~henrik-hw0/+archive/ppahttps://launchpad.net/~henrik-hw0/+archive/ppa)

---

### Post by lil_kid1333 on 2009-03-18
> **ugm6hr said:**
> If it is the original rt2870, then this should help:
[https://launchpad.net/~henrik-hw0/+archive/ppahttps://launchpad.net/~henrik-hw0/+archive/ppa](https://launchpad.net/~henrik-hw0/+archive/ppahttps://launchpad.net/~henrik-hw0/+archive/ppa)

omg I can't believe I don't understand the site sorry my god I feel embarrased :s im kind of out of it right now too...

can I just download it through terminal?

---

### Post by ugm6hr on 2009-03-18
Sorry.  It is impossible to know how much detail to give!

I presume you have an rt2870 device, if the CD came with an rt2870 driver on it.

If yes, the driver is not (yet?) included in Ubuntu kernel as default.

Someone (see the site linked) has taken the drivers, and compiled them specifically for fellow Ubuntu users, making installation much easier.

But, in order to give specific advice, I need to know:

Which version of Ubuntu do you use (inc 32 vs 64-bit)?

Do you have wired ethernet available?

---

### Post by lil_kid1333 on 2009-03-18
Yeah I was guessing he compiled it for Ubuntu :P

im using 8.10 intrepid 32 bit and i'm currently connected through ethernet

---

### Post by ugm6hr on 2009-03-18
It looks like that PPA repo is for Jaunty only.  Not sure why.

There is an Intrepid one with the same package (I think) here:
[https://launchpad.net/~mieszkoslusarczyk/+archive/ppa](https://launchpad.net/~mieszkoslusarczyk/+archive/ppa)

Anyway, here's how:

1. Add additional repo:
deb [http://ppa.launchpad.net/mieszkoslusarczyk/ppa/ubuntu](http://ppa.launchpad.net/mieszkoslusarczyk/ppa/ubuntu) intrepid main
See here if uncertain how: [https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

2. Update system:
```
sudo apt-get update
sudo apt-get upgrade
```

3. Install driver:
```
sudo apt-get install rt2860-linux-sta
```

It will complain about it being an unverified source.  If you trust the package maintainer, just agree.  I would suggest removing the repo afterwards, to ensure you don't install anything else from there with future updates.

Hopefully a reboot will then work.

---

### Post by lil_kid1333 on 2009-03-18
ok I did it im going to reboot now and report back thanks

---

### Post by lil_kid1333 on 2009-03-18
well I restarted and nothing came up 

oh yeah and after doing what you said their were updates but I just took the link of the repository and they were gone was I supposed to update it?

---

### Post by ugm6hr on 2009-03-18
Sorry, I just noticed a small spelling error in that command.

Try again with:
```
sudo apt-get install rt28**7**0-linux-sta
```

Obviously you will have to re-enable the rpo again.

And no, you don't want to install anything else from there (updates included).

---

### Post by lil_kid1333 on 2009-03-18
ok ill do it

btw I started getting an error message

Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = -1, can_write = 4096, errno = 111 (Connection refused)
This might be a sound hardware/driver specific problem (see aRts FAQ)

what is that :s

btw its ******* annoying man >.<

---

### Post by lil_kid1333 on 2009-03-19
Well I installed the new one and restarted the computer and nothing :s

---

