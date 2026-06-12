---
title: "Secure webcam streaming?"
date: 2017-08-11
forum: Multimedia Software
---

### Post by simoncks1994 on 2017-08-11
Hi everyone,

I am new to this forum and network streaming and I would appreciate any help!!

My girlfriend is going to study overseas and we would like to set up a stream/connection where we can access to see each other in webcam anytime. We tried Skype and Google Hangout before but the chat could not last long due to fluctuating internet bandwidth. We had to restart the chat once per ~20 mins. This is annoying and unfeasible as we are not at our computers all the time. We tend not to use IP camera as its traffic goes through the manufacturer's server in the middle which we do not know their location and security. Streaming is our option because even the connection is lost by one side, the receiver could still reconnect to the host once connection resumes.

We also tried to use RTP streaming with VLC client through Hamachi (VPN client) but it did not work even after disabling firewall. We find that the host can stream to HTTP with username and password specified, but we are still concerned with stealing content in the middle of transmission. Conclusively, our trials with VLC did not work.

Both of us use Ubuntu 16.04LTS and host/receive streams on campus networks. 

We are looking for secure solutions that WORK. Feel free to ask if my description is not detailed enough. We are even open to solutions using a commercial software as long as it is below the price of USD100 each year. However, any secure method will work fine. 

We are happy to include as many methods as possible. I appreciate any suggestion.:)

---

### Post by QIII on 2017-08-11
Hello!

You might try Jitsi.  It's open source, standards compliant and supports encryption protocols.  I believe the University of Strasbourg hosts its development.

At $0/mo, it's within your stated budget.

---

### Post by simoncks1994 on 2017-08-14
Hi QIII,

After some trial, indeed it works well. However, the Google Talk is something very similar to Skype where both of us have to connect once again. It is unlike streaming which the host would not need to initiate the connection every time.

Simon

---

