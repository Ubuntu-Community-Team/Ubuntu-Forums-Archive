---
title: "exit doesn't log out of remote system"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by netopalis45 on 2013-02-01
I log into a remote Ubuntu server for school that uses a tcsh shell. While trying to permanently set my default shell to bash (I don't have access to the /etc/passwd file) I came across the problem of instead of just typing "exit" to log out of the system, I now have to do it twice. First it logs me out of bash and then I think it is logging me out of tcsh before closing the connection. Is there any way of changing it so I only have to type "exit" once? I have also tried using logout but that doesn't work at all.

I have also tried using a sleep command ie. "exit && sleep 5 && exit" but that was just a long shot and it didn't work

---

