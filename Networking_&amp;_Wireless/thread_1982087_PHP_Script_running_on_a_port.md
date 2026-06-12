---
title: "PHP Script running on a port"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by JspPeterson on 2012-05-17
Hello, for several weeks I have been attempting to get a PHP socket to open up a port and connect to a JavaScript WebSocket. It only works on the machine hosting the script. I have port forwarded the port with my router, I don't know what I should I edit in apache or ubuntu config. Can someone type me up with a tutorial of how to forward on port 2000 for a PHP Socket?

---

### Post by JspPeterson on 2012-05-22
bump? :c

---

### Post by roelforg on 2012-05-22
Look up how to setup apache httpd port forwarding on your router and replace port 80 with 2000

---

### Post by JspPeterson on 2012-05-22
Apache works fine. It's just using PHP sockets that doesn't work. I forward port 2000 for example, it wont work. But port 80 works fine and if I change that port website will not work as expected. I have googled around and my last resort is asking on here

---

