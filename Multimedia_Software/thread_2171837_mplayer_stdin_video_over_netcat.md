---
title: "mplayer stdin video over netcat"
date: 2013-09-01
forum: Multimedia Software
---

### Post by kerryhall on 2013-09-01
Hello,

I am trying to view video over netcat with mplayer. On the client, I first run the following:

 nc.traditional -l -p 5000 | mplayer - -cache 2048

Then on the server I run the following:
mencoder tv:// -tv driver=v4l2:width=800:height=600:fps=5:device=/dev/video0 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000 -nosound -of avi -o - | netcat 192.168.1.10 5000

My issue is that mplayer will not open a window on the client until I issue a ctrl+c on the server and press enter in the terminal on the client that mplayer is running in. Once I do that, a window will pop up on the client and show the video briefly.

Anyone have any ideas? Open to other ways to stream video over the network in a lightweight manner. This would be cool to solve though.

I have also tried it the other way, where the server is the one that listens, and the client is the one that connects:
[http://n0ah.tumblr.com/post/30990262/streaming-movies-with-netcat-and-mplayer](http://n0ah.tumblr.com/post/30990262/streaming-movies-with-netcat-and-mplayer)
Exact same results, the mplayer window won't pop up until I issue ctrl+c on the server.

(I also realize that this is insecure. My plan is to eventually tunnel this over ssh.)
(I also realize that technically I might be incorrect about which machine should be classified as the client, and which as the server in the first example. Just didn't want to muddy the waters by changing naming schemes between examples :P)

---

### Post by rai_shu2 on 2013-09-01
Maybe I'm reading that wrong, but does nc -l even work with -p? I mean -l means to listen for a connect, and -p specifies particular port.

---

### Post by kerryhall on 2013-09-02
Sure, it just listens on a certain port, just as sshd listens on (normally) port 22. Try this:

Machine a:
netcat -l -p 999 (I had to use sudo for some reason)

Machine b:
echo "Hello" | nc.traditional <ip of machine a> 999

(You may have to fiddle with the naming, nc vs netcat vs nc.traditional)

---

### Post by rai_shu2 on 2013-09-02
Okay, I just looked this up and it says:

```
-l      Used to specify that nc should listen for an incoming connection
             rather than initiate a connection to a remote host.  It is an
             error to use this option in conjunction with the -p, -s, or -z
             options.  Additionally, any timeouts specified with the -w option
             are ignored.
```

---

### Post by kerryhall on 2013-09-08
Anyone have any ideas on this?

---

