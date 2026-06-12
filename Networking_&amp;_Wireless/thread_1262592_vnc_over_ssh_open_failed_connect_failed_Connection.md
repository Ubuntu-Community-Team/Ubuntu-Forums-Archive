---
title: "vnc over ssh: open failed: connect failed: Connection timed out"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by zippaplick on 2009-09-10
Hi,

I'm trying to connect to a vnc server that running behind an ssh server.

Basically this arrangement:

    [my box (vncviewer)] <--> [ssh.foobar.com] <--> [vncserver]

the vncserver is running on port 5901 so on "my box" I set up a tunnel with:

    ssh ssh.foobar.com -f -N -C -T -l zippaplick -L5901:vncserverip:5901

then I try:
    vncviewer localhost:1

but it always eventually fails to connect with:
    open failed: connect failed: Connection timed out

I know I'm setting up the tunnel correctly since i can forward the ssh port 22 like this:
    ssh ssh.foobar.com -f -N -C -T -l zippaplick -L5555:vncserverip:22

and then connect to it with:
   ssh zippaplick@localhost -p5555

Any ideas/suggestions on why the vnc connection is timing out?


Thanks!

---

