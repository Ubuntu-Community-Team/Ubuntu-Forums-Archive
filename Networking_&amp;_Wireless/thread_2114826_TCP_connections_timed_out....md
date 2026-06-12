---
title: "TCP connections timed out..."
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2013-02-11
This is an issue that I discovered recently that really freaks me out :confused:
I realized that my wireless connectivity whenever I use the embedded wireless card or the well proven USB WiFi DWA131 I get the same issue. From time to time the connectivity just hangs! It's really frustrating when I browse. And the freaky part is that during these periods of hangs, I've got an uninterrupted ping to the gateway, the DNS is working, the stream audio is running :confused: It's like the system is having issues with the TCP connections that the browser opens (i've tried many different browser, the same issue) and they're timed out. When I look at the traffic with Wireshark, I do notice a lot of connection resets. Any idea on how I could further troubleshoot this?

---

### Post by lz1dsb on 2013-02-11
The only workaround I've got for the moment is to just restart the Network Manager (sudo service network-manager restart). This usually solves it for about an hour or so...:confused:

---

### Post by lz1dsb on 2013-02-13
I've been playing around recently and I did a sample capture with Wireshark to really get a better idea what is going on:
1. While I have the issue, I test the connection with my other laptop and the phone... no issues. So I shouldn't blame the AP/Router.
2. In the capture file I noticed that there are a lot of tcp connections with something like a "flood" of TCP packets with the SYN flag set. An the delta time is quite short, I don't know but I think some web server might consider this as a DOS attack. 
3. All packets were captured while I was browsing with Opera.
4. Oddly enough during the time of the issue, the other browsers were also affected.
5. Today I didn't use Opera at all, and the issue hasn't reproduced. 
6. Last but not least, changed the AP radio channel to 13, I do notice a bit better performance. 

So to wrap up, I suspect that there's something wrong with the Opera version that I have installed and the way it is messing up with the system's TCP/IP stack.
I'll need more time to test on this...

---

### Post by lz1dsb on 2013-02-21
Just to wrap up.
I've been experimenting a bit these days and there's definitely something with the Opera browser. I haven't had any issues since I started using exclusively Chrome and Mozilla. That's odd. It looks like that from time to time Opera messes up the TCP/IP stack. I do not have any other explanation for this...

---

