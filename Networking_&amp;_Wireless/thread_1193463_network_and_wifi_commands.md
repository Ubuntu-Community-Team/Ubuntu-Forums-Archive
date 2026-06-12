---
title: "network and wifi commands"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by invinate on 2009-06-21
Hi!
I want to learn more about networking in ubuntu and especially about wifi. The thing is that i have no idea how to control the network connection from the command line. The networking manager says that my devices are not managed, so i guess they are managed by something else. Actually it's strange because everything seem to just work and that's odd in the linux world :)
I want to know how to do basic things such as listing the available wireless networks, set the keys and encyption to use for the network, restarting, etc. My wifi router uses WPA-PSK keys, but still ubuntu can somehow connect everytime, how? where is the key saved? Any guides you can suggest to read about these things? 
Thanks and sorry if my questions are lame :)

---

### Post by t0mppa on 2009-06-21
[Here]("http://ubuntuforums.org/showthread.php?t=571188")'s something to answer most of the questions concerning command line.

Gnome's network manager stores its data in gconf, which isn't exactly the most logical place and also considered as a flaw in its design by many. Should be able to Google plenty of information out of those two, in case you want to know more.

---

