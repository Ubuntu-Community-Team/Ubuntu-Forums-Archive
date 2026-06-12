---
title: "Having trouble getting Mozilla Thunderbird to work over a SOCKS proxy."
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-08-27
Currently, as I am typing this right now, I have Firefox connected to the Internet over a SOCKS proxy using the following command syntax:

```
ssh -D 9999 -C user@ipaddress
```

I changed the address in the above example from the actual command I'm using, but the important stuff is there of course.

When I use thunderbird over the direct connection I have to the Internet, it connects to the server (which should mean that I have the send/receive server settings correct).  But when I switch the Network settings in Thunderbird to use SOCKS and make it look the same way as I have it look in Firefox's network settings for using a proxy, the connection is refused...  So I'm not sure what I'm doing wrong.

---

### Post by Brandon Williams on 2009-08-27
This won't be too helpful, I'm afraid, but I can tell you that you're doing the right thing. Proxy configuration for firefox and thunderbird is identical, so making sure that all the settings between the two match is the right way to go.

One additional thing that occurs to me is that some ISPs configure their mail servers to only allow incoming connections from machines on their network. Does the machine that you're running the ssh client on also have an ssh server running? If it does, try connection to localhost with your proxy tunnel instead of the remote server. If that works, then open an ssh session to the remote server and then from that machine, use telnet or netcat to connect to the correct port on the mail server in order to verify connectivity from the ssh server to the mail server.

---

