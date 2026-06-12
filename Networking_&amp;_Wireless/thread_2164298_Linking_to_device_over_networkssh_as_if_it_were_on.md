---
title: "Linking to device over network/ssh as if it were on same computer"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Darvenkry on 2013-07-31
Hi guys, just wondering how I could tether a USB GPS from one linux machine to another one over ssh or network. Can you somehow create a symbolic link of the /dev/gps or wateva over ssh? 

Approaches?

---

### Post by ian-weisser on 2013-07-31
Let's say you have a GPS device attached to a server.
You want a client to be able to read the GPS data from the server (not the device on the server).

A couple ways to do this are described in forum thread: [http://navigatrix.net/viewtopic.php?f=4&t=172](http://navigatrix.net/viewtopic.php?f=4&t=172)
Some good information also at [http://nst.sourceforge.net/nst/docs/user/ch11.html](http://nst.sourceforge.net/nst/docs/user/ch11.html)
And there is even more good information on the gpsd manpage.

On the server end, run gpsd to listen to the locally attached GPS. 
```
gpsd [other args specific to your device] -S 2947      # create a gpsd server on TCP port 2947
```

On the client end, run gpsd to use a TCP connection instead of the default serial connection.
```
gpsd gpsd://your.server:2947    # get information from the gpsd server
```

If the server is behind a firewall from the client, then you will need to forward the port.

---

### Post by Darvenkry on 2013-08-01
Awesome. Didnt know this existed and is exactly what I am looking for. Thanks ian-weisser.

---

