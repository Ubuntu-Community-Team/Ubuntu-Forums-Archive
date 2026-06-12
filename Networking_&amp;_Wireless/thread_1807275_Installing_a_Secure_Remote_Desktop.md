---
title: "Installing a Secure Remote Desktop"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by Clear Obama on 2011-07-18
I need to securely control my home computer from work. My home computer is connected to the internet via a wireless router using Tomato. I'm using the latest Ubuntu on both ends. 

Is the Remote Desktop that's installed by default good enough? What settings do I need for my home router to safely allow my remote connections and not leave it open to intruders?

Any suggestions much appreciated!

---

### Post by Dangertux on 2011-07-18
I would not recommend exposing VNC openly to the Internet. 

Perhaps use OpenVPN and connect to a locally running VNC server. There is also a slightly more secure alternative to VNC that has been mentioned a few times on this forum. Which is X forwarding over SSH Some google research should turn up some decent tutorials for either of the above options.

---

