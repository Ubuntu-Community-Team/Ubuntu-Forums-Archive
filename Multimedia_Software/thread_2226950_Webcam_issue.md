---
title: "Webcam issue"
date: 2014-05-29
forum: Multimedia Software
---

### Post by dovah on 2014-05-29
Dear all, 
Lately, I experienced a little problem on my Asus laptop (running Ubuntu 12.04LTS): my webcam does not stock snaphots properly (ie: I cannot access the given storage path).It also appears undetected by messaging software. The problem persists, even after complete removal and reinstallation of a number of different software using synaptic (kamerka, cheese, camorama...). I also tried to change the stockage path, with no success. So I wonder if you have an idea for fixing this.

Here's the output of my ls command:
dovah@AsusX501A:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:5165 IMC Networks 

And here's the output of the webcam command via terminal (light turns on, but no GUI is shown, though):
dovah@AsusX501A:~$ webcam
reading config file: /home/dovah/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
^C
dovah@AsusX501A:~$ ^C

Thank you for your help! 
:cheers:

---

