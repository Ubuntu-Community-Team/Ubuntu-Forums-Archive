---
title: "scripts when connecting to a particular network?"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by accabrown on 2009-05-27
Is there a way to automate the running of particular scripts when my laptop is connected to one particular network?

I have a little script on my laptop that mounts a whole bunch of server shares from my home network. I would like it to run automatically when the laptop is on that particular network (and obviously not otherwise). I'd also like to have these shares umounted when the connection goes down. 

But I don't understand which scripts run when a connection is made and when it is dropped, since everything with network manager is so slick and runs so automagically. 

My instinct is to put some little test like a ping to my desktop, and if that gets a response, then run the mounting script. But where should the test go? Is there something more useful I could test for, like the name of the network?

I have tried, and failed, to find the answer to this with search tools, though I know it must be out there somewhere.

---

### Post by runderwo on 2009-06-18
[http://ldn.linuxfoundation.org/node/29576](http://ldn.linuxfoundation.org/node/29576)

---

### Post by accabrown on 2009-06-19
> **runderwo said:**
> [http://ldn.linuxfoundation.org/node/29576](http://ldn.linuxfoundation.org/node/29576)

Thank you so much! That's exactly what I needed to know, although a whole lot more complicated than I had hoped. Still, the magic of cut and paste ...

---

