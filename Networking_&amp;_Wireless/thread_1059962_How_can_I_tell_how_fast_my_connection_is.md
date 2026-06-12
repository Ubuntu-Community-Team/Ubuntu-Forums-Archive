---
title: "How can I tell how fast my connection is?"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by Jay D. on 2009-02-04
I have set up a desktop/fileserver, and was wondering how can I tell how fast i am connected to the network, or how fast I am transferring files?

Thanks!

---

### Post by OrangeCrate on 2009-02-04
[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

---

### Post by sedawk on 2009-02-04
```

sudo ethtool eth0

```
Check "speed" and "duplex".

Testing "real" network speed is a little big more complicated,
e.g. it depends on the network architecture, the target machine,
the general network load, etc.
When downloading a file from a heavily used disk you might
actually test the disk speed, not the network speed.

For a simple test you can take two linux boxes and put a big file that fits
into (half of) the free space of the /dev/shm "ramdisk" on both machines.
Then transfer the file with ssh from one machine to the other and
check speed. Keep in mind that this might cause heavy network load,
e.g. if the machines are in different subnets and other people will
experience a slowdown in the network.

---

### Post by markitoxs on 2009-02-04
I also always recommend to use some file transfer for this.

> **sedawk said:**
> ```

sudo ethtool eth0

```
Check "speed" and "duplex".

Testing "real" network speed is a little big more complicated,
e.g. it depends on the network architecture, the target machine,
the general network load, etc.
When downloading a file from a heavily used disk you might
actually test the disk speed, not the network speed.

For a simple test you can take two linux boxes and put a big file that fits
into (half of) the free space of the /dev/shm "ramdisk" on both machines.
Then transfer the file with ssh from one machine to the other and
check speed. Keep in mind that this might cause heavy network load,
e.g. if the machines are in different subnets and other people will
experience a slowdown in the network.

---

### Post by Jay D. on 2009-02-04
Well that ethtool got me to where I was looking for.

Thanks!

---

### Post by cariboo on 2009-02-04
I use iperf to check internal network performance. Run iperf as a server on one computer and use:

```
iperf -c <server>
```

there are more  options to be found in:

```
man iperf
```

Iperf is available in the repositories.

Jim

---

