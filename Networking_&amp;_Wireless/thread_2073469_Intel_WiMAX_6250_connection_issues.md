---
title: "Intel WiMAX 6250 connection issues"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by japhyr on 2012-10-19
Hello,

I am setting up 12.04 on a Dell Latitude E5410.  This is a dual-boot with Windows 7.  When I first installed 12.04 a few days ago, wireless just worked and I was able to install updates over the wireless connection.  I then installed some other packages as well - nothing to do with wireless, just a text editor.

When I logged in today, the connection is not working.  The computer is connecting to the wireless network, but it is not connecting to the internet.  My wireless card is an intel WiMAX 6250:

```
$ lspci | grep Network
02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 35)
```

I have read a number of threads, such as [this one]("http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi"), but can't figure out what to try.

Any suggestions?

---

### Post by nsturdev on 2012-10-19
@japhy

You said you computer connects to the network.  try running

```
 ifconfig 
```

you should show something for your wireless card

inet addr is what we look at first

if 169.x.y.z that is a no go.

if 192.x.y.z (most likely) then you need to try to ping the router.

```
 ping -c 5 192.x.y.1 
``` where x and y match what you have in ifconfig for wireless.

if you get reply
then try pinging 8.8.8.8 
that is google's public dns server
if you get reply from that you are getting to internet
if you get reply from route but no reply from internet then it is probably between router and internet and not computer.

---

### Post by ahallubuntu on 2012-10-19
Open a terminal window and type:

iwevent

and leave the window open; try disconnecting/connecting and see what happens.  (I'm using Ubuntu 10.04 LTS not 12.04 LTS so not sure if this is installed for you automatically or not.)

Also, are you getting an IP address?  What does ifconfig say?

Are you connecting to different access points with different types of security?  Or did this same access point work at first and not now?

---

