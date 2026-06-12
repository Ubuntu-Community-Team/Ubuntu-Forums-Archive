---
title: "Remote Desktop -&gt; How can I address machines outside my network?"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by QwUo173Hy on 2010-05-27
Basically, I'd like to set up my parents Ubuntu machine to be a remote desktop server and connect to their computer from anywhere in the world and perform the odd task for them.

I've read somewhere that I need a router that supports this kind of behaviour (and not the free one that comes from most ISPs).
I also would like to know how addressing would work, as every computer in their home (I believe) is seen as having the same IP from the internets point of view.

Can anyone explain a bit about it?

---

### Post by Peter09 on 2010-05-27
Basically you tell the router which is front of the target machine to forward the protocol that you are using to the target machine. This is normally done using Port numbers.
 
Most protocols have standard ports (shh = 22) you don't need to use these ports but to aid in this description I will.
 
You would run up shh on your machine and provide it with the internet facing IP address of the router at your parents home. When the requests gets to that router (on port 22) it will then forward to specified IP address (say 192.168.0.5) on the Local network behind it.
 
Most routers have this capability. Its called Port Forwarding. You need to get into the Admin screens for that router.
 
(A simplistic description)

---

### Post by QwUo173Hy on 2010-05-27
Thanks Peter. The simplistic description was very astute of you - exactly what I need :)

I'll give that a try.

Thanks again,
Jarlath

---

### Post by stevevartousky on 2010-05-27
If you're looking for a ramote desktop client try
[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

