---
title: "Ubuntu 10.10 loses connection to network"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by boombox1387 on 2010-10-21
This issue has actually been happening off-and-on for the past year, but it's been especially bad the past couple days, so I'm finally getting around to asking about it.

Beginning in Ubuntu 9.10, my computer would randomly lose its connection to the Internet.  This is not related to sleep or hibernate, as both of these options fail miserably with Ubuntu on my computer.  It happens during the middle of normal operation.  One minute the Internet is working fine, the next minute I can't connect to any sites until I restart the computer.

The problem is even more noticeable now that I own a SiliconDust HDHomeRun TV Tuner (which plugs into the network).  I'll be in the middle of watching TV when the connection to the device is randomly dropped, causing MythTV to freeze up for awhile before telling me that there is an error connecting to the device.

My laptop, on the same network, doesn't suffer from this issue.  For example, the laptop has an Internet connection right now, but my main computer won't until I restart it.  The desktop computer can't see the laptop (pinging 192.168.2.5 fails).  Also, trying to detect the TV Tuner gives different results from the laptop and desktop.  From the desktop:

```
hdhomerun_config discover
```

tells me that no devices are found on the network, while the laptop correctly finds the device at 192.168.2.3.

So my questions are these:  Is this a known issue?  Is there any good workaround?  What can I do to collect more useful debugging information.

---

### Post by boombox1387 on 2010-10-25
Just a friendly bump.

I'm not necessarily looking for answers here (although that would be awesome).  Even some tips in debugging would be extremely helpful.  I'm not sure how to run network manager from the command line, and there don't seem to be debugging packages for network-manager or network-manager-gnome.

Any help is much appreciated.

---

### Post by Hippytaff on 2010-10-25
Might be worth playing around with a network scanner like nmap. (zenmap has a gui) to discover whats where and called what (if that makes sense) though you can find info with

```

lshw network -C

```
```

ifconfig

```
 and it might be worth checking out some of the log files just after your connection has dropped to see if they indicate whats going on 
```

cd /etc/log/
ls

```
will list the log folders, syslog is a good place to start (I think :-s))

---

### Post by s.fox on 2010-10-25
Thread moved to [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by boombox1387 on 2010-11-08
Thanks for the response, Hippytaff.  In addition to your tips, I also happened to find my way to this page: [http://live.gnome.org/NetworkManager/Debugging](http://live.gnome.org/NetworkManager/Debugging)

With this combination of debugging info, I should be able to get what I need to put together a useful bug report.

---

