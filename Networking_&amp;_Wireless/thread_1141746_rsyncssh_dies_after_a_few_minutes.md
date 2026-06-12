---
title: "rsync/ssh dies after a few minutes"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by minime283 on 2009-04-28
So I just setup a computer with 9.04 server and 2 hard drives raided and I'm trying to rsync my stuff to the server. After a few minutes, the syncing just stops and disconnects, and (sometimes) I can no longer connect (I get a 'no route to host') with ssh to the computer and have to reboot it. Other times, I am able to connect using ssh after a few minutes. If I have the computer on, there is no noticeable difference in the speed of the terminal. I've tried a different NIC and that doesn't work either. This is a line I grabbed from ifconfig after I could no longer connect through ssh once:

RX packets: 14480727 errors:0 dropped:8005 overruns:0 frame:0

Any ideas on how to fix this? Please let me know if I need to put out more information.

---

### Post by omax on 2009-04-29
I have a similar problem. When I use ssh it disconnects me after a short period of time and after that I can't reconnect for several minutes. Must be a 9.04-specific problem, never happend before.

---

### Post by coutts99 on 2009-04-29
Can you post the full ifconfig

---

