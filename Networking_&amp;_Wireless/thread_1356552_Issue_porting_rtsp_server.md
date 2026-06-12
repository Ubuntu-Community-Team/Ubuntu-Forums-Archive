---
title: "Issue porting rtsp server"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by krishna_27 on 2009-12-16
Hi, I am new to Ubuntu  and I am trying to port a rtsp server that is running on windows to ubuntu(9.10). I have ported the code and it is compiling and running fine. But after my server goes an listens on port 554, if i try to connect from a client, i a getting a "Connection refused" at the client. The following things I have already checked.

1. My server and client are in the same network.
2. ufw is off on the server.
3. I got a wireshark log on the server. I found that it is not going ahead of the TCP handshake. When the client is sending SYN the ubuntu server is sending a RST.

Anyone who has any idea on this please help.

Thanks
KK

---

### Post by krishna_27 on 2009-12-16
Hi, I am new to Ubuntu  and I am trying to port a rtsp server that is running on windows to ubuntu(9.10). I have ported the code and it is compiling and running fine. But after my server goes an listens on port 554, if i try to connect from a client, i a getting a "Connection refused" at the client. The following things I have already checked.

1. My server and client are in the same network.
2. ufw is off on the server.
3. I got a wireshark log on the server. I found that it is not going ahead of the TCP handshake. When the client is sending SYN the ubuntu server is sending a RST.

Anyone who has any idea on this please help.

Thanks
KK

---

### Post by krishna_27 on 2009-12-16
Hi, I am new to Ubuntu  and I am trying to port a rtsp server that is running on windows to ubuntu(9.10). I have ported the code and it is compiling and running fine. But after my server goes an listens on port 554, if i try to connect from a client, i a getting a "Connection refused" at the client. The following things I have already checked.

1. My server and client are in the same network.
2. ufw is off on the server.
3. I got a wireshark log on the server. I found that it is not going ahead of the TCP handshake. When the client is sending SYN the ubuntu server is sending a RST.

Anyone who has any idea on this please help.

Thanks
KK

---

### Post by krishna_27 on 2009-12-16
Hi, I am new to Ubuntu  and I am trying to port a rtsp server that is running on windows to ubuntu(9.10). I have ported the code and it is compiling and running fine. But after my server goes an listens on port 554, if i try to connect from a client, i a getting a "Connection refused" at the client. The following things I have already checked.

1. My server and client are in the same network.
2. ufw is off on the server.
3. I got a wireshark log on the server. I found that it is not going ahead of the TCP handshake. When the client is sending SYN the ubuntu server is sending a RST.

Anyone who has any idea on this please help.

Thanks
KK

---

### Post by i.r.id10t on 2009-12-16
Why bother porting?  Check out Darwin Streaming Server from Apple...

---

### Post by cariboo on 2009-12-16
Please don't create multiple threads on the same subject. I have merged your 4 threads.

---

