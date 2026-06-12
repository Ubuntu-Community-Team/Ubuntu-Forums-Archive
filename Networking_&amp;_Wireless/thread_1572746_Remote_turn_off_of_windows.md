---
title: "Remote turn off of windows"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2010-09-11
I am writing a script that is goin to have my server to a automated backup of windows. I have it so it will wake the machine windows machine up and do a sync with the specified files. However I need the server to be able to shut the windows machine down. 

I found this guide:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html")

And they say to use this command:
```
"net rpc SHUTDOWN -C "some comment here" -f -I x.x.x.x -U user_name%password"
```

However when i try it I get this error
```

Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_CONNECTION_REFUSED 

```

---

### Post by ductiletoaster on 2010-09-11
no body?

---

### Post by RetchingRabbit on 2010-09-11
> **ductiletoaster said:**
> I am writing a script that is goin to have my server to a automated backup of windows. I have it so it will wake the machine windows machine up and do a sync with the specified files. However I need the server to be able to shut the windows machine down. 

I found this guide:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html")

And they say to use this command:
```
"net rpc SHUTDOWN -C "some comment here" -f -I x.x.x.x -U user_name%password"
```

However when i try it I get this error
```

Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_CONNECTION_REFUSED 

```

127.0.0.1 is the local loopback IP. It exists on the machine you ran the command on, not the remote server. Try using the correct IP address for the server.

---

### Post by ductiletoaster on 2010-09-11
> **RetchingRabbit said:**
> 127.0.0.1 is the local loopback IP. It exists on the machine you ran the command on, not the remote server. Try using the correct IP address for the server.

I was using the correct Ip but i just messed up the command

This is what i was typing in:
```
net rpc SHUTDOWN x.x.x.x -U user_name%password
```

This is what i should have used:
```
net rpc SHUTDOWN -I x.x.x.x -U user_name%password
```

The difference was the "-I". My mistake.

---

