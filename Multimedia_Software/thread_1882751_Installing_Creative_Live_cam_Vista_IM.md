---
title: "Installing Creative Live cam Vista IM"
date: 2011-11-17
forum: Multimedia Software
---

### Post by Dooa on 2011-11-17
Hi All,
I'm trying to get below instructions working on Ubuntu 11.04 and I get "Rastageeks.org:connection refused" after the lne : 

svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver

Any alternative reposts? suggessions much appreciated.
---------------------------------------------------------------------------------------------------

**Installing Creative Live cam Vista IM** 			 			 			 		   		 		 		Works for me, at least with Ekiga. I did something like the following:


 	Code:
 	sudo apt-get install subversion mkdir webcam-driver svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver cd webcam-driver sudo apt-get install linux-headers-2.6.20-16-386 make sudo make install sudo modprobe ov51x-jpeg

---

### Post by no2498 on 2011-11-19
see what driver shows up in dmesg
in a terminal type dmesg click enter
close to the bottom see what driver it loaded

---

