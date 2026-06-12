---
title: "ATM ADSL static ip in Ubuntu, old school genius needed..."
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by sir_nasty on 2009-04-21
so a combination of me being almost noob to linux and a lack of recent relevant documentation has lead me to MANY hours of reading and searching and reading....  Here's the issue.  My isp uses bridged mode routers with public static ip.  I have a USB DSL modem (got it working fine ATM 0).  How do I configure it properly now?  VPI/VCI is 8.35.  Most of what I found explains the setup for dial-up but I need to set a static ip....  

I'm guessing I need to create a couple of files as found in the file link below.  BUT, how do I specify the ip and I need this to run when I call it, then I have to figure out how to shut it down.  Any guidance or insight?  My brain is scrambled with info right now....


[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

---

### Post by sir_nasty on 2009-04-22
Found the solution.... just wanted to follow-up but for my particular situation LLC encapsulation, bridged, static ip, vpi/vci 8.35.

run

br2684ctl -b -c 0 -a 8.35
(-b run it in the background so it dumps back to a command prompt when done, simply putting '&' at the end won't work)
(-c create interface nas0)
(-a VPI.VCI)

ifconfig nas0 up

ifconfig nas0 [static ip]

usefull command for my situation:

/proc/net/atm/cxacru:0
(returns information about the connection)

the thing that held me up the most was to much information available and not enough knowledge of my adsl...anyway there it is!

---

### Post by JK3mp on 2009-04-22
Hmmm....

---

