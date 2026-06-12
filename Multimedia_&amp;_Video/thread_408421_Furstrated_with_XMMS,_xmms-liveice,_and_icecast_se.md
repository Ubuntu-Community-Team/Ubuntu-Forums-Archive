---
title: "Furstrated with XMMS, xmms-liveice, and icecast server"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by oldweasel on 2007-04-13
I have XMMS and XMMS-liveice setup to use ALSA to stream audio to my icecast server using LAME encoding. 

I start the sound file and i can see XMMS playing away happily, icecast detects the connection and shows the source as being connected, but no bandwisth useage. If I connect to the icecast server I get a client connection, but no sound.

Scanning other forums there appears that there might be an issue with XMMS-liveice, icecast, and ALSA. Does anyone know if this is the case?

Can anyone help me figure out what my issues might be? 

If this is a por way to send output audio from XMMS to my icecast server, can anyone suggest any other methods?

Thanks in advance!

---

### Post by trjnhrse44 on 2007-04-13
2 things.
What port are you streaming on? Is that port firewalled?
and also are you trying to listen from the same network or outside the network?  If it's outside you must forward the traffic on your router to that IP:port address

most likely you are using port 8000 and it is probably locked down on your server system.

---

### Post by oldweasel on 2007-04-13
aye, i am using port 8000, how do i detect if it is firewalled on my home system?

I use SSH (PuTTy) to connect to the server system with port 8000 forwarded to the recieving system. 

The client (Winamp) on the remote system can connect to the icecast server, but recieves no sound. 

What also concerns me is that icecast shows no bandwidth use. Is this normal?

---

