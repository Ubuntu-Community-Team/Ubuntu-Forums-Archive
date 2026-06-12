---
title: "Auto-orient scanned photos?"
date: 2011-10-17
forum: Multimedia Software
---

### Post by stuporglue on 2011-10-17
Does anyone know of Linux software that can auto-orient photos without any metadata? 

I don't need 100% accuracy, anything to lighten my workload would be welcome. I have at least two shoeboxes full of prints I'm going to scan.

---

### Post by stuporglue on 2011-10-23
If anyone else comes looking for something like this, I couldn't find any existing scripts/programs to auto orient scanned photos. 

So, I wrote a script that uses OpenCV to detect faces and uses that info to print how many degrees the photo should be rotated. If no faces are found, it finds the brightest edge of the photo (as a proxy for finding the sky), and returns the degrees to turn that edge upward.

[http://stuporglue.org/automatically-orient-scanned-photos-correctly-with-opencv/]("http://stuporglue.org/automatically-orient-scanned-photos-correctly-with-opencv/")

You'll need to install libcv2.1, python-opencv and either libjpeg-progs or imagemagick (or another library to do the actual rotation). 

You will also need one or more haar classification files from OpenCV. These files tell OpenCV what a face (or other feature) looks like: 
[https://code.ros.org/svn/opencv/tags/latest_tested_snapshot/opencv/data/haarcascades/]("https://code.ros.org/svn/opencv/tags/latest_tested_snapshot/opencv/data/haarcascades/")

I have attached the script here, and a bash script that I used to batch process my scanned images.

I get somewhere between 80% and 90% accuracy, so it's not perfect but it does save me some time. s

---

