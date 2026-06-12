---
title: "How to enable loopback connections on Ubuntu?"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by xanaftp on 2010-08-22
Hello!

Here's my situation:

I run a webserver Apache2, php5, and MySQL. They are all set up correctly and I can access my website at [http://localhost](http://localhost)

I have, also installed, noip2 to update my IP address to no-ip.com for my domain name.

Here's the problem: I can access my website through that domain name on other computers, both on internet and on the same network. But I cannot access it from my own computer (using the domain name instead of localhost).

I need to be able to access the domain name on my computer because some pages on my website have been defined as the address to my domain name and not localhost. I cannot change this to localhost because if I do then people outside cannot work the webpages correctly.

I had the same troubles on Windows before and I simply enabled loopback connections by typing in my private IP address along with the domain name into the Windows hosts file.

How do I fix this problem in Ubuntu?

I use version 10.04.

Help would greatly be appreciated!

---

### Post by relay_man on 2010-08-22
I'm not sure, but you may be able to add a line to  /etc/hosts and fix your problem.

Try "man hosts" (without the quotes) at the terminal for more info.

---

### Post by Iowan on 2010-08-22
*/etc/hosts* should have a line similar to:```
127.0.1.1 machine.domain machine
``` Alternately, you could add a line:```
internal.ip.address machine.domain machine
``` (dunno if this will conflict with the previous definition...)

---

### Post by xanaftp on 2010-08-22
Thank you. I didn't know Ubuntu had hosts file like Windows. It works now. Thanks guys!

---

