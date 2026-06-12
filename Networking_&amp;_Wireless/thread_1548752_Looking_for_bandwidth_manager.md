---
title: "Looking for bandwidth manager"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by thomas144 on 2010-08-08
Hi there, I'm looking for a good bandwidth manager to install on Ubuntu. I believe that's what it's called. I tried installing Trickle (sudo apt-get install trickle), but it doesn't "support executables utilizing kqueue(2). Does not support statically linked executables." This means that it doesn't work with Firefox, but it works with wget. Does anyone know of a good program? Preferably, it would be a graphical program, but I can use the command line, too.

---

### Post by thomas144 on 2010-08-09
*BUMP*
Hello? Anyone out there?

---

### Post by linux18 on 2010-08-09
I'll see what I can do, I was working on one a while back and lost interest.

---

### Post by thomas144 on 2010-08-09
Well, actually, I was just looking for something in the repos...

---

### Post by thomas144 on 2010-08-11
*BUMP*
Hello? Anyone?

---

### Post by TNT1 on 2010-08-11
> **thomas144 said:**
> *BUMP*
Hello? Anyone?

Went to software center:
typed in bandwidth, offered bmon... dunno if that's gonna do it for you?

(ps, i have no weird repositories added, pretty much all standard with me, we're simple folk in my house...)

There was also iftop, the netowrk version of top...

---

### Post by thomas144 on 2010-08-11
Thanks for offering your help, but it's not really what I was looking for. I'm looking for a program to control the usage of my bandwidth, not just monitor it.

---

### Post by TNT1 on 2010-08-11
Sorry. How do you mean control it?

---

### Post by thomas144 on 2010-08-12
Sorry for the slow reply. I said I was looking for a bandwidth manager, which is a program that you can use to...say...limit the bandwidth usage of a certain program.

---

### Post by thomas144 on 2010-08-16
*BUMP*
Hello? Anyone?

---

### Post by linux18 on 2010-08-16
>  **Now I**** will introduce you to Trickle:**
[Click Here to install trickle]("apt://trickle")
Trickle is a lightweight traffic limiter for applications like wget, firefox, and any other  user space internet application. 

Trickle  is handy for limiting single applications upload and download speeds,  what it does is starts the application in a speed limited sandbox.

**In short**

   trickle  is a portable lightweight userspace bandwidth shaper. It can run in  collaborative mode (together with trickled) or in stand alone mode.
   trickle  works by taking advantage of the unix loader preloading. Essentially it  provides, to the application, a new version of the functionality that  is required to send and receive data through sockets. It then limits  traffic based on delaying the sending and receiving of data over a  socket. trickle runs entirely in userspace and does not require root  privileges.

**Here are a few examples:**

**wget example that limits the download speed to 30 KB/s**
trickle -d 30 wget [http://somerandomdownloadsite.com/filetodownload](http://somerandomdownloadsite.com/filetodownload)

**Pidgin example that limits the upload/download speed of filetransfers**
trickle -u 30 -d 30 pidgin

**Firefox Example that limits download/upload browsing speed as well as file transfer speed:**
trickle -d 30 -u 30 firefox

As  you see above the -d operator means download speed and 30 is the KB/s  that is specified and can be changed to whatever you choose, the -u  operator is the upload speed in KB/s


found one!

---

### Post by thomas144 on 2010-08-17
My first post in the thread says:

> Hi there, I'm looking for a good bandwidth manager to install on Ubuntu.  I believe that's what it's called. I tried installing Trickle (sudo  apt-get install trickle), but it doesn't "support executables utilizing  kqueue(2). Does not support statically linked executables." This means  that it doesn't work with Firefox, but it works with wget. Does anyone  know of a good program? Preferably, it would be a graphical program, but  I can use the command line, too.
Is there another bandwidth manager?

---

### Post by wannabegeek on 2010-08-17
I think what you want is QoS--->Quality of Service

I recently bought a new Cisco wifi router and changed firmware to dd-wrt. QoS is an option.
I set it up but haven't gone through the lengths to confirm its operation and trouble shoot. Not entirely sure it is working ....

That is what you are asking for I believe...if you decide to try this method, post back as I am  curious
about tweaking it and will try to offer help if I can.

wbg

---

### Post by thomas144 on 2010-09-01
I don't really need a bandwidth manager. I already tried Trickle, and I don't think there are any good options...yet.

---

### Post by RegPerrin on 2010-10-06
KNemo is a good bandwidth monitor, but not a bandwidth controller

---

### Post by Sepiraph on 2010-10-07
> **thomas144 said:**
> Thanks for offering your help, but it's not really what I was looking for. I'm looking for a program to control the usage of my bandwidth, not just monitor it.

I don't think there are programs that does that, the closet you can do is to use something like ntop or mrtg to actively monitor the usage and I think you can use them (may need plugin) to generate alert when you reach a certain level.

---

### Post by r m h on 2010-10-07
Would ip_relay or NetSplitter meet your needs?

See the following:
[http://www.linuxlinks.com/Software/Networking/Tools/Proxy/]("http://www.linuxlinks.com/Software/Networking/Tools/Proxy/")
and
[http://www.linuxlinks.com/Software/Networking/Tools/Bandwidth/]("http://www.linuxlinks.com/Software/Networking/Tools/Bandwidth/")

Today I started looking for the same thing, but I also want to be able to analyze my incoming and outgoing traffic by machine, ports, and application if possible so I can be able to discover malware that may be active in my LAN so I can shut them down.

---

