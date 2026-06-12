---
title: "How to redirect pulse audio through ssh?"
date: 2011-05-20
forum: Multimedia Software
---

### Post by qiet72 on 2011-05-20
Hi,

I would like to redirect pulseaudio sound through ssh to a local client while seeing content through a vnc connection. Something like this:

Client: ssh -L 5901:localhost:5901 [email]user@server.net[/email]
Client: vncviewer localhost:5901
Server: Run a web browser with flash content on the server through vnc, but sound is redirected to the client.

A good example is Facebook flash games, most flash games require flash player 10 but my local client only supports up to version 9 because of the architechture.

Why?  A number of reasons:
- The local client is not powerful enough to run flash content
- The local client has an architechture that flash does not support, eg ARM, PowerPC, etc.
- Save battery power - use the resources of a server instead of the client.

Environment: 
Both the client and server have pulse audio installed and working.
The server does not have a physical sound card installed but the client does.
Server: Ubuntu 10.04
Client: Ubuntu 10.10

I have tried these links so far:
[http://razor.occams.info/blog/2009/02/11/pulseaudio-sound-forwarding-across-a-network/](http://razor.occams.info/blog/2009/02/11/pulseaudio-sound-forwarding-across-a-network/)
[http://superuser.com/questions/68048/ubuntu-getting-audio-to-play-from-local-speakers-over-ssh](http://superuser.com/questions/68048/ubuntu-getting-audio-to-play-from-local-speakers-over-ssh)

Suggestions?

br,
Qiet72

---

### Post by aeiah on 2011-05-20
before embarking on this.. does vnc really run smoothly enough over the internet for you to play flash games? and if you're doing this locally on the same network, why throw ssh into the mix? pulseaudio is networked already.

---

### Post by qiet72 on 2011-05-20
Hi,

Facebook games don't really required a lot of video bandwidth.  They do require a lot of cpu and memory though.  Anyways, I would like to use it more for google translate.  It requires flash 10 and it just needs to send audio, that's it.

The reason for ssh is security.  My server is on the internet and only ssh is allowed through.  My bandwidth should be high enough for audio as my uplink is 2Mbps.

qiet72

---

### Post by qiet72 on 2011-05-20
Hi,

I just tried some facebook game testing via vnc via a 4Mbps gsm connection.  It works amazingly fast compared to if I played it locally on my client.  Of course, no sound until I get pulse to work through ssh.

Qiet72

---

### Post by qiet72 on 2011-05-22
Hi,

After a lot of fiddeling around, I concluded that version 0.9.22 uses an incompatible protocol with version 0.9.15 of pulseaudio.  So I found another solution:

Well, here is my almost perfect solution:

```

local sound server: ssh -L 5901:localhost:5901 -L 1234:localhost:1234 <remote sound client>
remote sound client: mkfifo output.wav
remote sound client: parec | sox -t raw -r 44100 -s -L -b 16 -c 2 - "output.wav" & cat output.wav | nc -l 1234
local sound server: mkfifo fifo.wav
local sound server: paplay --volume=48000 -v fifo.wav & nc localhost 1234 >fifo.wav

```

As you can see, I use port 5901 for VNC and port 1234 to forward sound.  The only thing is it takes at least 30 seconds before it plays on the speakers.

Any ideas why such a huge latency?  I am guessing it has something to do with parec.

br,
qiet72

---

