---
title: "understanding the basics of x11vnc"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by andrea_bio on 2011-03-06
Hi
 
I'm trying to set up x11vnc server on a linux VM and I'm having some problems. I expect many of these are caused by my lack of understanding of network issues.
 
I believe if i start the server like so I am setting it up to listen on its default port of 5900 and that this isn't secure
 
x11vnc -forever -usepw 
 
I can see a server i have started in this way by ps -ef | grep 'vnc'
 
I believe i should be tunnelling over ssh to have a secure connection. I have tried this command
 
x11vnc -auth -forever guess -display :0 -localhost -rfbport 20000 -xkb -rfbauth ~/.vnc/passwd
 
What does this mean? I believe this is listening on the localhost on port 20000? are ssh requests forwarded to port 20000. Is that what tunneling over ssh means? Does this mean i need to set up port forwarding. I am using a non-standard port for ssh. 
 
What windows client can i use to allow me to tunnel over ssh. I have tried realvnc using hostname:non_standard_ssh_port and i get the error 'reading version failed: not anRFB server'
 
Also if i start the server by the second command, I cannot see the vnc server at all in the ps -ef list. Why is this?
 
thanks a lot

---

