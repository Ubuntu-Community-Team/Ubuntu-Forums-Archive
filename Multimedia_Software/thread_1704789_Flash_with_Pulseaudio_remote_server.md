---
title: "Flash with Pulseaudio remote server"
date: 2011-03-11
forum: Multimedia Software
---

### Post by scarleo on 2011-03-11
Hi, I'm usually using a remote server to play my audio which I in most cases find works pretty well. However lately when playing flash videos the audio and the video has started to stutter heavily when I use the remote server as audio sink. If I switch to a local audio sink it plays just fine. I have tried different browsers. 

Does anyone know what causes this or know how to fix it?

Thanks in advance.

Maverick 10.10

---

### Post by Tails9 on 2011-09-07
I have exactly the same problem. Really annoying. Especially since normal local video like .avi works great. I tried switching to youtube in HTML5 but that didn't help either.

I did found this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/511562](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/511562)
And this was a possible solution (haven't tried yet: 

"Here's a workaround that I'm using. On the server, do:

socat TCP-LISTEN:4000,fork UNIX-CONNECT:/home/tom/.pulse/f4bd336578327b5cd658a18b4afff4a1-runtime/native &

Important: You'll have to replace "f4bd336578327b5cd658a18b4afff4a1-runtime" with the correct directory that's present on your system. I also configured pulseaudio to listen for remote connections (using papref), but don't know if that's necessary.

On the client, do:
PULSE_SERVER=<server-ip>:4000 <program to run> &

For example:
PULSE_SERVER=<server-ip>:4000 firefox & 
"

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/511562/comments/14](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/511562/comments/14)

Natty Narwhal 11.04

---

