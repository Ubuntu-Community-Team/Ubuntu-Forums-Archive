---
title: "Long connection time for Mumble"
date: 2013-06-09
forum: Multimedia Software
---

### Post by oleoleole on 2013-06-09
I have a minor annoyance with Mumble and the connection. Mumble tries to use UDP connection, but it fails the first time. If I get connected the first time, I got into TCP mode first, and then after some time it turns back to UDP. If I close Mumble and restart it, it connects directly and fast as it should into UDP mode.

In my dual-boot windows, it's no problems at all, so firewall and router is not the issue here.

Is there some special kernel settings which has been set for ubuntu releases according to UDP? Or anything else that is temporarily blocking it?

---

### Post by Trustable on 2013-07-31
I have exacly the same problem. 
Mumble output:
 UDP packets cannot be sent to or received from the server. Switching to TCP mode.
 UDP packets can be sent to and received from the server. Switching back to UDP mode.

---

### Post by Trustable on 2013-08-05
I found a solution: Bind the server to an IP address:
[http://mumble.sourceforge.net/Murmur.ini%23host#host](http://mumble.sourceforge.net/Murmur.ini%23host#host)
Found it here: [http://sourceforge.net/p/mumble/discussion/492607/thread/dd5408be](http://sourceforge.net/p/mumble/discussion/492607/thread/dd5408be)

---

### Post by oleoleole on 2013-10-15
> **Trustable said:**
> I found a solution: Bind the server to an IP address:
[http://mumble.sourceforge.net/Murmur.ini%23host#host](http://mumble.sourceforge.net/Murmur.ini%23host#host)
Found it here: [http://sourceforge.net/p/mumble/discussion/492607/thread/dd5408be](http://sourceforge.net/p/mumble/discussion/492607/thread/dd5408be)

This doesn't work for me, I always had host defined, tried both hostname and IP.

This works without any problem in Windows (unortunatelly), connects directly with UDP. In Kubuntu, it takes about a minute before it connects to the server. First getting TCP connection before it switches to UDP. If I close mumble, and start it again, it joins the server right away. This happens only after the first launch of mumble in kubuntu.

---

### Post by oleoleole on 2013-10-29
Well, problem gone after upgrading to 13.10.

---

