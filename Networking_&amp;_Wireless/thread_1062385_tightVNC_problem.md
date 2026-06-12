---
title: "tightVNC problem"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-02-06
i was setting up tightvnc viewer so i could connect to my server remotely. It connects beautifully how ever i would like a couple things.

1)Be able to have the Guest displayed in fullscreen **and** be able to use the clients system. (or have the viewer come up in a window.....simliar to the built in vnc viewer)

2)Though this is not a major issue i wanted to have copy and paste in between the two machines over vnc


as of right now i am using tightvnc on the client and the built in vnc server on the server.

client: ubuntu 8.10
server: ubuntu 8.04

AND i dont want to use the built in vnc viewer because its super slow. Thanks for your comments ahead of time!

---

### Post by ductiletoaster on 2009-02-06
Well i feel dumb... to get the viewer to pop up in a window mode u just type:

```
vncviewer ###.###.#.###
``` for some reason i tought that wouldnt work

But is still would like to know:

1) how to have the server in fullscreen but still be able to use the client display....... like how in virtualbox u can have the virtual machine on fullscreen but u can still rotate the main systems cube.

2) be able to copy and paste would be cool


O and how hard is tightvnc server to configure?

---

### Post by superprash2003 on 2009-02-07
by fullscreen do you mean **vncviewer x.x.x.x -fullscreen**

---

### Post by ductiletoaster on 2009-02-07
Yeah i know thats how u get fullscreen but there is a problem atleast for me when i use it. When u use the vinagra in fullscreen u can still use the current machine and rotate cube and so on. but with tightvnc i get locked into that vnc.

---

### Post by trieb on 2009-02-13
Yea, I get the same problem.  I guess we are looking for a different viewer b/c the build in version of tightVNC is worthless.  

I try to run it in full screen mode and not only does the gui look years old, it will lock up and stop responding to keyboard events.  I use vnc all the time at work to go from a windows laptop to either a redhat or aix server, and I don't this problem with them.

---

