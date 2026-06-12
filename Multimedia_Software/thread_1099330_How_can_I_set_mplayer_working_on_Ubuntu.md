---
title: "How can I set mplayer working on Ubuntu?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by JinyongLee on 2009-03-18
Hi~

I'm trying to use mplayer to get rtsp packet from ffserver on Ubuntu 8.04.

And I set ffserver.conf all blocked but left only those lines.



# Port on which the server is listening. You must select a different
# port from your standard HTTP web server if it is running on the same
# computer.
Port 5454

# Address on which the server is bound. Only useful if you have
# several network interfaces.
BindAddress 0.0.0.0

# Number of simultaneous requests that can be handled. Since FFServer
# is very fast, it is more likely that you will want to leave this high
# and use MaxBandwidth, below.
MaxClients 1000

# This the maximum amount of kbit/sec that you are prepared to
# consume when streaming to clients.
MaxBandwidth 1000

# Access log file (uses standard Apache log file format)
# '-' is the standard output.
CustomLog -

# Suppress that if you want to launch ffserver as a daemon.
NoDaemon

.....
.....
(I've blocked all the lines)

##################################################################
# RTSP examples
#
# You can access this stream with the RTSP URL:
#   rtsp://localhost:5454/test1-rtsp.mpg
#
# A non-standard RTSP redirector is also created. Its URL is:
#   [http://localhost:8090/test1-rtsp.rtsp](http://localhost:8090/test1-rtsp.rtsp)

<Stream test1.avi>
Format rtp
File "/var/www/stream/test1.avi"
ACL ALLOW localhost
</Stream>


This is what I've set for the ffserver.conf file.

And I installed mplayer by apt-get install mplayer.

I try to open the test1.avi file on mplayer by..

mouse right click on mplayer -> open -> play URL:     and 

rtsp://localhost:5454/var/www/stream/test1.avi

then I get this message.

Couldn't resolve name for AF_INET6:127.0.0.1

So I googled for the message and got some answer for it.

I wrote in the terminal that

sudo emacs ~/.mplayer/config

and I wrote

prefer-ipv=yes

But the mplayer gives me the same error message.

I have no idea how I can handle it and I'm desperate T_T

Please give me some advice.

Thanks.


      -Jin

---

### Post by khelben1979 on 2009-03-18
Hi!

Have you ever looked at [this place]("http://ffmpeg.mplayerhq.hu/ffserver-doc.html") (FFServer Documentation) ?

---

### Post by JinyongLee on 2009-03-18
I'm really grateful for your reply.

I've read the article already, but I just remembered the sentence.

"It can also stream from files, though that is currently broken."

Hum.... then..

I have to find another way to stream the file T_T

Does anybody have some recommendation? 

Thanks always.


                        -Jin-




> **khelben1979 said:**
> Hi!

Have you ever looked at [this place]("http://ffmpeg.mplayerhq.hu/ffserver-doc.html") (FFServer Documentation) ?

---

