---
title: "Allow incoming ssh over PPP via usb modem connection"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by tra4d on 2009-06-09
I have gotten my ZTE MF636 USB modem to work (wvdial ppp connection) using posts like:

[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

I am running Ubuntu 9.04.  I can connect to the internet, etc. just fine.  But I want to be able to connect in via ssh to this machine.

I tried adding tcp for ssh to iptables using:
```
$ sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
```

This entry shows up when listing iptables.  But I can't connect to the machine.  Is there something special you have to do to get this to work over a ppp connection?

BTW: I get error:  No route to host

---

### Post by sedawk on 2009-06-09
1) Connect to the internet with your modem

2) Open checkip.dyndns.org in firefox (or some other browser).

3) The IP you see in there is the one you use on the Internet

4) From a computer on the internet an ssh __username__@__your_ip__
   should work.

The error "no route to host" might indicate you are using the
wrong IP (not the one from the PPP connection).

I never had to change the firewall rules on my ubuntu to allow
ssh login - are you sure you already installed the ssh server
(package openssh-server)?

---

### Post by tra4d on 2009-06-09
I had already done that.  Doesn't work.  I was using whatismyip.com.

Any other ideas?  Cell provider related?  ??

Yes, I have installed the ssh server.  If I connect both machines on my local network I can ssh into the machine no problem.

---

### Post by tra4d on 2009-06-09
Has anyone gotten this to work w/ a cell modem?  Perhaps if there are some with it working, it is related to my cell provider (Rogers Wireless in Canada).  ????

---

### Post by tra4d on 2009-06-09
I check with my provider (Rogers Wireless) and according to the guy I talked to, they don't block any ports.

Any ideas??  Seems weird that it would work locally (LAN), but stop when I connect via the modem.

---

### Post by tra4d on 2009-06-09
I have tried a different port (just in case they are blocking) and now I get a "Connection timed out" instead of no route to host.

---

### Post by sedawk on 2009-06-09
I'm not sure how good this works with ppp but you can try
this:

1) Find out the ppp-network-interface (ppp0?) (Should be visible
with ifconfig -a).

2) monitor the network traffic on that ppp interface with something
   like
```

tcpdump -i ppp0 src <ip_of_your_internet_machine> port 22
or
tcpdump -i ppp0 port 22

```

If port 80 is free on your local machine try to start sshd on
port 80, test it in the local network (ssh -p 80) and
then test it via ppp connection again.

---

### Post by tra4d on 2009-06-09
1) Yes, ppp0 is the interface.

2) It was the second option.  It says its listening.  When I try and ssh in, no messages/info appears.  

So I guess I'm not able to even get "to" the machine?  

I will try port 80.  I was currently trying 2222 just in case 22 was somehow blocked.

---

### Post by tra4d on 2009-06-09
Port 80:  works via local network.  I capture traffic w/ tcpdump.  When I try via ppp connection, do not get a response (get Connection timed out) and there is no captured traffic w/ tcpdump.

---

### Post by tra4d on 2009-06-11
Ok.  So after about 3 calls to my cell provider I found the right person to talk to.  The IP address you get from a cell modem connection is not routable.  So I signed up for a routable feature for my sim.

Now I get some responses when running tcpdump on port 22.  But I still get a connection timed out error.  What am I looking for in the tcpdump output?

---

### Post by tra4d on 2009-06-11
Ok.  I found the answer.  In attempting to monitor what was going on, I installed firestarter.  All I had to do was put the correct port number in the poicy section and boom.  I am now connected via ssh.  

sedawk: thanks for your help.

---

