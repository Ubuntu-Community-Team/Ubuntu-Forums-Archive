---
title: "remote shell"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by dink123 on 2010-07-19
hi..
i'm creating a remote shell using simple socket programming. where the client enters commands it will execute on the server and the output will be printed on the clients terminal.
the server will run the commands received by the client  through the 'system(char * cmd)' function.
the commands like 'pwd' , 'ls', 'df' which has a output, will be displayed on the clients terminal. but for the commands like 'rm' 'mkdir' which has no output to display, when entered through the client it will just hang there NOT allowing me to further run the commands.
arent there any way to overcome this problem?

---

