---
title: "Multiple Machine Multiple Display Wall"
date: 2010-08-04
forum: Multimedia Software
---

### Post by MarshallCTF on 2010-08-04
We are working on a project to create a display wall of 8 monitors arranged as 2 high by 4 wide.  Each monitor is connected to a single machine and all machines are networked with a master machine with its own, seperate monitor.  

Our goal is to get the 8 machines to share a single desktop, with the master machine acting as the server.  We have looked at using Xinerama or NMM, but we are unsure about how to get started configuring the multi-machine, multi-head display.

If anyone has any ideas about where to get started, please let us know.

---

### Post by cliffdodger on 2010-08-04
Can you tell us more about what you want to accomplish with this display?

"8 machines to share a single desktop" - from the sounds of it you're not really looking for a multi-head display that Xinerama would provide. (I could be wrong)

There are several ways to access the desktop remotely from one Linux machine to another - personally the best would be straight through xwindows.

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Creating_Additional_Desktops](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Creating_Additional_Desktops)

I've never done multiple remote logins of the same user (which would give you the same desktop) so I'm not sure how Ubuntu will behave. Try it and tell us how it goes.

---

### Post by MarshallCTF on 2010-08-09
> **cliffdodger said:**
> Can you tell us more about what you want to accomplish with this display?

"8 machines to share a single desktop" - from the sounds of it you're not really looking for a multi-head display that Xinerama would provide. (I could be wrong)

There are several ways to access the desktop remotely from one Linux machine to another - personally the best would be straight through xwindows.

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Creating_Additional_Desktops](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Creating_Additional_Desktops)

I've never done multiple remote logins of the same user (which would give you the same desktop) so I'm not sure how Ubuntu will behave. Try it and tell us how it goes.

Our goal is to make a display wall out of the 8 machines.  We would like to be able to run an OpenGL application with 8 monitors acting as one cohesive display.  Some people we have come across have accomplished this by using a single machine with multiple video cards, but our goal is to utilize a setup with one machine per monitor.  We would like to use the setup for displaying images and playing videos across all 8 monitors.

---

