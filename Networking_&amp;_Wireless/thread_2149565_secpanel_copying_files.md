---
title: "secpanel: copying files"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by ezk2 on 2013-05-29
Hallo, maybe this is not the right place to post and if so I apologise.
A few days ago I set up a server running ubuntu 12.04 server with webmin,samba and opessh installed. If I try to connect via webmin  I can login and I can administrate the server as I like; but if I try to connect via secpanel (installed on the client ) in order to copy files, I receive this:

```
debug1: Enabling compression at level 6.
debug1: Authentication succeeded (password).
debug1: Local connections to LOCALHOST:8820 forwarded to remote address 127.0.0.1:9920
debug1: Local forwarding listening on ::1 port 8820.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 8820.
debug1: channel 1: new [port listener]
debug1: Remote connections from LOCALHOST:9910 forwarded to local address 127.0.0.1:8810
debug1: channel 2: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: remote forward success for: listen 9910, connect 127.0.0.1:8810
debug1: All remote forwarding requests processed
debug1: Sending environment.
debug1: Sending env LANG = it_IT.utf8
debug1: Sending command: cat > .listserver; chmod +x .listserver; ./.listserver
-e Trying interpreters...

Trying tclsh...
debug1: client_input_channel_req: channel 2 rtype exit-status reply 0
debug1: channel 2: free: client-session, nchannels 3
debug1: channel 0: free: port listener, nchannels 2
debug1: channel 1: free: port listener, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 3280, received 2192 bytes, in 0.9 seconds
Bytes per second: sent 3679.2, received 2458.8
debug1: Exit status 127
debug1: compress outgoing: raw data 4862, compressed 1978, factor 0.41
debug1: compress incoming: raw data 128, compressed 109, factor 0.85

---------- SecPanel ----------
Connection closed
Press <Return> to continue...

```

at the bottom right end of secpanel there is agent active in a green background color.

Is anyone aware of this? How to solve it?
Thanks a lot to anyone answers.

---

