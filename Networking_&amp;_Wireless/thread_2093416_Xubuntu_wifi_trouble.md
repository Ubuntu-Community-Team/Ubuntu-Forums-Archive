---
title: "Xubuntu wifi trouble"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by greasegum on 2012-12-10
Apologies in advance. I hate to be the one coming around with the thorny technical issues. :confused: Since upgrading to Quantal I have noticed the following strange behavior with my Wifi:

When connecting to my school's network, I will get good connectivity, depending on where I am. Then without changing anything I start to experience horrific netlag.

Refreshing my network connection often fixes the netlag, but only for about 3-5 minutes. Then the buggy part: when I reconnect the wifi tray app, it will connect, but once connected:

1. the icon shows all grey bars (i.e. low signal) regardless of the network's actual signal strength.

2. clicking on the icon, it does not list a Wireless Network as connected, and the scanned network list remains unchanged. (although the tooltip shows the correct network id.)

Rebooting brings everything back to normal, until my network speeds get bogged down again...etc.

I don't know how to troubleshoot this problem, if it is indeed all symptoms of the same problem. It seems to be. Anyone got an idea of how to fix?

Thanks!!!

a bit more info: 

during lag issues, I get this message in the kernel ring buffer: ```
failed to flush all tx fifo queues
```

---

