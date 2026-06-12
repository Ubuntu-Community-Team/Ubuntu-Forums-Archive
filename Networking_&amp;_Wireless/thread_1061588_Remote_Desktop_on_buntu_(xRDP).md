---
title: "Remote Desktop on *buntu (xRDP)"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-02-05
Remote Desktop on Linux



A while ago I made [a thread about using remote desktop to connect to Vista Home Premium and Linux](ubuntuforums.org/showthread.php?t=439733), I was told to use VNC, but I keep getting connection closed and VNC is really slow, even with low settings, where as remote desktop is  fast and I can use it off my phone and see the whole screen and not have to zoom in to read text, where with VNC you have to zoom in on text (which makes it slower) and then I have cant see the whole screen.



I have found a way to make an RDP server on Vista ([link](http://www.unet.fi/fransblog/2007/08/30/enable-remote-desktop-connection-on-vista-home-premium/) and for Linux I heard about xRDP, but when I connect, the screen the attachment comes up. How do I connect?


When I connect I get the screenshot shown in the attachment, which option do I pick.

Also when I connect from outside my house from the internet by entering my IP Adress (I forwarded the port) it doesn't connect, but in Windows Vista Home Premium it does (Same computer, dual boot). I need to be able to access this machine from outside my network...

---

### Post by superprash2003 on 2009-02-06
does windows and ubuntu get the same local ip address from router?? 192.168.1.x or 192.168.0.x ??have you done the necessary port forwarding??

---

### Post by RealG187 on 2009-02-06
I am pretty sure they have the same IP address on my router, as my Router assigns IP adresses based on the MAC address, and I use the same wireless adapter in Windows that I do in Ubuntu.

I goto my Router's IP in an internet browser and right now it says the machine I am on is the only machine connected, and below it it says all the ports I have forwarded, including remote desktop.

---

### Post by superprash2003 on 2009-02-07
you could use this online port scanner to see if the required port is open or not [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by RealG187 on 2009-02-13
I found [this]("http://www.thinstuff.com/downloads-support/downloads/"), it's a .sh file, I am not sure how to install that. What would be better, that or XRDP? VNC is really slow and I can't wait to use somethine better (ie RDP)

---

### Post by RealG187 on 2009-02-16
There's got to be a way to do this...

---

### Post by RealG187 on 2009-05-01
Okay I just found out about ICA, which is supposed to be better than RDP and work on other platformms. In fact RDP is based on it.

[http://web.archive.org/web/20071017181738/http://purenetworking.net/RDPvsICA.htm](http://web.archive.org/web/20071017181738/http://purenetworking.net/RDPvsICA.htm)

I use VNC but the performance isn't as good as RDP, mainly on my phone. On that page it says Linux and Windows CE are supported (my Phone has Windows Mobile 6.1 professional.)

Does the remote desktop viewer that comes with Windows Mobile/Pocket PC connect to ICA? If so could I setup ICA on my Ubuntu computer and then use it to connect to my phone?

---

### Post by svtdragon on 2010-11-30
Just wanted to say for anyone who happens to google this that xrdp is the way to go, and that the first option in your attachment is the one to pick.  

To verify, port 3389 is the RDP port to forward.  

You may also get some use out of a service like DynDNS or NoIP if external connections are what you want.  

You also may be able to better diagnose your issue by seeing if any arbitrary connection to your linux system works.  Try setting up an SSH server (which will require forwarding port 22).  If that works, you can set up port forwarding over SSH instead of forwarding the RDP port directly.  (If you're interested in that, I have it set up and working; let me know.)

---

### Post by RealG187 on 2010-11-30
I haven't used Linux in a while and still need to get used to it again. Right now I am playing around in VMs (But need more space on my laptop for my VMs so I am running them off a USB HD which is not always plugged into this computer).

Since I am using VMs I can RDP into the host, but it still would be nice to RDP to the VM and good to know how to for my non-VM Linux installs. Would RDPing directly into the VM have better performance then connecting to the host and doing stuff that way?

I still need to use Windows as a host until I get my game working in VM Ware or Linux directly...

---

