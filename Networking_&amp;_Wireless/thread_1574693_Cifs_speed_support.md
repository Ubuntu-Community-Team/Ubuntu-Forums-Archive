---
title: "Cifs speed support"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by cyanguy on 2010-09-14
[COLOR=#000000][FONT=Verdana]Hello all, and thank you in advance for your time, and any help that may be given. I am emailing in hopes that some help, tips, or suggestions can be offered to help me achieve my goal. 


The heart of the question is: What can I do to increase my CIFS network speed?


Here is what I have, and what I have done. 


I am using two linux boxes, connected on the same network, via a Netgear 5 port Gigabit hub. Both boxes are using a Cat6 cable, and both boxes contain a gigabyte Ethernet card. 
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]First, I test the connection between the boxes using iperf. Off the bat, the connection was around 300 [FONT=&quot]Mbs[/FONT][FONT=&quot]. [/FONT][FONT=&quot]Once[/FONT][FONT=&quot]I enabled[/FONT][FONT=&quot] jumbo frames[/FONT][FONT=&quot], I got[/FONT][FONT=&quot] network connection [/FONT][FONT=&quot]over[/FONT][FONT=&quot] 700 [/FONT][FONT=&quot]Mbs[/FONT][FONT=&quot]. [/FONT][/COLOR]


[COLOR=#000000][FONT=&quot]I made one of the boxes[/FONT][FONT=&quot] serve[/FONT][FONT=&quot] a fileshare[/FONT][FONT=&quot] while the other box mount[/FONT][FONT=&quot]ed[/FONT][FONT=&quot] the [/FONT][FONT=&quot]share[/FONT][FONT=&quot]. The command I use to mount the share is as follows: [/FONT][/COLOR]


# mount -t cifs -o username=joe,password=eoj //192.168.2.40/SharedDocs /a


[COLOR=#000000][FONT=&quot]After successfully mounting the share, I used iper[/FONT][FONT=&quot]f[/FONT][FONT=&quot] to test the connection. [/FONT][FONT=&quot]The speed was still over 700Mbs. However, it took over 60 seconds to copy a 1 GByte file to the fileshare. (a speed of around 133 Mbs.) [/FONT][/COLOR]


Knowing that without the CIFS share, the network is able to support about 700 Mbs, and that with the share the network only supports about 133 Mbs, I have come to the conclusion that with a CIFS connection I am only able to support about 13% of my network capabilities. My goal is somewhere between 40% and 50%, which I think is reasonable. 


[COLOR=#000000][FONT=&quot]What [/FONT][FONT=&quot]parameters [/FONT][FONT=&quot]can be [/FONT][FONT=&quot]tuned[/FONT][FONT=&quot] in order to improve the cifs connection?[/FONT][/COLOR]

Thank you
[/FONT][/COLOR]

---

