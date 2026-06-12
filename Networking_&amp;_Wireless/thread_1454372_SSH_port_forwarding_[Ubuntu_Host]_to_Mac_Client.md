---
title: "SSH port forwarding [Ubuntu Host] to Mac Client"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by charliehorse55 on 2010-04-14
I have open-ssh installed on my ubuntu computer, and I can SSH into it perfectly. 

ssh myname@255.255.255.255
```

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

3 packages can be updated.
0 updates are security updates.

You have new mail.
Last login: Wed Apr 14 12:37:30 2010 from xxxx@xxx.com

myname@ubuntu~$:
```

However when I run 
```
sudo ssh -Nv -L 80:127.0.0.1:80 myname@255.255.255.255

```

I get 
```
debug1: Authentication succeeded (password).
debug1: Local connections to LOCALHOST:80 forwarded to remote address 127.0.0.1:80
debug1: Local forwarding listening on ::1 port 80.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 80.
debug1: channel 1: new [port listener]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Connection to port 80 forwarding to 127.0.0.1 port 80 requested.
debug1: channel 2: new [direct-tcpip]
channel 2: open failed: connect failed: Connection refused
debug1: channel 2: free: direct-tcpip: listening port 80 for 127.0.0.1 port 80, connect from 127.0.0.1 port 52112, nchannels 3

```

What did I do wrong? Do I need to modify the default Ubuntu SSH server settings?

---

### Post by Skaperen on 2010-04-14
There is nothing listening on port 80 of 127.0.0.1 on the remote host you connected to.  Web servers typically are configured to listen to specific, usually public, IP addresses.  You might first try to find out what IP address the web server is listening on.  On the remote try this command:```
netstat -antp | fgrep :80
``` to see what IP address the web server is listening on (if the remote is not running Linux, you may need to do some other command).

---

### Post by charliehorse55 on 2010-04-14
It returns nothing. If I remove the grep part, I only get about 20 lines or so. Is this a problem?

(Port 80 isn't among them!)

EDIT: the host is running linux 2.6.31-17-generic (Ubuntu 9.10)

EDIT2: It just worked. Came up with this line:

tcp        0      0 10.0.1.77:52763         74.125.67.138:80        ESTABLISHED 15168/firefox

---

### Post by dwarfolo on 2010-04-14
For what I can see you are trying to forward from localhost to 12.0.0.1 .... which, again, is localhost.

```
debug1: Local connections to LOCALHOST:80 forwarded to remote address 127.0.0.1:80
```

AFAIK, assuming A.B.C.D is the IP address of your ubuntu remote computer and you want to access a web server on this computer through an SSH tunnel, you need to use a different command

```
ssh -L 80:A.B.C.D:80 user@A.B.C.D
```

This way you can simply open your browser and navigate to [http://localhost](http://localhost), and you're actually connecting to [http://A.B.C.D](http://A.B.C.D) but through the SSH tunnel.

---

### Post by charliehorse55 on 2010-04-14
> **dwarfolo said:**
> 

AFAIK, assuming A.B.C.D is the IP address of your ubuntu remote computer and you want to access a web server on this computer through an SSH tunnel, you need to use a different command



What I'm trying to do is forward my HTTP traffic on my Mac Laptop through my Ubuntu desktop. 

So I visit website [www.ubuntu.com](www.ubuntu.com), the data is sent from my laptop to my desktop, my desktop downloads the data through my home internet connection, then reuploads it back to my laptop.

---

### Post by dwarfolo on 2010-04-14
AFAIK you cannot do that through SSH tunnel and SSH port forwarding.

You should setup your ubuntu box to act as a gateway or as a proxy.

---

### Post by Skaperen on 2010-04-14
You can forward to one specific web server with -L option.  But in this case, the web server is listening on 74.125.67.138 not 127.0.0.1.  So change the "[FONT=monospace]-L 80:127.0.0.1:80[/FONT]" to "[FONT=monospace]-L 80:74.125.67.138:80[/FONT]" on the ssh command line.  Then you'd be connecting to the address the web server is listening on.  Then on the web browser go visit URL [http://127.0.0.1/](http://127.0.0.1/)

Now, if what you want to do is pipe all your web surfing over through the Ubuntu machine, so it looks like it came from that Ubuntu machine, that's different.  If your web browser on the MAC supports proxy via SOCKS protocol, and the ssh client on the MAC supports the -D option, then you can do it that way.  If not, then regular HTTP proxy can be used by running a web proxy server, such as squid, on the Ubuntu machine, and redirecting to that.

---

### Post by charliehorse55 on 2010-04-14
> **Skaperen said:**
> Now, if what you want to do is pipe all your web surfing over through the Ubuntu machine, so it looks like it came from that Ubuntu machine, that's different.  If your web browser on the MAC supports proxy via SOCKS protocol, and the ssh client on the MAC supports the -D option, then you can do it that way.  If not, then regular HTTP proxy can be used by running a web proxy server, such as squid, on the Ubuntu machine, and redirecting to that.

Thanks, this is exactly what I needed!

---

