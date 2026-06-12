---
title: "Improving VNC internal remote desktop speed."
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by LLMNSTR on 2009-04-14
Hi,

I got an internal VNC remote desktop system working right now. I have x11vnc server on my Ubuntu 8.04 lts desktop, and I can successfully connect to it via TightVNC Client on my WinXP machine over my home network. The speed is nothing horrible. But I still receive a fair bit of cursor and window lag (usually about 1 or 2 seconds). It should be fast considering it's over a home network. The Ubuntu machine is connected by wireless router, but I still don't think that should bring the speed down that much. I was wondering if there are any configuration changes I can make to remedy this or if the software I'm using could be affecting it.

Thanks in advance.

---

### Post by Tr10 on 2009-04-14
> **LLMNSTR said:**
> Hi,

I got an internal VNC remote desktop system working right now. I have x11vnc server on my Ubuntu 8.04 lts desktop, and I can successfully connect to it via TightVNC Client on my WinXP machine over my home network. The speed is nothing horrible. But I still receive a fair bit of cursor and window lag (usually about 1 or 2 seconds). It should be fast considering it's over a home network. The Ubuntu machine is connected by wireless router, but I still don't think that should bring the speed down that much. I was wondering if there are any configuration changes I can make to remedy this or if the software I'm using could be affecting it.

Thanks in advance.

This entirely depends on what you're trying to do on it.

Reducing the ammount of colors/resolution will help lower the ammount of data transfered across your network.

It's not your hardware that is slowing it down, it's the program itself, it wasn't designed to handle gb/s. Which I think is the speed you're looking for. If you're looking for something faster, may I suggest SSH.
But again, it's completely dependant on what you're using it for.

---

### Post by krunge on 2009-04-14
> **LLMNSTR said:**
> Hi,

I got an internal VNC remote desktop system working right now. I have x11vnc server on my Ubuntu 8.04 lts desktop, and I can successfully connect to it via TightVNC Client on my WinXP machine over my home network. The speed is nothing horrible. But I still receive a fair bit of cursor and window lag (usually about 1 or 2 seconds). It should be fast considering it's over a home network. The Ubuntu machine is connected by wireless router, but I still don't think that should bring the speed down that much. I was wondering if there are any configuration changes I can make to remedy this or if the software I'm using could be affecting it.

Thanks in advance.

Have you applied the "-noxdamage" option to work around the bugs in Xorg/compiz?
```
x11vnc -noxdamage ...
```

You can search these forums for "noxdamage" for more info, and here too: [http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)

---

