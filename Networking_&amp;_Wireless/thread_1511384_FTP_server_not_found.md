---
title: "FTP server not found"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by cj.surrusco on 2010-06-16
I set up a FTP server on my desktop so that I could access my files from computers on other networks. I used vsftpd to set it up and I have it protected so that a user name and password have to be entered to access it. 

I am able to access it from other computers on the network by connecting to the local IP ([ftp://192.168.1.101](ftp://192.168.1.101)), but when I try to connect from other networks using my external IP (ftp:// *my IP*), it says that it is not found.

I'm pretty sure that I have to open some ports in my router configuration, but I'm not sure what settings to use or which ports exactly to open.

I appreciate any tips or help on getting this working.

Thanks.

---

### Post by new_tolinux on 2010-06-16
Long time ago since I played with an FTP-server, but this is what I remember:
Port 20+21 need to be opened.
There is some range of ports which can be used for passive transfers, but that's depending on which FTP-server you're using. That range also need to be opened. I had mine on Windows and as I remember the range was somewhere in the 6000-7000's.

Probably needless to mention that the opened ports should all be forwarded to the machine running the FTP server.

---

### Post by cj.surrusco on 2010-06-16
Thanks a lot for the info.

What mode should I forward those different ports in? My router offers UDP, TCP, and both.

EDIT: Opening both ports 20 and 21 using TCP did the trick.

Thanks for the help.

---

### Post by djeikyb on 2010-06-16
There should be a conf file where you can specify what folders to share, maybe? What ftp server are you running?

---

### Post by new_tolinux on 2010-06-16
> **cj.surrusco said:**
> Thanks a lot for the info.

What mode should I forward those different ports in? My router offers UDP, TCP, and both.

EDIT: Opening both ports 20 and 21 using TCP did the trick.

Thanks for the help.

Nice that you've got it to work, I was just about to answer that I really don't know if I forwarded TCP, UDP or both.
When I clicked the quote-button I saw you edited your message.

---

### Post by cj.surrusco on 2010-06-16
That comment was my fault. It was an isolated Firefox problem. Once I opened the server in nautilus, I was able to navigate freely.

---

### Post by cj.surrusco on 2010-06-16
> **new_tolinux said:**
> Nice that you've got it to work, I was just about to answer that I really don't know if I forwarded TCP, UDP or both.
When I clicked the quote-button I saw you edited your message.

Yeah, most how-to's on setting up FTP servers fail to mention that you have to open ports at all, let alone which type.

---

### Post by new_tolinux on 2010-06-16
> **cj.surrusco said:**
> Yeah, most how-to's on setting up FTP servers fail to mention that you have to open ports at all, let alone which type.
That's partly right.
Most how-to's I found back then mentioned to open ports, they only forgot port 20. But appearently the internet has changed as you didn't find a correct how-to.

Although I have to say that I used filezilla back then, and the FAQ/Manual was pretty clear on opening ports, the only thing they couldn't explain was how to do it (because every router is different). What I had to find out myself was the range of passive ports, which had some default values, but could be changed. 20/21 could also be changed as I remember, but since it had to work out-of-the-box for most users of that server I didn't change that.

---

### Post by cj.surrusco on 2010-06-17
Which ports should I open for passive transfers? Should I use port triggering to open those certain ports when port 21 is used?

---

### Post by new_tolinux on 2010-06-17
> **cj.surrusco said:**
> Which ports should I open for passive transfers? Should I use port triggering to open those certain ports when port 21 is used?
As far as I know that can be different for different FTP-software, so no "one solution fits all".
The documentation of the FTP-software you are using should cover which ports are used by default, but if you'd like to change it you should at least have a look on which ports aren't used yet (at least nothing under port 1000 since the important system-processes are using ports there and you don't want those to be accessed from everywhere around the world ;))
Besides that, for example, if you are running some process on an alternate port, say port 1234 for ssh, that port can't be in the passive port range that your FTP-server is using.
In general, every port can only be used by 1 program. There probably are some exceptions to that, but I'm not going to cover those.

---

### Post by cj.surrusco on 2010-06-17
Thanks for the info

Okay, so I set the FTP daemon to use passive mode, and set the ports. One more question: Should I simply forward the ports? If so, which mode (TCP, UDP, Both).
 
Or should I set up port triggering?

---

### Post by new_tolinux on 2010-06-18
I don't really remember that.
I always had port triggering disabled on my router, because I don't like hardware or software doing the thinking for me ;)
Especially some Windows configurations (didn't run linux at all back then) had the nasty habit of opening a bunch of ports of which it wasn't clear to me why they should be open at all, so the decision to disable it in my router was made quite easy (and very soon).

Sorry that I can't be of much more help.... it's almost 5 years ago yet that I did setup the FTP.

---

### Post by cj.surrusco on 2010-06-18
Thanks anyway. 

Everything seems to be working fine with the ports forwarded anyway.

---

