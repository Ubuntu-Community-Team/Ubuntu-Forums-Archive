---
title: "Port Forwarding from public address to private address."
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by daniel50096230 on 2010-02-23
Hi all.

I am beginner to Ubuntu. I have a question here and appreciate if anyone can advice me.
Currently my OS is Ubuntu 9.04 Jaunty Jackalope Desktop OS and my web server is Apache2. I have a public address 60.x.y.z and my pc local address is 10.x.y.z. I have a web app in my Apache2 which currently run in localhost(10.x.y.z).

I would like to enable the web app so that it could be browse from outside. I know there maybe some port forwarding process and some commands involved in order to do that. But I have no idea on the steps to do that.

Is there anyone can brief on the ways to doing that?

---

### Post by byStanderone on 2010-02-24
...i think you can do that using firestarter, configure it under policy.

---

### Post by daniel50096230 on 2010-02-24
do you means firestarter can perform the action that i need?

---

### Post by Iowan on 2010-02-24
Is the public address on the box - or is it on a router/modem that connects to the box? In other words - is there a router/modem between the server and the internet?

---

### Post by daniel50096230 on 2010-02-24
Yes, there is a router between the server and the Internet..Kindly advice.

---

### Post by Iowan on 2010-02-24
What *probably* needs to happen is to set up port-forwarding in the router.

---

