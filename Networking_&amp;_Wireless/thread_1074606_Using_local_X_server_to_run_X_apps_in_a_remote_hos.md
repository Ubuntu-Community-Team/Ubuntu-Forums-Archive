---
title: "Using local X server to run X apps in a remote host"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by bixejo on 2009-02-19
In my work network I can enable TCP connections to my laptop X server so that I can login into a server, set the DISPLAY environment variable and then launch an X application that is displayed on my local X server.

I'm trying to do it from my home Internet network, but there my laptop gets an internal IP assigned by my router, and only this last has got a true Internet IP.

Does anyone know whether it's possible to do it and hopefully how?

Thank you,

---

### Post by whoop on 2009-02-19
Use port-forwarding on your router..

---

### Post by bixejo on 2009-02-19
Thank you for your answer, whoop.

What you tell me lies beyond my knowledge, I'm afraid. Could you tell me, please, where can I find more info on this issue?

Thank you again,

---

### Post by bixejo on 2009-05-01
I found a direct way to do this. Just login into the remote host with

```

ssh -l username **[COLOR=Red]-X[/COLOR]** remote.host.address
```The -X option directly enables a tunnel that forwards X connections to your local machine.

---

### Post by xkaliburx on 2009-05-01
The only problem you might have is where the machine is you want (which is why the previous said about port forwarding).

Depending on your router, you can take normal ssh traffic (port 22) and forward it to your private machine.

Ex. if your X server is 192.168.1.10.  In your router, you say take all public traffic on port 22 and send it to the .10 local address.  You can then do your ssh -X publicIP which will give you an ssh termnial to that machine.  You then type the app name, ex. firefox and the X11 will forward and firefox will start on your home/local machine.

---

