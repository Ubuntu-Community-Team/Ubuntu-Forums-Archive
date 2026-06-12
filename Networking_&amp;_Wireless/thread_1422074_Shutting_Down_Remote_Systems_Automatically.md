---
title: "Shutting Down Remote Systems Automatically"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by linuxrockers on 2010-03-05
How to shut down the remote systems connected in my network? I have a GUI developed in Java and I need to schedule a time for all my clients and by that time I need all the clients to get shut down...!

---

### Post by kidders on 2010-03-07
Hi there,

Since you're working in Java, you could use RMI to instruct machines to shut down.

There are lots of other ways though, for example ...```
[[ "`nc -l -p 6969`" =~ "password" ]] && shutdown -h +60
```Alternatively, you could put something together involving SSH (probably the least convenient option) or SNMP.

One way or another, you'll need something listening on all the clients for an instruction to schedule a shutdown.

---

### Post by linuxrockers on 2010-03-07
Sorry ! I couldn't  understand what was given in the reply..! Can you tell me some what clear please...!!!

---

### Post by iponeverything on 2010-03-07
You can create a cronjob to shutdown at a given time.

---

### Post by kidders on 2010-03-08
> **linuxrockers said:**
> Sorry ! I couldn't  understand what was given in the reply..! Can you tell me some what clear please...!!!Are you trying to use Java to remotely schedule shutdowns? If not, iponeverything's suggestion will do what you need.

---

### Post by linuxrockers on 2010-03-09
Please tell me some simple way for remote shut down...!!!

---

### Post by kidders on 2010-03-10
Hi again,

It's still not clear if you're looking for a way to schedule a shutdown with Java, or if something independent of Java will do. The other important detail you've omitted is how secure your network environment is. For example, would you care if shutdowns could be triggered by someone other than you?

---

### Post by linuxrockers on 2010-03-10
Actually I need to implement it in a Lab where they check and shut down all the systems manually at the end of each day!!

---

### Post by kidders on 2010-03-10
Please post your answers to the following questions:


[LIST]
[*]Why did you mention Java? Are you looking for a Java-based method of remotely shutting machines down?
[*]Is security an issue? How hard does it need to be for someone other than you to schedule a shutdown?
[/LIST]
It's hard to post a useful answer to your question without a few details about what you're trying to achieve.

---

