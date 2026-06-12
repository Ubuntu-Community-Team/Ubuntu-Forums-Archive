---
title: "IP Address Redirection"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by JerryM on 2009-02-20
Hello everyone.

I have an application running on Ubuntu that will connect to a remote server. I am running another server application on the same machine. I would like to (transparently) redirect the application to my server. I would appreciate any help in being able to do this. I am not sure where I would start.

Currently:
Application -> Internet -> Server

What I want:
Application -> My Server

Thanks.

---

### Post by mpokrywka on 2009-02-21
You can redirect output traffic to your local server using iptables:
```

export PROTOCOL=tcp
export REMOTE_SERVER_IP=1.2.3.4
export REMOTE_SERVER_PORT=80
export LOCAL_SERVER_PORT=8080

iptables -t nat -A OUTPUT -p $PROTOCOL -d $REMOTE_SERVER_IP --dport $REMOTE_SERVER_PORT \
         -j REDIRECT --to-port $LOCAL_SERVER_PORT

```

this means: connections from this host that goes to remote_server:remote_port will be instead redirected to localhost:server_port

---

