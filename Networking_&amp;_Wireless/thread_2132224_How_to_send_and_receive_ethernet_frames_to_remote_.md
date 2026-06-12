---
title: "How to send and receive ethernet frames to remote systems using  tap interface"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by kalamram on 2013-04-04
Hello, I am using ubuntu 12.10 and gnuradio for my project purpose.
There I need to send a data stream using iperf to outside world.

Example 100 Mb data to host B from host A.
I need to spilit the data stream at lower level and send to different interfaces like eth0 and eth1.
Then in gnuradio stack, creating a virtual interfaece using tunctl mechanism. After creating tap interfaces, I want to send and receive the data through tap interface to my gnuradio,USRP tx/Rx.
Here, I need to get eth0 data stream in tap0 interface, same as eth1 data strem in tap2.

Is it possible to route the data stream from eth0 to tap0 and to gnuradio stack.
I tried bridge mechanism, but here I need to attach eth0 and tap0, and need to give IP address to bridge interface (e.g. br0).

But, my actual data traffic need to pass eth0 -> tap0 -> gnuradioStack -> usrp.

Here I have some problem in pass eternet frames into the above path.
Is the bridge mechanism usefull for this.

Thank you,

KR.SJ

---

