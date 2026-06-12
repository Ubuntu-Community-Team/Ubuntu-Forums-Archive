---
title: "4 second delay due to Silly Window Syndrome handling"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by alexmcmanus on 2011-05-18
I have a Mirrorbow Ethernet IO board - a network device that controls digital IO via a webservice. From Windows, it all works fine and HTTP requests to the board respond in about 200ms. From Ubuntu, however, there is a 4 second delay with every request. Note that I've tried this from a number of different Ubuntu machines, and also tried via a crossover cable connection, to eliminate the switch as a potential problem.

After some digging, I found this description of Silly Window Syndrome: [http://www.smarthome.com/forum/topic.asp?TOPIC_ID=7585]("http://www.smarthome.com/forum/topic.asp?TOPIC_ID=7585"). Having installed Wireshark, I found the symptoms match exactly:

> After receiving the TCP SYN packet, the SmartLinc controller responds with a WIN size of 1 (and no window-scaling). As a result, the Linux machine from which I am connecting enters SWS (silly window syndrome) avoidance mode, waiting for a larger window advertisement. After 1 second, the SmartLinc controller sends a TCP Keep Alive, which is promptly acknowledged. After an additional 3 seconds, the Linux machine sends the first data byte (the 'G' from HTTP request). This byte is acknowledged, and the SmartLinc controller advertises a window of 399 bytes. The rest of transaction completes as expected.

I can see how this is useful in general, but is there any way in which I can disable the Silly Window Syndrome avoidance? I get can access to the socket used for the HTTP connection, so is there any socket option/setting that I can use? Or anything to disable it globally?

Thanks in advance, Alex.

---

