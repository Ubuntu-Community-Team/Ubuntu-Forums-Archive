---
title: "make command not fouond"
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by 1richard on 2005-12-22
I am trying to install an x-eye cam, it is seen in the device manager, but I cannot install it, as it says make command not found, I am using sudo make and sudo make install, what am I missing?? Can someone one help me, I have spca5xx20051212 Thanks

---

### Post by Swab on 2005-12-22
you need to apt-get install build-essential

---

### Post by mostwanted on 2005-12-22
You're missing make basically ;)

```
$ sudo apt-get install build-essential
```

This installs basic compilers and buil tools (including make).

---

### Post by 1richard on 2005-12-22
got that thanks, but now it says

make: *** /lib/modules/2.6.12-9-386/build not found

---

### Post by Swab on 2005-12-22
[QUOTE=1richard]got that thanks, but now it says

make: *** /lib/modules/2.6.12-9-386/build not found[/QUOTE]

not to sure what to do here... I don't have that file on my box either.

---

### Post by daschl on 2005-12-22
[QUOTE=1richard]got that thanks, but now it says

make: *** /lib/modules/2.6.12-9-386/build not found[/QUOTE]

i suppose that there are also other messages, please post them here!

---

### Post by xtacocorex on 2005-12-22
[QUOTE=1richard]got that thanks, but now it says

make: *** /lib/modules/2.6.12-9-386/build not found[/QUOTE]

* I Think * you need to install the kernel sources, but I may be totally wrong, so sorry in advance if I am.
```

sudo apt-get install linux-headers-2.6.12-9-386

```

---

### Post by jpkotta on 2005-12-22
Sounds like you need the kernel headers.  I think the package name is "kernel-headers". ```
sudo apt-get install kernel-headers
```

Edit: Damn these forums move fast.  I don't think I'm cutout for this internet stuff.

---

### Post by Swab on 2005-12-22
[QUOTE=xtacocorex]* I Think * you need to install the kernel sources, but I may be totally wrong, so sorry in advance if I am.
```

sudo apt-get install linux-headers-2.6.12-9-386

```[/QUOTE]

yeah, that should work! then build is a sym link to /usr/src/linux-headers-2.6.12-9-386

---

### Post by 1richard on 2005-12-22
Thanks for the help. go the linux headers and it complied perfectly.
did sudo modprobe spca5xx that went ok

device manager sees it, but gnomemeeting does not see it, did I leave out a step??

also I took off the bottom task bar, and moved the top one down, when I squeeze a program down it disappears, no way top retrieve it, how do I make it appear on the task bar??

---

### Post by xtacocorex on 2005-12-22
I replied to your pm, hope that helps. Just letting you know if you didn't see it.

---

