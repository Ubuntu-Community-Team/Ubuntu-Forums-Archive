---
title: "managing Apache virtual host from the command line"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by fabjoa on 2010-11-20
Howdie Ubuntians

I have created a shell script in PHP to manage my virtual hosts in Apache2. Something like "```
a2vs -c -fqn my-new-virtual-server.local --port 8078 -ip 127.0.27.27 
```"... etc, and the script will update a virtual host template file and create the required files. But as I never like to reinvent the wheel, I was wondering if Apache already had a way to invoke that in a cli way as well. apache2ctl does not seem to, but maybe a "a2envs" something...

Do you know something about that?

---

