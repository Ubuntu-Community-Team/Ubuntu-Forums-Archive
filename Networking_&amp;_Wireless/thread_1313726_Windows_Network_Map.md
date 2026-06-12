---
title: "Windows Network Map"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by josh_moore on 2009-11-04
Not sure if this thread belongs here or not but its semi network related.
I am trying to configure my Ubuntu 9.10 system to function with the Windows Network Map.

I am looking for anyone that might be familiar with lld2d that might shed some light on what I might be missing.
I searched for and found the solution adding the Link Layer Topology Discovery protocol used by the network map to Linux. 
[http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny](http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny)
I was able to follow the instructions, including comments included at the bottom to build an executable from the source (though its not auto starting, I am working on that further myself). 

My problem is that my Ubuntu system is showing up on the network map in the incorrect location, as an incorrect device.
Included is a screenshot with description of devices to illustrate.
As seen in the screenshot my Ubuntu system with LLTD installed shows up between one of my PC's and my router, with an icon of a wireless AP/router instead of connected via wireless to the WRT54GS2 router
Again, I followed the directions in the article above exactly, save one edit as indicated in comments...

"*I had to add the following line to state.c to get this to compile for me without any errors: * *#include <LIMITS.H>*
 *Good luck.*"

I have searched both through the source code files, in my limited understanding of programming, and online for articles trying to see if further editing or configuration is needed or can be done to change what information is passed through the LLTD protocol and reflected in the network map. If I understand the readme and documentation included with the source code correctly this should be possible, at least as much as being able to specify a custom icon (.ico) file, though exactly when/where even that can be done I am at a loss.

Thank you in advance for taking the time to read and hopefully assist.

---

### Post by josh_moore on 2009-11-04
/bump

Anyone have any suggestions for this?

---

