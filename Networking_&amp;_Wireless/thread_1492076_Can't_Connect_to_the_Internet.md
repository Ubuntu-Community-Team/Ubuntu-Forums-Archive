---
title: "Can't Connect to the Internet"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by qrrbrrbbl on 2010-05-24
I'm just using Ubuntu for the first time, and am trying to get everything working on the Live CD before I install it. The only problem that I'm having right now is getting connected to the Internet. I'm trying to connect to my router, but it keeps asking for the WEP Key. I type it in and it pops up again a minute later. It works on Windows, though. I'm running Ubuntu 10.04 on an old Inspiron 8100 I got from a friend.

---

### Post by linuxonbute on 2010-05-24
> **qrrbrrbbl said:**
> I'm just using Ubuntu for the first time, and am trying to get everything working on the Live CD before I install it. The only problem that I'm having right now is getting connected to the Internet. I'm trying to connect to my router, but it keeps asking for the WEP Key. I type it in and it pops up again a minute later. It works on Windows, though. I'm running Ubuntu 10.04 on an old Inspiron 8100 I got from a friend.

When you left-click on the network icon does it show several wireless networks? If so is the one at the very top your network or another one?

---

### Post by qrrbrrbbl on 2010-05-24
It's only showing my network.

---

### Post by shahaam on 2010-05-24
> **linuxonbute said:**
> When you left-click on the network icon does it show several wireless networks? If so is the one at the very top your network or another one?

I have just installed the ubuntu too and facing the same problem. I can see the network name but it keep on asking the security key (WEP,WPA, LEAP etc)and the password. i am not sure which security key is mine.I have tried all the security options with the password but still doesn't connect to the internet. Hope to get some help?
thanks heaps.

---

### Post by TheGnomeOfMetal on 2010-05-24
goto whatever computer the router is connected to, and log in to the router through the internet. you will then see what your security key is. (to login you must know your passwd)

---

### Post by qrrbrrbbl on 2010-05-24
I have the right key, it just keeps asking for it.

---

### Post by linuxonbute on 2010-05-24
> **qrrbrrbbl said:**
> I have the right key, it just keeps asking for it.

When it is asking for the key can you tick a little box so it shows you what you are typing in?
If you can then please try that and see what happens then.

---

### Post by qrrbrrbbl on 2010-05-24
I've tried that too. Same problem. I can't connect with a wire either. I think the port's just broken, though. Could Ubuntu dislike my wireless setup?

---

### Post by SlidingHorn on 2010-05-24
> **qrrbrrbbl said:**
> I've tried that too. Same problem. I can't connect with a wire either. I think the port's just broken, though.

It's sounding like a driver problem.  Unfortunately (as you can see by my signature) that is not my strong point, lol.  I have a laptop that shows available networks, but refuses to connect.  Please post the output of the following commands:

```
lspci

lsusb

dmesg

sudo lshw -C network

sudo pccardctl ident
```

This should give us a starting point

---

### Post by qrrbrrbbl on 2010-05-24
That's a lot to type out. Are there any parts I don't have to worry about typing out?

---

