---
title: "bradford dissolvable agent"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by almightypacers on 2009-01-05
I am new to ubuntu and am trying to install bradford persistent agent on my labtop and having trouble. I can only save it on to my desktop and thats the most i can do. when i try to open it, it does nothing. Help anyone?

---

### Post by lucasg123 on 2010-03-29
Hello,

I am assuming you are at a university or something and trying to get your computer to be allowed on the network. My college mandates that Bradford Persistent Agent be installed. Fortunately for us, it is quite easy to install using Wine. I don't know if you are familiar with wine, but it allows you to run (some) windows programs. Install wine [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") (simple tutorial) Then shoot me an email at [email]lucasg123@gmail.com[/email]. I will be happy to forward you the correct Bradford agent to install with wine. (including instructions)

---

### Post by lucasg123 on 2010-09-29
[Update]

Bradford Networks identifies a computer based off its MAC address. If you fake your MAC address to the MAC address of something that doesn't require Bradford to run then it should solve your problem. May I suggest a smart phone with WiFi or a school computer that doesn't run Bradford? I believe you can get the mac address of a windows computer by typing "getmac" into the windows command line. On a iphone/touch go to Settings>General>About 

So....To spoof your computers MAC address you need to identify your networking interfaces. (ex. wlan0, eth0, eth1)

This will show them
```
ifconfig
```

Then you need to modify /etc/rc.local
```
sudo gedit /etc/rc.local
```

add the following things in before exit 0

-------------------------------------

ifconfig [interface] down hw ether 00:11:22:33:44:55 (your mobile wifi device MAC address here)

sleep 5

ifconfig [interface] up
-------------------------------------
So the whole file will look something like this...

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down hw ether 00:11:22:33:44:55

sleep 5

ifconfig eth0 up

exit 0

------------------------------------
Now when you reboot your MAC address will be spoofed to whatever you want

Let me know if it works!!!

--Lucas

---

