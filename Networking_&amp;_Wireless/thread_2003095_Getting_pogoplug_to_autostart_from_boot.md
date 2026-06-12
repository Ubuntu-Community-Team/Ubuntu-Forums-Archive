---
title: "Getting pogoplug to autostart from boot"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by thomasg62 on 2012-06-13
Using Kubuntu 12.04

I can get pogoplug started via a terminal once I'm onto my desktop, but I've had a number of failed attempts to get this to start from boot-up. I've created a script (using kate) and put this into the startup (via system settings) but this just caused my system to hang - no matter what tweaks I made. The script I tried is:

#!/bin/bash 
<path-to>/pogoplugfs --user (my_email) --password (my_password) --mountpoint <path-to-mount>

This was meant to execute the pogoplugfs file and mount the files. Unfortunately, I get nothing but hangs on my system. 

I did get it to work at one point - by a fluke I think but I cannot recall how it worked and unfortunately I made a bad decision elsewhere and had to do a restore and lost what I had.

Any suggestions appreciated

---

