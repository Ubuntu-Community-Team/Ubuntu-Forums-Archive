---
title: "Encoding video with Handbreak over network"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by S3loth on 2011-07-17
I have a Windows machine with a 2TB hard drive containing several raw videos I want to encode with Handbreak. I have two laptops I want to use to cut down on the time. These laptops have very small hard drives, and probably can't hold more than one or two videos at a time. I was wondering if there is a way to keep all the videos on my Windows machine and just use the laptop's to encode over the network, or at least have it automatically copy the raw videos, and put the encoded ones back as needed. Sorry if my explanation is hard to understand. Long story short: one big hard drive, three CPUs to encode, need to split the work up quickly.

---

### Post by SeaKing on 2011-07-17
Try this: First connect to the Windows Share (Places -> Connection to a server, choose Windows Share and type in the IP). Once you have logged in the windows share it should appear unter Places like "Videos on 192.168.1.25". Now you can start Handbrake and choose as source your mounted windows share and the same as destination.  I'm using the Handbrake GUI so I can choose places from the menus, if you use the CLI I think the path should be \\ip_windows_share\your_folder\...

---

