---
title: "Can access port 8081 locally but not across LAN"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by rkrizan on 2013-03-16
Hello,

I can access port 8081 locally on my laptop, but I cannot access the server via that port on my other laptop connected to the same wireless network. I am quite baffled. I can access any other typical port, 80, 22, 21, etc no problem, but not 8080 nor 8081. Any suggestions? I am using 12.10 64bit.

---

### Post by The Cog on 2013-03-16
First, let's see if it's listening for connections. Can you post the output of the command:
```
netstat -lntu
```
We're looking to see what address (if any) is listening on port 8081.

---

### Post by rkrizan on 2013-03-16
Here is my netstat ouput:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8080          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8081          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:8090          0.0.0.0:*               LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::5800                 :::*                    LISTEN     
udp        0      0 127.0.1.1:53            0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:55780           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:64783           0.0.0.0:*                          
udp6       0      0 :::34807                :::*                               
udp6       0      0 :::33861                :::*                               
udp6       0      0 :::5353                 :::*

---

### Post by papibe on 2013-03-16
Hi rkrizan.

What service are you trying to run?

Sometimes there are extra steps on the program itself. For instance, live pictures from 'motion' can be accessed from 8081, but they are restricted only to localhost unless you set it otherwise (on the conf file).

Regards.

---

### Post by rkrizan on 2013-03-16
papibe,

I am in fact using 'motion' -- after using the "configuration panel" to try and turn off local-only options, which motion was erroneously reporting was disabled, I completely went through the configuration file and found they indeed had not been. So, problem fixed. Thank you.

---

