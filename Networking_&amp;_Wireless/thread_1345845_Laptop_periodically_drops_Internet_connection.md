---
title: "Laptop periodically drops Internet connection"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by ld.4lpha on 2009-12-04
Jaunty.
Broadcom 4312.
Problem occurs with both wl and b43 modules.
Problem occurs on all WiFi networks - independent of network and independent of WPA or no encryption.

Periodically (sometimes 5x per day, sometimes none), my laptop just momentarily drops its Internet connectivity.  For example, I can be browsing the web and then all of a sudden my laptop cannot access the outside network.  I pull up a terminal and cannot ping google.com, nor can I ping DNS such as 4.2.2.2.

Then, after about 30 seconds or so and as suddenly as the problem arose, it goes away and all is fine.

During this time, the WiFi connection itself remains intact according to the Network Monitor.

Another example of this happening occured while I was watching a video stream.  Halfway through an hour-long video, the connection was lost for about 30 seconds, and I had to restart the stream.

Does anyone have an idea what is going on?  Is there a tool that I can run in the background that will monitor what is happening, or is there a default system log that might show something?  I have looked through the logs, but can't seem to find anything that makes sense.  My guess is that this is a Layer 3 issue, but could be 1 or 2.  ??

This is most annoying and baffling.

Thanks!
LD

---

### Post by Ted3929 on 2009-12-04
Have the same problem, partially alleviated in the past by changing the wi-fi connection.

If you add a third party software source under Synaptic (deb [http://apt.wicd.net](http://apt.wicd.net)) you should have access to another wi-fi connector that I've found works in previous versions of Ubuntu, but I'm not sure about 9.10 so tread lightly and research it first.

Best bet is to go to [http://wicd/sourceforge.net](http://wicd/sourceforge.net) to make sure it's up to the task.

---

### Post by ld.4lpha on 2009-12-04
> **Ted3929 said:**
> Have the same problem, partially alleviated in the past by changing the wi-fi connection.

If you add a third party software source under Synaptic (deb [http://apt.wicd.net](http://apt.wicd.net)) you should have access to another wi-fi connector that I've found works in previous versions of Ubuntu, but I'm not sure about 9.10 so tread lightly and research it first.

Best bet is to go to [http://wicd/sourceforge.net](http://wicd/sourceforge.net) to make sure it's up to the task.

Cool.  Thanks for the suggestion; I will check it out.

What do you mean by "partially alleviated?"  Do you still experience the problem from time to time?

---

