---
title: "How do I disable MPD support in forked-daapd"
date: 2015-11-18
forum: Multimedia Software
---

### Post by ocwo92 on 2015-11-18
I want to run forked-daapd on my server but it seems to conflict with MPD. Specifically, it fails with the following log output:

```
[  LOG]      mpd: Could not create connection listener for mpd clients on port 6600
[FATAL]     main: MPD thread failed to start
```
which makes perfect sense because MPD is already listening on port 6600.

However, I can't find any documentation on how to configure forked-daapd, so I don't know how to disable its MPD service, if at all possible.

How do I prevent forked-daapd from servicing MPD clients?

---

### Post by ejurgensen on 2015-11-20
Edit /etc/forked-daapd.conf and set the port to 0:

> # MPD configuration (only have effect if MPD enabled - see README/INSTALL)
mpd {
    # TCP port to listen on for MPD client requests. 
    # Default port is 6600, set to 0 to disable MPD support.
#    port = 6600

    # HTTP port to listen for artwork requests (only supported by some MPD clients
    # and will need additional configuration in the MPD client to work).
    # Set to 0 to disable serving artwork over http.
#    http_port = 0
}


---

### Post by ocwo92 on 2015-11-20
Wonderful, thanks! I wasn't able to find this documentation anywhere. Where did you find it?

---

