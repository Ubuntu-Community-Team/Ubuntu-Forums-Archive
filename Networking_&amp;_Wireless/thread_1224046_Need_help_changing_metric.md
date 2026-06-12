---
title: "Need help changing metric"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by maximus57 on 2009-07-26
I am trying out Ubuntu 9.04 and am new to the linux sceen. I have been able to get it connected to my wireless router (didn't work out of the box), and even now have it working with my usb EVDO aircard. My problem is that I can't get internet though the usb modem when the wireless is connected to my local network. I have had similar problems before with windows and solved the problem by manually changing the metric of the network adaptors. Below is what I have tried so far without success.
 
From the terminal- "sudo ifconfig wlan0 metric 20"
Result- "SIOCSIFMETRIC: Operation not supported"
I get the same result when trying to change the metric on any interface.
 
Added this to the etc/network/interfaces file-
auto wlan0
iface inet wlan0 static
address 192.168.0.177
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
metric 20
 
Result- wlan0 remains in dhcp mode and gets its ip address from the router and the metric remains at 1. It doesn't seem to look at the interfaces file.
 
I would really like to be able to change the metric from the command line if possible, so that way I could put it in a .sh file and run it when I want to use the usb modem (since I have to start the modem manually anyway). But I would be happy if I could get the interfaces file to work too.

---

### Post by shredkingj on 2009-07-27
Have to ask, did you restart the networking init script after you changed the metric in the interfaces file?  What does route -n give you for the interface metrics?

---

### Post by maximus57 on 2009-07-27
No, I did not restart init.d. However I was under the impression that a reboot would reset it, and have done many reboots.
 
Ok, now I try to reset it and get an error.
 
sudo /etc/init.d/networking stop
* deconfigering network devices
/etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
 
Does this mean that I have something wrong in the file? My next post I will post the whole file exactly as it is, as I am not posting from that computer right now and am typing all of it out.
 
Edit: I took out everything I changed in the file and put it back to original and still get the same error.
 
Edit again: the first entry was "-e auto lo", that was the origianal default interfaces file. I got rid of the "-e" and the error went away. Was it supposed to be something else? Or was it something that got changed in this version? Possibly a bug?
 
I had a couple things switched around myself, but now it uses the interfaces file. All of this has now got me to realize that part of my problem is that the usb modem does not create a gateway when it connects. If it's not one thing it is another.

---

### Post by shredkingj on 2009-07-27
You could create routes with the metrics instead.  For example. a default route:

route add default dev wlan0 metric 20

Not familiar with the particular error message you're getting, maybe a Google search will shed some light on that.

---

### Post by maximus57 on 2009-07-27
The error I was having with the interfaces file was that "-e" in the first line. I couldn't find anything about it in the man interface. A quick search brought up a few references, and everything had "echo" in front of the "-e" being used from the command line. That is what makes me think it is a bug of sorts.
 
-e auto lo
iface lo inet loopback
 
Is that how your original interfaces file looks? Most of the references I found online do not have that "-e" in front.

---

### Post by maximus57 on 2009-07-27
And yes, I am playing around with the route command now to see if it can work some magic.

---

### Post by maximus57 on 2009-07-27
Ok, first off the error with the interfaces file must have been created when I was setting up my wireless card. It is not there on a fresh install.
 
Second, I seem to have problems that go deeper than just needing to change any metrics. Anytime I turn the wireless on it kills the EVDO, and turning the wireless back off doesn't get it back. Not to mention that twice now the wireless seemed to turn off and not come back on at all. Thank goodness for Acronis True Image and making backups along the way!
 
I will do some more reading, and make new posts when I figure out what I need to ask.

---

### Post by njparton on 2010-06-01
Did you get this resolved?  I'd like to use metrics to give my wireless connection a higher priority than my lan connection.

---

### Post by maximus57 on 2010-06-04
No, I never got it working. My solution was to buy a router for my usb aircard.

---

### Post by Wieshka on 2010-10-18
For very simple control of metric i use ifmetric tool:

apt-get install ifmetric
ifmetric device 100

---

