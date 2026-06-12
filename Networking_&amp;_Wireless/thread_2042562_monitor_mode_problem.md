---
title: "monitor mode problem"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by Virtroon on 2012-08-14
Hi everyone,
Recently I've tried to set the monitor mode for my wireless card. I typed this:

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

After that, my laptop is unable to connect to internet and also if I restart Kubuntu, the wireless card goes back to managed mode.

I don't know so much about this topic. To be honest, I'm a completely newbie. Can anyone help me?

---

### Post by chili555 on 2012-08-14
Monitor mode is not used to connect to the internet; it's used to monitor the networks and, sometimes, traffic in the area. It listens only and on all available channels.

Managed mode refers to being managed by a router or other access point. The router sets the channel, asks for an encryption password, sets the bit-rate and more. Then your wireless card is free to listen *and* talk on one network only: the one to which it has associated.

They are two different modes for two different purposes.

---

### Post by Virtroon on 2012-08-15
Thanks for the explanation. I was completely clueless.

I'm a little concerned about security. I have one last question. Can another person catch all the packages sent by my laptop even if he's also connected to my network?

---

### Post by chili555 on 2012-08-16
You might get a better answer from the guys over here: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

