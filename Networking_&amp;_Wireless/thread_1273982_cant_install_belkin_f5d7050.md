---
title: "cant install belkin f5d7050"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by weedcali on 2009-09-24
ive read around and ive read that i should go into package installer or whatever and look up ndiswrapper-untils but i dont get any results. what do i do?

---

### Post by cariboo on 2009-09-24
Go to System-->Administration-->Synaptic Package Manager and type ndiswrapper in the search box, install both packages.

---

### Post by weedcali on 2009-09-24
as i said. i searched and i get nothing.

---

### Post by Cuba71 on 2009-09-24
I own and have tested this wireless usb adapater and it works with native Ubuntu drivers, no need for ndiswrapper.
Check your VID/PID and see if it matches mine.

[INDENT][B]Belkin F5D7050A USB  Wireless Adapter
ID: 050d:705a
Linux Driver:  RT73usb[/B][/INDENT]

Good luck

---

### Post by weedcali on 2009-09-24
um, i have no idea what VID/PID is. im still new to ubuntu :(

---

### Post by Cuba71 on 2009-09-24
It's the Vendor ID and Product ID.
You can find it by 

```

lsusb

```

---

### Post by weedcali on 2009-09-24
thank you :)

---

### Post by weedcali on 2009-09-24
will this also work in Kubuntu?

---

### Post by Cuba71 on 2009-09-24
If it works in Ubuntu it should work in Kubuntu

---

### Post by weedcali on 2009-09-24
well it didnt work in ubuntu. i opened the terminal and typed in lsusb and it just sat there.

---

### Post by weedcali on 2009-09-24
uuuh, bump?

---

### Post by weedcali on 2009-09-25
still no internet. still no help.

---

### Post by Cuba71 on 2009-09-25
When I'm trying something new in Ubuntu, I always use a LiveCD, this way I can make any modifications I want without affecting anything, taking notes of everything I do so I can recreate what works later on. 

Using a LiveCD gives you an unaltered environment, sometimes we do things that affect how the system works later on.

Get your Ubuntu Jaunty LiveCD, connect the Belkin wireless USB adapter and boot up.  Like I said in a previous post, it should work out of the box.

Important commands:  
[INDENT]lsusb
lshw -C network
lsmod[/INDENT]

---

### Post by weedcali on 2009-09-25
so boot with the belkin already in and the cd in?

---

### Post by Cuba71 on 2009-09-25
Yes, the idea is to boot up with an unaltered version of Jaunty 9.04.

Ubuntu should pick up the Belkin adapter with the rt73 driver

---

### Post by old fert on 2009-09-25
Good luck.  I have the identical usb adaptor.  I've never been able to make it work.  It just makes endless little circles in the upper right of my screen.

---

