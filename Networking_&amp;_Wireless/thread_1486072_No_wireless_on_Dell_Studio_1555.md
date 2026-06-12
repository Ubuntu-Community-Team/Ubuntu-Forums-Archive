---
title: "No wireless on Dell Studio 1555"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by LazyLlama on 2010-05-17
Hey Guys,
I just installed Ubuntu via Wubi on my Dell Laptop, 10.04.
Everything seems fine, but wireless isn't working. It says "device not ready".
This seems odd, as sound and graphics seem to be working fine - so drivers must have been installed.
In "Hardware Drivers" I get the message:

"Downloading package indexes failed, please check your network status. Most drivers will not be available."

I'm new to Ubuntu and don't really know what to do.
Any help will be much appreciated!

---

### Post by LazyLlama on 2010-05-17
Bump.

---

### Post by SlidingHorn on 2010-05-17
Please don't bump so quickly...usually it's recommended that you wait 24-48 hours before bumping a thread.

People are working hard to help other members and will get to your thread as soon as possible.

---

### Post by LazyLlama on 2010-05-17
> **SlidingHorn said:**
> Please don't bump so quickly...usually it's recommended that you wait 24-48 hours before bumping a thread.

People are working hard to help other members and will get to your thread as soon as possible.

Apologies. I understand you guys are working hard - I was in a bit of rush.

---

### Post by nwilson5 on 2010-06-01
I'm having this same issue.

I'm unfamiliar with ubuntu to know where to begin.

My netbook has a button you 'press' to turn wireless capabilities on and off. Normally when it's 'on' it is blue, but it remains red/orange no matter if I press it or not.

---

### Post by pdc on 2010-06-01
If you have access to an ethernet cable from a router, download this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

run it; it will give you answers

post the results back here if you need more help

___________

or just open a terminal 

type

> lspci

and look for the network line: I suspect you may see something about broadcom: 

if so, have a look here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by nwilson5 on 2010-06-01
Yeah it was broadcom.

I got it to work, surprisingly easily... Thing was earlier nothing showed up in the 'Hardware Drivers'. I actually had xubuntu installed (because it wouldn't let me install ubunto on the netbook). So I did "sudo apt-get install ubuntu-desktop". I decided to check the hardware drivers again before checking here again and it actually showed the wireless devices. I activated them and restarted and now it works.

Anyways, thanks for the link and taking the time to reply.

---

