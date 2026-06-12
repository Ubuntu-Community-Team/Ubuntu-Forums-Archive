---
title: "Lubuntu 12.04: Netcat timeout problems"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2012-10-31
I've installed the netcat-traditional package on both my client (Lubuntu 12.04) and server (Debian 6.0) and would like to use the tool to transfer files from server to client. 

Server side :

```

$ nc -l -p 8888 < file.txt

```

Client side:

```

$ nc -w 3 server.ip.address 8888 > file.txt

```

In my example the **-w** flag sets the timeout to 3 seconds, however things just hang indefinitely at client side and I have to Control-C to end the session. The file is transfered none the less. Is there syntax error or is there a better way to end a session once the said file has been transfered ? I have never had this problem with previous versions of Ubuntu.

Cheers,
UC

---

