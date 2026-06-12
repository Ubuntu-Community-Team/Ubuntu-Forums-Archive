---
title: "OpenDC Hub connection problems"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by KaridaSerious on 2006-07-06
Hi!

I installed opendchub recently. I installed it with 'sudo apt-get install opendchub' and ran it with 'sudo opendchub'.

It asked me a few default questions concerning about port, admin password etc. I configured the opendchub to listen on port 411. When we tested it, my friend connected to the hub succesfully and I was having strange connection problems. When I joined to the hub, it connected and immediately disconnected after that. Error message below:

```
*linuxdcpp*; Connect failed: Connection Closed
```

and output from opendchub when I made the connection:

```
Jul  6 16:25:32 ***Started Open DC Hub version 0.7.14***
Hub is up and running. Listening for user connections on port 411
and listening for admin connections on port 53696
Jul  6 16:25:32 Got alarm signal
Jul  6 16:26:03 New connection on socket 6 from user at xx.xxx.xxx.xxx
```

What seems to be the problem. I have configured my firewall and router to allow the traffic through port 411 and still I cant logon to my own DC Hub? Is opendchub somehow restricting my access to the hub? Can someone, who has been using opendchub, clarify me what I am doing wrong?

-KDS

---

### Post by tribut on 2006-09-11
> **KaridaSerious said:**
> ```
*linuxdcpp*; Connect failed: Connection Closed
```

Yeah, just run into the same problem. This is caused by a bug in opendchub which is fixed in 0.7.15 - however this version hasn't made it into ubuntu yet... :( 


regards,
felix

---

### Post by Similar on 2006-11-22
Yeh, i have the same problem idd

---

### Post by madaleno on 2007-09-28
Same problem here... 
Ubuntu 6.06 server....
"apt-get install opendchub" installs version 0.7.14...
How con i get the latest 0.7.15 installed correctly?

---

### Post by slicer on 2008-05-16
Solution is to download and compile source.

Get sources from [http://prdownloads.sourceforge.net/opendchub/opendchub-0.7.15.tar.gz](http://prdownloads.sourceforge.net/opendchub/opendchub-0.7.15.tar.gz).

Extract with:
```

$ tar zxvf opendchub-0.7.15.tar.gz
```

Compile:
```

$ cd opendchub-0.7.15
$ ./configure && make && sudo make install
```

Your opendchub version should be correct now:
```

$ opendchub --version
Open DC Hub 0.7.15
```

---

