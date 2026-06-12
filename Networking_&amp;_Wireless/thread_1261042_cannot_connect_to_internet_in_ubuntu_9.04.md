---
title: "cannot connect to internet in ubuntu 9.04"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by bogart_2003 on 2009-09-08
hi to everyone. i'm kind of new to ubuntu, and i installed 9.04 , dual boot with windows xp using wubi.

my internet connection works fine in windows, yet i can't get it to work in ubuntu. i tried reading some forums, and tried the "sudo pppoeconfig" command, and the message that appeared was

"Sorry, I scanned 2 interfaces, but the Access concentrator of your provide did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

I've seen this message occur to other users as well in different forums, but i can't find the right solutions for me. i know the ubuntu community is very friendly, and any response will be highly appreciated.

P.S. this happened to me when i tried using 8.04 a few months ago, and i got to a end dead. figured might as well wait for the new release, but still stuck here apparently.

---

### Post by jamest09 on 2009-09-08
How do you connect to the interwebs? Via a router?

---

### Post by bogart_2003 on 2009-09-08
Yeah I think so. When I'm using Windows, it automatically connects to the internet (don't have to click connect or something). Sorry kind of noobish. Thanks.

---

### Post by bogart_2003 on 2009-09-09
anyone please?

---

### Post by Iowan on 2009-09-09
Along similar lines... are you connected via dial-up, DSL, cable? Is there a "box" between your computer and whatever cable connects to your ISP? Some dial-up providers had (maybe still have) custom Windows-dialing software. Most have a router or modem - into which you simply plug an ethernet cable.

---

### Post by ddrichardson on 2009-09-09
Can you open a terminals, type:
```
sudo tail -f /var/log/messages
```
Connect (or try to) and report the messages from the terminal.
I suspect it's to do with your ISP, because Windows doesn't need a return-ping, linux does which is a common issue.

---

