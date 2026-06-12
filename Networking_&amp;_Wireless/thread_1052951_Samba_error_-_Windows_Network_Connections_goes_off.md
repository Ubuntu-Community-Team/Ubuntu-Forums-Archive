---
title: "Samba error - Windows Network Connections goes offline many times"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by johnybgood11 on 2009-01-28
Hi everyone,

I have an Ubuntu server installed to serve for file, ldap and printer in a small office network.

I've installed and configured samba, openldap and cups and all is working apart form samba server which sometimes goes down.

Sometimes, my windows users loose connections to the mapped network drives. From what i could understand if I deactivate my local area connection and activate it the network becomes avaible again.

The samba error log, is:

```
Samba Error log:
 
[2009/01/28 12:18:44,  0] lib/util_sock.c:write_data(1059)
[2009/01/28 12:18:44,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Connection terminated by peer
[2009/01/28 12:18:44,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2009/01/28 12:18:44,  0] lib/util_sock.c:write_data(1059)
[2009/01/28 12:18:44,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Connection terminated by peer
[2009/01/28 12:18:44,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2009/01/28 12:18:50,  0] lib/util_sock.c:write_data(1059)
[2009/01/28 12:18:50,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Connection terminated by peer
[2009/01/28 12:18:50,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2009/01/28 12:19:37,  1] smbd/service.c:make_connection_snum(1194)
  welka-1 (192.168.1.10) connect to service Media initially as user nobody (uid=65534, gid=65534) (pid 11900)
[2009/01/28 12:19:41,  1] smbd/service.c:make_connection_snum(1194)
  welka-1 (192.168.1.10) connect to service Carlos Paixao initially as user carlos.paixao (uid=1011, gid=513) (pid 11900)
```

Any idea??

Thanks in advance
João Ribeiro

---

### Post by HvRooyen on 2009-03-04
[Bump]
Similar problem here, any ideas?

TIA

---

### Post by johnybgood11 on 2009-03-04
> **HvRooyen said:**
> [Bump]
Similar problem here, any ideas?

TIA

Yup I solved by removing user authentication.

---

### Post by HvRooyen on 2009-03-07
Thanks, but no joy there. Security = share already.

Consistent error in log file seems to be:
lib/util_sock.c:get_peer_addr_internal(1596)
 getpeername failed. Error was Transport endpoint is not connected
 read_socket_with_timeout: client 0.0.0.0 read error = connection timed out.

Google is not my friend with this one.

Does anyone know the meaning of this error?

TIA
H.

---

### Post by redmk2 on 2009-03-07
> **HvRooyen said:**
> ...

Google is not my friend with this one.

Does anyone know the meaning of this error?

TIA
H.

Try [http://www.google.com/search?q=%22Transport+endpoint+is+not+connected%22+*+samba&btnG=Go%21]("http://www.google.com/search?q=%22Transport+endpoint+is+not+connected%22+*+samba&btnG=Go%21")

---

