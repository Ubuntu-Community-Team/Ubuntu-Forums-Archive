---
title: "Wlan0 wont stay in monitor mode!"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by Crashedata on 2010-08-05
Well this is an interesting problem. I am running Ubuntu 10.04, and I have to set my wireless chip to monitor mode. I boot into the terminal and type

$ sudo su
$ iwconfig wlan0 mode monitor

It returns the error:

"Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy."

But I am not connected to any wireless networks. So I tried disabling the wireless by right clicking on the network icon and unselecting enable wireless. I repeat the commands and it appears to work, but the moment I re-enable wireless, it switches back to Managed mode. Is there any way to force it to stay in monitor mode?

Here is the driver for my wireless: b43-fwcutter.

---

### Post by Crashedata on 2010-08-05
Bump

---

### Post by varunendra on 2010-08-05
See if this helps:
[airmon-ng]("http://manpages.ubuntu.com/manpages/lucid/man1/airmon-ng.1.html") (Download+Manual for lucid)
[video tutorial]("http://www.securitytube.net/AirmonNG-video.aspx")
[tutorial + examples]("http://www.aircrack-ng.org/doku.php?id=airmon-ng")

---

### Post by nathanf534 on 2010-08-06
try this

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

---

