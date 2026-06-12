---
title: "VPN connection"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by peteho1990 on 2009-09-23
Hi.
Recently started at Newcastle Uni. I've been told I need to connect to a VPN in order to access the internet and network (Due to security reasons apparently!). But, I can't :(
I've tried installing network-manager-pptp with no luck, downloading it on a public PC and then transferring to my personal one via a USB thumb, due to not being able to access the internet on my machine.
I have also tried to get it to work using the method here; [http://ubuntuforums.org/showthread.php?t=1136020](http://ubuntuforums.org/showthread.php?t=1136020)
But, I cannot get passed step one. I am unable to edit " /etc/ppp/chap-secrets "
Also, I cannot simply add VPN PPTP connection, within Add/Remove programs, due to not having an internet connection.
Anywhere I can download the appropriate package/install wizard to establish a VPN?
Also, under Network connections, under the VPN tab, I am unable to simply click on the add button, which is why I need pptp I think.
I would appreciate any help, and preferrably not in code, as that is jargon to me.
Running Jaunty 9.04.
Thanks.

---

### Post by sedawk on 2009-09-23
To edit /etc/ppp/chap-secrets you need to get temporary root
access the ubuntu way:
```

sudo vi /etc/ppp/chap-secrets

```
should do the trick.

Long journey, small step ...

---

### Post by peteho1990 on 2009-09-24
I can't open the file /etc/ppp/chap-secrets. So where would I have to write that?
I really don't want to have to return to Windows, it's a nightmare!
Thanks

---

### Post by chris1950 on 2009-09-24
Go to Applications > Accessories > Terminal. when the terminal opens copy and paste this code  
sudo vi /etc/ppp/chap-secrets  (hit enter - it will ake you for your password - enter the password then press enter)
You should now be able to edit the file.:)

---

### Post by peteho1990 on 2009-09-25
I followed that, but still could not access the file. Apparently my machine can't recognise the file type?
Any other suggestions please?
This is getting more and more frustrating......:(

---

### Post by peteho1990 on 2009-09-28
Finally worked out how to fix this problem. :):)
I'll try and explain what I did. I needed to install the network-manager-pptp package in order to set up a VPN connection.
I went to: System, Admin, Synaptic Package Manager. 
And then used quick search, entering "pptp". 
This brought up a list of 6 available packages. 
Find "pptp-linux" and "network manager pptp"
Right click on each one and mark for installation
Once marked for installation, go to file, and generate downlaod script
This will give a website, go to this website and download the right thing.

Alternatively, rather than following that, the two web pages I needed were: 
[http://gb.archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-pptp/network-manager-pptp_0.7.1~rc4.20090316+bzr23-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/n/network-manager-pptp/network-manager-pptp_0.7.1~rc4.20090316+bzr23-0ubuntu3_i386.deb) and
[http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pptp-linux/pptp-linux_1.7.2-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pptp-linux/pptp-linux_1.7.2-1_i386.deb)

But this may be different if it's a slightly different problem.
As I didn't have an internet connection, as I need to go through the Uni VPN, I couldn't download these straight away, so transferred them on to my PC using a USB Thumb.

Just thought I'd share my finds!
Glad I didn't have to resort to Windows :)

---

