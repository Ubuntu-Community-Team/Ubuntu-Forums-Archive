---
title: "email relay"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by Ckal on 2013-04-21
Hello,

I have four Panasonic network security cameras in my house. They can send an email if there is an alarm condition. Unfortunately they are using port 25 for SMTP and my ISP is blocking that port lately. I have a UBUNTU 12.04 machine available on the network that could act as somekind of relay. What is the easiest way of relaying the emails from the cameras (using port 25) to the ISP (using port 587). All the cameras are sending email to the same email address.

Thank you

---

### Post by priyans on 2013-06-25
If the email volume is very low (I assume) , you can use smtp relays for free provided by some providers like sendgrid.

---

