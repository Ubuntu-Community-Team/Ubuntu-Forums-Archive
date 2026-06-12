---
title: "x server connect 10.10"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by cjpetrie on 2012-03-13
(Based on post on closed thread by mpenda)
1. Removed "-nolisten TCP" from /etc/X11/xinit/xserverrrc
2. Changed true to "false" for the DisallowTCP on schemas.
3. Did xhost + on localhost
4. Edited gdm/custom.conf as suggested by posts and blogs.
5. ssh'ed to remote machine and setenv DISPLAY to internet address from ifconfig.

I'm running 10.10. No joy. Remote machine cannot connect to my X server.

Want to run hulu etc. on my machine while traveling in Germany. Thought this would be simple if slow. Guess it's been a while. Yes, I could upgrade, but my experience with 11.xx has caused immense reluctance to do so. Did Ubuntu reach a peak a while back?  Really frustrating that Ubuntu has made a basic linux networking function so difficult.

---

