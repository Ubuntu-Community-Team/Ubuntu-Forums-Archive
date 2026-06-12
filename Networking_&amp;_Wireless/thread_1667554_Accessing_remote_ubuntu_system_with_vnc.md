---
title: "Accessing remote ubuntu system with vnc"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by lovelyvik293 on 2011-01-15
I am trying to connect my ubuntu system from remote computer through vnc. I installed vncviewer on the conmputer i want access and x11vnc on the other one. I used the port 5431 for listning vnc. And i got my public ip from 
[http://www.whatismyip.com/](http://www.whatismyip.com/). Now when i used the command 

```
x11vnc -connect myIp:5431

```

I am getting 
```
15/01/2011 12:48:13 called initialize_xfixes()
15/01/2011 12:48:23 selection_send: no send: uninitialized clients
15/01/2011 12:48:24 selection_send: no send: uninitialized clients
15/01/2011 12:49:02 selection_send: no send: uninitialized clients

```

So please help me to resolve this problem.
Thanks.

---

### Post by krunge on 2011-01-17
Are you sure it is really connecting to the viewer? Does the viewer indicate something is happening? Note that there is some ambiguity in whether one specifies the port or VNC display number to the viewer.

Run netstat -ant on the viewer end to see which port it is actually LISTENING on.

Run netstat -ant on the x11vnc end to see which port x11vnc is connecting to.

The messages you pasted in pasted in probably don't mean anything but x11vnc is trying to connect to the viewer.

If it still doesn't work with my suggestions above, paste the full x11vnc output and the vncviewer output.

---

