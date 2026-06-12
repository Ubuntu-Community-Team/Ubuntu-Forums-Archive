---
title: "Using xfm over ssh?"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by raincityrunner on 2012-10-29
I've managed to stream files over SSH over my LAN. The problem is that some of the pathnames for my files are ridiculously long. I've heard that it's possible to run x-windows apps (e.g. xfm?) over SSH -- how can I go about doing this so that I don't need to use command line to type extremely long and complex pathnames?

---

### Post by Lars Noodén on 2012-10-30
You can connect to the remote machine using ssh with X11 forwarding (-X) enabled.  Then any graphical programs you run on the remote machine will have their output forwarded to the local display.

```

ssh -X -l raincityrunner othermachine.example.org
firefox &

```

That can be condensed further if you only want to run one program and then exit afterwards.

```

ssh -X -l raincityrunner othermachine.example.org firefox

```

You'll want a fast connection with low latency because it can be a little sluggish otherwise.  Usually it is fine over the LAN.

---

