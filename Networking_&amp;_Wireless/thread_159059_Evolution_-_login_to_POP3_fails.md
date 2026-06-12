---
title: "Evolution - login to POP3 fails"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by Erle on 2006-04-12
I set up Evolution for connecting to my ISP for email.  I can send mail, no problem, but when I try to receive, I get a login failure message:

Unable to connect to POP server mail.xxxx.com.
Error sending password: -ERR Login failed.

Please enter the POP password for [email]yyyy@xxxx.com[/email] on host mail.xxxx.com

In the error popup, I re-enter my password but get the same error.

Any ideas?

---

### Post by cstudent on 2006-04-12
This is probably a simple settings problem. Who is your isp? And do they have a web page with instructions on how to setup a pop email client. It doesn't matter  what email client it is written for. You should be able to use the instructions to determine what Evolution settings you need.

---

### Post by Erle on 2006-04-12
[QUOTE=cstudent]This is probably a simple settings problem. Who is your isp? And do they have a web page with instructions on how to setup a pop email client. It doesn't matter  what email client it is written for. You should be able to use the instructions to determine what Evolution settings you need.[/QUOTE]

Been there done that!  I have a cable modem, and have been using Internet Explorer 6.  I just got Ubuntu loaded on another PC and am trying to get things set up.  I can send mail OK so SMTP works fine.  For some reason my password doesn't seem to be working right.

---

### Post by cstudent on 2006-04-12
Have you messed around with the authentication types under the Receiving Mail tab in the account setup? There is also a button for checking supported types.

---

### Post by Erle on 2006-04-13
I've messed around with just about everything that makes sense (to me, at least). It's almost as if I'm sending a wrong password, so maybe I'll check with my ISP to have them reset it and I'll start over.

---

### Post by roundtrip on 2006-04-30
[QUOTE=Erle]I've messed around with just about everything that makes sense (to me, at least). It's almost as if I'm sending a wrong password, so maybe I'll check with my ISP to have them reset it and I'll start over.[/QUOTE]

This nOOb can confirm the exact same error type here. 

Is there a way to control the number of simultaneous connection that Evolution will make at any one time? Wonder if it is a problem with too many connections from Evolution to the server, resulting in the server dumping on / complaining.

---

