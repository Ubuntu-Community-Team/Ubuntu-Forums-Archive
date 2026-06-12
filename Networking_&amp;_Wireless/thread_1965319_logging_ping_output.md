---
title: "logging ping output"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by rozo on 2012-04-25
Hello,

I want to periodically log ping output to a file but if I get the error: "connect: Network is unreachable" it's not logged, it's only written on a console. Why? How can I log also this error message?

---

### Post by jonobr on 2012-04-25
How are you doing this?

Have you written a script or something to do this?

Depending on requirements, you may want to get some small monitoring application, but again, Id recommend posting more info on what you have currently

Thanks
jonobr

---

### Post by cmont899 on 2012-04-25
To log both stdout and stderr to a file use the following:


ping google.com &> output.file

---

### Post by rozo on 2012-04-26
Thanks cmont899, that is what I need!

---

### Post by Vishal Agarwal on 2012-04-27
The tee command can be used.

ping [www.google.com](www.google.com) | tee output.log

---

