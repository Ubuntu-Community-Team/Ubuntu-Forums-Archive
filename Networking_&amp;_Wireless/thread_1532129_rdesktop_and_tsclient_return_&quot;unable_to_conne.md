---
title: "rdesktop and tsclient return &quot;unable to connect&quot; with no explanation"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by suckerpunch on 2010-07-16
Hey all,

So I was trying to remotely access my XP laptop from my Ubuntu laptop. I read up on tsclient and rdesktop and tried both methods. For example, in the terminal, I typed:

rdesktop <host ip>

However, this came back with the following error:

autoselected keyboard map en-us.
ERROR: <host ip>: unable to connect.

After a bit of internet searching, I found the solution to the keyboard problem. I typed:

rdesktop -k en-us <host ip>

This yielded the following error:

ERROR: <host ip>: unable to connect.

No clarification, no explanation. nothing. Does anyone have any ideas?

-Lily

---

### Post by paulcauchon on 2010-10-10
Hi Lily, 

The first line concerning the keyboard is not really an error as much as an indication that it automatically selected the en-us keyboard layout. 

As far as the unable to connect line, I ran into the same problem today. In my case, the problem was that my XP laptop was not running XP Professional. Is your windows machine running a version of XP other than Pro? That could be your problem.

Are you using a router? If you are, make sure you set up port forwarding on the router to send traffic at your Internet IP on port 3389 to the host machine. 

Make sure as well that you have set up RDP on your Windows machine to be enabled in the firewall and under computer settings. I think its right click on my computer--> properties-->remote--> check some box and enable remote desktop connection. 

I hope at least some of this helps!

---

