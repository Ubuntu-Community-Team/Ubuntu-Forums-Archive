---
title: "Ati driver and Kernel sources"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by elbryan on 2006-06-09
Double problem at the same time.. whoa! ^^

I've followed some istructions in order to configure the 3D driver for my ATI video card. (I have a Radeon 9550).

Here is the link: [http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29]("http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29")
(Sorry that is in italian but you need only to look at the command I had prompted).

I've done almost everything wrote on that site but when I try to do this:
```

sudo module-assistant build,install fglrx-kernel

```
I receive this: "Bad luck, the kernel headers for the target kernel version could not be found and you did not specify another valid kernel to use".

I went on Synaptic to try to install my kernel headers but i have found only for the "2.4.27-2" and I have 
```

elbryan@ubuntu:~$ uname -r
2.6.15-23-686

```

So I have a few questions.. 
- Do I have to install fglrx kernel headers or Linux kernel?
- Why on apt (Synpatic) I can find only an old version of kernel?
- What should I do now?

Thanks all ^^

---

