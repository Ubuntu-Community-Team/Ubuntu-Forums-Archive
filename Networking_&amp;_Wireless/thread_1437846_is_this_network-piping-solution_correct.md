---
title: "is this network-piping-solution correct?"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by maweki on 2010-03-24
Hello,

I have a remote site with one linux server acting as a proxy and as the only connection between their local subnet and the subnet where the router (with nat) is on.

On this remote network are many devices with webinterfaces. Since they often use frames they are not usable with those browsers I have on my ssh-terminal on the proxy.

So I devised this solution with the named pipe "httppipe"

```
cat httppipe | nc -l -p 8000 | nc 192.168.144.222 80 >> httppipe
```

I forwarded port 8.000 from the Router to the linux-server.

This connection seems to work only every second time (every other time it shows an error in Firefox).

Is this idea correct for a simple pipe to and from this device?

---

