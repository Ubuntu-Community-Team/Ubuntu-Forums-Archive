---
title: "Juniper networks VPN on ubuntu 11.04 not working"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by machielr on 2011-06-24
Good day guys

       I have a problem which I am not sure whether it has been posted as yet as I can not find anything.

       I was running ubuntu 10.04 for quite a while and one of our clients uses the Juniper SSL VPN connections in order to connect to them.


       This was working perfectly.

       However, this week I made a backup of my system, wiped my drive and installed Ubuntu 11.04 with which I am very happy except for the fact that the connection to this client now does not work.

      Every time I try to connect to the client using the ssl connection it simply says "connection time out".

      I thought that it might be a setting on my machine due to the backup restores, so I did a fresh 11.04 installation on a different machine and directly after base installation tried it again, yet the same thing happened.
 
       I also thought it might be specific to firefox so I tried 2 other browsers with no luck.

       This does work with my credentials on my windows VM and on my ubuntu 10.04 vm though.


       Can anyone please assist me or point me in the right direction in order to solve this problem as I am not sure what else to look at.

    I would REALLY appreciate assistance in this as it is critical that I get this connection working properly.

Regards
Machiel

---

### Post by passyspam on 2011-07-25
I'm having the same problem with 11.04, besides I've already tried using the sun java jdk with no luck.

Thanks,

---

### Post by cyberluigi2k on 2011-08-15
Did you guys managed to resolve it?
I'm having the same issues here...

Thanks

---

### Post by passyspam on 2011-08-24
No, no luck, I'm using windows in the meantime. My guess is that it's related to something in ubuntu 11.04

---

### Post by texmorgan on 2011-09-22
I hate to break it to all of you, but it is likely not a problem with Ubuntu as much as it is a problem with the browser or security requirements.

I've tried multiple browsers and most of them barely work or don't work at all.  The best luck I have had has been with Epiphany and Chromium.  Firefox and others just fail completely.

Please let me know if you do find anything better.

---

### Post by passyspam on 2011-09-23
I've tried everything with Chrome, the juniper window opens and after exactly 30 secs the "Time Out" message appears. With epiphany no juniper window opens at all.
Were you able to make it work with any browser? What do you mean by "barely work"?

Thank you!

---

### Post by goombalord on 2011-09-26
I too couldn't get the browsers to work with this in 11.04, but I found this, [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html), and it works for me. Hope this helps you too.

---

### Post by passyspam on 2011-09-27
That didn't work for me as I don't use certificates, the log in process I have involves a token a pin a user and password...

---

