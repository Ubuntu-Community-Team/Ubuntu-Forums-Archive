---
title: "OpenVPN hostile login attempts"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by csnafu on 2012-06-28
Hi there!
I was checking on my OpenVPN log when I saw this:
```
...
Jun 28 16:43:37 server ovpn-srv[1350]: 66.249.66.164:49042 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Jun 28 16:43:37 server ovpn-srv[1350]: 66.249.66.164:49042 TLS Error: TLS handshake failed
Jun 28 16:43:37 server ovpn-srv[1350]: 66.249.66.164:49042 Fatal TLS error (check_tls_errors_co), restarting
Jun 28 16:43:37 server ovpn-srv[1350]: 66.249.66.164:49042 SIGUSR1[soft,tls-error] received, client-instance restarting
...
Jun 28 21:13:58 server ovpn-srv[1350]: 66.249.66.164:64767 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Jun 28 21:13:58 server ovpn-srv[1350]: 66.249.66.164:64767 TLS Error: TLS handshake failed
Jun 28 21:13:58 server ovpn-srv[1350]: 66.249.66.164:64767 Fatal TLS error (check_tls_errors_co), restarting
Jun 28 21:13:58 server ovpn-srv[1350]: 66.249.66.164:64767 SIGUSR1[soft,tls-error] received, client-instance restarting
...
Jun 28 23:04:08 server ovpn-srv[1350]: 66.249.66.164:37146 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Jun 28 23:04:08 server ovpn-srv[1350]: 66.249.66.164:37146 TLS Error: TLS handshake failed
Jun 28 23:04:08 server ovpn-srv[1350]: 66.249.66.164:37146 Fatal TLS error (check_tls_errors_co), restarting
Jun 28 23:04:08 server ovpn-srv[1350]: 66.249.66.164:37146 SIGUSR1[soft,tls-error] received, client-instance restarting
Jun 28 23:04:08 server ovpn-srv[1350]: TCP/UDP: Closing socket
```Now from my understanding this is a failed login attempt from the IPs listed. The fun stuff is that the IPs belong to Google accrding to my web research. Now is some crazy stuff going on there or is it because my OpenVPN server is running on TCP 21 (have to get into it from a place where more or less all ports are closed, so I had to choose TCP 21) and it is a webcrawler that wants to index an FTP server?

Cheers

---

