---
title: "Remote Desktop"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by rhpeters@priddis.cn on 2009-11-09
My home network includes 5 Macs running OS X 10.6.1 and 6 machines running Ubuntu 9.10. I travel often and keeping all the machines updated is a chore.  On the Mac side, I can use Remote Desktop across the internet through MobileMe and Sharetool to login remotely to each of the Macs to do my maintenance chores.  Using Sharetool I can also "see" the Ubuntu machines and if I am already logged in I can use Remote Desktop to control the machines and provide the required maintenance.  The problem is that I have to be logged in already ie I can't login remotely.  Can someone describe how I can remotely login to the desktop on the Ubuntu machines. My kids and I thank you.

R.

---

### Post by Kokopelli on 2009-11-09
The answer to some extent will depend on how technical you are.  IMHO the best remote admin tool is ssh.  It is (obviously) command line but it is the best tool for the job.  With "ssh -X" you can launch X application from said command line and have them on your desktop as well.  (Note: ssh - X requires more work if you are a windows guy on your laptop.)

For a full session the problem you are having is that unless you are logged in you do not have a session for VNC to connect to.  What you can do is have a session start when VNC does:

[http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx](http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx)

This explains it for a headless machine but it should work in an identical fashion for a machine with a monitor.

Alternatively a slightly more advanced option would be to use NX or FreeNX.  The NX protocol is much friendlier over a attenuated connection.

---

### Post by rhpeters@priddis.cn on 2009-11-09
Thanks.  I've used nx before and will again.

---

