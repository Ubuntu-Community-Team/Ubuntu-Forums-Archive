---
title: "ssh vpn keeps hanging up on me"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by therealtroff on 2012-12-12
Hi everyone

I've been using ssh -w to set up some temporary layer 3 tunnels. However, after a few times (or a few weeks - not sure which one is important), the tunnel has started going down after 10-20 seconds and I can't make out why from the debug outputs.

Here is the server side:
```
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: read<=0 rfd 8 len 0
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: read failed
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: close_read
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: input open -> drain
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: ibuf empty
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: send eof
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: input drain -> closed
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: send close
Dec 12 14:30:04 localhost sshd[12098]: debug3: channel 0: will not send data after close
Dec 12 14:30:04 localhost sshd[12098]: debug2: channel 0: rcvd close
Dec 12 14:30:04 localhost sshd[12098]: Received disconnect from x.y.z.w: 11: disconnected by user
Dec 12 14:30:04 localhost sshd[12098]: debug1: do_cleanup

```

Several seconds after the server claims the client disconnected, I get the following output on the client side:
```
root@beer:/home/user# debug2: channel 0: write failed
debug2: channel 0: close_write
debug2: channel 0: chan_shutdown_write: shutdown() failed for fd 4: Socket operation on non-socket
debug2: channel 0: output open -> closed

```

Both sides are running openssh 5.8p1. It used to work and I haven't touched the configuration files at either end. Ideas are most welcome.

---

