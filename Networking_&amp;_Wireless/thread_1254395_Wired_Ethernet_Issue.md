---
title: "Wired Ethernet Issue"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by TheStarLion on 2009-08-31
So, my ethernet's just started acting oddly.
The router the computer's connected to has had no changes, the computer itself (Runnung 9.04 Jaunty) has had no changes, the cable connecting is the same one as always, but now after logging in, the ethernet works for a few seconds, then just drops. Conky on the desktop tells me it still has a connection and an IP address, but the Logging part just keeps reporting eth1: link up continually.

I've tried using a different cable, and a different port on the router and nothing's worked at all. There isn't any other ethernet port I can use on the computer.

Trying to connect the same way on another computer (a laptop running Intrepid) works perfectly with both cables tried, and all ports on the router.

Does anyone have anything that might help?

---

### Post by shredder12 on 2009-08-31
Well, it could be some problem with your port..
but have u tried restarting your network connection.
or try to unplug the cable and plug it again..

In order to find out if it is really some problem with the port why don't you use a Live CD and check if you are facing the same problem there..??

If the problem persists then probably its the port and if not then it could be some problem with Jaunty.

---

### Post by TheStarLion on 2009-09-02
Yes, I've tried restarting the connection, and even gone and got the .deb by usb to try reinstalling, and no change.
The cable's been unplugged and tried in different ports on the router several times, I've tried two cables now as well - did say that.

And the LiveCD works fine, but that doesn't tell me what's wrong with it, and how to fix it short of yet another fresh install, which this was, a few days before I opened this thread.

---

### Post by shredder12 on 2009-09-02
since when have you been accessing network on ubuntu without any problem??
Well, sometimes such an issue arises because of your network card / ethernet controller
could be a driver compatibility issue or something else..

Could you post the output of 
```
lspci
```

---

### Post by Iowan on 2009-09-02
When the connection dies, does **ifconfig -a** still show valid IP address? can machine be **pinged** from another machine?

---

### Post by TheStarLion on 2009-09-04
I've since fixed it by shifting to wireless.
No, by the way, it's not ping-able when it loses the connection, but conky still showed the IP address

Shredder: It worked quite normally for several days, and then just stopped. It wasn't caused by an update, it wasn't caused by any changes at all, I checked that for sure, so since it was working before, it can't be drive incompatibility.
But for now, solved.

---

