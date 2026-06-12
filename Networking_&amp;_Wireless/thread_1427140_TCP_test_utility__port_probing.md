---
title: "TCP test utility / port probing"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Nilzor on 2010-03-11
I need a simple tool that acts as a TCP server on a specified port for testing firewall settings. From the client side I can then simply telnet into the port and see if I get answer. Would also be nice to be able to type something from the server so that I see that the communication also works, not just the initial connection.
 
Might be that Ubuntu comes with such a tool by default, I simply just don't know if that's the case. Also, I'm sure this could be coded with < 100 lines of C code.
 
Anyone?

---

### Post by Nilzor on 2010-03-12
Found the solution: netcat (nc)

---

