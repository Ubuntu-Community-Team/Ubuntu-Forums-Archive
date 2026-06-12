---
title: "4oD, Demand5 &amp; ITV Player RTMPDUMP"
date: 2012-03-19
forum: Multimedia Software
---

### Post by paulemony on 2012-03-19
Ubuntu 11.10 connected via UK VPN (I'm abroad). Using Ron999's RTMPDUMP instructions I've never actually managed to download from any of those players:
[B]1 Start the server with this command:-
Code:
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
2
See the message in console:-
Streaming on rtmp://0.0.0.0:1935
3
Refresh the page and play the video, now wait till the RTMPDump command appears in console.
4
Interrupt the server:-*Ctrl-c
5
Stop the server with this command:-
Code:
sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
6
Copy and paste the RTMPDump command to download the video.[/B]

With 4oD & Demand5 the the video stops & the connection closes itself after step 3 with error  messages [B]WARNING: HandShake: Type mismatch: client sent 6, server answered 8
ERROR: Handshake failed
Closing connection... done![
ERROR: WriteN, RTMP send error 32 (42 bytes)
ERROR: RTMP_ReadPacket, failed to read RTMP packet header[/B]

Same with ITV Player with a variation on the last error message:
[B]ERROR: RTMP_ReadPacket, failed to read RTMP packet body. len: 4698489
Closing connection... done!
[/B]
Anybody managed this & how?

---

