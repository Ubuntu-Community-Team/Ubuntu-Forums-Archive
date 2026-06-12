---
title: "Localhost not working!"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2006-07-13
Hi 

I have been trying to follow the 'how to setup a email server' thread on this forum buy after doing so I have a curious problem...

Now I can't visit [http://localhost](http://localhost) with firefox, although I can do it with konqueror. What I should see is my apache default page... and I do when I use konqueror, but with firefox it just hangs!

Anyone see this before or know how to fix it?

Mike

---

### Post by tkjacobsen on 2006-07-13
make sure you have a line like this:
127.0.0.1 localhost 
in /etc/hosts

also check if lo (the loopback device) is configured:
ifconfig

---

### Post by Mickeysofine1972 on 2006-07-13
Yep lo seems to be OK:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:412 (412.0 b)  TX bytes:412 (412.0 b)

Also, I checked /etc/hosts and it had localhost as 127.0.0.1 

BUT

hibbert-desktop was 127.0.1.1

I changed it to the same as localhost and restarted apache2 which now says it is using 127.0.0.1!

Are there any more files that tell firefox where to go for localhost?

Mike

---

