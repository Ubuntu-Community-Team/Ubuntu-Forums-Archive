---
title: "Ssh x2x ???"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by Rim3nX on 2011-03-04
I have two computers: desktop (10.04) and laptop (10.10), and I have a router Huawei HG520c.
Desktop is connected to routers LAN1 socket (via UTP cable).
Laptop is connected to router on Wireless Lan.
Computers can share files with no problem (over Giver for example) so they work nicely as LAN.
I want to control laptop from desktops keyboard and mouse.
I found that it could be done with x2x and ssh server.
So I've installed openssh-sever and x2x on both.
I'm kinda bad with ssh protocol, haven't used it much, so really have no idea how it works.
Any way... this is how things are setup on computers:
user on laptop is "x" (simple as that) host is "xlt".
On desktop user is "rimen", host is "xhome".

I'm not sure, but I think, for me to connect from desktop to laptop and control it, I must use this:
ssh -XC rimen@xlt x2x -west -to :0.0

Well, it does the job, but it asks me for password. At first I thought it asks for password of laptops user... obviously...
"Permission denied, please try again." seas otherwise.
Witch password do I have to input to make this ssh connection to work ???
I would like someone to better explain me how this whole thing works, and what are those -XC  and :0.0 parts of command.
I still can't connect, any help would be welcome.
Thanks.

---

### Post by mikewhatever on 2011-03-04
-XC are ssh options, -X is for X forwarding, and -C is for compression. The latter may be useful when communicating over the internet, but will only slow things down on a 100Mbps LAN or 54Mbps wLAN. Look and 'man ssh' for more options.
About the password, make sure you can ssh to the laptop first.

ssh rimen@xlt

alternatively,

ssh rimen@internalIPaddress (for example: 192.168.1.100)

---

### Post by Rim3nX on 2011-03-05
> **mikewhatever said:**
> 
About the password, make sure you can ssh to the laptop first.

ssh rimen@xlt

alternatively,

ssh rimen@internalIPaddress (for example: 192.168.1.100)

Well I did "ssh rimen@xlt" and it asks for password.
I've entered the one password witch I enter each time on xlt when I use sudo, you know, that one and only password.
And for that I get "Permission denied, please try again." So ssh connection, (to me it seams) works, but wtf is with password wrong, is there some other password that I have to enter ??

---

### Post by Rim3nX on 2011-03-05
I think it might have something to do with router.
Since IP address of desktop is in eth0, laptops is in wlan0, that might be a problem I guess, or not ???

---

### Post by Rim3nX on 2011-03-05
This is what I'm doing all the time !!!
And another thing... seams like ssh from xlt didn't work with command like "ssh x@xhome", until I added xhomes ip address to /etc/hosts
cmn people, I'm dying here of ignorance !!!
HELP !!!

---

### Post by mikewhatever on 2011-03-05
```
user on laptop is "x" (simple as that) host is "xlt".
On desktop user is "rimen", host is "xhome".

```

To connect to the laptop, use ssh x@xlt and the password for x.
To connect to the desktop, use ssh rimen@xhome and the password for rimen.

---

### Post by Rim3nX on 2011-03-05
> **mikewhatever said:**
> 
To connect to the laptop, use ssh x@xlt and the password for x.
To connect to the desktop, use ssh rimen@xhome and the password for rimen.

Been there, done that.
Same s**t happens.
```
$ ssh x@xlt
x@xlt's password: 
Permission denied, please try again.

```

BTW, users password is my regular one on both machines, so I'm not mistaking it, that might cross someones mind.

---

