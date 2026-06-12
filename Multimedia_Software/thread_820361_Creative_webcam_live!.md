---
title: "Creative webcam live!"
date: 2008-06-06
forum: Multimedia Software
---

### Post by LaoTzu13l on 2008-06-06
Just finished installing Ubuntu 8.04(amd64) onto my laptop. Got wireless set up and all that fun stuff, except for my webcam. Did a bit of playing around, and googeling, but I haven't had any luck.

My guess is drivers for my cam aren't installed, but I might be wrong. /dev/video doesn't exist when i plug the cam in like it should from what I've read. Here's the output from lsusb

```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 041e:405f Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  

```

Any help?


________________________________________

I found it, friend helped me figure it out, driver for the cam is ov51x-jpeg.

---

