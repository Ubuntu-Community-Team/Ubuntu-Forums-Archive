---
title: "Xinetd (connection refused)"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Dannik on 2010-06-02
I am in the process of learning network programming with Python, and currently I am trying to learn how xinetd works with servers. So wrote a small Python script, installed xinetd, and added the following code into /etc/xinetd.conf (the code was copied from the book I'm reading):

```

service pythontestserver {
	flags = NAMEINARGS
	type = UNLISTED
	port = 51423
	socket_type = stream
	protocol = tcp
	wait = no
	user = root
	server = /root/example.py
	server_args = /root/example.py
}

```

Now, I try to test the script with telnet (using "telnet localhost 51423"), but I get the "connection refused" error. Yes, I restarted xinetd and made sure it's working.

If I run a server that listens to the port directly, I can connect with telnet just fine. But when I let xinetd listen on it, the connection gets refused. I have a feeling I'm missing something simple here (which would make sense, since I'm a noob).

Please help me, I really want to get xinetd working so I can continue my studies. Thanks in advance.

---

### Post by Dannik on 2010-06-02
Okay I removed xinetd and installed inetd, which is working (yay). Nonetheless, I would still like to know any suggestions about why xinetd didn't work for me. Maybe I missed an elementary step while setting it up? Thanks,

---

