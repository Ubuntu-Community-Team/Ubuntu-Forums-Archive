---
title: "T-Mobile USB internet question"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2011-06-26
Hi all,

I got my VODAFONE usb internet stick, finally... 
It's a huawei k4505 stick and it is recognized out of the box by 11.04.
It gives me the option to connect (after setup) and then it asks for a pincode... I never got a pincode from the store, is this normal? At the store they say I have to install VMB to get it to work but this program says it needs libboost-serialization1.40.0 (>= 1.40.0-1) and it cannot be installed. But I am using Natty and have got libboost-serialization1.42.0 installed. This means that the software is badly written, right?

I am thinking that it's a normal sim card, so I should get a pin and a puk code, right?

I am going back to the store tomorrow, but I would like to be well informed before I do.

thanks!

---

### Post by Ashrael on 2011-06-26
W000t! It works, and this is how it's done!

Don't use software provided by vodafone, it gives the libboost dependency error..

instead goto:

[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu](http://www.betavine.net/bvportal/resources/datacards/os/ubuntu)

This worked for me!

Strange though, that vodafone needs it's own software. Ubuntu recognizes the usb modem out of the box. And now I have to do things before I get connected AND my network applet doesn't show the connection.....

But what the heck, I got mobile.....

---

