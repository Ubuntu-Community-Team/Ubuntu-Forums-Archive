---
title: "disable onboard nvidia... no option in BIOS. need device manager?"
date: 2009-03-01
forum: Multimedia Software
---

### Post by iansane on 2009-03-01
Hi,

I have a ATI video card I got from a friend. I need to disable the onboard nvidia. There is no option to disable it in BIOS on my Gateway GM5072. If I was in Windows I would use the device manager to disable it. Is there a similar way to disable in Ubuntu Hardy?

I found some posts asking for a device manager in which most of the responses were "hardware information" and "lspci" and things like that. Those are not device manager. Can someone tell me the steps to find and disable the onboard through ubuntu?

Thanks

---

### Post by damis648 on 2009-03-01
I suppose
```
sudo rmmod nv
```
should do the trick, followed by blacklisting it:
```
gksudo gedit /etc/blacklist
```
and adding in
```
blacklist nv
```

---

### Post by iansane on 2009-03-06
Thanks for the response damis648

I haven't had a chance to install it yet since I only have the one computer and my job and school have kept me extremely busy. Hopefully it will be as simple as the steps you listed when I am able to get to it. 


Thanks

---

